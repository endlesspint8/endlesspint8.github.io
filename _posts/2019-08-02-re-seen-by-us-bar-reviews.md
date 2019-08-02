---
layout: post
title: Reseen By Us
subtitle: Discounting the Past to Better Appraise the Present
tags: ["bars", "nyc", "Excel", "line"]
shortlink: 
twitimg: 
image: http://endlesspint.com/gallery/2019/reseen/cv_wgt_avg.png
sideof: []
---

<img src="/gallery/2019/reseen/close-up-color-countdown-39396.jpg" alt="close-up-color-countdown" align="middle" width="100%" /><br />

## Forgetting, To Move Forward 

The Internet never forgets but perhaps it would be best if we occasionally exercised our selective memory. When reviewing services in particular it would do us well to refresh our assessments. While discounting the past may lend recent impressions an overvalued status, there is an intuitive appeal in listening more attentively to what people who have just had an experience have to say about it. Times, places and tastes change. We need not keep in stone the ratings of several years ago when we have more recent inputs to consider. Studio 54 of recent times is not the Studio 54 of yore; it would be absurd to expect the orgies of yesteryear when going today. On a less dramatic note we can pursue this hunch when it comes to beer bars. 

Over the past decade-plus craft beer has stepped out of a niche interest into a conversation topic of general interest, even among those who cannot distinguish a Pilsner from a pale ale. In that time bars, breweries, styles, and knowledgeable consumers have proliferated. What was once considered a hop bomb now appears quaint; that 30-tap bar selection, rotated seasonally, was a unicorn a couple of decades ago; and the light lager swigger has learned about a variety of beers. All of which is to say, perhaps it is time to consider discounting historical reviews so as to get closer to the pulse of the zeitgeist. A gradual removal of past reviews accomplishes two things, it captures a rating more in line with contemporary appraisals (quality) and it identifies the number of reviews within a selected time window (quantity).


## Time is like a river

Once again we can leverage a toy example to investigate alternative angles on viewing things and remind ourselves that the answers we get often depend on the questions we ask. Those questions in turn are inspired by our interests. This is not a case for relativism but a re-emphasis on the bootstrapping nature of many metrics and views we take for granted, grounded in the beings we are.

Three key features to track: review counts, review scores, and time. The final element introduces flow, movement. Numbers carry about them a certain finality and certitude that does not always warrant the authority we bestow upon them. Be skeptical of precise numbers. Look for ranges, confidence intervals and other bits of wiggle that help provide a more complete picture of the situation. Speaking of pictures, charts can be of great help when there is not much to differentiate among summary statistics (e.g. [Anscombe’s quartet](https://www.quora.com/What-is-the-significance-of-Anscombes-quartet)).

<img src="/gallery/2019/reseen/simp_cuml_avg_all.png" alt="simp_cuml_avg_all" align="middle" width="100%" /><br />
<sub>Data Source: <a href="https://www.tripadvisor.com/Search?redirect&uiOrigin=MASTHEAD&default_scope&ssrc=e&singleSearchBox&pid=3826&searchSessionId=F76948E90EF8BE131AF3BEE1299AC2D61564751070207ssid&supportedSearchTypes=find_near_stand_alone_query&searchNearby&geo=60763&q=beer%20bars&enableNearPage=true&queryParsed=true&social_typeahead_2018_feature=true&returnTo=__2F__Restaurants__2D__g60763__2D__zfg11776__2D__New__5F__York__5F__City__5F__New__5F__York__2E__html&startTime=1564751081922&sid=F76948E90EF8BE131AF3BEE1299AC2D61564751087254" target="_blank">TripAdvisor</a> (<i>Accessed: 26 Jun 2019</i>) </sub>


## Caught Between Bar Stools

Selecting the top 30 beer bars in NYC as per TripAdvisor we can review past ratings for each. Grouping ratings by the months they were submitted in easily lends them to weighting by month, with decreasing significance to those occurring earlier on, eventually dropping altogether from consideration. To get started we set the window of interest at 24 months. This was a judgment call that seemed about right for allowing past input without overvaluing  either what came before or more recent impressions. Setting aside specific numbers, we get what we expect globally: squiggly lines indicating patron preferences over time, general trends, and rates of change. There are also gaps in the ratings, sometimes of multiple months, resulting in rating lines breaking off on the chart. 

<img src="/gallery/2019/reseen/24mo_wgt_avg_all.png" alt="24mo_wgt_avg_all" align="middle" width="100%" /><br />
<sub>Data Source: <a href="https://www.tripadvisor.com/" target="_blank">TripAdvisor</a> (<i>Accessed: 26 Jun 2019</i>) </sub>

This breaking off of reviews raised a subsequent thought regarding how long to retain ratings in the absence of online customer engagement. Here too we resorted to personal discretion and set a cutoff of six months. Bars that had gone six or more months without a rating had their scores shelved. These visual gaps help to send a message to potential patrons about traffic, interest, and/or whether the platform is adequate for the review of beer bars generally and the impacted bar, specifically.

<img src="/gallery/2019/reseen/24mo_wgt_avg_active_samp.png" alt="24mo_wgt_avg_active_samp" align="middle" width="100%" /><br />	
<sub>Data Source: <a href="https://www.tripadvisor.com/" target="_blank">TripAdvisor</a> (<i>Accessed: 26 Jun 2019</i>) </sub>

Thus at minimum we are left with three ways of viewing bar appraisals: a simple rating average;  a time-discounted rating, with accompanying time series to visualize changes; and the latter with the added wrinkle of suspending ratings in the absence of engagement. The question of which of these is the most informative relies on what one is looking for.<sup id="a1">[1](#f1)</sup>  Keeping in mind that all models are wrong but some are useful.

<img src="/gallery/2019/reseen/ratings_tbl.png" alt="ratings_tbl" align="middle" width="65%" /><br />	
<sub>Data Source: <a href="https://www.tripadvisor.com/" target="_blank">TripAdvisor</a> (<i>Accessed: 26 Jun 2019</i>) </sub>


--- 

**Notes**

[Opening Photo by Pixabay on Pexels](https://www.pexels.com/photo/clear-glass-with-red-sand-grainer-39396/)

<b id="f1">1</b> Process and becoming; always moving, always changing, ever in flux; snapshots are informative as well as misinformative, dangerous to chase an image – a frozen representation of desire, which itself constantly changes; chasing shadows, of course never fulfilled when grasped, grasping at air; life is not fixicity and stasis can only mean death; even prominent goods are not guaranteed to meet expectations, as both production methods and tastes change. (Excuse me, [too much coffee](http://endlesspint.com/2019-05-17-sleep-no-more-caffeine/)). 

Below are graphical representations of the coefficient of variation for the opposing ways of measuring ratings touched on here. We can see that in the latter, 24-month weighted moving average, incoming reviews predictably continue to make an impression, while the cumulative average develops a lock-in situation:[↩](#a1) <br>

<img src="/gallery/2019/reseen/cv_simp_avg.png" alt="cv_simp_avg" align="middle" width="100%" /><br />	
<sub>Data Source: <a href="https://www.tripadvisor.com/" target="_blank">TripAdvisor</a> (<i>Accessed: 26 Jun 2019</i>) </sub>

<img src="/gallery/2019/reseen/cv_wgt_avg.png" alt="cv_wgt_avg" align="middle" width="100%" /><br />	
<sub>Data Source: <a href="https://www.tripadvisor.com/" target="_blank">TripAdvisor</a> (<i>Accessed: 26 Jun 2019</i>) </sub>

Code @[nbviewer](https://nbviewer.jupyter.org/github/endlesspint8/endlesspint8.github.io/blob/master/code/reseen/ta_reviews.ipynb)
