---
layout: post
title: Data Guide for the Beer Perplexed IV
subtitle: Part IV - Graphs and Paths 
tags: ["longestpath", "NetworkX"]
shortlink: 
image: http://endlesspint.com/gallery/2017/beer-prplxd/longestPath28_NetworkX.PNG
sideof: ["Longest path containing American style IPA", "http://eepurl.com/cj8urH", ", everyone's favorite."]
---

## Motivation

If handed a pale ale and in the other hand you hold a stout it should be simple enough to identify differences.<sup id="a1">[1](#f1)</sup> These observations would be fairly common and not overly informative. Being introduced to beers in this ham handed manner would not be productive to identifying similarities instead of differences or trying to get from one beer style to another in an instructive way. It would be more helpful to home in on a style you enjoy and branch off steadily from there. There will be some jumping around to test the boundaries for sure, but if we stretch too far we can be reassured of a foundation to return to. Additionally, it is the differences among like things and minded people that is truly interesting. This is where we start digging in, both from a learning perspective and a defensive stance. We begin to see what people hold onto and, perhaps, why. Given that you have found a style you like, or dislike, how do you branch out and connect the dots in between?

There are standards of taste, of general principles available to all of us. Physical attributes give rise to stimulations and these arouse feelings of appreciation or disapproval. We often defer to each other’s tastes when they are in close agreement but have no qualms in dismissing the judgements of those whose appraisals are far off from agreed standards, betraying that the appreciation of an object is not solely the scope of subjective experience. There is no reason why we cannot, through effort and the setting aside of our preconceived notions, develop and refine our observational capabilities. One of the primary ways of doing so is through comparison.<sup id="a2">[2](#f2)</sup> 

We need items to compare against one another in order to advance our observational abilities, to get an idea of common attributes and differences. Through comparison we may contrast features brought to our attention more clearly and forcefully. The difference between a stout and a light lager are clear, obvious, and mostly uninteresting. Perhaps when first starting out being made aware that two drinks so different in character are still considered the same type of drink might prove enlightening but the differences remain so great that we would be left with only the most pedestrian of observations moving forward. 

Experiencing different styles that are closely related helps to reveal the nuances to the many attributes that go into a style. The experience touches all of our senses and each is enhanced in ability by working out the differences and similarities of approximate styles. By sharpening our observational capabilities we enhance and deepen our appreciation and experiences. This is the motivation for identifying the longest path across the 70+ styles as recommended in the <a href="http://www.craftbeer.com/beer-styles" target="_blank">data source</a>.

## Data Process

The recommendations from one beer style to another are not necessarily mutual. Networks such as these, where connections may run one-way (think Twitter, Followers versus Following), are called directed graphs. Even so, there were instances of mutual agreement between styles and occasionally we found ourself back at a beer style simply by following certain paths long enough, the recommendations circling back. In cases such as these it is technically impossible to identify a longest path since the loops can be navigated indefinitely. In order to resolve this two preparatory passes were made through the network. 

<iframe src="https://docs.google.com/presentation/d/1mhjrXSGxzu8X98F8nvCLTK6MPUisyMlhd-OtVD2R1pU/embed?start=false&loop=false&delayms=3000" frameborder="0" width="100%" height="500" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

<sub><a href="http://bit.ly/ep8_lngpth" target="_blank">Slides Link</a> 
  
The first looked at all bi-directional relationships. With mutually recommending beer styles identified it was possible to choose at random a direction to drop and one to keep. The second pass stepped through the links, flagging when we returned to a previously seen beer style and ending the path. The starting point of each path was selected at random. With mutual connections and loop/look backs identified and dropped, both at random, the longest path algorithm was run ten thousand times. This gave the greatest reassurance that whatever longest path was possible would be identified.<sup id="a3">[3](#f3)</sup> The end result was a list of 28 beer styles. 

## List Graph

The direction of the recommendations run top to bottom. The beer styles are clearly labelled down the middle of the list graph with the background color reflecting the SRM color designation of that respective beer style. This provides a simple visual cue as to the type of beer and malt roasting involved. Two other beer style features are provided, one on either end of the beer names. On the left we have ABV as a relative bar length and on the right the IBU. These two features are standardized across beer styles to provide a relative comparison. In one glimpse the viewer can identify the order of recommendations, the color of the respective beers, and those beers’ alcohol and bitterness levels. 

<img src="/gallery/2017/beer-prplxd/longestPath28_NetworkX.PNG" alt="longest path tipsy" align="middle" width="100%" /><br />
<sub>Data Source: <a href="http://www.craftbeer.com/beer-styles" target="_blank">CraftBeer.com</a> 
  
What we see is an eclectic and cosmopolitan array of beers covering well known European centers of influence and no scarcity of American styles. On the list are Belgian, German, British, and the aforementioned American styles. We have ales and lagers, sweet beers (dubbels), sour beers, malt focused offerings, hop forward drinks, as well as fruit beers. It would be no exaggeration to say that someone familiar with these styles is  well on their way to becoming a connoisseur and developing a sophisticated palate. The recommendations on the graph are directional but our suggestion is not so parochial. With a nudge and a wink we recommend starting from either end of the list, even somewhere in the middle, and branching out at your pleasure. However, one thing is conspicuously missing for the modern craft drinker: IPA, specifically American style IPA. A close look at the list should provide sufficient clues as to where it would fit in (click [here](/flights/#longIPA)  if you give up). 


## A Spare Moment

Beer consumption is an epicurean pursuit.<sup id="a4">[4](#f4)</sup> From the drink itself to the surroundings, from the accompanying food to the company kept, discussing topics of interest but often of little significance, we find ample evidence to view the activity as trivial. Taken out of context imbibing is no serious matter. Family, community, and work are serious. However, with our responsibilities put to bed it is natural and healthy to unwind in order to provide some balance and a few moments of appreciation and reflection. The scarcity of these moments heighten their value providing even more reason to cherish and make the most of them. 

> Leisure is essential to civilization, and in former times leisure for the few was only rendered possible by the labors of the many. But their labors were valuable, not because work is good, but because leisure is good.		- **Bertrand Russell**, [In Praise of Idleness](https://www.goodreads.com/work/quotes/1314555-in-praise-of-idleness-and-other-essays)

Time spent drinking good beer is time well spent. As long as you keep an open mind you are bound to find styles that match best with you, a meal, or some specific occasion. There are a ton of styles and substyles with more coming and going each year, more so than ever with the craft beer craze. Having a grounding in the fundamentals will ensure a solid base from which to judge and appreciate the beers you come across. While [picking at random may be a better policy in choosing stocks over going with an actively managed account](http://www.telegraph.co.uk/finance/personalfinance/investing/9971683/Monkeys-beat-the-stock-market.html) you should have more luck and more fun, coupled by lower stress, selecting your own beers. With a list of recommended and chained styles you have the opportunity to see the “lay of the land” and better understand the context of flavor. 

Practice is good but it dawned on us long ago that [the right kind of practice](https://en.wikipedia.org/wiki/Practice_%28learning_method%29) makes all the difference, otherwise you risk wasting time and forming sub optimal habits that will require even more time and energy to disabuse yourself of later on. We are still talking of leisure so it may seem odd to stress the importance of effectiveness but our free time is no insignificant thing and it should be done right in order to get the most from it and to honor our most valuable blessings, time spent with family and friends. 


---

**Notes**

<b id="f1">1</b> Double fisting, any problems with that? Questions? [↩](#a1) <br>

<b id="f2">2</b> Shout out, David Hume! More about our beloved Scot soon. [↩](#a2) <br>

<b id="f3">3</b> I cannot claim for certain that this is the “final answer”, but feel free to [apply the process](/code/beer_prplxd_IV) yourself and let me know what you return and what you think. [↩](#a3) <br>

<b id="f4">4</b> A deceptively obvious statement with [deeper significance](http://oll.libertyfund.org/titles/carus-on-the-nature-of-things). [↩](#a4) <br>
