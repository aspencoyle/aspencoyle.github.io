---
layout: post
title:  June Summary
date: '2022-06-23'
categories: summary
tags: writeup
---

Alright, I've been working for a while without a post! That's because I've been nearly entirely focused on writing, which I haven't considered post-worthy. But after a lab meeting, Chris suggested making a quick summary of each day's work, so I can still track progress without writing up full posts! So that's what I'm doing!

**Thurs, June 23rd**

Got a good amount done today - generally focused on tightening up my methods, correcting word choices, etc. Remade my two WGCNA heatmaps (the ones I'll be using as figures in my paper) to make them more publication-worthy. Specific changes include:
    - Adding contig counts to eigengene labels
    - Removing title
    - Changing x-axis labels to be more publication-worthy
    - Rotating x-axis labels
    - Removing the "ME" prefix from all eigengene labels

I also moved the structure of the scripts around a bit - I moved the heatmap to the end of the script, and added some lines earlier to obtain contig counts.

Am currently a bit stuck - I did all this on Raven, and pushing it to GitHub is giving me fits. Posted it as a GitHub issue, hopefully it gets resolved!

**Friday, June 24th**

Made a figure I've been meaning to get done for a while, it describes the overall experiment! It's my new Figure 1. Just describes the timeline of temperatures each treatment group was exposed to, along with the sampling points. Purpose is to orient the reader with a simple diagram. Took the rest of the afternoon off for Pride!

**Monday, June 27th**

Sent my proposal along to Chelsea! Plus while it took a while, I resolved the issues around pushing from Raven. You can check out that process [here](https://github.com/RobertsLab/resources/issues/1487). Hint: secret was running Bash from an .Rmd file

I also made some changes to the heatmaps. Specifically, the Hematodinium heatmap - I removed a module that only had 5 contigs within it from the graph, as that's way too small of a module. Had to look through some code to see how it happened - looks like that's just where WGCNA put all the leftover contigs that didn't fit into a module.

New project that's underway is remaking the GO-MWU graphs. Goal is to make the phylogeny tree on the left-hand side match the text scaling on the right! Seems pretty tricky since it's all inside of a custom function from GOMWU, but fingers crossed I can get it quick.