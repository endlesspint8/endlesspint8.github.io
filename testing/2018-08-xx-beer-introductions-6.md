---
layout: post
title: Data Guide for the Beer Perplexed VI
subtitle: Part VI - Tangled Up in Brew Chords 
tags: ["chord chart", "seaborn", "perplexed"]
shortlink: 
image: http://endlesspint.com/gallery/2018/beer-prplxd/pr_links.png
sideof: ["Second level beers", "http://eepurl.com/cj8urH", " into top PR style (grandparent sytles)."]
---

## More Data, More Problems

Beer, like any worthwhile topic, may be approached from various angles and on different levels. In [this series](/tag/perplexed) we have focused on individual beer styles, looking at their characteristics and how they relate to each other. We reviewed the recommendation from one style to another and divized different approaches for making sense of this: link & node (link), longest path (link), and PageRank (link). In our current piece we are going to step back and look at the style categories, cutting down on the nearly 80 styles to just over a dozen elements, lessening the cognitive load and allowing us to appreciate the landscape at a different scale. 

These families of beer styles have been with us all throughout our journey. In the beginning we used them to determine summary characteristics for ABV, IBU, and SRM (link), and later we leveraged this grouping when creating the (Les Mis) grid (link). While the recommendations were somewhat scant in the latter instance we made the vis more robust by coloring like-category beers in the grid and encouraging exploration within categories, in addition to the direct recommendations supplied in the data (data is not always complete to our needs, sometimes it is overly complete; a theme to return to). Lastly, even when the categories were not called out explicitly, the use of color coding was used to (when possible) identify beer styles of the same family (link). A gentle reminder of connections inherent in beers. 

Much as the categories were carried through, even in pieces where they were not highlighted, we will leverage style information to help inform our current representation. By leveraging beer style links/recommendations we are able to develop a visualization that aggregates connections among categories, and stick with this coarser detail. By abstracting away the more particular associations for a higher level consideration we are loosening the recommendation criteria (yet again). Instead of a prescription or recipe this is a guideline, a general way of thinking about beer styles in relation to one another. Rather than bogging the viewer down with what appear to be countless relationships, which become as unwieldy in the mind as they do in the “hairball” link and node graph (link) we now have a more simple and general way of considering the relationships. Moreover, we see what many of us thought to be the case, as long as you continue exploring the beerscape you will visit all of the categories. In returning back to where you started, having a circle play a part in the visualization is only fitting. 

Beer drinking and exploration is circular and circuitous but that does not necessarily mean it is repetitive (your friends’ tired conversations notwithstanding). Each go-round provides an opportunity to employ a new perspective. The flash and punch of an IPA may grab you at first but with more experience you may begin to appreciate the more nuanced, muted, and balanced brews of other styles, other kinds of IPA’s included. The chord chart serves as a gentle guide to bouncing from one style to another.

## Wanting More from Less

Collapsing our 70+ styles into 15 categories has not automatically made the data vis more user friendly. Naturally, this is a factor of the underlying data and vis idiom chosen, both. If we may take anything away from the chord chart it is that things are intertwined and overlapping (back to the circuitous nature of the exploratory endeavor). The eye cannot help but jump around the connecting threads and different colors. This is beneficial from the perspective of inviting further investigation but it also makes it difficult to focus on specific relationships for any length of time, tiring the eyes… Many times the connections that go across several categories become obscured by other category pairings. 

Changing the representation to a 15x15 grid, with matching category names across both axes, with boxes representing the meeting of two categories, the color saturation determined by the strength/number of underlying connections (the 70+ styles, again)... 

This piece is one of several that has prompted me to want to approach future attempts with a different motivation, one that is more heuristic driven. Of course one could play with the charts more and improve them on several criteria but ultimately what fun is there in consulting a table or graph when the information might be condensed into a few memorable and accessible guidelines? 


<img src="/gallery/2018/beer-prplxd/chord_bokeh_plot2.png" alt="chord chart" align="middle" width="100%" /><br />
<sub>Data Source: <a href="http://www.craftbeer.com/beer-styles" target="_blank">CraftBeer.com</a> 


## Half Map, Twice as Accessible

<img src="/gallery/2018/beer-prplxd/half_map.png" alt="half map" align="middle" width="100%" /><br />
<sub>Data Source: <a href="http://www.craftbeer.com/beer-styles" target="_blank">CraftBeer.com</a> 
  

<img src="/gallery/2018/beer-prplxd/half_map_rotate.png" alt="half map" align="middle" width="100%" /><br />
<sub>Data Source: <a href="http://www.craftbeer.com/beer-styles" target="_blank">CraftBeer.com</a> 



---

**Notes**

<b id="f1">1</b> Larry Page’s father was a university professor. [↩](#a1) <br>
<b id="f2">2</b> "Where’s the buyback, bro?" [↩](#a2) <br>
<b id="f3">3</b> First thought, leverage data about average user ratings per style. [↩](#a3) <br> 
