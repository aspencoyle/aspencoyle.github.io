---
layout: post
title:  July Summary
date: '2022-07-12'
categories: summary
tags: writeup
---

I took the first week of July off - headed back to Ohio for Pop's funeral - but now it's back to daily notebook posts! Goal is to do the following:
- Incorporate edits on proposal (ASAP)
- Finish first draft of paper (ASAP)
- Clean survey data to prepare for modeling (by end of month)

**Monday, July 11th**

Spent the day examining Chelsea's edits to my proposal! There's a lot of varying degrees of difficulty. Focused on the easy ones for today. I tend to not have the easiest time incorporating edits (I get stressed out and avoid them), so this might take longer than it should. Still, trying to push myself to get em back quick!

**Tuesday, July 12th**
 
Another day of proposal editing! Got to a fairly good place - hopefully should have them all finished by tomorrow. Need to read some papers and do some major reorganizing (particularly the methods section) and then rewrite my opening paragraph or two, and then should be set for another round of edits! Think I'll send em to Steven next and get his feedback, then get final approval from both him and Chelsea.

**Wednesday, July 13th**

Continued on proposal editing, it's going slower than anticipated. The rewrites are pretty major, and reorganizing a doc this big is slow going. Ah well, slow and steady.

**Thursday, July 14th**

Shit shit shit. Found a major error in my analysis. Good news: it's small and easily fixable, though it may take a while. Basically, when running DESeq2 for the *C. bairdi* transcriptome on *Control Day 2 vs. Control Day 17*, I accidentally ran it on *Control Day 0 vs. Control Day 17*! Luckily, I don't really consider *Control Day 2 vs. Control Day 17* to be a major part of my experiment, it's pretty marginal and only factors in when talking about changes over time. Still, I'll re-run it and see how things change.

I also didn't originally run *Control Day 2 vs. Control Day 17* for the *Hematodinium* transcriptome, so I'll add that one in to my analysis to, now that I'm focusing more on time.

**Tuesday, July 26th**

Alright, I've been slacking off on my notebook posts, but I have not been slacking off on my work! Updated status:

- Issue mentioned above completely fixed, although it took a few days
- Incorporated all edits from proposal
- Finished first draft of paper

Project for the last two days has been moving on to modeling _Hematodinium_ using the ADF&G data collected from SE Alaska over the past few decades. But to do that, first I need to extract all temperature data. And to do that, I need to sort out the _extremely_ complicated file systems that they've been placed in. Every year has a completely different format and often different file types. 

Good news: I've accomplished that! Progress can be seen at https://raw.githubusercontent.com/afcoyle/hemat_modeling/main/scripts/2_3_fixing_temp_file_structure.ipynb?token=GHSAT0AAAAAABU6MQPITO2FYGIBYMXMIPXYYXEQW6A

At this point, I've got raw folders with .txt (or .csv) files with the temperatures measured by each data logger. New task is as follows:

First, I need to amalgamate the data logger info together. Then, I need to connect the info for each data logger to the info for each pot, and extract only the time in which the data logger was set in the pot and the pot was at the bottom (data loggers ran continuously). I then need to merge the data logger temp and pot info

Once I've accomplished that, which will be v v tricky, I can merge the info on the temp experienced by each pot with our crab data, which will give us the temp experienced by the crab at its time of capture. We can then explore that data a bit to give us the average temp at each location within years, between years, etc. Then we can finally get started with our modeling!

**Wednesday, July 27th**

I've started on the task mentioned above! I've managed to do connect the info for each data logger to the info for each pot, and extract the time where the data logger was in the pot + the pot was at the bottom. I even managed to merge the data logger temp/pot info!

So far, I've only pulled it off for the 2005 data (and holy moly did that take a lot of work and a long script), but now that I've got the basic concept down, it should just take me a day or two to write a few functions to automatically perform the above for all.

Link to the file I used to sort out the process: https://raw.githubusercontent.com/afcoyle/hemat_modeling/main/scripts/2_5_merging_temperature_data.Rmd?token=GHSAT0AAAAAABU6MQPIYWRTF4BV57TB6TUYYXEQXIQ

Link to the file I'm using to create the functions: https://raw.githubusercontent.com/afcoyle/hemat_modeling/main/scripts/hemat_modeling_functions.R?token=GHSAT0AAAAAABU6MQPIMFA3W2VEWFGCPB3OYXEQXQQ

Big obstacles are, as usual, disparities within the data. I'm having to write a good number of if/then statements to sort through edge cases (did they mess up the headers? Did they put it in a .xls file instead of a .txt file? Are there summary data files for the specific leg, or for the whole survey? and so on). But I guess that's what happens when you've got 15-odd years of data collection. Still, this is really driving in the importance of STANDARDIZING THINGS, PLEASE DO IT!!

**Thursday, July 28th**

Wild overestimation of how easy it'd be to read in all the data yesterday. The data is so incredibly heterogenous that I had to create a new script to just clean some of it up before reading it in. I also inadvertently edited some of the data files, so will have to run everything from scratch when I do it for real. Though I should do that anyways. Mental note to self: remember the basics, put any edited files in a separate output directory (though man, that basically means duplicating the full data directory). 

Anyways, corrected all weird cases in 2006, 2007, and 2008. Working through 2009 too, and making progress. But wowwww, this is really tricky

**Friday, July 29th**

Oh my god I can't believe I finished it! 1600 temperature files from 50+ survey legs in just about a billion formats, and I actually managed to successfully read in everything! Crazy happy with how it's gone!

Progress has been split between three files. Description as follows:

- [2_4_fixing_temp_files.Rmd](https://raw.githubusercontent.com/afcoyle/hemat_modeling/main/scripts/2_4_fixing_temp_files.Rmd?token=GHSAT0AAAAAABU6MQPJ7PGD6T3SJAXBETQEYXEQYGQ). In 2_3 I cleaned up the names within the file structure. This one is fixing the actual files so that I didn't need to have a million if/else statements within my functions to read in the data. It does things like standardizing formats, changing headers, removing lines with unnecessary info. This doesn't mean files are *fully* standardized after this point (there's still a lot of variance). Conceptually, think of this file as a first run-through to remove major snags.

- [2_5_merging_temperature_data.Rmd](https://raw.githubusercontent.com/afcoyle/hemat_modeling/main/scripts/2_5_merging_temperature_data.Rmd?token=GHSAT0AAAAAABU6MQPJC4BHPYHXRTYMYXGQYXEQYAQ). I really only used one line of this file - the one where I called my custom function, read_tidbit_data(). My basic process was to run the function on a year's worth of Tidbit data, see which entry it broke on, and then fix either the file or the function.

- [hemat_modeling_functions.R](https://raw.githubusercontent.com/afcoyle/hemat_modeling/main/scripts/hemat_modeling_functions.R?token=GHSAT0AAAAAABU6MQPIMFA3W2VEWFGCPB3OYXEQXQQ). This is where I built my functions. I had four functions built for this task total - the aforementioned read_tidbit_data(), and then three quick functions that just automated some of the repetitive tasks I had to do in 2_4_fixing_temp_files.Rmd. Those are fix_long_csvs(), fix_timetemp_comma(), and fix_longhead_txt().

However, while I successfully read all the data in, there's still quite a bit of work to do before we start merging it with our pot data. A few notable tasks:

- Change all data back to the original data, and move all processes in these scripts to an output/ folder where we modify the files (and filenames).

- Edit some of the filenames of the Tidbits to be consistent with the Tidbit names in the pot data file (ex: 20_07 vs. 2007)

- See if we can get the 2019 RKC Leg 2 survey data. I believe it was all stored as .jmp files, which we automatically removed in our script (of course we have backups of everything). We might try a 30-day trial download of some program that can access .jmp files

- Check to make sure we aren't missing any Tidbits

- Check for data entry errors (NAs, blanks, incorrect values/formats, etc.)

That's a fair amount of work to do so I can't get too excited. Still, made a ton of progress over this week and I'm really happy with it.
