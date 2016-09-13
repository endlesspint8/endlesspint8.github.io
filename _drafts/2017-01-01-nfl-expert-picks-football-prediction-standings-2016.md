---
layout: post
title: Experts? Pfff, let's measure their BS
subtitle: We'll Put Their Name to the <a href="https://www.youtube.com/watch?v=sByxTCQU8Rc" target="_blank">Test</a>
---

## Experts Know Things, Right?

What we hope to discover in this season-long investigation into _American_ football game predictions is which major outlet has the best brain trust. By major outlet we mean the networks that carry the games, CBS, ESPN, FOX and NBC,<sup id="a1">[1](#f1)</sup> and best, at least initially, will be determined by how well the respective crews, as a collective, do against game results. Game results should be self explanatory and in addition we will be looking at performance against the spread (using <a href="http://www.sportsline.com/nfl/odds/" target="_blank">SportsLine</a>), where applicable. What exactly "as a collective" means is simple enough to guess at but will be explained further below after introducing the prediction sources and explaining a bit about the data sets. 

To begin with we have 2 human panels, CBS and ESPN, and 2 data models/simulations, FiveThirtyEight and FOX. CBS offers straight up (SUP) and against the spread (ATS) picks, ESPN only SUP. CBS and ESPN have 8- and 9-men<sup id="a2">[2](#f2)</sup> expert crews, respectively. We will be tracking all of the picks on an individual (each expert's choice) and collective level, taking each expert's pick as a vote for that game. Regarding the latter voting process, we will be using the percentage of votes for a specific team as a proxy for that panel's expected winning probability. Due to CBS having an even number of experts, introducing the very likely scenario of 50/50 splits, we will give the push to the away team in SUP and to the betting dog in ATS. The CBS split decisions of 50/50 will not be a problem in determining forecast probabilistic accuracy as we will be using the <a href="https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=brier%20score" target="_score">Brier score</a> (BS) and this method takes this eventuality into consideration.

Both FiveThirtyEight and FOX provide their predictions as a probability. FiveThirtyEight relies on ELO ratings and besides winning expectations also provides ELO based point spreads (how this part will be analyzed will be made clear after week 3). FOX is partnered with <a href="https://www.whatifsports.com/" target="_blank">WhatIfSports.com</a> and I am looking to get more information on <a href="https://www.whatifsports.com/nfl" target="_blank">their methodoloy</a> but it is stated that the winning percentages and average scores are based on 501 game simulations. Both data models/simulations, FiveThirtyEight and FOX, released their predictions for the entire season ahead of any live snaps and will be updated throughout the season. I intend to track the performances of both the pre-released data picks (referred to here as "a priori") and those updated on a week-to-week basis (referred to as "in situ"). 

Perhaps you're already seeing how much of this will play out based on what's been described above. The probabilities for each of the 4 initial sources will be compared to actual game results to determine the effectiveness of the predictions. Should you not have bothered to click on the Brier score link above let us summarize it by saying that a) the more confident the predictions, the greater the  reward/penalty based on outcome, & b) the lower the BS (Brier score or bullshit, you deside) the better. There will be 8 anticipated predictive performances to track (this is expected to grow, stay tuned): 

  1. CBS SUP 
  2. CBS ATS
  3. ESPN SUP
  4. FiveThirtyEight "a priori"
  5. FiveThirtyEight "in situ"
  6. FOX "a priori"
  7. FOX "in situ"
  8. Random probability prediction
  
We are interested in a number of anticipated comparisons (expert panel v. expert panel, humans v. algorithms, algo v. algo, and of course all against the random predictor which we suspect coming in last but is presented here as a sort of baseline) and expect others to come to the fore as the season proceeds. Chart, tables, and occasional interactive visualizations will be made available on a weekly basis (Wednesdays) for the duration of the season. Each week will provide an opportunity to look at the football season and predictions in a new light. 

---

## Week 1 - Humans Haven't Been Replaced, Yet

Let's start slow for this first installment. We have all season to get to know each other and get fancy-shmancy with the analysis. We will introduce our most basic metric, the Brier score (BS), and layout the predictive performance of the major outlets we're covering. As the section's heading above hints at the expert panels, the humans, did a solid job of demonstrating their worth. It cannot be any earlier in the season but I wish to congratulate the CBS panel especially for coming in first, in both wins and predictive accuracy. Time will tell if this was a happy fluke or a sign of things to come.

**Predictive Standing, Straight Up**

|Source|Week 1 Brier Score|Wins|
|---|---|---|
|CBS|0.174|13|
|FiveThirtyEight|0.210|10|
|FOX|0.254|9|
|ESPN|0.256|11|
|Random|0.520|5|

### Week 1 Whiffs

 * **The CBS committee** had only of 3 of sixteen games wrong, picking CAR, ARI and LA. The ARI choice was the most damaging as it was an unanimous selection resulting in the largest penalty possible for a prediction, 1.0. This was off-set by solid and confident choices in other places, such as the 3 other unanimous picks that did work out: HOU, SEA and PIT. This right away brings to mind the thought that human panels, certainly ones as small as these, are prone to over estimating probability of wins (granted the way I am using their input is not the intended purpose, but that's what makes it so fun). It is doubtful that the data models we will be dealing with in this exercise will ever give a probability of 1.00. This means that the human panels leave themselves open to big wins and big loses, as far as the Brier score is concerned. This is something worth keeping an eye on. If it turns out that this becomes too much of a detriment I will consider regularizing unanimous selections (including a +1 to denomiators such that an 8/8 vote, 100%, becomes 8/9, 89%).<sup id="a3">[3](#f3)</sup>

|Source|Avg Prob of Pick|Best Possible BS|Worst Possible BS|
|---|---|---|---|
|CBS|0.766|0.055|0.586|
|FiveThirtyEight|0.633|0.135|0.401|
|FOX|0.658|0.117|0.433|
|ESPN|0.813|0.035|0.660|
|Random|0.789|0.045|0.623|

 * adsf
 * adsf
 * 

---

**Newsletter**

> Sign up for the <a href="http://bit.ly/ep8nlw" target="_blank">newsletter</a> and receive advance notice of posted content, added site features and opportunities to ask questions & make suggestions for future data related beer pieces and miscellany.
>
> Drink well & stay curious, Reggie

<br>

---

**Notes**

<b id="f1">1</b> Except for NBC, at this point (week 1). These punks have not made their experts' picks readily available, at least not in the panel-friendly way of CBS and ESPN. [↩](#a1) <br>
<b id="f2">2</b> They are in fact all men. Sorry ladies. [↩](#a2) <br>
<b id="f3">3</b> Not a bad policy in dealing with prognostications in the real world either.  [↩](#a3) <br>
<b id="f4">4</b>   [↩](#a4) <br>
<b id="f5">5</b>   [↩](#a5) <br>
<b id="f6">6</b>   [↩](#a6) <br>
<b id="f7">7</b>   [↩](#a7) <br>
<b id="f8">8</b>   [↩](#a8) <br>
<b id="f9">9</b>   [↩](#a9) <br>
