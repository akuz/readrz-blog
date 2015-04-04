---
layout: post
title:  "What is Exploratory Search?"
date:   2012-03-08 12:00:00
---

When I explain to people what are we working on, I try not to mention the term 
"exploratory search" because almost no one has any idea about what it is. 
I'll try to collate some definitions and provide an example of a task 
when the exploratory search is needed.

### Overview

One of the definitions I like was given in the recent paper from FXPAL 
(Fuji Xerox Palo Alto Laboratory) titled 
<a href="http://www.fxpal.com/publications/FXPAL-PR-10-573.pdf">Interactive 
Information Seeking via Selective Application of Contextual Knowledge</a>:

<blockquote>Exploratory search is often characterized by an evolving information 
need and the likelihood that the information sought is distributed across multiple 
documents. Thus the goal of the search process is not to formulate the perfect 
query or to find the ideal document, but to collect information through a variety 
of means, and to combine the discovered information to achieve a coherent understanding 
of some topic.</blockquote>

A good outline of this paper was 
<a href="http://lifidea.wordpress.com/2011/09/22/fxpal-paper-on-exploratory-search/">posted by Jin Y. Kim</a>.

<!--more-->

In the <a href="http://en.wikipedia.org/wiki/Exploratory_search">Wikipedia article on exploratory search</a>, 
it is defined as:

<blockquote>Exploratory search is a specialization of information exploration 
which represents the activities carried out by searchers who are either:

a) unfamiliar with the domain of their goal (i.e. need to learn about 
the topic in order to understand how to achieve their goal)

b) unsure about the ways to achieve their goals 
(either the technology or the process)

c) or even unsure about their goals in the first place.</blockquote>
Gary Marchionini, in his paper <a href="http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.97.4576&rep=rep1&type=pdf">Exploratory Search: 
From Finding to Understanding</a>, approaches exploratory search as:

<blockquote>a blend of querying and browsing strategies.</blockquote>

For an interesting, albeit very abstract, description of possible user 
interactions during exploratory search activities, 
see <a href="http://www.laurencenoel.fr/wp/?p=154">this post by Laurence Noel</a>. 
 my opinion, the "information space" described in this post lacks another 
 very important dimension, that is of <em>time</em>.

The need for the emergence of exploratory search tools is recognized by 
leading experts in the enterprise software solutions industry, 
such as John Porter of Vivisimo (see his post on exploratory 
search <a href="http://informationoptimized.com/blog/2012/01/09/evolving-beyond-traditional-search/">here</a>).

### An Example

Imagine you are a finance student or professional. 
You want to learn what's been published in the top 25 
financial blogs in the last month. That would be about 
7,000 blog posts. You can go ahead and read all of them, 
of course. You must be quite a fast reader if you still 
want to keep up on your other responsibilities.

The way you can approach your task is to start reading 
the recent posts. As you gain more knowledge about possible 
topics you are interested in and you will narrow down your 
interests. After that you will need to come up with relevant 
<em>search queries</em> that you will need to type in a 
search engine to narrow down the results.

However, there is a number of drawbacks of this approach:

* You might need to read a lot of articles you will not be interested in.
* You don't know whether by reading a certain number of articles you have covered all potential topics that have been discussed during the last month (for example, if there was a big discussion of some issue two weeks ago, but since then a lot of other posts on other issues were published, with only sporadic mentions, if any, of the previously widely publicised topic).
* Your user experience will be highly fractured by switching between the reading mode and search mode. In addition, you will need to keep completely in your head any relations or issues that you identify as interesting for you (for example, the relation between articles on government debt yields, articles on stock prices, and European debt crisis).

Of course, this problem has already been identified by many. 
Below are some examples of applications that feature some exploratory 
search capabilities. However, I think that all of them are still 
providing only rudimentary capabilities for exploratory search, 
and there is much more to be discovered and implemented.

### Current Solutions

* <a href="http://news.google.com/">Google News</a> - by far the most advanced implementation of 
exploration capabilities (ha ha, what other company did you expect to do it?), where you can 
track various entities mentioned in the news, and also see other relevant entities that are 
mentioned in a news story, displays relevant information from 
<a href="http://www.freebase.com/">Freebase</a> where available.
* <a href="http://www.google.com/">Google Search</a> - after you type a query, 
a toolbar on the left side allows you to narrow down the results by the source 
of information, time of publication, etc.
* <a href="http://news360app.com/">News360</a> - an application for readers of 
the news on mobile devices, allows tracking of entities mentioned in news articles, 
displays relevant information from <a href="http://www.freebase.com/">Freebase</a> 
where available.
* <a href="http://www.news-republic.com/">News Republic</a> - another quality app 
for mobile news reader that allows tracking the entities mentioned in the news and 
seeing other relevant articles.

These solutions are highly biased towards application to news. 
But there are a lot of other areas that would benefit from a 
similar approach. If you think widely enough, you can imagine 
that in the future, as we accumulate more and more data, all 
information navigation/search will converge towards the tools 
that are by nature exploratory.

In the future posts I will discuss more ideas related to exploratory search in more details. 
In particular, the following topics are very interesting to explore:

* How to group relevant articles according to various levels of abstraction and relations between them
* How to design new user interfaces, and which features we will need for better exploration of texts
