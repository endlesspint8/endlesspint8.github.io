---
layout: post
title: Data Guide for the Beer Perplexed III
subtitle: Part III - Beer Descriptors 
tags: ["BertinMatrix", "D3"]
shortlink: http://bit.ly/prplxd2
twitimg: pic.twitter.com/NKltUlWk71
image: http://endlesspint.com/gallery/2017/beer-prplxd/wheel_spin.gif
---

## How would you describe this?


<iframe src="http://endlesspint.com/gallery/2017/beer-prplxd/wheel/index.html" width="800" height="800" marginwidth="0" marginheight="0" scrolling="no" frameBorder="0"></iframe>
<sub>Data: <a href="http://www.brewerydb.com/" target="_blank">BreweryDB</a> / Vis Source: <a href="https://bl.ocks.org/mbostock/4348373" target="_blank">Mike Bostock</a></sub>


Many who begin their beer adventures and step outside the "comfort" of the golden piss pushed by the global players, most especially the males amongst them, get carried away by IBU's, as witnessed in part by the <a href="https://www.craftbrewingbusiness.com/business-marketing/ipa-is-the-most-popular-craft-beer-style-is-this-potentially-a-long-term-problem/" target="_blank">explosion and sustainability of IPA as a top category</a>. For many the style is a gateway, a steady go-to, or just something to fall back on when inspiration flags (isn't it for most of us when it is the only alternative style a venue will carry?). It is a fine style and one of the primary ones that got me going but the sooner we quit chasing the hop bombs, the sooner we grow up a bit and leave the scalp collecting to others, the better served we will be in finding, or confirming, the right style for ourselves. This is an exploration versus exploitation scenario. 

It can be shown that given a long time frame, which undoubtedly we all hope our craft beer drinking careers will be, a reward seeking agent is better served <a href="https://www.youtube.com/watch?v=f8_ZIe8Wfkk" target="_blank">retaining some level of exploration</a> in its policy in order to not commit too soon to any option that could lead to non-optimum results. Besides the idea of delicious beer as a reward, which of course it is, there is the added wrinkle of the right beer for the occasion. 

Factors that go into this decision include weather, food, place, and occasionally a hangover. I'm not a great fan of the hair of the dog remedy but I have tried it (hey, you gotta explore!) to know both that I do not enjoy it as a solution and that even in that situation different beers have different levels of appeal, or none at all as your preferences may suit you. 

So we attempt to dig still yet a little deeper in our beer quest. We now bring to the fore characteristics that nearly all of us are familiar with from our lifetime’s experience of eating and drinking. We bring this experience and preference to bear on our beer choices for greater appreciation and continued learning, both of the beer and our preferences.

## Some background motivation

Thus far we only looked at the relationship [between beer styles](/2016-10-10-beer-introductions-1) and certain [characteristics of those styles](/2016-11-18-beer-introductions-2), the latter focusing on alcohol, bitterness, and color. We now take a more direct approach at identifying what qualities are associated with which styles, further helping place the many beers into context. For this third installment of the guide we are going to leverage the style descriptions to help categorize and group the 100+ beers available.

Friends of mine went to the most recent <a href="https://www.greatamericanbeerfestival.com/" target="_blank">GABF</a> and while staying in touch I was prompted to look up the official festival app. I never got around to downloading it because, first of all I wasn't attending and did not need another reminder of that fact and, I was distracted by the <a href="http://www.brewerydb.com/" target="_blank">BreweryDB</a> API source. It was just as mentioned on the GABF site and as I had hoped for, paragraph-long descriptions one API pull away. Once I had the data I tried to see what could be done with what was on offer. Besides the descriptions there was additional information about the category and beer numbers related to ABV, etc. That had already been taken care of in [an earlier guide](/2016-11-18-beer-introductions-2) but I fooled around and made a bubble chart all the same.

<img src="/gallery/2017/beer-prplxd/style_stn.png" alt="style_stn_bubble" align="middle" width="800" /><br>
<sub>Data Source: <a href="http://www.brewerydb.com/" target="_blank">BreweryDB</a></sub>

## Original Goal 

I wanted to identify the key descriptive terms for each beer style, find descriptive terms common across styles so as to create some form of context, and to order this data into a meaningful visualization. In searching for an appropriate visual idiom I was hoping not to reinvent the wheel (pun!). Lo and behold I did not have to. 

There is already a precedent for categorizing flavors along, you guessed it, a flavor wheel for <a href="http://www.thewinecellarinsider.com/wine-topics/wine-educational-questions/davis-aroma-wheel/" target="_blank">wine</a>, <a href="https://www.jasondavies.com/coffee-wheel/" target="_blank">coffee</a>, and of course <a href="http://www.beerflavorwheel.com/" target="_blank">beer</a>, but in a slightly different way than what I had in mind. In each of these instances the most commonly shared descriptors are at the center with refinements and distinctions radiating out. This is like a decision tree folded onto itself to create a sort of pie chart. At least you can use that metaphor to help navigate the many layers and interlocking descriptors. After identifying the data source for this exercise I experimented with different approaches. 

The resulting charts come from several tweaks and variations on the following: I read in each beer style's descriptions, ran each description through a <a href="http://www.nltk.org/" target="_blank">natural language package</a> to determine parts of speech and isolated the nouns and adjectives of each style, intuiting these being the most appropriate kinds of terms to work with for our purpose. 

## Start Broad, Go Narrow

Having created a dictionary of beer styles and respective parts of speech, filtering on nouns and adjectives to the exclusion of all other terms, I attempted several approaches to mixed success. There was bag of words, bigrams, and term frequency. The results were for the most part unsatisfying in the sense that no simple function/approach provided me with a quick and dirty solution. I am nothing if not lazy. I harnessed this laziness in an effort to come up with a creative solution. Ultimately I decided on a naïve approach. 

The exercise turned into a two-pronged approach, one for the beer categories and the second for the underlying styles. Having identified the most common and relevant nouns and adjectives through a combination of algorithms and human sifting I then categorized the terms and grouped them according to the object they described. I settled on what is presented in the table below along the horizontal axis. Using this breakdown and grouping of descriptors should make it more manageable to search for a feature of choice. The table could've been extended to the 100+ beer styles but that would've been unwieldy, besides the flavor wheel had already firmly entrenched itself in my consciousness. 

<!-- img src="/gallery/2017/beer-prplxd/bertifier_Matrix (3).svg" width="800"-->

<object type="image/svg+xml" data="/gallery/2017/beer-prplxd/bertifier_Matrix (3).svg">
  Your browser does not support SVG
</object>
<sub>Data: <a href="http://www.brewerydb.com/" target="_blank">BreweryDB</a> / Vis Creation: <a href="http://www.bertifier.com/" target="_blank">BERTIFIER</a></sub>

Identified all nouns or verbs that appeared in at least 10 styles. I did a human review of worthless labels and tossed those out. With the remaining data I…. Technically naïve but colored with subject matter expertise (hey mom!). 

Using yet again the combination of computer and human approaches I narrowed the terms to the following for description categories, in increasing order of specificity or nesting: taste, flavor, appearance, and chemical compound (this one is for the real beer nerds out there), followed finally by the respective beer style matching all of the relevant criteria. 

The resulting flavor wheel appearing at the top of this piece can be used in two primary ways: from the center out and from the outside in. The former provides an opportunity to ask yourself which among the several choices you prefer and step further until arriving at a style. A sort of chose your own adventure, beer edition. The latter approach allows you to dig into the beer style characteristics and see what styles are adjacent at each step of the way. A few things are missing which could've made this a bit more user-friendly, such as beer category specific colors and of course labels for the terms and beer styles being present without having to hover, especially if you're using this in an hair of the dog moment, but I think it gets the message across and serves to further our understanding of beers.

<img src="/gallery/2017/beer-prplxd/wheel_spin.gif" width="600" align="middle">
<sub>Data: <a href="http://www.brewerydb.com/" target="_blank">BreweryDB</a> / Vis Source: <a href="https://bl.ocks.org/mbostock/4348373" target="_blank">Mike Bostock</a></sub>

Getting closer to mastery, one sip at a time. 
