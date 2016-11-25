---
layout: post
title: Still Razor Thin
subtitle: Three Data Approaches to a Controversial Decision
tags: ["KovalevWard", "dataviz"]
shortlink: 
twitimg: 
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

The purpose of narrowing in on the rounds and breaks was two-fold, to make the above graph and to only use the scores in the moment. I wanted to get the "as it happened" impression from fight fans. I was not interested in Monday morning quarterbacks or rationalizations of any sort. 

What I found was a whole lot of handwringing and excited viewers. Many rounds went unscored on an individual basis, many times people simply commentating on how close and tense the fight was. The scores varied with wide margins on both sides but overall the ultimate proportions fall inline with most people's expectations, though there were some surprises from my perspective (see round 12, which I thought was much closer). 

Below are the percentages associated with how people saw the fight on a round-by-round basis. The darker the red the more Kovalev was favored. Meanwhile, the darker the blue the more impressed Twitter'ers (I guess that's one way of spelling it) were with Ward.

<img src="/gallery/2016/boxing/kov-ward/kov_rnd_twt_scoring.PNG" alt="kov_rnd_twt_scoring" align="middle" /><br>
<sub>Data Source: Twitter</sub>

What we see is the story of two halves. Early Kovalev domination, including the knockdown in round 2,<sup id="a1">[1](#f1)</sup> followed by a steady Ward resurgence. Going on the straight majority votes it is clear that the fight is a six rounds to six split, with Kovalev winning by a point due to the knockdown. That observation is boring, however, and obscures individual scorecards by aggrogating all of the votes. 

In order to get a slightly more nuanced appreciation for how close the fight was I used these votes as probabilities, ran one thousand simulations of the bout, and came up with a range of possibilities for scoring it.

<img src="/gallery/2016/boxing/kov-ward/kov_rnds_won_density.PNG" alt="kov_rnds_won_density" align="middle" /><br>
<sub>Data Source: Twitter</sub>

Turns out the judges' decision of five rounds to Kovalev and seven to Ward, a one point win in the opposite direction from above, happens in 47.4% of the simulated bouts (Kovalev winning 5 rounds or less). This would suggest that the judges and Twitter-folk did not see it too differently. However, there is that second peak in the chart above. Just over round 6. And it's higher than the one for round 5. In nearly one third of all simulations (32.2%) Kovalev wins six rounds. So who "deserved" to win? Still  to tough to call.

## Round Features v. Judges' Cards

... to be continued

## Well, Hello ELO

... to be continued

<br>

---

**Notes**

<b id="f1">1</b> Amazingly I didn't find any knuckleheads who scored the round even or in favor of Ward. It's the internet, you never know. [↩](#a1) <br>

https://boxstat.co/bout/2898784/sergey-kovalev-vs-andre-ward
