---
layout: post
title: A Guide for the Beer Perplexed
subtitle: Part I - Looking at Beer Style Connections 
---

Beer is delicious but it is not one thing. If you disagree with the former part of the previous sentence please keep the latter in mind. Think of sports, for instance. Many would agree with the blanket statement "sports are fun" but depending on what you have in mind two people can easily have opposite reactions to being presented the opportunity to play ping-pong. Sports are not one thing, music is not one thing, and neither is beer.

Presented with a finely crafted brew in a style of your preference it is difficult to have a more pleasurable gastronomical experience. Throw off one of those two criteria, craftsmanship or style preference, and you're likely to have a tolerable experience at best or an off-putting one at worst (first world problems are nevertheless fraught with disappointment).<sup id="a1">[1](#f1)</sup> Setting aside craftsmanship for another time, I will be focusing on beer styles and helping you find ones suitable to your preferences, current and developing. Think of me as your craft beer sherpa and the visuals below simply as my tools. 

The (over?) abundance of beers now available makes it understandable if one is overwhelmed by the choices. Forget about picking just between two options (Bud Light or Bud Heavy, really no option at all), you have dozens upon dozens of choices (take that <a href="https://en.wikipedia.org/wiki/Buridan%27s_ass" target="_blank">Buridan’s ass</a>!). You could easily be stopped before even beginning. I am here to provide a helping hand with some simple analysis to ward off any onset of paralysis. 

Discovering that beer does not have to taste bad is something that happens on a regular and enthusiastic basis if the year-over-year growth in craft beer business is any indication. The hurdle to personal discovery and preference, as is so often the case, can appear to be a daunting one, even for something as delicious and intoxicating (literally) as "real" beer. I can speak from experience and say the options available can be equal parts intimidating and frustrating (then you have a couple and it doesn't seem so frustrating after all). 

With innumerable options and not knowing where to begin it is forgivable to simply throw one’s hands up and  rush into any old style. This tactic, while commendable for its action and much better than doing nothing (including, heaven forbid, not drinking beer at all), has the unfortunate effect of being unfocused and leaving you to the whims of external vagaries. There is the added likelihood of running into a beer style that is not a particularly good match, resulting in disappointment and pushing you back, short term let’s hope, into the familiar but underwhelming arms of a light lager. One is made more painfully aware of all this with hindsight. To begin imbibing craft beer is to bring on short term pleasure, medium term disappointment in reflecting on all the lost opportunities, and, finally, gleeful acceptance of never going back.

To the uninitiated the awareness of available styles may feel not unlike the way the following node and link visual looks. When things get as cluttered as this data vis people (not so) affectionately refer to it as a hairball and I believe it is clear why. You can see there are relationships and make out some if not all of the individual points but there is a lot going on. Now before we crap on this visual too hard let's play around a bit to get a better idea of what is available to us. This can be a metaphor for the real life journey many of us take trying one style after another.

<iframe src="http://endlesspint.com/gallery/2016/cb/cb_other_styles_rev.html" width="810" height="510" marginwidth="0" marginheight="0" scrolling="no" frameBorder="0"></iframe>
<sub>Data Source: <a href="http://www.craftbeer.com/beer-styles" target="_blank">CraftBeer.com</a> / 
Scraping Template: <a href="https://github.com/cs109/content/blob/master/labs/lab2/Lab_2_A_Live.ipynb" target="_blank">CS109</a> / 
Vis Code: <a href="http://bl.ocks.org/mbostock/4062045" target="_blank">Force-Directed Graph</a> & <a href="http://www.coppelia.io/2014/07/an-a-to-z-of-extra-features-for-the-d3-force-layout/" target="_blank">Extra Features</a></sub>

Hover your mouse over any one point to see the name of the beer style appear. If you click and drag you can pull the hairball around. Fun but the amusement won't be long lasting.<sup id="a2">[2](#f2)</sup> There are a few other features I wish to bring your attention to and we can do this best by using one of them now. Choose a point and double-click on it. What you should see is that point and it's related beer styles highlighted by way of unrelated styles being muted and fading into the background. Having a subset available allows me to bring your attention to additional visual cues. 

The color of the dots/points are dependent on the group the beer style is a part of.<sup id="a3">[3](#f3)</sup> Additionally, the links between the points have an arrow indicating the direction that the beer recommendation runs in. We will argue later that the links are hardly one way but for the time being we are going to stick with the underlying data.

Ultimately we have a visualization that carries information about style grouping (color), style name (hover), recommendation links (lines), and direction of the recommendation (arrows). Lastly, we may cut through the clutter by double clicking a specific style and investigating its immediate relations more fully.<sup id="a4">[4](#f4)</sup> 



<br>

---

**Notes**

<b id="f1">1</b> I have used some version of this intro in submissions to other sites but never on my own so I feel no shame in self-plagiarising myself here. [↩](#a1) <br>
<b id="f2">2</b> <i>That's what she…</i> ah, you know the rest.  [↩](#a2) <br>
<b id="f3">3</b> Style groups per this data set: Belgian Styles, Bocks, Brown Ales, Dark Lagers, Hybrid Beers, India Pale Ales, Pale Ales, Pilsners and Pale Lagers, Porters, Scottish-Style Ales, Speciality Beers, Stouts, Strong Ales, Wheat Beers, & Wild/Sour Beers  [↩](#a3) <br>
<b id="f4">4</b> Many of these added features come courtesy of @CoppeliaMLA. [↩](#a4) <br>
<b id="f1">1</b> asdf  [↩](#a1) <br>
