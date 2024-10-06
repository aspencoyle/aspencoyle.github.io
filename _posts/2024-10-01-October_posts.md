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
- 


Goals for tomorrow:
- Continue rewriting modeling paper with Chelsea's edits
- Continue reading thru Linux book