---
layout: post
title:  "Today's Optimisations"
date:   2013-10-24 12:00:00
---

Mid-morning update on today’s optimizations:

* Gzip compression for all interaction with server
  * Bandwidth reduction of 75%
  * Overall summary size down to 150Kb from 700Kb
  * Hence, speed of getting a response from server up 4 times
* Precalculation of search section combinations
  * Various section combinations results are precalculated (kept alive)
  * This applies to different time periods (selected at the top)
  * Summaries should on average now load in 2 seconds