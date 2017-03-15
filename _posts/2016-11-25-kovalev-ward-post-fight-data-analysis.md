---
layout: post
title: Still Razor Thin
subtitle: Three Data Approaches to a Controversial Decision
tags: ["KovalevWard", "dataviz"]
shortlink: http://bit.ly/KovWrdep
twitimg: pic.twitter.com/I4duoYZyjC
image: http://endlesspint.com/gallery/2016/boxing/kov-ward/fight_hour_tweets.PNG
---

## Still too Close to Call

Nice build up, two top quality fighters, one hell of a tactical and willful bout, one knockdown and a controversial decision. That's boxing, baby!

I have my impressions on who won between Kovalev/Ward I (let's all hope there's a sequel in the near future) and am apparently curious enough about the result to want to dig deeper in order to get a more complete take.

This three part (more or less) piece will explore the fight from several different angles. 

First we'll see what social media thought was happening in the moment. Then we will take a closer look at the round features and judges' score cards (how do they line up?). Finally, there will be a review of the respective fighter's ELO ratings coming into and exiting the fight. 

## What do the Masses Have to Say?

I pulled the fight night tweets associated with the two primary hashtags, #KovalevWard and #WardKovalev, focused in on the bout itself, and identified the round and rest period time ranges.

<img src="/gallery/2016/boxing/kov-ward/fight_hour_tweets.PNG" alt="fight_hour_tweets" /><br>
<sub>Data Source: Twitter</sub>

The purpose of narrowing in on the rounds and breaks was two-fold, to make the above graph (pretty!) and to just use the scores in the moment. I wanted to get the "as it happened" impression from fight fans. I was not interested in Monday morning quarterbacks or rationalizations of any sort. 

What I found was a whole lot of handwringing and excited viewers. Many rounds went unscored on an individual basis, many times people simply commentating on how close and tense the fight was. The scores varied with wide margins on both sides but overall the ultimate proportions fall in line with most people's expectations, though there were some surprises from my perspective (see round 12, which I thought was much closer). 

Below are the percentages associated with how people saw the fight on a round-by-round basis. The darker the red the more Kovalev was favored. Meanwhile, the darker the blue the more impressed Twitter'ers (I guess that's one way of spelling it) were with Ward.

<img src="/gallery/2016/boxing/kov-ward/kov_rnd_twt_scoring.PNG" alt="kov_rnd_twt_scoring" align="middle" /><br>
<sub>Data Source: Twitter</sub>

What we see is the story of two halves. Early Kovalev domination, including the knockdown in round 2,<sup id="a1">[1](#f1)</sup> followed by a steady Ward resurgence. Going on the straight majority votes it is clear that the fight is a six rounds to six split, with Kovalev winning by a point due to the knockdown. That observation is boring, however, and obscures individual scorecards by aggregating all of the votes. 

In order to get a slightly more nuanced appreciation for how close the fight was I used these votes as probabilities, ran one thousand [simulations of the bout](/code/kov_ward_sim_bouts), and came up with a range of possibilities for scoring it.

<img src="/gallery/2016/boxing/kov-ward/kov_rnds_won_density.PNG" alt="kov_rnds_won_density" align="middle" /><br>
<sub>Data Source: Twitter</sub>

Turns out the judges' decision of five rounds to Kovalev and seven to Ward, a one point win in the opposite direction from above, happens in 47.4% of the simulated bouts (Kovalev winning 5 rounds or less). This would suggest that the judges and Twitter-folk did not see it too differently. However, there is that second peak in the chart above. Just over round 6. And it's higher than the one for round 5. In nearly one third of all simulations (32.2%) Kovalev wins six rounds. So who "deserved" to win? Still too tough to call.

## Round Features v. Judges' Cards

Having seen how the Twitter folk saw the fight we now turn our attention to the ringside judges. To help give us context regarding _what_ people were seeing we bring in the fight numbers as measured by CompuBox.

The data is built up of two primary features: jabs and power punches. These numbers are combined, for total punch output, and broken down into thrown and connected hits, for percentages. We will take all of these criteria into consideration and review.

Below is a head-to-head graphical representation by round of jabs, power, and total punches. The top row shows the actual counts for each of the aforementioned measures. The second row shows the same data as percentages. In each of the charts I have provided a 45-degree line to help provide a visual cue when one fighter is outperforming the other for any specific round.

<img src="/code/kov_ward_rd_feat/output_5_0.png" alt="punch4punch" align="middle" /><br>
<sub>Data Source: <a href="http://compuboxonline.com/" target="_blank">CompuBox</a></sub>

These two rows appear to tell slightly different stories. In the first we see a nearly balanced fight, depending on how you favor jabs versus power shots. The second row tells a much more partisan tale. Here we see that Ward holds a definitive advantage.

Taking a look at this data in another way I identified each round with the judges' scores. There were eight rounds that were unanimously agreed upon, three for Kovalev (red) and five in Ward's favor (blue), and four that were split (green). I replotted the data points with colors to identify the judges' take on the fighters' performance.

<img src="/code/kov_ward_rd_feat/output_7_0.png" alt="punch4punch_judges" align="middle" /><br>
<sub>Data Source: <a href="http://compuboxonline.com/" target="_blank">CompuBox</a></sub>

With the added context of the official score cards you might say that Ward was favored in more active rounds, possibly due his higher accuracy shining through in busier rounds. Beyond that I am a bit hard pressed to distinguish how the split rounds should be distributed. While certain split/green rounds appear closer to Kovalev they often times fall into Ward's half of the graph. The fact that Kovalev had a knockdown in one of the rounds doesn't exactly help matters. That round goes to the fighter who scored the knockdown in the absence of a remarkable in-round comeback by the floored opponent. For our purposes punch numbers from round two may be difficult to generalize to other rounds.

Setting aside the head-to-head comparison I wanted to visualize the performances side-by-side. The benefit of splitting the fighter inputs from each other is to combine jabs and power punches for a single fighter (again per round). Plotting the two-feature data points, with distinguishing colors and markers, could allow for a more complete view of the fighters' round performances. Unfortunately we lose the connection with the other fighter's contributing performance in the same round. 

I could have added distinguishing colors/markers for each round but that would have been too much of a CF.<sup id="a2">[2](#f2)</sup> Instead I decided to meet the need halfway. We already know this is a fight of two halves so I distinguished the markers for fighter by color, again red v. blue, and rounds by shape, circle (1st half of bout) v. square (2nd half). 

What we see in the first row below is Kovalev routinely landing more power punches than jabs and doing so at a better percentage. Ward had a varied "approach". The blue squares show us that it was in the latter half of the fight that Ward raised his output and connect percentage, lending strong evidence to the way the fight was scored. In fact, if we take a look at the bottom right graph below, we see that in all of the five rounds Ward swept he connected at +50% for jabs or power punches. Now that is impressive.<sup id="a3">[3](#f3)</sup>

Less impressive is my rendering of the data on the second row below. What I attempted to show were outright round wins by fighter using full red/blue geometric figures, outright fighter round loses by red/blue "X's", and split rounds in green. In the latter instance of split rounds I kept the circles for Kovalev and boxes for Ward. This association of shapes is not an exact match with the first row and may lead to confusion. Ultimately I went with this less than perfect representation because I found it the least bad of the candidates I was working with.

<img src="/code/kov_ward_rd_feat/output_12_1.png" alt="punch4punch_judges2" align="middle" /><br>
<sub>Data Source: <a href="http://compuboxonline.com/" target="_blank">CompuBox</a></sub>

Having come to the end of basic exploratory visual analysis I switched my attention to [learning and prediction](/code/kov_ward_rd_feat). This was a tough thing to ask due to the small number of examples. I partly mitigated this by creating three instances of each round, one for the decision of each judge. With the punch stats as features and the judge decisions as labels I applied several quick techniques to see what if anything popped out.

Using bagging (7-5 Ward), random forest (7-5 Ward), kNN (6-6), and k-means (6-6) my appreciation for how close the rounds were, or rather the fight as a whole, grew. What I was hoping to find where anomalies in the round statistics that one of these techniques would pick up on, leading to a significantly different result. That might have suggested a round or two that were more similar to one fighter's better performance over another being "unfairly" given to the wrong fighter. Unfortunately from the point of view of a "gotcha" piece I was not able to determine such a thing having happened.

But this isn't meant as a gotcha piece. This is a search for clarification to the judges' cards and what I have clarified, at least for myself, is a certain level of consistency among the data to give me some reassurance to the decision.

## Well, Hello ELO

... to be continued

<br>

---

**Notes**

<b id="f1">1</b> Amazingly I didn't find any knuckleheads who scored the round even or in favor of Ward. It's the internet, you never know. [↩](#a1) <br>
<b id="f2">2</b> Or chart junk as Edward Tufte more politely calls it. [↩](#a2) <br>
<b id="f3">3</b> I initially thought it was a bit fishy that Ward won five rounds straight and unanimously from the beginning of the second half of the bout. It seemed too close to a script. However, when we see the numbers it is clear that his precision was very high for those rounds. This analysis looks at raw numbers as punch outputs only differentiated by jab or power punch. We have not looked at nor is there as yet an adequate way of measuring "<a href="https://www.youtube.com/watch?v=lSPNQ82Sq4E" target="_blank">pain</a>". [↩](#a3) <br>
