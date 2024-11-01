---
layout: post
title:  October Summary
date: '2024-10-01'
categories: summary
tags: writeup
---

**Tuesday, October 1**

Another productive day! I started off by doing some FISH 250 stuff and updating some of the class sheets. After that, I moved on to my AFS chapter - I got my last set of edits back, so spent a good portion of the day chatting about that, reflecting on the edits, and updating the chapter accordingly. 

After that, time to move on to the modeling paper! Last time, I rewrote the whole abstract and intro. That meant it was time to move on to the methods! I did a bunch of work on the various comments in the methods, along with clearing up a number of the relatively quick and easy edits in the results and discussion. After that, I started tackling the bigger stuff. First on the list: remake my first figure. It really needs a total redo - the mapping package I used when I originally created it is just totally inadequate, and doesn't have the level of detail necessary. I decided to switch over to ggmap, following [this guide](https://www.youtube.com/watch?v=2k8O-Y_uiRU). However, in order to do so, I needed to install a ton of R packages - after all, I'm working off a fresh Linux install! Kept getting error after error, as I was missing a whole bunch of compilers. Had a bit of a cycle for a while - get an error installing the R package, go install the compiler, successfully install the package, get an error installing the next R package. 

I also got around to migrating my blog over from the Bittercrab Wordpress site to Substack. The Bittercrab site felt, unsurprisingly, very tied to bitter crab research, and I'm wanting to write about a wider array of topics. I came up with the name Aligned Reads, which I'm very proud of. Anyways, I spent a good chunk of time copying over my old blog posts, setting up the site, et cetera!

**Wednesday, October 2nd**

More progress! I spent today on a mix of logistical issues and thesis work.

Logistical issues:
- Sorted out funding for oSTEM trip
- Bought tickets for Amtrak (for oSTEM trip)
- Messaged Sam and Steven about getting First Aid training and the logistics thereof

Misc issues:
- Read through AFS chapter one more time

Thesis work:

Completely redid Figure 1! Previously, it was a frankly pretty crappy map showing Tanner crab infection rates by location. I redid it from scratch. Some changes:
- Used a much more detailed and beautiful Stadia map.
- Changed it from showing infection to showing survey (Tanner vs RKC survey)
- Added shapes to represent the two surveys
- Added a zoomed-out map in the corner showing Alaska more generally
- Put a box in the zoomed-out Alaska map showing the area this map focuses on
- Put a border around the zoomed-out map in the corner

This last step gave me absolute fits, as there's some weird buffering going on with draw_line() in the cowplot package - the coordinates (0,0) don't correspond to the bottom left corner, but instead to somewhere even further left and lower. But it wasn't being consistently interpreted by the mapping function, which was the absolute worst. So (forgive me Steven), I used Gimp to throw a dashed border around the corner map.

Anyways, productive day. Now off to my self-criticism session in which I'll be held accountable for drawing that border and thus violating reproducibility principles! If I don't post again, you know what happened to me.

**Thursday, October 3rd**

Well, Thursdays are my chaotic day - got two labs to TA back-to-back! Both went great, but since I was teaching from 8:30-4:30, I didn't have much time or energy to work on non-TAing stuff. Did accomplish a few things though!

- Sent in AFS chapter!!!!
- Set up appointment to get First Aid cert, and got it booked by Sam so no reimbursement things to deal with!
- Submitted TREQ request for reimbursement for oSTEM trip
- Graded all the late papers for FISH 250 Lab 1
- Made a teensy bit of progress reading through Linux book

**Friday, October 4th**

Filled in for Celeste's 250 lab today, so most of the day was that! Beyond that, I did the following:

- Sorted out a bunch of TREQ issues re: reimbursement
- Got in touch with TREQ to updat emy name in their system

**Sunday, October 6th**

Came in after a lil Quaker meeting to get some stuff done (also got an oyster knife from the meeting,
neat!). Good news: I ended up going through all of the paper edits from Chelsea!!! Yay, yippee, go Aspen!!!

**Monday, October 7th**

First lab meeting of the new quarter! Fun times and good vibes were had by all

Had office hours + lab meeting + FISH 250 meeting today, so haven't had a bunch of time.
However, I was able to get Figure 2 figured out!!! R was giving me fits, I couldn't for the life of me
figure out how to turn a model summary table into a regular table - none of the usual functions
are built for an object of class "summary.averaging". Turns out, I just had to create
the summary and then specify the full coefficient matrix (coefmat.full).

Anyways, once I did that, it was pretty simple to create the figure!

Current question: should I sort the predictor variables (y-axis) based on alphabetical order,
or based on absolute value of the estimated coefficient?

Update: figured that out, I'll base them on absolute value! I also decided to eliminate the intercept variable.

I continued on, and created plots for the male-specific and female-specific models! However, they'd look
cleaner if they were incorporated together as a single figure (with a shared axis?)

Also, cannot BELIEVE I never thought of working in the line "but why male models?" somewhere into my paper
when discussing the existence of my male-specific models. Ah well, even the most beautiful puns fade into dust

I also made some small changes to my website - added a link to Aligned Reads, etc.

**Tuesday, October 8th**

No work today - got a small medical procedure done on my toe. Between that and getting my 
COVID and flu shots Monday afternoon, I was out of commission all day. Still, a restful day in bed!
Movie recommendation of the day: "Los Tallos Amargos" (The Bitter Stems). Mid-50s Argentinean noir - 
delightfully tense and full of twists. Great way to spend the day (thanks, Scarecrow Video!)

**Wednesday, October 9th**

Spent the morning at the UW career fair, and the afternoon working on my graphs. Made some important changes, including the following:
- Got some feedback (thanks, Ariana!) and decided on two figures. Figure 2 would be just the general model coefficients, while Figure 3 would be the sex-specific models
- Created both those figures
- Edited figures so that significant coefficients were plotted in black, and non-significant coefficients in grey. 
- Played around some with sizing and captions
- Went through a piece Niamh is writing about my modeling research and made sure everything was shipshape
- Did some office hours and things of that nature

**Thursday, October 10th**

It's Thursday, so it's teaching lab day! Couldn't get much lab work done, of course. But I did get
through a few dozen pages of the Linux book (taking very detailed notes!) and scheduled a meeting with Steven for tomorrow!

Once I'd eaten my academic veggies, I also got started on another post for Aligned Reads on thinking like a scientist (and why it's not always great). 
Fun to write, really love being able to articulate these thoughts and turn them from something abstract to something more concrete.

**Friday, October 11th**

Spent most of the day in a First Aid class! Learned a bunch, and got my First Aid/CPR cert (required for TAing). 
Aside from that, had a meeting with Steven, and sent an email out establishing my plans to him and Chelsea. 

A brief summary

- Complete the modeling paper (get edits, do supplemental tables, submit)

- Complete the gene expression paper (correct edits, submit)

- Get both papers formatted for thesis

- Schedule presentation

- Present and graduate!

**Saturday, October 12th**

Finished my Aligned Reads post! Was v fun to write, a great time. I also started on some grading!

**Sunday, October 13th**

Well, it took a full day of work on a weekend, but I got done with all the grading for FISH 250 Lab 2 (which was only submtited a few days ago)!!!

I'm now in a much better place for the conference - already worked ahead some, so I can focus on getting things done for the rest of my academic life, packing, etc. Yay, yippee!

I also read over the thing from Niamh again and sent in some important edits! A productive day, even if it did end up taking one of the last precious sunny weekend days.

**Monday, October 14th**

Got some important notes back! First, from Chelsea - she won't be able to read my drafts until mid-November. Not optimal, but I'll wait to hear from Steven on how that impacts my timeline.

I also heard back from AFS w/r/t my chapter - they loved it, and said it was OK for me to share more widely! Very excited to do so if/when I choose. 

Most of today was meetings. DEI interview (not eligible for the position sadly) -> FISH 250 meeting -> lab meeting -> queer group meeting -> office hours -> SAFS Cafe! 

Didn't have a ton of time to do other tasks, but in my free time, I addressed a few of the edits on the sequencing paper and applied for a job (IOOS).

**Tuesday, October 15th**

Got a few more edits in on the sequencing paper. Also heard that Chelsea getting to my drafts in mid-November won't be an issue for me graduating this quarter! Yay! Still need to schedule the meeting though.

Aside from that, didn't get much today. 

This post is in honor of Felix, the best cat in the world. May he rest in peace - he will be missed by all <3

**Wednesday, October 16th**

Continued editing the sequencing paper! Redid several figures (the WGCNA module heatmaps), and reconsidered my notation for formatting crab IDs. New method is less intuitive for me specifically,
but more intuitive for paper readers, as they don't need to know the specific ways in which I identified samples. New module heatmaps look pretty great in my opinion!

I still need to redo the WGCNA module heatmaps for Hematodinium, but that should be fairly straightforward. Just need to keep doing what I did!

Ooh, one more thing - I fixed up Figure 2 of the modeling paper by removing the now-unnecessary title!

**Thursday, October 17th**

Thursday, so teaching day! In my spare time, I redid that WGCNA module heatmap. Looks good now! 

I think I need to redo my GO-MWU figures, especially for the individual modules, and get something that looks a bit fancier. Perhaps remove the dendrogram? Unsure!

I also addressed a few more comments on the expression paper. Slowly getting it there!

Tomorrow, I'm heading to oSTEM (leaving the house at like 6:15am, jeez!), so another busy weekend incoming.

It has now been: *12* days without a day off, and that'll hit at least 16 before I have the chance. Oof!

**Wednesday, October 23rd**

Well, I took some time off! I got a bad case of conference crud at oSTEM, and was totally wiped out for Monday and Tuesday. Started feeling better in the evening, 
and am at about 90% today. 

More in-depth thoughts on oSTEM incoming on Aligned Reads, but there were some elements I liked about it and others I really didn't (hint: I now own a Lockheed Martin "Love Is Love" tote bag)

Today's work: graded a ton of stuff for FISH 250, and also....FINISHED EDITING THE GENE SEQUENCING PAPER!!!! WOOOOOOOO!!!!! I also reformatted my whole USAJobs setup for the first time since starting
grad school - definitely some new stuff there - and applied to a job! 

I also started on formatting everything for my thesis! Got the first few pages done (the title page/copyright page), but now I gotta write the abstract! Probably won't be able to get to it tomorrow, but
maybe Friday!

**Thursday, October 24th**

Lab all day today! No real time to do anything else - went to the NOAA career thing during the break between my two labs.

After lab, I ended up working really late. Good news: I made a ton of progress on formatting for my thesis!!! I've got all the original stuff in there. Still to do:
- Write abstract for thesis
- Reread through everything to make sure it's accurate
- Create table of contents for figures
- Create table of contents for...tables
- Reformat table of contents to match actual pages after everything is accurate

**Friday, October 25th**

Made a ton of progress on things!!! Here's what I've accomplished:
- Literally everything on the thesis to-do list!!!! More detail:
- Wrote abstract, acknowledgements, dedication
- Created a table of contents for figures/tables
- Got table of contents to match actual pages
- Formatted figure numbering to be consistent
- Re-read through everything for accuracy, typos, etc.

First draft of the thesis is DONE!!!!!! Holy moly, really moving fast on this thing. Really happy with how fast I'm making progress. 

**Monday, October 28th**

Spent today in a bunch of meetings! FISH 250 meeting -> SAFS DEI working group meeting -> College of the Environment queer meetup -> office hours

In my spare time, I graded papers for FISH 250 (Lab 4)

**Tuesday, October 29th**

More grading for FISH 250. Also met with Lisa Crosson over at WDFW, former Roberts Lab member and developer of the qPCR assay for _Hematodinium_! Super neat conversation, lovely to 
catch up and hear how things were back in the day

**Wednesday, October 30th**

Fully caught up on FISH 250 grading! 

**Friday, October 31st**

Oooooh, spooky lab entry!!!

Had labs to teach all day today. Afterwards, 

Up next:
- Continue reading Linux book
- Schedule committee meeting
- Aligned Reads post on oSTEM
- Check through thesis formatting guidelines and ensure there's not anything I'm missing
- Check if there's any SAFS-specific formatting guidelines. I should be fine, as I'm basing my formatting off Grace's, but just in case!




