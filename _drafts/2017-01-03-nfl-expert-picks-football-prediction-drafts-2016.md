---
layout: post
title: Experts? Pfff, ... a season long digression
subtitle: This Week's Draft
---

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

Things to be looking out for: 
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



**TODO**: create 1-season "refreshing" win standings, to show variation, using win prob

1. loop through games and pick winner based on prob & Math.random()
2. winning team += 1
3. pass team & wins, along with conf & div, to json (maybe?)
4. create table from json
5. sort table by conf, div, wins

 * http://bl.ocks.org/LeeMendelowitz/11383724
 * http://bl.ocks.org/jfreels/6734025
 * http://bl.ocks.org/gka/17ee676dc59aa752b4e6
     * https://gist.github.com/gka/17ee676dc59aa752b4e6
 

Misc

 * http://bl.ocks.org/mmparker/3670696
 * http://www.d3noob.org/2013/02/add-html-table-to-your-d3js-graph.html
 * http://www.d3noob.org/2013/02/update-d3js-data-dynamically-button.html
 * http://bl.ocks.org/mbostock/4061502
 
Season line-chart

 * https://derekswingley.com/2016/01/22/make-a-chart-from-a-table/
    * http://bl.ocks.org/mbostock/3883245
    * https://gist.github.com/swingley/b5fb2cdf5532581c26b0
