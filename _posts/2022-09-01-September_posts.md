---
layout: post
title:  September Summary
date: '2022-09-01'
categories: summary
tags: writeup
---

Alright, monthly goals are to do the following!
- Get feedback on models, use proper diagnostics
- Interpret modeling results
- Finish methods of modeling paper, start on results/intro

We also have some secondary goals - these are more dependent on when I get the edits back, but
- Another round of edits on temperature analysis paper

**Thursday, September 1st**
Modeling: Crafted some nice loops to do some diagnostics. Found a persistent issue - when I use simulate() to check model accuracy and then compare the number of simulated BCS+ crab vs. the true number, it's persistently underestimating (by a little for the All Crabs model, by a lot for the Females model), or overestimating (for the Males model) the number of BCS+ crab. I'm not sure exactly what is going on here. Could be a minor issue with how random effects are specified in simulate(), could be a more major issue with the model in general. Either way, reached out to Julia + Sarah Converse for advice!

Modeling, pt 2: Ran a different set of diagnostics to check for zero-inflation and examine residuals. We have three full models (a fourth in progress): Male, Female, and All. dredge() returns ~10 models with weights > 0.01 for each full model. I checked each of those models (i.e. all models contributing to a final averaged model), and saw no issues whatsoever!

Modeling pt 3: In the process of crafting the aforementioned fourth model to examine maturity. Using dredge() for model selection at the moment, so it should hopefully be pretty speedy. Will follow it up by running diagnostics!

Temperature (gene expression) paper: Got back a bunch of edits from Pam (thanks, Pam!). Really helpful stuff, especially some discussion of citation suitability - shifted some citations to more recent/relevant research. Also found out some cool info - apparently there's two types of dinospores, but only one type is seen within an individual crab! 

Tomorrow's goal: Finish running the fourth model and run current diagnostics. At that point, I'll be waiting to hear back from the modeling experts for advice, so won't really have a clear avenue for progress. Will likely switch over to just working on paper edits. Maybe find a way to save models as files so I don't have to keep running dredge()! This has been an issue for a bit - I've been needing to re-dredge the model whenever my Mox RStudio session expires (or RStudio on Raven crashes). Likely an easy solution here, I just haven't bothered to find one yet.

**Wednesday, September 2nd**
Alright, I finished running the fourth model, and figured out a way to save models as files - just use saveRDS(). At this point, I now have four models total. To recap, those are:
- All crabs

- Female-specific: only females w/ egg data. Note: this includes females confirmed to be eggless, only excludes ones with incomplete data.

- Male-specific: only males w/ maturity data. Reminder: maturity is calculated via the chela height:carapace width ratio, so this is only crabs with chela height measured

- Maturity-specific: only crabs w/ maturity data

I want to make sure everything's running properly, and we have a long weekend (happy Labor Day!), so I'm re-running all four models from scratch. After that, I'll run diagnostics for each and confirm all is well. Then, it's on to paper edits + writing until we hear back from more expert modelers!