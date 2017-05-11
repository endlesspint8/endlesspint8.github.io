---
layout: post
title: Data Guide for the Beer Perplexed III
subtitle: Part III - Beer Descriptors 
tags: ["BertinMatrix", "D3"]
shortlink: http://bit.ly/prplxd2
twitimg: pic.twitter.com/NKltUlWk71
image: http://endlesspint.com/gallery/2016/beer-prplxd/beer_prplxd2.gif
---

## What's in a style?

Capture motivation/inspiration: 

so far we have only looked at the relationship between beer styles and certain characteristics of those styles, the latter based on alcohol, bitterness, and color. We will now take a more direct approach at defining what goes into a style, further helping place the many beers into context. Why? To better know what you want to drink. Why no anything? Knowledge of the world is determined by how close of an approximation or mental model is to reality. If you want a good beer, Job, friend you need to first know yourself-I'm not going to be helping you with that part, not here at least-and match that up with an idea of the target. Then use your reason to get a best guesstimate as to whether or not things are likely to work out. For this third installment of the guide we are going to leverage the style descriptions to help categorize and group the 100+ beers available. Some beers were dropped for the sake of the visualization [footnote: there were…]. 

Friends of mine went to the most recent GABF (link) and while staying in touch with them I looked up the official festival app. I never got around to downloading it because I was distracted by the API source, BreweryDB (link). Once I have that info I was off and running, trying to see what could be done, what was on offer. It was just as mentioned on the GABF app and as I had hoped for, the beer descriptions came from BreweryDB and were one API pull away. Beside the paragraph long descriptions that was additional information about the category and beer numbers related to ABV, etc. That had already been taken care of in the earlier guide but I fooled around and made a bubble chart all the same.

Understand the problem: to identify the key descriptive terms for each your style, to find a descriptive terms most common across styles so as to create some form of context, and to order this data into a meaningful visualization. as it turns out I would not be inventing the wheel (pun!), as this idea and approach had been previously developed for both wine and beer enthusiasts. The original thinking was to process the descriptive text by word into parts of speech. 

Envision success: 

a word wheel visualization via D3 with a possible heat map/sparse matrix for the styles and corresponding word stems as an intermediary visualization. In searching for an appropriate visual idiom I was hoping not to reinvent the wheel. Lo and behold I did not have to. There is already a precedent  of categorizing flavors along, you guessed it, a flavor wheel. The most common descriptors are at the center with refinements and distinctions radiating out. In truth, this is like a decision tree with branches standing out. At least you can use that metaphor to help navigate the many layers and interlocking of descriptors. After identifying the data source for this exercise I experimented with different approaches. 

The resulting chart comes from several tweaks and variations on the following. I read in each style in their respective descriptions, these descriptions were typically 3 to 4 sentences long with an average of X words. I ran each description through a natural language package to determine parts of speech. Specifically I wanted to isolate the nouns and adjectives of each style. Intuiting these being the most appropriate kinds of terms to work with for our purpose. 

Having created a dictionary of beer styles and respective parts of speech and having filtered out nouns and adjectives to the exclusion of all other terms I attempted some approaches to mixed success. There was bag of words, bigrams, and term frequency. The results where for the most part unsatisfying in the sense that no simple function/approach provided me with a quick and dirty solution. I am nothing if not lazy. I harnessed this laziness in an effort to come up with a creative solution. Ultimately I decided on a very naïve approach. Identified all nouns or verbs that appeared in at least 10 styles. I did a human review of worthless labels and tossed those out. With the remaining data I…. Technically naïve but colored with subject matter expertise (hey mom!). 

<img src="/gallery/2017/beer-prplxd/bertifier_Matrix (3).svg" width="100%">

Perhaps the limitations of time, skill or energy conspired against my automating the entire process. At the same time I'm trying to focus more on the output and not getting bogged down in the process of any one project. Each of the projects will contribute to a broader and deeper appreciation of the process, however askance or exaptive. Ultimately I relied on a visual process/cue to get to the final visualization. Using an Excel file and pivoting the key terms with the styles and coloring in the intersections I was able to get an idea of where to go and how to proceed. 

This was a low sophisticated but higher tech version of a Berion matrix (link). which reminded me that I could use an online resource to further this exploration. The process was in perfect but forgiving due to the large, relative, count of terms and styles. If this were science, even data science, it would be a bad way of proceeding. I forced the data into a visual representation, pruning as needed. I knew what I was looking for and I made the evidence to match it: bad science. I am able to sleep at night by reminding myself that the whole point was to develop an instructive tool and not necessarily an exhaustive one. The entire process is an abstraction of sorts and not meant to, or have an illusion of, representing A ground truth. Far from it. Besides the Excel representation I also used chaining of styles depending on the terms they contained, a sort of longest path for each style through the term is deemed most relevant to the task of visually representing site and taste characteristics of beer styles. This longest path approach will be revisited and more effectively implemented later on (stay tuned). 
