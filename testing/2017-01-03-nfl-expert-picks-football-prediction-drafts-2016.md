---
layout: post
title: Experts? Pfff, ... a season long digression
subtitle: This Week's Draft
---


Upcoming graphs:

1. <strike>wk04 - Bubble matrix: sources (y-axis); weeks (x-axis); z-bubbles (size~wins, color~brier)
2. wk05 - Bullet graph: in situ change win% v.
3. wk06 - Diverging Stacked Bar Chart ([Excel](http://www.slideshare.net/annkemery/diverging-stackedbarcharts)): 
 * ATS Arbitrage: 538 and FOX
 * home line: data model projection (DMP) > SPR = away; DMP < SPR = home; DMP == SPR = 'no pick' 
4. wk07 - pie chart (what?! wtf) unanimous wins / suicide paths 
5. wk08 - Heatmap: 
    
    a) SIMULATION: games won prob for 10k sims ([Bokeh](http://bokeh.pydata.org/en/latest/docs/reference/charts.html#heatmap) v [Plotly](https://plot.ly/python/heatmaps/)); </strike>
    b) ACTUAL: 4x4 SUP heatmap for favorites (both axes: AFC home/road & NFC home/road)
6. <strike>wk09 - Treemap: conf/div sup & ats
7. wk10 - small multiples of prob/source (x, top)/week (y, desc)/WL-split</strike>
8. wk11 - [pick source perform above .500](http://thedailyviz.com/wp-content/uploads/2013/02/Screen-Shot-2013-02-25-at-2.21.48-PM-620x383.png)
9. wk12 - [Stream graph](https://plot.ly/~empet/13409/streamgraph-with-minimized-wiggle-1/#code)... of something... BS, duh
10. wk13 - [donut chart](http://bokeh.pydata.org/en/latest/docs/gallery/donut_chart.html): sources in middle; "medals" replaced by home/road and/or fav/dog; regarding "and" of and/or: add a third ring to donut
11. wk14 - a priori wins/week [slopegraph](http://www.edwardtufte.com/bboard/q-and-a-fetch-msg?msg_id=0003nk); parallel coordinates of wins by source
12. wk15 - tree branch of... something
13. wk16 - [projected v actual arrow charts](https://public.tableau.com/static/images/TH/THTProjectedStandingsChanges/2014-2015ProjectedStandingsChanges/1_rss.png) ([Excel](http://peltiertech.com/arrow-charts-in-excel/))
14. wk17 - [bump graph / position time plot](http://vizthinker.com/wp-content/uploads/2014/01/BCS-Top-25-College-Football-2013-01.png); ([Excel](http://best-excel-tutorial.com/56-charts/306-bump-chart))

After Season

1. Expert panels: chalk and avg win shares
2. 


## Week 10 - Big Picture with Small Multiples
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 10</a></b></sub></p>

EDIT: `h4 id="week5WinProb" Average Model-Projected Win Probability for Changed Picks h4`

At the end of the week 5 post I listed in a table the "<a href="#week5WinProb">Average Model-Projected Win Probability for Changed Picks</a>", which now that I read the title have no idea what it means. Actually, it was meant to show the confidence that the data models had in their changed picks from the pre-season choices, by win/loss split. That little throw away insight got me thinking about looking at these numbers at a larger level, for all pick sources for the season to date.

There have been hints at what is presented this week right from the beginning, with an understanding that with only so many human experts per panel unanimous votes and high levels of confidence probabilities were more likely to occur than in the data models. Below we visualize this and see if anything interesting comes to the fore.

Two versions of the same data appear below. Each presentation may be considered an instance of <a href="https://en.wikipedia.org/wiki/Small_multiple" target="_blank">small multiples</a>, a data representation that is especially astute at making comparisons across many data points. See which one tells a story more clearly.

In the first instance we line up the sources across the ten weeks to date. The order of the bars is identical week to week, first the two expert panels, CBS and ESPN, followed by the two data models, FiveThirtyEight and FOX. The green bars extending up from the middle (50% to 90+% pick) represent the average confidence probability of winnig picks, the black bars extending downward show the average confidence probability of incorrect picks.

<img src="/gallery/2016/football-picks/wk10_smmult2.PNG" alt="wk10_smmult2" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>	
 
The second chart has the same data set but broken out by pick source across the top and the weeks down the lefthand side. This version makes it easier to compare confidence probabilities per source across weeks.

<img src="/gallery/2016/football-picks/wk10_smmult1.PNG" alt="wk10_smmult1" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>	

Between the two graphs it is clear that,

* the expert panels are routinely confident, cocky really, in their choices;
* the data models are much more restrained in their picks' confidence probability;
* FOX is most modest, but appears to be most consistent;
* FiveThirtyEight looks to have the best ratio of win/loss confidence probability.

However, all of the above is quite relative. A pick source may have only a couple of incorrect picks in any given week and if they had been overly confident the black bars would have you believe they had a rough week. In a sense they have, confidence in their picks should be questioned. I bring this up to remind the reader that it is not just getting picks right that matters but the level of confidence in the pick, which can help determine how trustworthy a source may be considered.

To that end I'm throwing in a freebie chart to smooth away the week to week anomalies and see big picture how much the sources can be trusted. Below is a simple bubble chart that represents the following:

* confidence probability of picks (x-axis)
* winning percentage of picks (y-axis)
* data source (color)
* number of picks (size)

Lastly, I have included a 45 degree gray line to serve as a guide to determine which picks are performing up to snuff and which are not.

<img src="/gallery/2016/football-picks/wk10_probwinbubble.png" alt="wk10_probwinbubble" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>	

The only sources above the diagonal line are from FiveThirtyEight and FOX. This says to me not to put too much credence in the expert panels. While most of the expert picks are above the outright .500 line (not visualized, but you can use your imagination), that would cut horizontally across the chart, this representation shows that the level at which picks made by the experts win are well below their expected frequency. 


## Week 9 - Team Performance: SUP & ATS
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 9</a></b></sub></p>

twitimg: pic.twitter.com/nTFzCRSFT8

It would have been nice to include everyone this week but our spotlighted team from last week, the Cleveland Browns, couldn't pull the upset and as a result they will be partly left out from this week's visual representation. Initially I thought this was inconvenient and a break in the streak of good luck I've had in the way the season has played out, being conveniently aligned with the visuals picked out, but then I realized this is equally perfect and suits the Browns' season just right.

Last week we looked at the universe of possible outcomes for each team over thousands of simulated seasons. This week, with every team having played eight games, we look at reality to date.

Below is a treemap (wiki link) that shows the share of wins by team, division, and conference as a spatial representation. This is done by grouping division teams spatially and by color, and splitting the conferences. Additionally the user may toggle between the two wins representations: straight up (SUP) and against the spread (ATS).

<iframe src="http://endlesspint.com/gallery/2016/football-picks/wk09_treemap.html" width="800" height="400" marginwidth="0" marginheight="0" scrolling="no" frameBorder="0"></iframe>
<sub>Vis Source: <a href="https://bl.ocks.org/mbostock/4063582" target="_blank">Mike Bostock</a></sub>

(it's halftime lyric)

While the above is not immediately linked to our picks' sources, it is not tangential either. The halfway point of the season seems like an appropriate time to see where we stand, who has under- or over-performed, and help recalibrate our knowledge and expectations moving forward.

ATS/SUP ratio: overachievers & underachievers

Expectation rating: SUP wins/times_favored * ATS/SUP ratio 


## Week 8 - Here's to Cleveland
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 8</a></b></sub></p>

Not a great year for the Browns to date. Through the first two months of the season they have a big fat doughnut in the win column, their loss total inching inexorably toward double digits. That's pretty rough but how likely is this? Let's look at some data to get an idea and get a grasp on the bigger picture as well.

In <a href="#week2">week 2</a> we took the pre-season game-to-game probabilities of FiveThirtyEight and FOX to determine the average expected wins for each team and thus create a projected final standings. We used these same game-to-game probabilities and ran the seasons over and over again, <a href="https://gist.github.com/endlesspint8/2eaae1e452ce7d5a5edd46277c0459fb#file-nfl_10k_season_sim-py" target="_blank">ten thousand times</a>. The purpose was to identify the probabalistic outcomes for each team. If you can write a for-loop, you can do statistics, <a href="https://www.youtube.com/watch?v=Iq9DzN6mvYA" target="_blank">right</a>? 

Chance of Seattle going undefeated: 0.12% according to FOX; the Jets going winless: 0% chance according to FiveThirtyEight and simulated seasons (phew!); Cleveland winning 8 games: 9.6% and 5.7% according to FiveThirtyEight and FOX, respectively. Those last odds look equal parts welcoming and wishful thinking at this point. 

Below is the full chart with hover tool to allow for reviewing the chances for each team (y axis) reaching specific win totals (x axis). The first is from FiveThirtyEight the latter from FOX.

<iframe width="810" height="720" frameborder="0" scrolling="no" src="//plot.ly/~ep8/6.embed"></iframe><br>
<sub>Data Source: <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a></sub>

The zero wins for Cleveland seem a bit "unfair" when both FiveThirtyEight and FOX gave them about a 60% chance of winning between 4-7 games. The lower end of that projection may still be in play but the higher almost certainly not.[FN: This is based on intuition. I did not break out win probabilities for first and second half of the season. Get your nerdy cousin to do the math, we're keeping it high level here.] So what happened, has the team been unlucky? I cannot say from watching the games (who watches Browns games?) but we can get an idea from looking at some game specifics and cumulative numbers to date. 

For one, the Browns have never been favorites in a game to date, despite five of their eight games being at home. On the flip side they have beated the spread four of eight times, so there's that (next week we'll present a visual that will allow for the toggling between SUP and ATS wins to see how they compare to other teams). Nor has Cleveland fooled any of the models but once. Through eight weeks and across four models/panels (CBS, ESPN, 538, & FOX) they have been picked against 31 of 32 times (talk about no one believing in them). Only in the most recent week were the Browns able to <strike>fool</strike> sway the FOX data model [FN: This is an in-season pick change and is indicative of the poor performance FOX has had on their revised picks to this point in the season (so far the in situ FOX model has done worse on both overall picks and Brier Score than the pre-season release).] into picking them over the Jets. 

Aside from some close games (a 2 point loss at TEN and half of the loses coming by 5 or fewer points) when we take a big picture view the Browns have the worst point differential overall (TB is worse at home; NYJ & SF are worse on the road). 

There are many possibilities before the beginning of the season, some more likely than others (see <a href="#week2">week 2</a> below), a few quite obvious in retrospect (never a remarkable talent). But the football gods can be a fickle bunch and it appears that Cleveland is taking the brunt of that so far. Perhaps a World Series win will make it all worth it. 

<iframe width="810" height="720" frameborder="0" scrolling="no" src="//plot.ly/~ep8/8.embed"></iframe><br>
<sub>Data Source: <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>

## Week 7 - Any Port in a Storm
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 7</a></b></sub></p>

More input is not always a good thing apparently. I would have hoped that the common and unanimous votes among the game picking sources, by necessity requiring an overlap of weights and perspecitve and thus being more restrictive, would result in a better correct pick percentage than relying on fewer sources. In five out of seven weeks this did not prove to be the case. 

Mixing picks between expert panels and data models usually resulted in a middling win percentage between the two and in one instance, week 6, even provided a percentage worse than either. The thinking was that there would be a majority of weeks like weeks 5 & 7 where the combination of inputs were greater than their parts. Consensus so far appears to compromise results, akin to "<a href="https://www.youtube.com/watch?v=QrGrOK8oZG8" target="_blank">Too Many Cooks</a>". We have yet to pass the halfway part of the season so I hold out hope that results will improve.

<img src="/gallery/2016/football-picks/wk07_consensus2.png" alt="consensus_picks" /><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>	

At the very least, in most cases the consensus model picks were better than just going with the favorite. So there's that.

An additional thinking beyond the unanimous picks being a safe way to choose winners (SUP) was that <a href="https://www.youtube.com/watch?v=KM2K7sV-K74" target="_blank">surely</a> it would provide valuable input for a suicide pool [fn: For those who are not familiar with this term/league, generally speaking each contestant must select one team per week to win; lose and you're out; pick correctly and you move on to the next week; continue until there is only one person remaining; you may NOT pick a team more than once in a season]. Where would we be if we followed the crowd (of experts and models), especially when they're all pointing in the same direction? Most likely for a <a href="http://www.surfing-waves.com/surf_talk.htm" target="_blank">wipe out</a>. Below is a pie chart (<a href="https://www.quora.com/How-and-why-are-pie-charts-considered-evil-by-data-visualization-experts" target="_blank">wtf</a>?!) [FN: Originally I thought of generating a tree branch visual of suicide paths but the itertions are at 95k+ through week 7 alone, for the still surviving paths, alone... ] representing the random surfing of going with the unanimous picks.

**Suicide Squad Wipe-Out**

<img src="/gallery/2016/football-picks/wk07_suicide_wave.png" alt="wk07_suicide_wave" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>	

Week 1 is in the center with each successive week occupying the next concentric circle outward, ending with the most recent week, week 7. Light blue represents the proportion of correct picks, dark blue the proportion of incorrect picks. Starting with week 2, the second circle out from the center, the graph introduces black as the color that represents the lost opportunities of previously incorrect choices. This is a fanciful illustration of, to mix metaphors, how difficult it would be to thread the needle and survive into week 8, just under 3%.

That low chance of survival is slightly overly optimistic due to the naive representation above which <a href="https://gist.github.com/endlesspint8/2eaae1e452ce7d5a5edd46277c0459fb#file-nfl_suicide_wave-py" target="_blank">simply calculated percentages</a> and did not take into consideration previous picks (see footnote re suicide pools and picking teams to see how this matters).

_Maybe you're in the <a href="https://www.youtube.com/watch?v=HSfxl1KI6y8" target="_blank">middle of a storm</a>, the sky is falling in on your head, the waves are crashing over your little boat, the oars are about to snap..._


## Week 6 - Arbitrage (maybe)
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 6</a></b></sub></p>

Most of the previous posts have had to do with wins and loses straight up (SUP). There was a brief dipping of the toes into performance against the spread (ATS) back in week 3 but that had more to do with home team performances by conference and did not look at predictions. Today we take more of a dip into predictions ATS and evaluate performances to date. 

There are four sources of ATS predictions: 

* CBS expert panel 
* Random predictor
* FiveThirtyEight data model
* FOX data model

I will take these four and deal with them in pairs first, for reasons that will become clear, CBS v. random & FiveThirtyEight v. FOX.

CBS panel predictions for ATS are devised similarly to SUP: each expert gets a vote; majority determines pick; in case of tie, dog gets the pick (as compared to road team for SUP); and the votes are regularized to avoid harsh Brier score (BS) penalties for unanimous choices. 

The random number generator simply takes the dog if it returns 0.500 or larger. That's it. No regularization beyond that. The pick is made and we move on. 

Given the nature of picking ATS, where favorites have to win by a certain amount of points, it stands to my expectations that the random generator would fare better here than in SUP, where no knowledge is leveraged. This expectation has so far turned out to be validated. 

Though by some fluke coincidence the number of correct picks by the **Random** "models"[fn: two separate number generators were implemented, one for SUP and one for ATS] is identical, 41, for both SUP and ATS through week 6, this number carries different significance in each context. Forty-one correct picks for SUP places it last in the standings against the other sources while beating out the CBS experts in ATS: 41 correct picks versus 38 for the human panel. 

**Predictive Results, Against the Spread** (three games tied ATS)

|Source|Season Brier Score|Season Wins|
|---|---|---|
|Random|0.351|41|
|CBS|0.329|38|
|CBS (regularized)|0.305|38|

In fact, the random ATS picks come close to matching the data model choices but I'm getting ahead of myself. Let's introduce those models and how we calculated their picks ATS. 

The data models of FiveThirtyEight and FOX do not make outright predictions against the spread. This is not technically true for FOX but due to the nature of ever changing lines and the need to standardize a source (Sportsline in this article) to measure against I am treating the two models in a similar way. 

For both data models we use the in week most up-to-date projections ("in situ"). FiveThirtyEight provides an ELO-based spread for each game while FOX provides average final scores based on 10k game simulations. I used the FiveThirtyEight lines and FOX score differentials to determine who the models favored and by how much. I compared the data models' lines against the current week's line and used the discrepencies as proxies for picks ATS. 

Examples of what I mean can be outlined in the table below.

|Week|Game|Home Line|538 Home Line/Pick|FOX Home Line/Pick|
|---|---|---|---|---|
|week 1|LA @ SF|2.5|-1 (SF)|6.1 (LA)|
|week 3|SF @ SEA|-9.5|-8.5 (SF)|-10.3 (SEA)|
|week 6|NYJ @ ARI|-7.5|-6 (NYJ)|-4.2 (NYJ)|

Now a quick rundown through the rows to explain what is listed.

* Week 1 - SF is a 2.5 point dog; FiveThirtyEight views SF as a one point favorite; FOX thinks of SF as an even bigger dog.
* Week 3 - SEA is favored by 9.5; FiveThirtyEight sees SEA as less of a favorite; FOX likes SEA even more.
* Week 6 - ARI is favored by 7.5; both FiveThirtyEight & FOX consider ARI less of a sure thing, they pick NYJ.

The above comparisons were done on a game by game basis. Where games ended in a tie ATS (3 times) results were not calculated. In the unlikely event that lines matched (FiveThirtyEight == SporstLine OR FOX == SporstLine) game picks were not made for that model on that game (there was no advantage in using that specific model, no arbitrage).

Okay, enough with the foreplay. Let's get to this week's visualization. Below are a pair of diverging stacked bar charts, one a piece for FiveThirtyEight and Fox related to their ATS picks performance. Each horizontal bar represents a week of games to date with week 1 at the top going down in chronological order to week 6. 

<img src="/gallery/2016/football-picks/wk06_538_ats3.png" alt="wk06_538_ats" /><br>	
<sub>Data Source: <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a></sub>

There is an invisible line down the middle of each graph that demarcates the boundary between away picks (left) and home picks (right). The sections on either side of this boundary have two different hues. The lighter hues, the ones grouped around the middle, represent the number of incorrect picks (home or away). The darker hues on the end represent the correct picks or the "wins".

<img src="/gallery/2016/football-picks/wk06_FOX_ats3.png" alt="wk06_FOX_ats" /><br>
<sub>Data Source: <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>

I find these representations to be very helpful in identifying:

* **General skew** - FOX clearly prefers the road teams; FiveThirtyEight is more balanced in its choices
* **Pick breakdown week to week** - FiveThirtyEight was road heavy in week 3, home heavy in week 5
* **Zero categories** - zero home loses FiveThirtyEight/week3; zero home wins FOX/week 6; zero away picks FiveThirtyEight/week 5
* **Total weekly selections** - when bars line up, or are close to lining up (FOX: weeks 1,3,4,&5), you can quickly see a difference in length providing a visual distinction total games.  

While helpful in giving an overview of comparative performance I will spare you the work of summing the numbers to determine the final breakdown of the above. The pick count breakdown of above:

**Predictive Results, Against the Spread** (three games tied ATS)

|Model|ATS Away W's|ATS Away L's|ATS Home L's|ATS Home W's|
|---|---|---|---|---|
|FiveThirtyEight|21|15|21|25|
|FOX|33|34|11|10|

If you're going to use a model, go with FiveThirtyEight's ATS.

## Week 5 - Less Words, More Empathy
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 5</a></b></sub></p>

One motivating drive of this ongoing piece is to set up the premise using words, tables, and simple graphs, especially in the beginning, and then allow subsequent visuals to speak for themselves and deliver the information. Thus the drop off in word count from week to week is intended both by design and disposition (lazy efficient, if you will). 

A recurring and expected theme is that football game predictions are difficult, not quite stock picking difficult where a <a href="https://priceonomics.com/how-well-do-blindfolded-monkeys-play-the-stock/" target="_blank">blindfolded monkey</a> is likely to outperform you in the market, but difficult. For that reason I try to keep my derision to a minimum, especially when it comes to the data models. I don't want to be a on the machines' (s)hit list when they <a href="https://youtu.be/JJ1yS9JIJKs" target="_blank">take over</a>. 

This week the game prediction results SUP aligned perfectly for my implementing a <a href="https://en.wikipedia.org/wiki/Bullet_graph" target="_blank">bullet graph</a> to show where we stand to this point in the season. Specifically, through week five the human expert panels, both CBS and ESPN, accumulated an identical number of SUP wins, 43. This coincidence allows for the traditional three category background of the bullet graph (and the added benefit of more easily appropriating  <a href="http://www.d3noob.org/2013/07/introduction-to-bullet-charts-in-d3js.html" target="_blank">available code</a>; lazy efficient), but I am getting ahead of myself. 

Below is an example graph with labels for clarification. It is fairly self-explanatory and we will be going over the parts a second time when we breakdown the game prediction results further below. There is really no need then to continue reading this paragraph. I will assume you will take that not so subtle hint to skip ahead. Now that you're gone I'll just ramble a bit... about... puppies? Sure, they're adorable. I don't care if you're not a dog person you have to admit they are the cutest things around. Better than babies. Okay, I'm done now.  

<img src="/gallery/2016/football-picks/bullet_legend_wk05.PNG" alt="bullet_legend" /><br>

Using the above image as a guide we can confidently make sense of the visual below. I am going to spell it out so if you already understand how to read these graphs jump ahead and/or see you next week. 

First, the grey backgrounds from left to right: 32 random correct picks, 43 expert panel correct picks, of 77 total games.

Second, the color bars: 45 in season/situ FiveThirtyEight correct picks shown by the orange line & 42 in season/situ FOX correct picks shown by the dark blue line.

Third, the floating black marks or "comparative measures": 46 and 45 preseason/a priori correct picks by FiveThirtyEight and FOX, respectively.

**Bullet Graph of SUP Wins thru Week 5**

<img src="/gallery/2016/football-picks/bullet_wk05b.PNG" alt="bullet_wk05b" /><br>

Bullet graph take aways:

* Preseason data models have been the top performers with respect to correct picks SUP.
* Both of the in-season data models, FiveThirtyEight & FOX, have under performed their preseason win totals to date.
* FiveThirtyEight has been the best in-season game predictor so far, followed by both expert panels (CBS & ESPN), and the data model used by FOX.
* Our random picker is performing at less than 50% correct picks. Perhaps those blindfolded monkeys aren't such hot stuff afterall (so far!).

Something the graph does not show are the number of changed picks per model. It may be tempting to make the incorrect leap, using just the above graph, into thinking there has been a change of only a game or two so far. Not so. FiveThirtyEight has made 5 in-season pick changes (2 wins/3 loses) and FOX 13 (5 wins/8 loses). 

Of course the other element the graph does not cover is BS score (nor is it intended to). This will be a focus in the next week or so but I will provide the following probability table as a wrap up. Make of it what you will.

**Average Model-Projected Win Probability for Changed Picks** 

<h4 id="week5WinProb">Average Model-Projected Win Probability for Changed Picks</h4>

||Wins|Loses|
|---|---|---|
|538|0.51|0.55|
|FOX|0.55|0.60|

<sub>I couldn't resist my 2¢: the modles don't give you much to choose between; when they're confident they're wrong, when they're less confident they may win. Make of it what you will, after all.</sub>

## Week 4 - I'm Just a Professional
<sub><a href="http://bit.ly/2d3tw04">Tweet</a> Week 4</sub>

_That's what everyone keeps saying and I'm getting sick and tired of hearing it_. Now that I'm done channeling my inner <a href="https://youtu.be/DYa6FNKSgbk" target="_blank">John Creasy</a> let's get on with what is turning into a less than impressive showing for the game pickers. I guess there's a reason people get paid big bucks for calling it <a href="http://www.imdb.com/title/tt0417217/?ref_=nm_flmg_act_26" target="_blank">like it is</a>, while the rest of us make cute little visualizations about others' struggles. 

Week 4, first week with a Bye so we had 15 games instead of the usual 16. Who broke even? Not CBS or FiveThirtyEight. Uh-uh, each of them had only 7 wins SUP. FOX did them one better and our big winner was ESPN with 9 wins for a weekly winning percentage of 60%. That wouldn't even get me a passing grade in Spanish class. Los siento, expertos! [fn: Damn. I wish I could enter an upside down exclamation point for this sentence] 

On the season the experts/models are not much more impressive. Each of them are lingering, like a stale fart, at 35-37 wins. <a href="https://www.youtube.com/watch?v=oOoqtsNReIU" target="_blank">Shiiit</a>, my random generator has 28 wins alone. [fn: Two MM references in the same week. Let's make that the record.] 

<img src="/gallery/2016/football-picks/bs_wins_wk04b.png" alt="bs_wins_wk04" /><br>

Above is a representation of the weekly (x-axis) performances by source (y-axis). The larger the cirlce the more wins for the given source/week.

<img src="/gallery/2016/football-picks/bs_wins_key.png" alt="bs_wins_key" /><br>

The lighter and more yellow the color the better performing on the Brier Score (BS), darker and green colors represent the opposite.

<img src="/gallery/2016/football-picks/bs_score_key.png" alt="bs_score_key" /><br>

On the right side of the main plot we have a second chart that summarizes the season to date. Each bar is in line with the sources on the original y-axis and their length represents total wins SUP. The color saturation follows the same meaning as for the circles. 

Bear in mind however, that the colors are relative to the universe of inputs. For instance, in a world where G-d is making game predictions and is getting everything right, naturally, he/she would have a BS of 0, because again it's G-d, and the yellow would represent that low of a number. Meanwhile, someone who got every pick 100% wrong, <a href="https://youtu.be/8PLSyFzk-6g?t=1m7s" target="_blank">a mush</a>, would have a BS of 1 and a color of dark green, ironically the color of money. Those colors are represented above, but again they are relative to the universe of these 5 sources. This decision was made to make differentiation more easy.


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

Upcoming graph: Home Team W/L SUP & ATS: favored-by (x-axis); ptd (y-axis); home line (45• m==1 dashed line)
 - two versions: AFC/NFC; week 3

**TODO**: create 1-season "refreshing" win standings, to show variation, using win prob

1. loop through games and pick winner based on prob & Math.random()
2. winning team += 1
3. pass team & wins, along with conf & div, to json (maybe?)
4. [create table](http://www.d3noob.org/2013/02/add-html-table-to-your-d3js-graph.html) from json
5. [sort table](http://www.d3noob.org/2013/02/more-d3js-table-madness-sorting.html) by conf, div, wins
6. apply color coding: font per conf; row per div winners
<br>

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
    * 
---

<h2 id="week2">Week 2 - Back to the Future Full Season Recap</h2> 

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

