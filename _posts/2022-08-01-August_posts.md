---
layout: post
title:  August Summary
date: '2022-08-01'
categories: summary
tags: writeup
---

Alright, monthly goals are to do the following!
- Clean survey data to prepare for modeling (ASAP)
- Carry out modeling project (by end of month)

We also have some secondary goals - these are more dependent on when I get the edits back, but
- Incorporate Steven's edits in the proposal and submit
- Incorporate Steven's edits in the paper and finish Draft 2

**Monday, August 1st**

After a lot (a _lot_) of edits and revisions to the code, I managed to clean the (very messy) temperature files from all survey legs. This typically required re-doing the read-in process - a common issue was that my code would successfully read in the file, but would leave me with NAs in a column, as the file delimiters and formats were pretty wildly different.

Work has been done both in [2_4_fixing_temp_files.Rmd](https://raw.githubusercontent.com/afcoyle/hemat_modeling/main/scripts/2_4_fixing_temp_files.Rmd?token=GHSAT0AAAAAABU6MQPJ7PGD6T3SJAXBETQEYXEQYGQ) and in [2_5_merging_temperature_data.Rmd](https://raw.githubusercontent.com/afcoyle/hemat_modeling/main/scripts/2_5_merging_temperature_data.Rmd?token=GHSAT0AAAAAABU6MQPJC4BHPYHXRTYMYXGQYXEQYAQ), with a few in my R script containing my functions.

I also accomplished the following steps on this:

- Edited some Tidbit filenames to be consistent with the Tidbit names in the pot data file (though since there's generally more variance _within_ names in the pot data file, there's still a lot of work to do for consistency here)

- Downloaded the HOBOware software (required for viewing .hobo files and converting them to .csv files), and used it to obtain the temperature data for the 2019 RKC Leg 2 survey data (available only as .hobo files)

- Moved all processes in these scripts to an output/ folder so we aren't directly editing the data

- Checked for NAs, blanks, incorrect values/formats in the data

Tasks still remaining:
- Check to see we aren't missing any Tidbits

- Get the pot data file (../data/ADFG_SE_AK_pot_surveys/Pot_Set_Data_for_Tanner_and_RKC_surveys.csv) cleaned up. Notably, this is going to involve moving a _lot_ of comments into the Tidbits data column - there are some years in which all data on Tidbit matching took place in this column. It'll be a huge, huge pain, but hey!

**Tuesday, August 2nd**

Spent today working on the pot data file (mentioned above), and successfully moved all comments describing Tidbits into the data frame! Per usual, tons of different formatting methods were used originally (new bumper sticker: standardize your data, make a future researcher happy), but at this point, it should all now be fixed!

Four years (2005-2008) had either all or nearly all Tidbit IDs entered into the comments column, and 2009 had a number that were there as well. In other years, there were only a few odd cases to deal with.

I also spent a good portion of the day accomplishing what I _thought_ I did yesterday - completing the read-in of all Tidbit temperature files. Turns out, the formatting on a few files wasn't quite right, and my function was ignoring the files. 

Finally, I worked on double-checking that all files read in correctly. A number of different time formats were used, and I was worried that either a) the AM/PM component was being ignored within some files, leading to incorrect times, or b) times were rounding oddly. I was correct with b) in a few cases, but fixed the issues and all is now well!

Next goal: merge the pot set dataframe with the huge Tidbit temperature dataframe. Since both files are quite large (around 20,000 lines and 400,000 lines, respectively), I think it likely makes the most sense to do this on a year-by-year basis. But hey, might as well give merging the whole thing at once a shot and see if it takes an unreal amount of time!

**Wednesday, August 3rd**

Took almost the full day off today - physically wiped out from the monkeypox vaccine and didn't wake up until 2pm! Still, managed to successfully merge all the temperature and Tidbit data! Set up a neat little for loop to accomplish this in R. 

One concern: it looks like for a few surveys (2016 and 2019 RKC surveys in particular, potentially some others), the datetimes may not have read in correctly. I'm getting anomalously high average temps (10C and above, with one up to 14C). This _could_ be natural, but it definitely sets off some red flags. I think non-submerged datetimes may be present within these values. Next goal: take a closer look at them and see what's up!

**Thursday, August 4th**

Three solid accomplishments today! First, I went back and fixed up something I forgot yesterday! I've got these two dataframes - one with all the pot data, and one with all the tidbit data. I had merged them by Tidbit ID (and then filtered by haul times to ensure I only had temperatures for when the pot was in the water). However, I forgot that the pot data sometimes had odd names in Tidbit ID! For example, the same Tidbit might be called 22, 2207, or 22-07. I spent a good portion of the day making that tidbit_id column in the pot data consistent with the names in the tidbit data, thus improving the join and getting more data.

Next, I took a peek at the anomalously high average temperatures for some surveys, and fixed them! The issue was a failure to read in AM/PM times for certain _legs_ of the survey (specifically, legs that were saved in a .csv format). Spent half an hour looking for the error, and then fixed it in like half a line. Ain't that how it always goes?

I also examined some additional anomalously high average temperatures, and filtered out any pot sets that looked iffy. "Iffy" to me meant the following:

- Pots with a set time or haul time of 0:00:00 (likely to be missing true time info)
- Pots in which the maximum temperature was 3+ degrees above the minimum temp over the course of the deployment

I also took a long look at any days that were overrepresented in the highest temperatures. I specifically examined the temperature pattern - did it get colder after deployment? did it warm up after being hauled? - along with the NOAA weather data from that time period and area. One I decided to eliminate (2011 Tanner crab, Leg 1, pots set on 10-07).

Finally, I took a peek at any remaining elevated temperatures and eliminated if they were suspicious!

The next accomplishment: actually joining the crab data with the merged pot/temperature data! We've got about 150,000 crab that were examined for bitter crab syndrome AND have temperature data! 

Next steps:

- Clean up the data a bit
- Start exploring the data! Look at temp by location, by year, etc.

**Friday, August 5th**

Didn't do any lab work today - it was dedicated entirely to merch!

**Monday, August 8th**
Spent the day exploring the pot data! Didn't find anything particularly interesting honestly, though I did locate some errors in the latitude/longitude values! It's just a few rows, but don't think it's worth manually fixing those - we'll just remove them entirely. 

**Thursday, August 11th**
Today I finished up exploring the pot data! Everything looks good so far, and spotted some potentially interesting relationships (keep my eye on temp vs. date, but temp vs. latitude should be fine, for instance). Goal for tomorrow: clean up the crab data!

**Monday, August 22nd**
First update in a while - my bad! Good news - I was able to successfully build a model!! Key was using glmmTMB() instead of glmer(). Two big benefits to this - first, I could build the model in a single step instead of using update() to add each term! Second, when I ran dredge(), all the models converged, while I had a ton of non-convergence with the glmer() model. One complicating factor - VIFs are a bit harder to get, as vif() isn't compatible. However, check_collinearity() worked great!

Next step: run model diagnostics to see if everything looks nice and neat!

**Tuesday, August 23rd**
Worked on some model diagnostics, mostly using the DHARMa package. Things look pretty good - my Q-Q plot looks lovely (on my full model), and I made some neat little plots of effects using plot(predictorEffect()). Summary is:
- Strong effect from shell condition, with new-shell crab most vulnerable to BCS
- Strong effect from temperature, with warmer temps having higher BCS rates
- Strong effect from CW, with bigger crab being more likely to have BCS
- Medium effect from Black Mat, with black mat-infected crab less likely to have BCS
- Marginal effect from day, with later days being less likely to have BCS
- Marginal effect from latitude, with higher latitudes more likely to have BCS
- No real effect from leg condition
- Marginal effect from depth

I also started on my second model, which focuses in on female crabs! I had to do some data cleaning prior to running my model (all that work is in my model-running script, rather than where it likely should be - in the data-cleaning script). I combined a few egg-related measurements into a single column, removed marginally-relevant categories (eyed vs. uneyed eggs, since there were only 3 eyed), etc. I then ran a new model on female-relevant variables, which are as follows:

_Same as All Crabs model_
- Shell condition
- Black Mat
- Leg Condition
- CW
- Temperature
- Depth
- Latitude
- Julian day

_New to Female model_
- Egg development
- Egg percent

_Not present in Female model, was in All Crabs model_
- Sex

Ran an initial set of models to get the AIC of each variable separately (formula: Bitter ~ variable + (1\|Site) + (1\|Year)). Got the following results. Right column is the AIC of the model including the variable minus the AIC of the null model (smaller number = bigger improvement over null)

Alright, here's the results!

| Variable        | AIC_vs_null |
|-----------------|-------------|
| Shell.Condition | -3436       |
| Egg Percent     | -558        |
| Egg Development | -163        |
| Black Mat       | -148        |
| Leg Condition   | -39         |
| CW              | -37         |
| Temp            | -9          |
| Depth           | -6          |
| Latitude        | -3          |
| Julian Day      | 2           |


Next steps: check that all our diagnostics are legit, get some advice on additional diagnostics, and run the female-specific model! Then later, run the male-specific model (where we'll calculate maturity using chela height).

**Wednesday, August 24th**
Had a chat with Julia Indivero, who knows a whole lot more than me about modeling! She took a peek at my model. Good news - everything looks pretty fine! There's a few additional diagnostics to be run - I'll just post my notes from our chat below:

- Plot errors against y-hats
- What is outlier test and KS test?
- Use function predict() on GLMM object. Predicts bitter values based on model parameters. Predictive posterior
    - predict.glmmTMB()
-ggeffects package
- vizreg package
- Ensure errors look normally distributed
- Check that glmmTMB() spits out an error if it doesn't converge
- Use hatvalues(model) to look for leverage points
- Do predictions for each separately, see if any are fundamentally not giving me aroudn the right number of bitter/non-bitter
- Also compare weighted models (top 4 or top 8) to single models! Factor in number of parameters (less is better)
- Should re-run diagnostics that I previously ran on my full model on each of my best models
    

**Friday, August 26th**
Spent most of yesterday writing up the methods section of the modeling paper! Got to a good place with it - included all info from the surveys, though relatively little from the modeling process (after all, I still need to finish the modeling!). I also ran the female-specific model AND wrote a model for male crabs

I spent today cleaning all the data for my male crab model! I also figured that hey, as long as I've got maturity data on males (and already had maturity data on females) why not run a model on all crabs that incorporates maturity? Not sure how useful it'll be - almost all my female crabs are mature, with only ~75 immatures, so it might be similar to the male specific model. But I went ahead and wrote that too, just for fun! I also ran my male-specific crabs model! Like usual, dredge() is taking a long time, so we'll see the results later!

**Monday, August 29**
Hmm, running into some issues. Started running diagnostics, and accidentally introduced a line that crashed R (at least, the instance running on Raven) and had to re-start the whole model run. 

**Tuesday, August 30**
Spent the day setting up Mox to run this too! Since it takes about a day to run dredge() on a model when using Raven, and I've got four different models, I figured I'd run models in parallel! Installed all necessary libraries, which required building a new RStudio singularity on Mox, and started running the female model while I run the All Crabs model on Raven!