---
layout: post
title: "Google Codejam 2018"
author: "Landon"
math: true
---

I participated in Google Code Jam for the first time last year, making it through the first two rounds to the round of 3000. I looked at the problems in the round of 3000 last year, but didn't happen to have time to actually make a good effort at solving any of them.

This year BLAH BLAH BLAH

## Qualification Round

I glanced at the problems Friday night shortly after the release, but then got distracted playing a game of _Werewords_ with my roommates and finishing reading _Ready Player One_. On Saturday morning, I woke up early and looked at the problems again, intending to get enough points in the morning to guarantee moving on. I opened Cubic UFO first and started drawing some things out. I pretty quickly worked out the geometry as either a rectangle or a hexagon. The rectangle covered cases for \\(A \leq \sqrt{2} \\), and the hexagon covered larger cases. I worked out the specifics of the geometry after a half hour of struggling to remember how trig works, and coded up a quick binary search numerical solver, determining that binary search would be fast enough for the input spec. Unfortunately, the server was experiencing high load, and wouldn't accept my answer before I had to head out for the day.

I came back later in the day to find that my answer had *not* been accepted, and with very little to debug with, I decided to just do the first two problems and call it a day. Saving The Universe Again I quickly worked out a bucket system, where each shot was in a certain power bucket. The President could swap commands to move a shot down one bucket, halving its power. After that realization, the coding was a straightforward greedy simulation. When submitting that problem, I realized that my output line for Cubic UFO had been missing a colon after copying it over for the new problem, so I fixed that and resubmitted Cubic UFO. Since the server had been fixed, both solutions went through and were marked correct.

Now that the server was working again, I decided to go ahead and finish up the remaining two problems. I pretty quickly realized that Trouble Sort was flawed because it could not change the parity of any element, and coded up a solution with a dictionary of `{element value -> (count_even, count_odd)}`, which then subtracted from the same dictionary after sorting. The first time a count went negative on the second pass was the problem element. This isn't exactly what the problem was asking for, but as it turns out, the two are equivalent. I didn't even realize until reading over the problem again to write this blog post. Go figure.

For the final problem, Go, Gopher!, I decided that a clever predictive algorithm probably wasn't necessary (or if it was, I didn't care enough to code it). I started by squaring off the area into a low-aspect-ratio rectangle (in retrospect, I could have hard-coded 5x4 and 15x14). I first approached with an algorithm that would calculate the "expected value" of each interior cell of my target rectangle, then realized that I could carry this information over for each step, so I refactored to keep track of the expected value of each cell, commanding the gopher to dig at the best cell. This turned out to work just fine on pretty much the first try (modulo syntax errors and off-by-one errors), completing the contest. Final "actual time" per problem: it was about 55, 15, 15, and 30 mins for Cubic UFO, Saving The Universe Again, Trouble Sort, and Go, Gopher!, respectively. I felt pretty rusty at the beginning, but was feeling better by the end.