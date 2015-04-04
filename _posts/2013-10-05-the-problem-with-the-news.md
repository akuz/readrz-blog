---
layout: post
title:  "The Problem with the News"
date:   2013-10-05 12:00:00
---

Millions of news, blog articles, and status updates are published every day. You like to know what is going on in the news (let’s just call it news, even if it’s actually a blog post). So what are the options you have in the Internet?

{% picture 20131005/information_overload.jpg %}
<br />

#### Curated Media

You rely on your favourite manually curated website that selects the news for you. You may read through a few of such websites. This gives you access to content with predictably good quality. But at the same time, you relinquish your control of what information (and what opinions) get a chance to appear before your eyes. You are under a total control of your selected news source(s).

#### Social Voting

You visit your favourite social voting site ([Reddit](http://www.reddit.com/), [Hacker News](https://news.ycombinator.com/), [Digg](http://digg.com/)). You look through top 20 links. You read the discussions. This gives you something to feed your brain with. You expect the community to produce the top links that would be generally relevant to your area of interest. This is great, as it gives you a fine entry point to the world of information. But this is also very limited. It’s like using MTV top 20 to get to know what’s going on in the world of music.

#### Aggregator Sites

The news are grouped by how similar they are to each other, and then packed into a predefined set of standard sections. Think [Google News](https://news.google.com/), [Yahoo News](http://news.yahoo.com/), [News360](http://news360.com/). You can browse overall top news. You can also choose a section and browse top news within that section. Within each group of news, you can explore other articles – which provides you with an additional dose of objectivity that is lacking within the curated media and social voting sites. Already better. But is this all that can be achieved? No.

#### “Like” (Filter Bubble)

Don’t people all have different interests? Let’s give them a chance to tell us what their interests are, and we can learn from them, and show them better quality news tailored for each one of them! Of course, we cannot ask people to actually type in their key words, people are so lazy these days. But surely people can click like or dislike button on a specific news article. We can then use sophisticated algorithms to infer the interests of a specific person, and then overlay this on top of our aggregated news feed, and make everyone happy by showing them the news they would actually like. Think [Zite](http://zite.com/), and the above aggregators.

Isn’t it great? No. Here are the reasons why (and what can be done about it).

<!--more-->

By telling the system what you like, you are building your own prison. It may not be as extreme as “if I like a news article about the International Space Station, then I will see all news about it in the future.” People building recommender systems are not stupid, ok? They will infer your interests within a model that has substantially fewer degrees of freedom than the number of things you can like or dislike. To translate this into a normal language, they will build a profile of you, a virtual model of you, which has only a few parameters. These parameters can be how interested are you, from 0.0 to 1.0, in each of the 5 top sections. Additionally, within each of these sections, a model of you would have additional 5 parameters between 0.0 and 1.0 showing how much you are interested in the subsections. This gives a total of 5 x 5 = 25 parameters of virtual you (for example).

These parameters will later serve as hints to the system which news to show you. The system might have another card up its sleeve. It may sometimes show you the news that you are surely haven’t shown interest in before. Just to check if real you hasn’t deviated too much from the virtual you. But this might be just too slow (see additional drawbacks below).

Empowered with this algorithm, the system takes control of what you are allowed and not allowed to see, while you dwelve in a blissful state of happiness of knowing only about the things you actually like to know. Just like in [The Matrix](http://en.wikipedia.org/wiki/The_Matrix).

This is called a bubble, in which you now begin to live. Please see a classy presentation about this at [dontbubble.us](http://dontbubble.us/) (a.k.a. [DuckDuckGo](https://duckduckgo.com/) vs. [Google](https://www.google.com/)).

Here are some additional drawbacks:

* I may be interested in tech and business at work and entertainment and sports at home – so do I create two different profiles for that? Can I?
* I may start doing an MBA – so how long will it take for the system to adjust to my new areas of interest? Then I decide it’s not for me, please can I adjust that back?
* What does the system actually know about me? Can I change that?
* Can I see the world through another person’s eyes? Privacy?

This kind of filtering can actually work well and be very useful for some people. It can make people happier, albeit at the expense of objectivity. It’s just not something I choose for myself. And it’s a question for you, which pill do you choose – [red or blue](http://en.wikipedia.org/wiki/Red_pill_and_blue_pill)?

I believe recommender systems will serve an important role. But it will be just one of different ways to look at the information. Let me present you with a simple idea. It is generally considered to be an area of [exploratory search](http://en.wikipedia.org/wiki/Exploratory_search), but I was unable to find good implementations of any of the ideas.

#### Adaptive Browsing

Imagine you a looking at a virtual cloud of 1,000,000 news articles. You want to know what’s out there (and also you don’t want to “take a blue pill”, and let someone decide what you should see).

You see the following options:

* A search box
* Top search queries you can use
* Top sections, and top news within each
* Top ways to sort the news by

The  sorting mechanism is important because it lets you look at the same set of news though a different dimension. For example, you could sort the financial news by country to get a picture of the economy, and sort them by the company to see how it affects the individual players.

Let’s now say you review the top news you see, and then:

* Enter (or select) a search query, or
* Select one of the sections that are suggested, or
* Select one of the items you sorted by (a country for example)

**By doing this, you effectively reduce the number of articles you could be interested in from 1,000,000 to a significantly smaller number, say 1,000.**

Here comes the key point.

The system then takes these 1,000 articles and presents the results in **exactly the same** way as before, but customized for the remaining 1,000 news you might be interested in, and you see:

A search box
Top search **sub**queries you can use
Top **sub**sections, and top news within each
Top ways to sort these 1,000 news by

You can repeat this step until you reach that one key article, and then start over, or make a parallel shift to another section, and then clear some of the search parameters to look at a wider scope.

The beauty of this approach is that the **amount of information reduces exponentially with each choice you make**. That means that you could reach any single article of 1,000,000 in just a few steps. And I mean a few – more like 5 steps than like 50.

This makes it very easy for anyone to reach any specific information within a very short time frame. There is no need to learn user profiles. Users can express their interests here and now, and get a reasonable overview of the information matching their interests at this very moment.

The same user interface at any level makes it easy for you to see the information in the same format, although with different search and sorting parameters.

#### Conclusion

This is what is being built at [Readrz.com]({{ site.url_readrz }}).

{% picture 20131005/information_surfing.jpg %}
<br />

A lot of things are still being improved: the user interface, the coverage of news sources, performance of the computations, sections, and ways to sort by. But it is already available for you, as it is now. If you feel this work is important, please visit [Readrz.com]({{ site.url_readrz }}).

#### Bonus

How to reproduce the Economist:

* Sort all news by Countries

How to reproduce the Business section of FT:

* Select the Business section
* Sort the news by Companies

How to reproduce the Economy section of WSJ:

* Select the Finance section
* Sort the news by Countries

Do it at [Readrz.com]({{ site.url_readrz }})