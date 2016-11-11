---
layout: post
title: Data Guide for the Beer Perplexed
subtitle: Part II - What's in a Style? 
tags: ["RShiny", "datavis"]
shortlink:
twitimg: 
---

## What's in style?


As we inch our way closer to beer authority [FN: that's a great name but it's already taken by a New York City bar situated across the street from the port authority] , approaching the topic from many angles it is important to occasionally take a deeper dive. This is not one of those times. Not really. We’ll get a little more information on the beer categories and develop an idea of their characteristics on a closer but still superficial level. It's like knowing the stats of a player. You may be able to discuss them with more understanding but if you haven't seen them in action you can't truly speak about their presence. Ultimately knowing an item is to have made yourself more intimate with it then just reading about it. So once you're done with this piece (but not before!) go out there, grab a pint, and get yourself some learnin’.


The characteristics we will cover here are primarily three: ABV, IBU, & SRM. in my throwing acronyms at you, you can say that the sports analogy above was apropos. While these letters do provide a solid grounding, and perhaps a necessary one, it will ultimately be sterile and insufficient without some first-hand experience. Nevertheless, this information is important in getting closer to understanding what is out there and how it relates when comparing one beer to another.


To give these three measures more soul let's bring in our senses into the mix and associate each of the measures with one or more of them.


ABV -> taste & touch
IBU -> taste & smell
SRM -> sight
Temperature -> taste & touch (that's right newbie, temperature has an impact on the taste of beer)


This association only leaves out hearing, which is a weird one to consider for the direct tasting of beer but is indispensable to learning from others and convivial company. Additionally we’re stretching a little bit though not much to mention smell with respect to IBU. Now that we've teased this out long enough it is time to get down to particulars.


I can rattle off specifics on what style has what and how it compares to another, how the styles are similar, how they're different and so forth. However, you need not sit here idly through my rambling, shit you may have already clicked over to another site by now. No sir, instead we're going to use the wonderful interactive features of the Internet to breathe still more life into these characteristics.


We will use two primary graphs to explore this data world further. 


The first is a one feature exploration by category: 
category, glass, yeast. 
Or ABV, IBU, SRM, & Temp


The second is a two future exploration begins similar groupings. This allows for a deeper understanding, especially as it read leads to comparisons.


Far from it for me to tell you how to go about your exploration but I suggest for the first graph, which displays group characteristics as box-and-whiskers, we stick with the categories. Categories?! Wait, what? I thought we were talking about the 70+ styles from the previous guide entry. We still are but at one higher level up. You may have noticed that's some of the styles, even if you knew nothing else about beer, would appear to have natural groupings based on their names. For instants there are the several country specific names, such as American, Belgium, British and German. A country named Shirley does not suggest all such beers or similar but there is a common heritage nonetheless, something for another time. Beyond that easily identifiable country names there are the similar description: pale L, Indian pale, stout, etc. You can be sure that regardless of country origin there would be some distinguishing characteristics that cross borders here.


Besides, don't get so excited by the category idea, this was already introduced last time by way of the colors used in both the link and node and cooccurrence matrix. It is these groupings that we are looking at. Will get a handle on the general categories first. This will be easier since there are fewer and are more distinguished between themselves. Trying several styles within the category helps to pick up a nuances of both the styles and categories. You will see the features in common that bind them together as well as their differences which help distinguish them. This latter may not be readily identifiable but comparing across categories isn't is your comparison and helps build up our observational qualities.


Back to the graph. Sticking with the style categories on the X axis, mess around and vary the Y axis to display the features. If you haven't seen a box-and-whisker plot in a while, maybe since high school math class, allow me to provide a quick recap. Each box represents information in the same way: the bisecting line represents the median, fancy talk for the 50th percentile, half the beers appear above this lint and the other half below. The top of the box is the 75th percentile and the bottom the 25th.


The second graph is slightly more sophisticated and is truly meant to be used as a comparative tool. What you will see here are the beer features standardized (Wikipedia link). Here we have the opportunity to map three data elements onto each point, A variable each on the X axis, Y axis, and the dots themselves by way of using color. The graph defaults to 80 BV against IBU. Without doing anything else it is pretty clear that in general there is a positive correlation between the two beer characteristics. Beers with higher alcohol content tend to have more bettering units and the other way around. To get an idea of what styles for wear, use the third drop-down menu option, "color by", dislike the grouping of your choosing. again, I recommend "category ". There are a lot of dogs and a lot of colors. Don't just sit there, use your zoom capabilities and make the graph bigger in order to get a better view. Still a lot going on but we see some general groupings: strong ales, IPAs, and stouts gravitate toward the upper right-hand corner while weeds, wild sours, and dart loggers may be found in the opposite corner. What's the relation of IB used to color? Change the Y axis from ABV to SRM. We now have a more dispersed cloud. In order to see the general trend click the "smooth" checkbox. you should see a lazy upside down "you". This says that the lighter colored beers are on either end of the IPU spectrum (weeks and pills) with the darker beers in the middle (porters and stouts).



