---
layout: post
title:  "Suspending Readrz Services"
date:   2015-04-04 12:00:00
---

I am suspending all services behind the [Readrz.com]({{ site.url_readrz }}) infrastructure today:

* Feeds scanning service
* Duplicate finder service
* Search indexer service
* Image scanner service
* Summarizer service
* Mongo database
* Web site

All the code (apart from AWS connection details) is released here: [<i class="fa fa-github"></i> akuz/readrz-public](https://github.com/akuz/readrz-public)

There is a high chance that I can bring the infrastructure up again, if there is interest.
Hopefully, one day I can also release the exciting innovative JavaScript menus as standalone components.
I am keeping the database of all the news scanned between Jan, 2011 - Mar, 2015.

For now, I've decided to redirect $150 it costs to run it monthly to another project.

<br />

#### Good Bye Screenshots

Here are a few screenshots I've taken just to remember how it looked like at the last iteration.

Front page (celebrating the Iran deal at the top news item):

{% picture 20150404/shot1.png %}
<br />

<!--more-->

Filtered showing all news in the Finance category (notice the sub-categories too):

{% picture 20150404/shot2.png %}
<br />

Search results when searching for "Ukraine":

{% picture 20150404/shot3.png %}
<br />
