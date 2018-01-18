---
layout: post
title: Data Guide for the Beer Perplexed V
subtitle: Part V - PageRank 
tags: ["pagerank", "NetworkX"]
shortlink: 
image: http://endlesspint.com/gallery/2018/beer-prplxd/pr_links.png
sideof: ["Longest path containing American style IPA", "http://eepurl.com/cj8urH", ", everyone's favorite."]
---

## Motivation

Capturing the link relationships of beer styles offers the opportunity to discover relationships and patterns that are not immediately apparent from simply reading the information or dealing with the recommendations on an one off basis. Leveraging the insight that informed the [PageRank algorithm](https://en.wikipedia.org/wiki/PageRank) and unleashed a little company called Google upon the world, we can traverse the directional links, the recommendations from one beer to another, to identify the highest scoring beer style as a function of references.

The PageRank algo is inspired by academia and paper citations, specifically. The reasoning goes that the more citations a paper is, the more important that paper is. The quality of the citations also mattered. Citations from six major works are worth more than six, or a hundred, from unheard/unread papers. How do we determine the quality of the citations? By the number/quality of the papers citing them. This smells of an endless regress but the papers do eventually run out and the math is up to the task of determining the scores once the universe of documents are identified and their links/citations identified. What was inspired by academic publications (Larry Page’s father was a university professor) and wildly successful in rating web pages can be turned upon our toy set to determine the rank of the beer styles. 

Instead of web sites we have beer styles, instead of hyperlinks to pages we have recommendations. Propping a random beer style in front of an imaginary drinker, with an obscenely high tolerance, and having them go from beer to beer based on the recommendations, and repeating this “thought experiment” hundreds of times, we calculate the frequency/percentages that they arrive at each beer style. The most often visited style(s) get the highest scores.

In some respects this retains the idea of drinking at random (link) but with the constraint of picking the next beer only from the recommendations made from the present style. You may have noticed a shortcoming to this simple approach. I point you to the link and node visualization (link) to provide a hint. What happens for beers that have no incoming recommendations, either because they are floating out on their own or they provide recommendations to other styles but are never returned the favor? [FN: “Where’s the buy back, bro?”] This is where randomness comes to our assistance. Called the random surfer, as in web surfer (nee random tippler for us), for some small fraction of choices we hop around completely unrestrained, so as to help us see/taste all pints (usually set at or around 15%, as we did here).

## Drum roll, please...

The highest scoring beer by this method is the Belgian Dubbel. The reason being that it has the highest quality links. The style has the highest number of incoming links, recommendations from other beer styles, and these are generally of high quality. It is not the case as mentioned earlier that more links means higher scores. The Belgian Dubbel additionally has a large number of unique grandparent styles that recommend it as a style, two steps/degrees removed. I say unique because some of the beers recommend several of the beers that feed directly into the Dubbel and it would be unproductive to double (pun!) or triple (pun, pun!) count these. As expected, these grandparent beer styles also carry high average ratings. The rich get richer, which is something we see in many disciplines and studies (Matthew effect).

To tie together the assumption and challenges of the data, the fact that this style scores highest does not necessarily mean it will or should be the highest selling style. Foe one, the market may still be traeering these links and not settled onto the model’s expectations. More likely, tastes vary over people, time, and fashion. Just because there is a bridge between two styles does not ensure that most will cross it and having crossed it does not mean they will remain on the other side. What this PageRank can suggest to brewers and marketers are avenues of positioning their beers to capture more of the natural affinities between styles. 

<img src="/gallery/2018/beer-prplxd/pr_links.png" alt="pagerank tipsy" align="middle" width="100%" /><br />
<sub>Data Source: <a href="http://www.craftbeer.com/beer-styles" target="_blank">CraftBeer.com</a> 

As we should do with most (all?) things data we question the results and see what assumptions were made and how this matches up with our experience and the larger expectations of society/the market. A few things about the data: it covers a lot of styles (70+) but certainly not all, that is something worth remembering; the links are from one reference source and could benefit from a second, third, or tenth opinion; preferences and opinions change over time, these links are not set in stone though some are less likely to be modified than others; the majority of recommendations/links are one way which works well for this exercise but may be overly restrictive; additionally, the links are equally weighted, regardless of whether or not they point to a beer style in the same category or one considered wholly unrelated. 



|style|PageRank|children|parents|parent PR avg|share of parent links|grandparents (unique)|grandparent PR avg|
|---|---|---|---|---|---|---|---|
|Belgian-Style Dubbel|<b><font color="blue">0.059657</font></b>|3|<b><font color="blue">12</font></b>|0.014583|37.5%|<b><font color="blue">27</font></b>|0.014047|
|American Sour|0.055769|3|6|0.027033|37.5%|17|<b><font color="blue">0.022757</font></b>|
|Barrel-Aged Beer|0.052094|2|5|0.033770|35.7%|22|0.018776|
|Fruit and Field Beer|0.051072|3|7|0.022776|35%|24|0.014908|
|American Black Ale|0.035242|3|4|0.016503|<b><font color="blue">57%</font></b>|12|0.011367|
|German-Style Dunkel|0.033789|2|3|0.037326|33.3%|16|0.016987|
|English-Style Brown Porter|0.033325|3|2|<b><font color="blue">0.046723</font></b>|40%|13|0.018050|
|Belgian-Style Tripel|0.033268|3|5|0.016726|38.5%|15|0.013445|
|Belgian-Style Wit|0.033025|3|5|0.018597|41.7%|18|0.013387|
|American Wheat|0.027091|2|5|0.016703|35.7%|10|0.022229|

<sub>Data Source: <a href="http://www.craftbeer.com/beer-styles" target="_blank">CraftBeer.com</a> 

This last point bears expounding on if only to show the decisions that go into capturing data and how numbers are not as objective as they so often are portrayed. Each recommendation is considered to be of equal weight when we can all bring to mind certain beer styles that lend themselves more strongly to recommending another. A naive but well founded approach would be to give extra weight to beer recommendations within the same category. Conversely we may decide to give extra weight to recommendations across categories in order to preference wider exploration.



Besides the links between the beers we also begin with the assumption that each beer is of equal value. Our simple implementation works off of this assumption but we may decide to introduce some discretion (link to Hume piece) as to the hedonic quality of each style. [FN: First thought is to leverage data about average user ratings per style]
To finish we will only mention that when and in what environment these beers are to be enjoyed is not even considered. There is instead an idealized state implied, but setting and food are a major influence on what is “best” to drink. End of the day, even when it is just beer, you gotta stay skeptical.
