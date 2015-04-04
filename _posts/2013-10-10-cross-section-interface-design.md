---
layout: post
title:  "Cross-Section Interface Design"
date:   2013-10-10 12:00:00
---

Readrz search engine uses several unique algorithms, which in combination provide a service that is not available anywhere else:

* Automatic detection of article topics – and search by these topics
* Summarization of multiple articles into a two-level tree
* Cross-sectional topic analysis of results

Cross-sectional topic analysis allows you to intersect two topics, and see the results that have both of them. It is the highest-level feature that is supported by all other lower-level functionality. It is the top of the pyramid of code, and it is the most useful feature – it is at the pinnacle of what Readrz can do.

Now, cross-sectional analysis user interface… here we come to the dark area. Of course, you can imagine how that can work. First, you choose one section. Second, you choose another section. And voila, you are looking at the cross-section. You can already do cross-sectional analysis at the current website, which uses two different menus allowing you to choose first and second sections.

Using two menus is not a good idea for cross-sectional user interface:

* It looks like a usual user-interface that you see on all websites, so it doesn’t provide any indication that Readrz can do something that other search engines can’t do
* There is no clear indication of a link between two menus – it is not obvious that the second one depends on selection in the first, and that they together produce a cross section of results

That’s why we’ve been working on a completely new user interface for cross-sectional search.

Recently, I have learnt about the [D3](http://d3js.org/) javascript library, which can do amazing things (data-driven display of information for the web). After that we have spent a few days experimenting and working on the ideas for a new design.

Here is how the home page will approximately look like (using [Bilevel Partition Sunburst](http://bl.ocks.org/mbostock/5944371)):

{% picture 20131010/cross-section-home.png %}
<br />

I am attaching some sketches that show how cross-sectional design will work (see below).

I am working hard on implementing it right now…

<!--more-->

This is how the search results will look like:

{% picture 20131010/cross-section-block.jpg %}
<br />

Home page showing all news and available sections:

{% picture 20131010/cross-section-page-1.jpg %}
<br />

User selects the “Business” section, and:

* Sees all results from the “Business” section
* Sees cross-sections available for intersecting with “Business”

{% picture 20131010/cross-section-page-2.jpg %}
<br />

Use selects “Countries” cross-section (to intersect with previously selected “Business”):

{% picture 20131010/cross-section-page-3.jpg %}
<br />
