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
7. wk10 - small multiples of prob/source (x, top)/week (y, desc)/WL-split
8. wk11 - [pick source perform above .500](http://thedailyviz.com/wp-content/uploads/2013/02/Screen-Shot-2013-02-25-at-2.21.48-PM-620x383.png)
9. wk12 - [Stream graph](https://plot.ly/~empet/13409/streamgraph-with-minimized-wiggle-1/#code)... of something... BS, duh
10. wk13 - [donut chart](http://bokeh.pydata.org/en/latest/docs/gallery/donut_chart.html): sources in middle; "medals" replaced by home/road and/or fav/dog; regarding "and" of and/or: add a third ring to donut
11. wk14 - conf% v win% [slopegraph](http://www.edwardtufte.com/bboard/q-and-a-fetch-msg?msg_id=0003nk) in [Excel](http://peltiertech.com/slope-graphs-in-excel/), prolly MPL; wk10 bubble chart revisited</strike>
12. wk15 - tree branch of... something; rather [ROC curves](https://en.wikipedia.org/wiki/Receiver_operating_characteristic)/source with weekly dots 
13. wk16 - [projected v actual arrow charts](https://public.tableau.com/static/images/TH/THTProjectedStandingsChanges/2014-2015ProjectedStandingsChanges/1_rss.png) ([Excel](http://peltiertech.com/arrow-charts-in-excel/))
14. wk17 - [bump graph / position time plot](http://vizthinker.com/wp-content/uploads/2014/01/BCS-Top-25-College-Football-2013-01.png); ([Excel](http://best-excel-tutorial.com/56-charts/306-bump-chart))

After Season

1. Expert panels: chalk and avg win shares
2. 



## Week 17 - The End of a Bumpy Road
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 17</a></b></sub></p>

After four short months we conclude this piece with a final overview of how the season played out for our respective sources. I will focus on the straight up (SUP) picks since this includes all sources, we never did find a way to attribute against the spread (ATS) picks to ESPN. First up are the win totals for the season followed by a bump chart showing weekly and cumulative rankings for the season. 

Only on a few (fluke?) occasions was the random game picker not in last place. This could have been expected by intuition (there's obvious information in game match-ups) or gleaned from the <a href="#week11">week 11</a> above/below .500 graph. When it came to the SUP comparisons we saw a clear split between the actual game sources and the "coin flip".

|Source|Season Wins|1st Place (weekly)|
|---|---|---|
|FiveThirtyEight (in situ)|**161**|**7**|
|ESPN (regularized)|160|5|
|CBS (regularized)|157|**7**|
|FOX (in situ)|157|4|
|RANDOM|117|1|
 
<img src="/gallery/2016/football-picks/wk17_bump_chart_wins.PNG" alt="wk17_bump_chart_wins" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>

Of course we could not possibly sign off without one final mention of the Brier score (BS). Full season numbers and positioning again in table format followed by a similar bump chart to catalog the season's progress.

|Source|Season Brier Score|1st Place (weekly)|
|---|---|---|
|FiveThirtyEight (in situ)|**0.221**|**8**|
|FOX (in situ)|0.233|3|
|ESPN (regularized)|0.246|2|
|CBS (regularized)|0.253|4|
|RANDOM|0.360|0|

<img src="/gallery/2016/football-picks/wk17_bump_chart_BS.PNG" alt="wk17_bump_chart_BS" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>

All in all FiveThirtyEight held tough and proved the most trusted source of game picks on a number of different metrics. It was close all the way through, however. 

Any big surprises? Tough to say after 17 weeks of being submerged in the process. While it may take some time to fully appreciate what to make of all this I fully acknowledge how difficult the picking of games is. This was especially underscored by no one model running away with the season. There were moments when that looked like it would happen but as far as this season playing out the breakout never occurred.

A quick look at ATS, where the random model did considerably better (with a wrinkle). 

|Source|W-L-D|win%|ATS BS|
|---|---|---|---|
|CBS|128-120-8|.5|0.302|
|FOX|119-122-8, no pick: 18|.478|n/a, <a href="#week6">week 6 arbitrage</a>|
|538|114-118-8, no pick: 28|.475|n/a, <a href="#week6">week 6 arbitrage</a>|
|RAN|121-127-8|.473|0.337|

Though the random selection of ATS games turned out more correct picks than either FiveThirtyEight or FOX, it did so at a lower percentage. This was due to spreads sometimes matching those estimated by FiveThirtyEight and/or FOX, resulting in "no picks" on those occassions for those sources. As a result the random choices turned up _both_ more wins _and_ more loses.

Going back to fully appreciating what this entire effort has meant, I think it is safe to say that the findings are full or wrinkles, like I just said, and nuances. I will be updating all of the below graphs over the coming weeks with full season numbers, some new commentary, and additional charts as a PDF file [sign up for update link].

## Week 16 - Arrows Abound
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 16</a></b></sub></p>

It is not clear if my coverage over the past several months has come across as dismissive or condescending of the game predictions. Believe me that has not been my motivation or purpose. The times I do bring up less than spectacular performance is more meant to highlight the difficulty of the task rather than heap any disparagement on the sources. Am I getting defensive? No, not really, but I think it's worthwhile re-calibrating every once in a while, even at this late stage.

With respect to being late in the season I thought it was worth looking back at what some of the preseason expectations were and how the season played out as a comparison. This recap will hearken back to week two when we highlighted the average expected win totals for teams by both FiveThirtyEight and FOX (the only two where we could take such a long term view).

In case you can't be bothered to remember or click back… Even with one more week of games looming we can get a general idea of the difference between expectations and reality.

I've taken the expected win totals, rounded to whole games, identified the difference between this number and win totals through week 16 (giving half a game to ties). Again, this throws off the final analysis by a game but the visuals below still get across the point. The difference is in actual wins versus expectations, with differences sorted by biggest positive results at the top, trickling down until we get to the biggest duds against expectations.

To help some of these graphs I have calculated root mean squared error  (RMSE) different for each. This one number score, FiveThirtyEight and FOX, helps provide a quick comparison. 

There are a few strands that we can follow from here. First and foremost we see which data modeling source had the most accurate expectations overall. From here we can look at the changes in game predictions. FOX for instance switched its choices of winning team more often than FiveThirtyEight. Naturally we can then look at the winning performance of those changed game picks (week five). Lastly, we see what the overall win-total and Brier scores are, not just for the data models but also bringing in the human expert panels (next week). 


## Week 15 - It's the ROC! 
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 15</a></b></sub></p>

Didn't mean to beat you over the head with all of those confusion matrices back in week 13. I'm referring to the true positives, false positives, etc. of the home/favorite picks. Now, I don't regret bringing it up mind you but I realize I may have left you hanging, which was partly by design. Whether you were confused (pun'd!) or wanted more the following is meant to resolve either situation. 

To better summarize the performance of our game classifiers we will use a variation on the <a href="https://en.wikipedia.org/wiki/Receiver_operating_characteristic" target="_blank">ROC curve</a>. Here a classifier's performance is determined by mapping it's true positive rate against its false positive rate. A 45° line is drawn from the bottom left to the upper right hand corner as a guide. This line represents a random classifier, a.k.a. a coin flip. If your classifier does not get above this threshold you're in trouble. A quick look at the confusion matrices I mentioned earlier shows that each of the pick sources avoided the ignominy of falling below this threshold. At least up until then they had.

Those week 13 numbers were an aggregate up to that point in the season however. Breaking out the picks into weekly performance provides a more mixed picture. More than a few times we see our experts and models under performing.

<img src="/gallery/2016/football-picks/wk15_oneplot.png" alt="wk15_oneplot" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>

The above is a little busy so we will split apart the sources into their own separate subplots. That's better. Now we more clearly see the weekly dots, with sizes representing the number of games predicted when a home favorite was in play.

<img src="/gallery/2016/football-picks/wk15_subplots.png" alt="wk15_subplots" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>

The above charts contain the performance through the latest week, in which we saw both human expert panels dip just below the 45° line (random pick performance).

**Updated Sensitivity (TPR) and Specificity (FPR) through week 15**

||TPR|FPR|
|---|---|---|
|cbs|0.824|0.827|
|espn|0.863|0.865|
|538|0.931|0.827|
|fox|0.833|0.750|

There is an additional tool available to help measure this sort of performance still further. Different subject areas will require different considerations of what makes an _effective_ classifier. For example, tracking fraudulent credit charges typically allows for fewer false positives then a medical screen. Regardless of the subject area however, when dealing with the same classification task, in our case correctly picking football games, you may leverage the use of one number to compare competing classifiers: the area under the curve, (<a href="https://en.wikipedia.org/wiki/Receiver_operating_characteristic#Area_under_the_curve" target="_blank">AUC</a>).

Basically, the larger the shaded region under the line the better.

Using the most recent TPR and FPR rates I plotted this area for each game prediction source. Below are the less than pretty results.

<img src="/gallery/2016/football-picks/wk15_auc_plots.png" alt="wk15_auc_plots" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>

Ouch! Consider that if one had simply chosen all home favorites (154) to win (102 did in fact win), adding no discriminatory sophistication, the resulting TPR and FPR would be 1.0 each (landing on the top right corner of the plot). The AUC for such a scenario would be .500.   

## Week 14 - Slippery Slope 
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 14</a></b></sub></p>

<p>At the start of this process I wasn't sure how well the Brier score (BS) measure would resonate, with myself included. I've done my best to bring it up, occasionally highlighting it, but also attempting to not beat the reader over the head with it. <img src="http://endlesspint.com/gallery/2016/football-picks/wk14_slopegraph.png" alt="wk14_slopegraph" width="360" height="900" align="right"> In some respects the weekly visuals are an effort to make BS a more intuitive yardstick.</p> 

<p>A couple of weeks back I thought I may have hit upon an approach that drove home the point (without even specifying the metric). This was back in <a href="#week10">week 10</a> where I provided a throwaway graph in the form of a bubble chart, plotting the confidence percentage by source against the actual winning percentages. What that chart meant to show, in a simple though occasionally busy and cluttered way, was the general reliability of the sources or lack there of. Simply by identifying the color of the bubble (source), it's size (number of said predictions), and placement above or below the 45° line (beating or missing expectations, respectively) the user could see who was the most reliably trustworthy.</p>

<p>This week I apply the same motivation with updated data to present this takeaway once more. Instead of dots or bubbles I implemented lines in a slope graph. The left hand position of the plot represents the percentage confidence of the prognosticating sources. On the right side we have the resulting winning percentages. Line colors represent the sources, thickness the game counts, and the slope of the line, whether upwards or down, how far off the sources are from their intended outcome. A flat horizontal line would signify expectations matching results. An upward moving line from left to right would indicate beaten expectations while a downward slanting line the opposite.</p>

<p>A few things of note. The human panel sources have fewer, thicker, and downward sloping lines. The fewer and thicker aspect go hand-in-hand as the human panels have a set number of experts, resulting in a reliably repetitive set of possible confidence percentages week-to-week. The data models being more "fine-tuned" provide something closer to a continuous range of confidence percentages, resulting in many more and thinner lines. While it is not possible for us to break out the human panel picks into more fine-level percentages, which might allow us to see some upward moving lines, we are able to <a href="https://gist.github.com/endlesspint8/2eaae1e452ce7d5a5edd46277c0459fb#file-nfl_bucketize-py" target="_blank">bucket the data model picks</a>. Grouping the data model confidence percentages will allow us to more reliably compare the computers versus humans and see how well they perform against one another.</p>

Having bucketed the FiveThirtyEight and FOX picks into five groupings each we are better able to read the new graph. Much of the clutter is gone. Additionally, and unexpectadely, we see a lone upward sloping CBS line that was previously obscured (this is a unique conf % due to one of the panelists withholding a vote on one game). Instead of data model lines going all over the place we see a more stable view. Many of the distracting upward lines that seemed to suggest the data models were routinely outperforming their expectations now appear to be overstated impressions. It would appear that the data models are not far off in their accuracy from their human expert counterparts, though perhaps a little less carried away with their picks. While there are some very thin upward sloping lines and a few gradually depressed ones, overall the data model trends look more flat than the expert panels of CBS and ESPN.

<img src="/gallery/2016/football-picks/wk14_slopegraph_buckets.png" alt="wk14_slopegraph_buckets" width="800" height="430" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>

Something glossed over and assumed, in both the original bubble chart and these slope graphs, is that we want "better" performing results than the expected confidence. But is that correct? Wouldn't a dot above the 45° line or an upward line, if either were far enough off from the stated percentage, indicate a problem in prediction just as well as if they were in the opposite direction? Of course they would. Being aware a game predictor is habitually optimistic or pessimistic is a good gauge in knowing how to hedge but it does not specify by how off the predictor is.

[Running a simple RMSE](https://gist.github.com/endlesspint8/2eaae1e452ce7d5a5edd46277c0459fb#file-nfl_slope_rmse-py) calculation on the above we find that when grouping the data models into buckets (and CBS' lone odd game) they have the lowest errors among the four sources. 

|source|bucket RMSE|orig vis RMSE|
|---|---|---|
|CBS|0.181|**0.181**|
|ESPN|0.166|**0.167**|
|FiveThirtyEight|**0.042**|0.191|
|FOX|**0.083**|0.213|

However, when we stick to the original visualization's underlying data we see that the human panels do better, their naturally aggregating probabilities ironing out much of the variation in game outcome (think of all those 90% confidence choices that were outright duds). What happens if we analyze source performance by game? Well, then we're basically talking about the Brier score [FN: did you see what I did there? I jiujitsu'd your ass.] and as we approach the end of the season we will certainly be highlighting this metric one more time to drive home the point of game picking reliability. 

## Week 13 - Total Recall 
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 13</a></b></sub></p>

This week I wanted to look at where the correct SUP picks were being made. Would there be big discrepencies or different mixes among the sources? I split the picks between two different criteria: favorite/dog and home/road. I wanted to know what number of correct picks fell into the four resulting catetgories: home-fav; home-dog; road-fav; road-dog. Each of these four segments would apply to our four sources, resulting in 16 potential buckets baring zero counts (FOX has to date zero home-dog correct picks out of five such calls).

One of the inspirations for this breakdown was the Bokeh donut graph example (http://bokeh.pydata.org/en/latest/docs/gallery/donut_chart.html). In that instance the underlying data was from the Olympics and the presentation was a slicing of country medals by Gold, Silver, and Bronze. I flirted with using the sample code from the gallery but was unhappy with the color scheme and inability to nest home/road ontop of fav/dog, ultimately deciding it was not worth the bother. I did not want to make two graphs when I could get away with the one (no disrespect to Contact (https://youtu.be/Et4sMJP9FmM?t=2m))?

<img src="/gallery/2016/football-picks/wk13_donut_sup2.PNG" alt="wk13_donut_sup" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>	

The results were not immediately surprising but they did raise some further questions which is sometimes better than a quick conclusion. As might be expected the majority of correct picks came from choosing the favorite. A majority of these correct picks were of home favorites, again no big deal. What was a bit curious was the breakdown of dog picks. For each pick source the majority of correct dog picks were of road teams. What constitutes a favorite? The betting line. This begs the question, how much of a dog were these dogs? We'll get to that but first a closer look at home-favorite performance by source via <a href="https://en.wikipedia.org/wiki/Precision_and_recall" target="_blank">confusion matrices</a>.

<img src="/gallery/2016/football-picks/wk13_confmx.PNG" alt="wk13_confmx" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>	

What at first looks like similar performances in the first graph are sliced into clearer detail above. The boxes are divided into True Positive (TP), False Positive (FP), False Negative (FN), and True Negative (TN) and are layed out as shown in the table below:

|||
|---|---|
|TP|FN|
|FP|TN|

What we see is consistent with the underlying trends to date. The data models are slightly better. The human panels are slightly more error prone.

What's the correct/winning Road Dog avg line? There have been 46 road dog wins through week 13. The average line... home team favored by 3.86 points. 



## Week 12 - Who's Got the Best BS?
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 12</a></b></sub></p>

Time to check in on one of the primary predictive metrics, the Brier Score (BS). This was an excellent opportunity to use yet another visualization idiom. Perhaps it's a bit of overkill but I <strike>wanted</strike> needed to get it out of my system. This week I show a streamgraph to represent the week over week BS for each of our sources regarding SUP picks.

For the human expert panels I used the regularized rating and the data models charted are (naturally) for in-season picks.

<p>
<iframe width="810" height="400" frameborder="0" scrolling="no" src="//plot.ly/~ep8/16.embed"></iframe>
</p>

<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub><br>

The visualization leaves something to be desired. For learning purposes this is a good thing. Let us count the ways in which the graph could provide the data more effectively. 

First, the difference in non-Random BS is quite small week to week. As such, a chart that uses area to represent divergence may not be the best way to get the difference across, especially when the stacking of these areas/streams makes the point of reference more difficult to ascertain. Second, by moving the Random stream to the bottom, which is consistently the largest, I may have lost out on the aesthetic if not the practical use of this sort of graph. 

Third, what at first looks like a helpful attribute in the form of hover tools turns out to leave something to be desired. The hover tool indicates the stream source and y-coordinate. What it should have shown is the BS for that source/week. The user can still identify the BS but only by finding the difference in y-coordinates between sources. This is asking too much of the user and defeats the purpose of making the data easier to "read" than via a table.

We can still answer who generally has the best BS but beforehand I wish to volunteer my execution of this graphic as being the biggest BS of the bunch. Having cleared my conscience I can get back to the task at hand.

Best BS means smallest BS so we're looking for the tightest stream. Right away Random can be tossed out, followed by the occasionally pregnant looking CBS (light blue) and ESPN (red) lines. That leaves us with the two data models, FiveThirtyEight and FOX. Hmmm. I'm gonna call it a tie. Too close to call.

What have we learned? I'm lazy (efficient?), have no shame, and for specific comparisons a streamgraph may not be the best tool. Instead, the streamgraph is helpful for getting a general picture of trends.



---

<h2 id="week11">Week 11 - Breaking Even, Breaking Bad</h2>
<p align="right"><sub><b>Share <a href="" target="_blank" title="Share on Twitter">Week 11</a></b></sub></p>

The last chart of last week used a diagonal line to help provide guidance on which level of confidence predictions were performing above or below expectations. In the description of that graph I mentioned performing at or above .500, breaking even with picks.

This week we will remove the hints and speak directly to performance above .500. Just to be clear I am counting the difference between correct picks ("wins") and incorrect picks ("loses") as the number above/below .500. There seems to be <a href="https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=calculate%20games%20above%20500" target="_blank">some debate out there</a> on how to count this depending on what you want to measure. I've said my piece, I'm moving on.

First up is the SUP performance where we are able to see all pick sources as well as the random picker. Predictably the latter is a dud. The actual professionals are all above .500 through week 11 and have been since the very beginning. There has been some jockeying at the top, especially early on, but over the long term FiveThirtyEight has shown itself to be most consistent. CBS started out strong, stumbled, has been in every position (1st, 2nd, etc.), and is now trailing behind though it is in a upswing. Unfortunately the recent upswing is shared by all of the other pick sources and as a result CBS has made up no ground.
	
<img src="/gallery/2016/football-picks/wk11_sup_chart.PNG" alt="wk11_sup_chart" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://www.espn.com/nfl/picks" target="_blank">ESPN</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>	

Our next chart shows a less rosy picture. One thing is consistent and that is FiveThirtyEight once again coming out on top. Damn that ELO is a good way to make predictions. CBS is again not showing well, even falling below the random generator in performance. Meanwhile, Fox is dancing around the breakeven .500 line.

<img src="/gallery/2016/football-picks/wk11_ats_chart.PNG" alt="wk11_ats_chart" align="middle"/><br>
<sub>Data Source: <a href="http://www.cbssports.com/nfl/features/writers/expert/picks/straight-up/7" target="_blank">CBS</a>, <a href="http://projects.fivethirtyeight.com/2016-nfl-predictions/" target="_blank">FiveThirtyEight</a> & <a href="http://www.foxsports.com/nfl/predictions" target="_blank">FOX</a></sub>

That's it people. Short week, gobble-gobble.

<h2 id="week10">Week 10 - Big Picture with Small Multiples</h2>
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


<h2 id="week6">Week 6 - Arbitrage (maybe)</h2>
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

