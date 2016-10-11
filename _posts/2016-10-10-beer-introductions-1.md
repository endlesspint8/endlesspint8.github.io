---
layout: post
title: Data Guide for the Beer Perplexed
subtitle: Part I - Looking at Beer Style Connections 
tags: ["D3", "BokehPlots", "link & node"]
shortlink: http://bit.ly/prplxd1
---

## Whole Lotta Beers Out There

Beer is delicious but it is not one thing. If you disagree with the former part of the previous sentence please keep the latter in mind. Think of sports, for instance. Many would agree with the blanket statement "sports are fun" but depending on what you have in mind two people can easily have opposite reactions to being presented the opportunity to play ping-pong. Sports are not one thing, music is not one thing, and neither is beer.

Presented with a finely crafted brew in a style of your preference it is difficult to have a more pleasurable gastronomical experience. Throw off one of those two criteria, craftsmanship or style preference, and you're likely to have a tolerable experience at best or an off-putting one at worst (first world problems are nevertheless fraught with disappointment).<sup id="a1">[1](#f1)</sup> Setting aside craftsmanship for another time, I will be focusing on beer styles and helping you find ones suitable to your preferences, current and developing. Think of me as your craft beer sherpa and the visuals below simply as my tools (**note**: the following visuals are not always mobile friendly.). 

The (over?) abundance of beers now available makes it understandable if one is overwhelmed by the choices. Forget about picking just between two options (Bud Light or Bud Heavy, really no option at all), you have dozens upon dozens of choices (take that <a href="https://en.wikipedia.org/wiki/Buridan%27s_ass" target="_blank">Buridan’s ass</a>!). You could easily be stopped before even beginning. I am here to provide a helping hand with some simple analysis to ward off any onset of paralysis. 

Discovering that beer does not have to taste bad is something that happens on a regular and enthusiastic basis if the year-over-year growth in craft beer business is any indication. The hurdle to personal discovery and preference can, as is so often the case, appear to be a daunting one, even for something as delicious and intoxicating (literally) as "real" beer. I can speak from experience and say the options available can be equal parts intimidating and frustrating (then you have a couple and it doesn't seem so frustrating after all). 

With innumerable options and not knowing where to begin it is forgivable to simply throw one’s hands up and rush into any old style. This tactic, while commendable for its action and much better than doing nothing (including, heaven forbid, not drinking beer at all), has the unfortunate effect of being unfocused and leaving you to the whims of external vagaries. There is the added likelihood of running into a beer style that is not a particularly good match, resulting in disappointment and pushing you back, short term let’s hope, into the familiar but underwhelming arms of a light lager. One is made more painfully aware of all this with hindsight. To begin imbibing craft beer is to bring on short term pleasure, medium term disappointment in reflecting on all the lost opportunities, and, finally, gleeful acceptance of never going back.

## I Got a Pretzel in My Head (good, have a beer w/that)

To the uninitiated the awareness of available styles may feel not unlike the way the following node and link visual looks. When things get as cluttered as this data vis people (not so) affectionately refer to it as a hairball and I believe it is clear why. You can see there are relationships and make out some, if not all, of the individual points but there is a lot going on. Now before we crap on this visual too hard let's play around a bit to get a better idea of what is available to us. This can be a metaphor for the real life journey many of us take trying one style after another. 

<iframe src="http://endlesspint.com/gallery/2016/cb/cb_other_styles_rev.html" width="810" height="510" marginwidth="0" marginheight="0" scrolling="no" frameBorder="0"></iframe>
<sub>Data Source: <a href="http://www.craftbeer.com/beer-styles" target="_blank">CraftBeer.com</a> / 
Scraping Template: <a href="https://github.com/cs109/content/blob/master/labs/lab2/Lab_2_A_Live.ipynb" target="_blank">CS109</a> / 
Vis Code: <a href="http://bl.ocks.org/mbostock/4062045" target="_blank">Force-Directed Graph</a> & <a href="http://www.coppelia.io/2014/07/an-a-to-z-of-extra-features-for-the-d3-force-layout/" target="_blank">Extra Features</a></sub>

Hover your mouse over any one point to see the name of the beer style appear. If you click and drag you can pull the hairball around. Fun but the amusement won't be long lasting.<sup id="a2">[2](#f2)</sup> There are a few other features I wish to bring your attention to and we can do this best by using one of them now. Choose a point and double-click on it. What you should see is that point and it's related beer styles highlighted by way of unrelated styles being muted and fading into the background. Having a subset available allows me to bring your attention to additional visual cues. 

The color of the dots/points are dependent on the group the beer style is a part of.<sup id="a3">[3](#f3)</sup> Additionally, the links between the points have an arrow indicating the direction that the beer recommendation runs in. We will argue later that the links are hardly one way but for the time being we are going to stick with the underlying data.

Ultimately we have a visualization that carries information about style grouping (color), style name (hover), recommendation links (lines), and direction of the recommendation (arrows). Lastly, we may cut through the clutter by double clicking a specific style and investigating its immediate relations more fully.<sup id="a4">[4](#f4)</sup> 

## Find a Beachhead

Think of a beer you already appreciate, one you may have enjoyed on vacation, or with a Bohemian cousin (Bohemian?! Paging 1960’s Village poets. Paging?!…<sup id="a5">[5](#f5)</sup>). Having tracked down the beer in your mind, search the internets for what style it is and now you have a holding. Though this may not end up being the ultimate style for you at least you have an opening. Moreover, you have for yourself the missing link. Years later you will be able to trace back your journey to this beer/style. 

Many a fellow imbiber can look back at past dalliances with wheats, IPAs, and brown ales. It is fun to keep these beers in mind to see how you feel about them a year, five years later. Don't take my word for it alone, but ask anyone who has been drinking craft beer for more than a year and they can often attest to how their tastes have "matured" over time. It is not uncommon that your gateway beer will one day soon either fall out of favor or certainly be diminished by the expanded experiences of your palate.<sup id="a6">[6](#f6)</sup>

Armed with a beer style the next time you're at a bar with a handful of taps you do not recognize ask the bartender for a suggestion. This is one of the true pleasures of drinking "real" beer. Similar styles have differences in taste from brewery to brewery so it makes sense to ask for samples, usually complementary, or getting yourself a flight, typically 4 to 6 small size servings of different beers. 

Note the styles you like, those you don't, and repeat. That's it. 

Oh, you want more instruction grasshopper? Let's take a second look at the relationships/likeness/similarity among the 70+ styles. Don't worry if some of these are foreign to you, appreciate the novelty while it lasts and realize it gets even more esoteric later on, should you choose to accept this mission. This is a high level approach not a deep dive into the Kabbalah-like minutia of beer offerings.

## Styles on top of Styles

Our second visualization represents the same data set as a grid, a co-occurrence matrix. The beer styles are duplicated across the left side and the top, clustered into style groups. At the intersection of any two beers is either a clear space or a darkened square indicating a recommendation. Lightly color saturated boxes indicate groups, more fully saturated colored boxes are beer recommendations within the same style, something that carries relevant information for the less intrepid. Sticking to the underlying data structure we have here a nonsymmetrical matrix, think of the arrows in the direction of style recommendation above. 

<iframe src="http://endlesspint.com/gallery/2016/cb/cb_style_req.html" width="810" height="810" marginwidth="0" marginheight="0" scrolling="no" frameBorder="0"></iframe>
<sub>Data Source: <a href="http://www.craftbeer.com/beer-styles" target="_blank">CraftBeer.com</a> / 
Vis Inspiration: <a href="https://bost.ocks.org/mike/miserables/" target="_blank">D3 Les Misérables</a> / 
Vis Code: <a href="http://bokeh.pydata.org/en/latest/docs/gallery/les_mis.html" target="_blank">Bokeh Les Mis Occurrences</a>
</sub>

The way to read this grid is at least twofold. First off, find a style you like along the left side, pan horizontally across the row of that style. Anywhere a darkened box appears is a suggestion for expanding your horizon. Alternatively, you can find a style you're interested in across the top and scan down its column to find yourself a gateway beer into appreciating this curiosity. The graph is at times difficult to read due to squeezing in so many styles into a limited space but this issue is partially mitigated by a hover tool that tells you directly the beers represented by each square, "like this" then "try that". This representation of the data allows the user to see groupings more clearly and see relationships at a glance, arguably more quickly than a hairball like the one above.

## Conclusion: We're Just Getting Started

This is just a taste for the ways in which we can leverage data to augment our beer explorations. In future installments of the Beer Perplexed we will look more closely at beer category features, links beyond just two beers, and approaching beers based on your descriptive preferences. Happy exploring. 

<br>

---

**Notes**

<b id="f1">1</b> I have used some version of this intro in submissions to other sites but never on my own so I feel no shame in self-plagiarising myself here. [↩](#a1) <br>
<b id="f2">2</b> <i>That's what she…</i> ah, you know the rest.  [↩](#a2) <br>
<b id="f3">3</b> Style groups per this data set: Belgian Styles, Bocks, Brown Ales, Dark Lagers, Hybrid Beers, India Pale Ales, Pale Ales, Pilsners and Pale Lagers, Porters, Scottish-Style Ales, Speciality Beers, Stouts, Strong Ales, Wheat Beers, & Wild/Sour Beers  [↩](#a3) <br>
<b id="f4">4</b> Many of these added features come courtesy of @CoppeliaMLA. [↩](#a4) <br>
<b id="f5">5</b> Ad nauseum.  [↩](#a5) <br>
<b id="f6">6</b> It would be surprising if this were not the case. How likely would it be that the beer you are leveraging now to build your appreciation will end up being the beer of choice after heading down this road? If that is the case, it is more likely you haven't explored enough or maybe beer isn't your favorite adult beverage after all. Of course, there is always the outside shot you're drinking the number one beer of the moment and you weren't aware you already had a refined palate… but I digress.  [↩](#a6) <br>
