---
layout: post
title:  "Towards Sentiment Analysis"
date:   2012-06-28 12:00:00
---

I am beginning a new foray deeper into computational linguistics in the area of sentiment analysis. In this post I want to outline the main goals and the reasons behind them. Later I am planning to post updates on the progress.

**Exploratory Search.** We have been working for some time on exploratory search at Readrz. The goal was to allow people to explore a collection of texts. Overall, this is a very big topic. The texts can be explored along semantical dimensions, and along the time dimension if texts are timestamped. Semantical dimensions can be predefined categories, tag clouds, search queries, or more vaguely defined topics (more on this in next paragraph). When semantical dimensions are specified manually as categories/tags and then associated with documents by people working with them, exploratory search becomes a relatively easy task. We can implement filtering by the defined categories and by time. We can let people see related categories by inferring them from associations of documents with multiple categories. We can also easily compute the “activity” in different categories over time and present graphs to the users, and let them navigate through time. This have been implemented in many online systems that allow tagging documents, photos, etc.

<!--more-->

**Categories Extraction.** However, we do not always have a luxury of employing actual humans for sorting out the texts for us and creating a set of interrelated categories that would make sense for a given collection of documents. In this case we want to automate the process of finding the categories (semantical dimensions) that would be appropriate for exploring a collection of documents. As part of designing this algorithm we will need to define 1) how our semantical dimensions are described, and 2) how these semantical dimensions are related to the documents. This step is very important, as it not only defines the core of the computational model, but also influences what kind of user interfaces can be produced using the automatically inferred categories.

**Evolution of Categories.** One important aspect of the model for automatic inference of categories is the way the categories relate to time, if timestamps of documents are available. Often it is assumed that semantical categories do not change over time. It makes sense in many cases. We are currently only looking at ideas that make this assumption. However, it may be of interest to see how the document collection changes over time, whether there are new topics appearing, etc. For example, see <a href="http://www.cs.princeton.edu/~blei/papers/BleiLafferty2006a.pdf">*Dynamic Topic Models*, Blei, Lafferty, 2006</a> (PDF).

**Topic Models.** A famous class of a models for semantic categories extraction are topic models. They make several assumptions. First is a “bag of words” assumption, i.e. the order of words in a document is not important. There are variations of the model that take into account pairs of words, but the these pairs are also exchangeable within a document. Then based on this assumption, if we define the semantical categories as topics described as a discrete probability distribution over words, we can define a generative process which relates topics to documents.  We basically define how would the documents be produced given the topics are known, and then reverse engineer the topics from the document collection we have. Each document would be generated as follows. For each document, select a distribution of this document over topics. Then for each word position in document, select a topic from document-specific distribution over topics, then select a word from topic-specific distribution over words, and then place the word at the current position. Continue until the document is complete. The model details are more complicated than that, see <a href="http://www.cs.princeton.edu/~blei/papers/BleiNgJordan2003.pdf">*Latent Dirichlet Allocation*, Blei, Ng, Jordan, 2003</a> (PDF) for more details.

**Bag-of-Words Limitations.** Topic models can produce semantic categories (topics) that give a good overview of a document collection. But, because of the bag-of-words assumption, the internal structure of the documents is lost, and therefore the results are necessarily limited in their ability to extract textual information that is represented using deeper linguistic structures. At first, when a person doesn’t know what the document collection is all about, the topics can be very useful because they provide clues as to what kind of subject areas are present in the document. After more information is available about the subject areas, people want to ask deeper questions.

**Topics and User Interface.** As I mentioned above under “Categories extraction”, the details of the model for automatic identification of sentiment categories will influence what kind of UI it is possible to design, given the semantic categories found from the texts. In case of topic models, the topics are generally defined as discrete probability distributions over words. Various model tried to define relationships between topics. For example see <a href="http://www.cs.cmu.edu/~lafferty/pub/ctm.pdf">*Correlated Topic Models*, Blei, Lafferty</a> or <a href="http://books.nips.cc/papers/files/nips16/NIPS2003_AA03.pdf">*Hierarchical Topic Models and the Nested Chinese Restaurant Process*, Blei, Jordan, Griffith, Tenenbaum</a>. So, topic models can have some degree of flexibility to produce semantic categories (topics) with some interrelations between them. But the most you can get is: either a flat list of topics, a list of correlated topics, some hierarchy of topics, or combinations of hierarchical and correlated topics. So in the UI that you can produce from this, you are limited to dissecting the documents collection using these topics that are distributions over words that can occur anywhere within a document. You, by design, largely due to the bag-of-words assumption, lack the tools that will allow you to dissect the meaning further.

**Drilling Down Topics.** After our experiments with topic models to design the UI at <a href="{{ site.url_readrz }}">Readrz.com</a>, we understood that after people get an overview of what the documents can be about (for example finance, business, and international relations, or some more fine-grained topics), then they want to drill down. The way they want to drill down is usually limited to some set of concepts that they know about the subject area, and a set of sentiments that can be attached to them (good / bad / etc). Normally the concepts would be expressed as (collections of) nouns, and sentiment would be expressed with verbs and adjectives (of course, I am simplifying). See more below under sentiment analysis.

**Linguistic Information.** I would like to add that topic models are purely bootstrapped from the statistics of the word occurrences within the documents collection. They do not accomodate any further linguistic information into analysis. However, this information is readily available. Using <a href="http://wordnet.princeton.edu/">WordNet</a>, it is possible to obtain the information about the part-of-speech possibilities for a given word, as well as various senses (meanings) for different uses of the word, plus synonyms, antonyms, hyponyms, etc. There are also various lists available expressing the sentiment for various words. Using all this information within the model for automatic identification of semantic categories can increase the richness of the results that may be extracted from a collection of texts. The richness of the results will enhance the richness of the UI that can be generated for the people to explore the documents collection.

**Sentiment analysis.** Let’s now consider the situation when people know what the subject area of the documents collection is. In this case, to explore the documents further, they will want to drill down using some additional tools. If you think independently of the subject area, then there are always some things described in text that can be referred to as having positive or negative sentiment. The sentiment would normally be attributed to adjectives and verbs. People, when confronting a document collection in a known subject area, will often want to be able to split it  along the sentiment dimension, i.e. find the statements that express good or bad (or some other) sentiment. There are colletions of words <a href="http://wordnetweb.princeton.edu/perl/webwn">available</a> that would provide you with sentiment ranking for the words in general English. This sentiment ranking for words can be further re-fit to a specific training document collection, for which the sentiments of individual documents are known. This way we can extract subject-specific sentiment ranking for words. Then the sentiment of a given document can be scored from the words that it contains.

**Drilling Down Sentiment.** However, it is not always possible to attribute a specific sentiment to an entire document. A single text can express different sentiments towards different things. For a more fine-grained analysis we would need to define (or extract) the important things that the sentiment can be expressed about. Let’s call these things concepts. For example, in the area of finance some of the concept would be: stock price, acquisition, bailout plan, GDP. In a naive approach, if we already know the subject area, we could manually define the concepts that people may care about. Then we would score and aggregate the sentiment towards these concepts by examining the words around the mentions of these concepts in texts. This gives us an additional option for a potential UI. We will be able to show not only an overall sentiment of specific documents, but also allow people to drill down and see the breakdown of sentiment by various concepts. Introducing this additional dimension for filtering actually non-linearly increases the exploratory capabilities of the UI. Let’s say you had three sentiment ranks: good, neutral, and bad. Now, say you introduce three concepts that can be tracked. Your overall number of options available to user increases to nine (three times three). We don’t need to worry that we are creating too many possible combinations if we add more concepts. We can always calculate and suggest what would be the most useful / related concepts that user can add to their search based on their cooccurrence.

**Concepts Extraction.** It is also possible to infer the concepts in a specific subject area from a training collection of documents. We can bootstrap the process by starting with a list of words (generally verbs or adjectives) that express certain sentiments. Then by analysing the documents we can extract nouns or collections of nouns that occur near the words that express sentiment. By collecting this statistics we can extract the concepts that are important in a certain subject area. We can either fully automate this process, or allow a manual approval of detected concepts. When some concepts are detected, we can further use this data to extract more words that express the sentiment in the specific subject area by doing some more linguistic analysis. We can then repeat the process of extracting the concepts again.

**Time References.** It is also important to detect what time period an expressed sentiment relates to. Is it for something that just happened, something in the future, or just bringing something from the past? Some very sophisticated systems exists that do all of the above, but the one that also takes into account the time dimension is <a href="http://www.recordedfuture.com/">Recorded Future</a> (acquired by Google). They aggregate sentiment expressed about the future and map it to a complex user interface that aggregates displays public opinion about various events in the future. I would say that this is probably the most advanced version of an NLP system that I know of. They have a lot of technology that we would like to have out of the box. However, even using that technology you could design lots of user interfaces that allow users to see information in different ways. Recorded Future’s UI is very advanced, but in my opinion it thus lacks focus on a particular task. It is a UI for research. We want to design something simpler and focusing on a more specific business problem.

**The Plan.** We are now working on a better system for exploratory search that would have the user interfaces described above, and maybe more. In general it should be able to be applied to any documents collection, although I think we might still keep the manual approval step for the concepts extraction. I am starting refactoring of the basic NLP tasks that we have implemented, and then will gradually move to more complex tasks. The beginning of the plan looks like this:

1. Improve basic words parsing (including detecting abbreviations, all caps, various apostrophes, etc)
1. Create a more generic version of entity detection (this would be needed for my version of part-of-speech detection)
1. Implement basic sentiment detection and lexicon fitting (using bag-of-words assumption)
1. Create a simple user interface for displaying basic sentiment ranking of tracked entities
1. Implement part-of-speech tagging (I am planning to use WordNet with a little probabilistic inference on top for disambiguation)
1. Try out concepts extraction using a fitted sentiment lexicon
1. Advanced sentiment detection with concepts
1. User interface with advanced sentiment

I am planing to report on the progress here.