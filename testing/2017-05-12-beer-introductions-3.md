---
layout: post
title: Data Guide for the Beer Perplexed III
subtitle: Part III - Beer Descriptors 
tags: ["BertinMatrix", "D3"]
shortlink: http://bit.ly/prplxd2
twitimg: pic.twitter.com/NKltUlWk71
image: http://endlesspint.com/gallery/2016/beer-prplxd/beer_prplxd2.gif
---

## How would you describe this?


<iframe src="http://endlesspint.com/gallery/2017/beer-prplxd/wheel/index.html" width="800" height="800" marginwidth="0" marginheight="0" scrolling="no" frameBorder="0"></iframe>
<sub>Data: <a href="http://www.brewerydb.com/" target="_blank">BreweryDB</a> / Vis Source: <a href="https://bl.ocks.org/mbostock/4348373" target="_blank">Mike Bostock</a></sub>

Many who will begin their beer adventures and step outside the comfort of the golden piss pushed by the global players, most especially the males amongst them, get carried away by the statistics of the beers, as witnessed in part by the explosion of IPA as a category. For many the style is a gateway, the steady go-to, or just something to fall back on when inspiration is lacking (especially if it is the only alternative style a venue will carry). It is a fine style and one of the primary ones that also got me going but the sooner we quit chasing the hop bombs, the sooner we grew up a bit and leave the scalp collecting to others, the better served we will be in finding, or confirming, the right style for ourselves. This is an exploration versus exploitation scenario. 

It can be shown that given a long time frame, which undoubtedly we all hope our craft beer drinking careers to be, a reward seeking agent is better served retaining some level of exploration (link) in its policy in order to not commit too soon to any option that could lead to non-optimum results. Besides the idea of delicious beer as a reward, which of course it is, there is the added wrinkle of the right beer for the occasion. Factors that go into this decision include weather, food, place, and occasionally a hangover. I'm not a great fan of the hair of the dog remedy but I have tried it (hey, you got explore!) to know both that I do not enjoy it as a solution and that even in that situation different beers have different levels of appeal, or none at all as your preferences may suit you. And so we attempt to dig still yet a little deeper in our beer quest. We now bring into the fore characteristics that nearly all of us are familiar with from our lifetime’s experience of eating and drinking. We bring this experience and preference to bear on our choices so as to appreciate the beer and continue exploring and learning, both about the beer and our preferences.

## Some background motivation

Thus far we only looked at the relationship [between beer styles](/2016-10-10-beer-introductions-1) and certain [characteristics of those styles](/2016-11-18-beer-introductions-2), the latter based on alcohol, bitterness, and color. We now take a more direct approach at defining what goes into a style, further helping place the many beers into context. For this third installment of the guide we are going to leverage the style descriptions to help categorize and group the 100+ beers available.

Friends of mine went to the most recent GABF (https://www.greatamericanbeerfestival.com/) and while staying in touch I was prompted to look up the official festival app. I never got around to downloading it because I was distracted by the API source from <a href="http://www.brewerydb.com/" target="_blank">BreweryDB</a>. It was just as mentioned on the GABF app and as I had hoped for, paragraph long descriptions were one API pull away. Once I had that info I tried to see what could be done with what was on offer. Besides the descriptions there was additional information about the category and beer numbers related to ABV, etc. That had already been taken care of in [an earlier guide](/2016-11-18-beer-introductions-2) but I fooled around and made a bubble chart all the same.

<img src="/gallery/2017/beer-prplxd/style_stn.png" alt="style_stn_bubble" align="middle" width="800" /><br>
<sub>Data Source: <a href="http://www.brewerydb.com/" target="_blank">BreweryDB</a></sub>

## Original Goal 

To identify the key descriptive terms for each beer style, find descriptive terms common across styles so as to create some form of context, and to order this data into a meaningful visualization. In searching of an appropriate visual idiom I was hoping not to reinvent the wheel (pun!). Lo and behold I did not have to. There is already a precedent for categorizing flavors along, you guessed it, a flavor wheel for wine (link), beer (link) and coffee (https://www.jasondavies.com/coffee-wheel/). The most common descriptors are at the center with refinements and distinctions radiating out. In truth, this is like a decision tree with branches spreading out. At least you can use that metaphor to help navigate the many layers and interlocking of descriptors. After identifying the data source for this exercise I experimented with different approaches. 

The resulting charts come from several tweaks and variations on the following: I read in each beer style's descriptions, ran each description through a natural language package (nltk link) to determine parts of speech and isolated the nouns and adjectives of each style, intuiting these being the most appropriate kinds of terms to work with for our purpose. 

## Start Broad, Go Narrow

Having created a dictionary of beer styles and respective parts of speech and having filtered out nouns and adjectives to the exclusion of all other terms I attempted some approaches to mixed success. There was bag of words, bigrams, and term frequency. The results were for the most part unsatisfying in the sense that no simple function/approach provided me with a quick and dirty solution. I am nothing if not lazy. I harnessed this laziness in an effort to come up with a creative solution. Ultimately I decided on a very naïve approach. Identified all nouns or verbs that appeared in at least 10 styles. I did a human review of worthless labels and tossed those out. With the remaining data I…. Technically naïve but colored with subject matter expertise (hey mom!). 

<img src="/gallery/2017/beer-prplxd/bertifier_Matrix (3).svg" width="100%">

<object type="image/svg+xml" data="/gallery/2017/beer-prplxd/bertifier_Matrix (3).svg">
  Your browser does not support SVG
</object>

Perhaps the limitations of time, skill or energy conspired against my automating the entire process. At the same time I'm trying to focus more on the output and not getting bogged down in the process of any one project. Each of the projects will contribute to a broader and deeper appreciation of the process, however askance or exaptive. Ultimately I relied on a visual process/cue to get to the final visualization. Using an Excel file and pivoting the key terms with the styles and coloring in the intersections I was able to get an idea of where to go and how to proceed. 

This was a low sophisticated but higher tech version of a Berion matrix (link). which reminded me that I could use an online resource to further this exploration. The process was in perfect but forgiving due to the large, relative, count of terms and styles. If this were science, even data science, it would be a bad way of proceeding. I forced the data into a visual representation, pruning as needed. I knew what I was looking for and I made the evidence to match it: bad science. I am able to sleep at night by reminding myself that the whole point was to develop an instructive tool and not necessarily an exhaustive one. The entire process is an abstraction of sorts and not meant to, or have an illusion of, representing A ground truth. Far from it. Besides the Excel representation I also used chaining of styles depending on the terms they contained, a sort of longest path for each style through the term is deemed most relevant to the task of visually representing site and taste characteristics of beer styles. This longest path approach will be revisited and more effectively implemented later on (stay tuned). 


# Poo-poo

a word wheel visualization via D3 with a possible heat map/sparse matrix for the styles and corresponding word stems as an intermediary visualization. 

Why? To better know what you want to drink. Why no anything? Knowledge of the world is determined by how close of an approximation or mental model is to reality. If you want a good beer, Job, friend you need to first know yourself-I'm not going to be helping you with that part, not here at least-and match that up with an idea of the target. Then use your reason to get a best guesstimate as to whether or not things are likely to work out.  Some beers were dropped for the sake of the visualization [footnote: there were…]. 

