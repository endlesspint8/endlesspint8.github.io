---
layout: post
title: Experts? Pfff, ... a season long digression
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

## Week 4 - I'm Just a Professional

_That's what everyone keeps saying and I'm getting sick and tired of hearing it_. Now that I'm done channeling my inner <a href="https://youtu.be/DYa6FNKSgbk" target="_blank">John Creasy</a> let's get on with what is turning into a less than impressive showing for the game pickers. I guess there's a reason people get paid big bucks for calling it <a href="http://www.imdb.com/title/tt0417217/?ref_=nm_flmg_act_26" target="_blank">like it is</a>, while the rest of us make cute little visualizations about others' struggles. 

Week 4, first week with a Bye so we had 15 games instead of the usual 16. Who broke even? Not CBS or FiveThirtyEight. Uh-uh, each of them had only 7 wins SUP. FOX did them one better and our big winner was ESPN with 9 wins for a weekly winning percentage of 60%. That wouldn't even get me a passing grade in Spanish class. Los siento, expertos!<sup id="a4">[4](#f4)</sup> 

On the season the experts/models are not much more impressive. Each of them are lingering, like a stale fart, at 35-37 wins. <a href="https://www.youtube.com/watch?v=oOoqtsNReIU" target="_blank">Shiiit</a>, my random generator has 28 wins alone.<sup id="a5">[5](#f5)</sup> 

<img src="/gallery/2016/football-picks/bs_wins_wk04b.png" alt="bs_wins_wk04" /><br>

Above is a representation of the weekly (x-axis) performances by source (y-axis). The larger the cirlce the more wins for the given source/week.

<img src="/gallery/2016/football-picks/bs_wins_key.png" alt="bs_wins_key" /><br>

The lighter and more yellow the color the better performing on the Brier Score (BS), darker and green colors represent the opposite.

<img src="/gallery/2016/football-picks/bs_score_key.png" alt="bs_score_key" /><br>

On the right side of the main plot we have a second chart that summarizes the season to date. Each bar is in line with the sources on the original y-axis and their length represents total wins SUP. The color saturation follows the same meaning as for the circles. 

Bear in mind however, that the colors are relative to the universe of inputs. For instance, in a world where G-d is making game predictions and is getting everything right, naturally, he/she would have a BS of 0, because again it's G-d, and the yellow would represent that low of a number. Meanwhile, someone who got every pick 100% wrong, <a href="https://youtu.be/8PLSyFzk-6g?t=1m7s" target="_blank">a mush</a>, would have a BS of 1 and a color of dark green, ironically the color of money. Those colors are represented above, but again they are relative to the universe of these 5 sources. This decision was made to make differentiation more easy.

---

## Week 3 - Well, That Escalated Quickly

Rough week for the favorites, human prognasticators, and predictions in general. Where should we even start? Ten of 16 games were unanimously agreed upon (SUP) by the panels/models, but half of them proved incorrect. Meaning if we were using the unanimous model selections there would be a just better than one-third chance (34%, 0.875x0.778x0.5) of making it to Week 4 in a suicide pool. This is definitely something that's made me repeatedly curious, you can expect a graphic of some sort in the coming weeks. 

We mentioned getting into the betting line and this is us tipping in our toe. Of the 16 betting line favorites 9 lost outright, 6 of which were home favorites. The breakdown of the aforementioned favorite performances by week to date:

|Week|Betting Line Favorite W's SUP|Home Favorite W's SUP|
|---|---|---|
|Week 1 | 62.5% (10/16)| 55.6% (5/9)|
|Week 2 | 62.5% (10/16)| 66.7% (8/12)|
|Week 3 | 43.8% (7/16)| 50% (6/12)|

Below is an interactive graph showing game outcomes by home teams through week 3. The x-axis displays the number of points the home team was either favored or not-favored by. The y-axis displays the point difference (PTD) of the final game score for the home team (positive for wins, negative for loses; it's not rocket surgery, stick with me). The 4 quadrants created by these two axes, starting in the top right box and moving clockwise, are winning favorites (+x, +y), losing favorites (+x, -y), losing dogs (-x, -x), and winning dogs (-x, +y). The color/shape of the marks indicate conference (red circles for AFC, blue squares for NFC). Game details such as teams, final score, and home line can be identified by hovering over the marks. Lastly, there is a 45-degree dashed line bisecting quadrants I and III, winning favorites and losing dogs, respectively. This is the home line that identifies wins/loses against the spread (ATS). The size of the circles/boxes are an indication of how greatly the final PTD differed from the home line.

<iframe src="http://endlesspint.com/gallery/2016/football-picks/sup_ats.html" width="640" height="640" marginwidth="0" marginheight="0" scrolling="no" frameBorder="0"></iframe><br>
<sub>Data Source: <a href="http://www.sportsline.com/nfl/odds/" target="_blank">SportsLine</a> and <a href="https://gist.github.com/endlesspint8/2eaae1e452ce7d5a5edd46277c0459fb#file-nfl_sup_ats_bokeh-py" target="_blank">Code</a></sub>

Plans are to update this graph weekly, leaving a static image in its place to capture the week 3 snapshot:

<img src="/gallery/2016/football-picks/sup_ats_wk3.png" alt="sup_ats_wk3" /><br>
<sub>Data Source: <a href="http://www.sportsline.com/nfl/odds/" target="_blank">SportsLine</a> and <a href="https://gist.github.com/endlesspint8/2eaae1e452ce7d5a5edd46277c0459fb#file-nfl_sup_ats_mpl-py" target="_blank">Code</a></sub>

The two data models, FiveThirtyEight & FOX, performed best, both for wins and Brier Score (BS). Meanwhile, the humans of CBS and ESPN proved easily swayed by favorites, picking 14 of 16 to win (though there was a slight discprency on two of the choices). As we have noted in numerous places in this piece the experts are prone to unanimous votes of their own, something we have been smoothing to help damper the impact of such situations. Despite the "dampering" both data models leap frogged our previous front runner, CBS, putting themselves in the top too spots followed by the expert panels, with not much to differentiate this latter pair. The Random game picker incidentally made the greatest gains (keep in mind a low Brier Score, BS, is preferable) and following another similar week may be breathing down the necks of the "experts" (too soon for quotes? time will tell).

**Predictive Standing, Straight Up
(with Wk 3 change in parantheses)**

|Source|Season Brier Score|Season Wins|
|---|---|---|
|FiveThirtyEight (in situ)|0.217 (-0.002)|30 (+10)|
|FOX (in situ)|0.253 (-0.009)|27 (+10)|
|CBS (regularized)|0.281 (+0.063)|28 (+5)|
|ESPN (regularized)|0.282 (+0.046)|27 (+7)|
|Random|0.353 (-0.049)|22 (+10)|

---

## Week 2 - Back to the Future Full Season Recap 

As we plod along tracking game prediction accuracies week-to-week it may be tempting to get lost in the most current data and side tracked by the latest revisions. With that idea in mind let us now take a moment to look forward and document what the two quant models, by FiveThirtyEight and FOX, predicted for the season by using their respecitve game-by-game winning probabilities.

FiveThirtyEight provides a team-by-team season win total, released preseason and updated weekly. No need to reinvent the wheel, however there is, to the best of my web surfing, no breakdown of how this looks by conference and/or division. That could be meaningful for playoff purposes. Below is table of the preseason expected wins for FiveThirtyEight. Teams are grouped first by conference, then by division, and sorted by overall wins, followed by division and conference wins. I have highlighted the division winners and the additional two wild card teams per conference.

**FiveThirtyEight Game Probability Season Standings**

<img src="/gallery/2016/football-picks/538_prob.PNG" alt="538 prob" /><br>
<sub>Data Source: <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a></sub>

FOX does not even provide an overall win total for the teams, again to the best of my web surfing, which made this excercise worthwhile just to see where they stand big picture. The table is similarily grouped and sorted. By the way, the wins for both tables were calculated with the following <a href="https://gist.github.com/endlesspint8/2eaae1e452ce7d5a5edd46277c0459fb#file-nfl_season_standings_w_prob-py" target="_blank">code</a>.

**FOX Game Probability Season Standings**

<img src="/gallery/2016/football-picks/FOX_prob.PNG" alt="FOX prob" /><br>
<sub>Data Source: <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>

Clearly a good amount of overlap but also some interesting differences in details to keep in mind moving forward (win distributions by conference and division; outcome of competitive divisions [NFC East, especially]). 

**Notes & Updates to Last Week**

FiveThirtyEight's model improved against its preseason predictions in both wins, making one game prediction change (from CHI to PHI), and BS. FOX recalibrated from its preseason predictions with less success. FOX's model made two game prediction changes, but only one of them turned out to be correct (IND to DEN). Additionally, the probabilites for wins were further off post-recalibration. CBS continues to hold strong, slightly edging out FiveThirtyEight's model with respect to BS and predicting three more games correctly. 

**Predictive Standing, Straight Up**

|Source|Season Brier Score|Season Wins|
|---|---|---|
|CBS (regularized)|0.218|23|
|FiveThirtyEight (in situ)|0.219|20|
|FiveThirtyEight (a priori)|0.221|19|
|CBS|0.232|23|
|ESPN (regularized)|0.236|20|
|FOX (a priori)|0.255|17|
|ESPN|0.256|20|
|FOX (in situ)|0.262|17|
|Random|0.402|12|

Things to look out for: 

* quant model recalibrations and subsequent performance (FiveThirtyEight has a 1.00 win% on changes; FOX is at 0.50, granted on a _tiny_ sample set)
* random predictive performance (improved from last week)
* continue to monitor human/experts against regularized  panel probabilities, possibly drop outright votes based on future performance
* suicide pool survival based on unanimous picks (& win% for same)
    * Unanimous picks: Week 1, 7/8 correct (87.5%); Week 2, 7/11 correct (77.8%)

|away|home|away_score|home_score|winner|unanimously|
|---|---|---|---|---|---|
|BAL|CLE|25|20|BAL|correct|
|CIN|PIT|16|24|PIT|correct|
|DAL|WSH|27|23|DAL|"nobody believed in us!"|
|MIA|NE|24|31|NE|correct|
|NO|NYG|13|16|NYG|correct|
|SF|CAR|27|46|CAR|correct|
|TEN|DET|16|15|TEN|"nobody believed in us!"|
|SEA|LA|3|9|LA|"nobody believed in us!"|
|TB|ARI|7|40|ARI|correct|
|ATL|OAK|35|28|ATL|"nobody believed in us!"|
|IND|DEN|20|34|DEN|correct|

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

### Week 1 Notes

 * **The CBS committee** had only of 3 of sixteen games wrong, incorrectly picking CAR, ARI and LA. The ARI choice was the most damaging as it was an unanimous selection resulting in the largest penalty possible for a prediction, 1.0. This was off-set by solid and confident choices in other places, such as the 3 other unanimous picks that did work out: HOU, SEA and PIT. This right away brings to mind the thought that human panels, certainly ones as small as these, are prone to over estimating probability of wins (granted the way I am using their input is not the intended purpose, but that's what makes it so fun). It is doubtful that the data models we will be dealing with in this exercise will ever give a probability of 1.00. This means that the human panels leave themselves open to big wins and big loses, as far as the Brier score is concerned (see table below showing average probabilities amongst the sources for the week, with the range of possible scores). <br>

|Source|Avg Prob of Pick|Best Possible BS|Worst Possible BS|
|---|---|---|---|
|CBS|0.766|0.055|0.586|
|FiveThirtyEight|0.633|0.135|0.401|
|FOX|0.658|0.117|0.433|
|ESPN|0.813|0.035|0.660|
|Random|0.789|0.045|0.623|

<br>

 * **This is something** worth keeping an eye on. If it turns out that this becomes too much of a detriment I will consider regularizing expert selections (numerators +1 & denominators +2).<sup id="a3">[3](#f3)</sup> In fact, I may just do this moving forward to have at my disposal. The choice of team will remain the same per panel but this step will help mitigate the exuberance of a unanimous decision. Again, time will tell which is the wiser approach. <br>

|CBS Panel Votes|CBS Panel Votes, Regularized|ESPN Panel Votes|ESPN Panel Votes, Regularized|
|---|---|---|---|
|4/8 (50%)|5/10, (50%)|5/9 (55.6%)|6/11 (54.5%)|
|5/8 (62.5%)|6/10, (60%)|6/9 (66.7%)|7/11 (63.6%)|
|6/8 (75%)|7/10, (70%)|7/9 (77.8%)|8/11 (72.7%)|
|7/8 (87.5%)|8/10, (80%)|8/9 (88.9%)|9/11 (81.8%)|
|8/8 (100%)|9/10, (90%)|9/9 (100%)|10/11 (90.9%)|

<br>

 * **FiveThirtyEight had 2** fewer overall correct choices than CBS but, as the above table suggests, the probabilty of these choices were low enough to not penalize their BS rating too greatly (avg of 0.588). When we dig a little deeper we see that both data models had lower averages for their poor picks than the human votes. What can account for this human confidence? Group think, hubris, more information? It could be as simple as our not taking more expert inputs into consideration. A short term solution would be combining the two panels into one. Something else to keep track of moving forward. <br>

|Source|Avg Prob of Correct Picks|Avg Prob of Wrong Picks|
|---|---|---|
|CBS|0.769|0.750|
|FiveThirtyEight|0.660|0.588|
|FOX|0.666|0.648|
|ESPN|0.808|0.822|
|Random|0.699|0.830|


 * **Half of the** games were unanimously agreed on by the panels/models, 7 correct and 1 wrong. <br>

|away|home|away_score|home_score|winner|unanimously|
|---|---|---|---|---|---|
|CHI|HOU|14|23|HOU|correct|
|CLE|PHI|10|29|PHI|correct|
|GB|JAX|27|23|GB|correct|
|MIN|TEN|25|16|MIN|correct|
|SD|KC|27|33|KC|correct|
|MIA|SEA|10|12|SEA|correct|
|NE|ARI|23|21|NE|"nobody believed in us!"|
|PIT|WSH|38|16|PIT|correct|

<br>

 * **There's currently no** difference between the "a priori" and "in situ" model simulations. Week 2 and beyond will introduce divergence between these two models and we will definitely be keeping an eye on how well the FiveThirtyEight and FOX models "learn" during the season. 

 * **Performace ATS will** be allowed to play out for another week or two in this space before being introduced. Part of the delay is considering how to include FiveThirtyEight and FOX models into the head-to-head match up with CBS. We have our ideas, are pretty confident of how to go about it, but want a little more time to get the wrinkles worked out and automated.

<br>

---

**Notes**

**intro**

<b id="f1">1</b> Except for NBC, at this point (week 1). These punks have not made their experts' picks readily available, at least not in the panel-friendly way of CBS and ESPN. [↩](#a1) <br>
<b id="f2">2</b> They are in fact all men. Sorry ladies. [↩](#a2) <br>

**week 1**

<b id="f3">3</b> Not a bad policy in dealing with prognostications in the real world either.  [↩](#a3) <br>

**week 4**
<b id="f4">4</b> Damn. I wish I could enter an upside down exclamation point for this sentence.  [↩](#a4) <br>
<b id="f5">5</b> Two Matthew McConaughey references in the same week. Let's make that the record. [↩](#a5) <br>

**week 5 & later**

<b id="f6">6</b>   [↩](#a6) <br>
<b id="f7">7</b>   [↩](#a7) <br>
<b id="f8">8</b>   [↩](#a8) <br>
<b id="f9">9</b>   [↩](#a9) <br>
