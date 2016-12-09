---
layout: post
title: Still Razor Thin
subtitle: Three Data Approaches to a Controversial Decision
tags: ["KovalevWard", "dataviz"]
shortlink: http://bit.ly/KovWrdep
twitimg: 
---

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

With the added context of the official score cards you might say that Ward was favored in more active rounds, possibly due his higher accuracy shining through in busier rounds. Beyond that I am a bit hard pressed to distinguish how the split rounds should be distributed. While certain split/green rounds appear closer to Kovalev they often times fall into Ward's half of the graph. The fact that Kovalev had a knockdown in one of the rounds doesn't exactly help matters. That round goes to the fighter who scored the knockdown in the abscence of a remarkable in-round comback by the floored opponent. For our purposes punch numbers from round two may be difficult to generalize to other rounds.

<img src="/code/kov_ward_rd_feat/output_12_1.png" alt="punch4punch_judges2" align="middle" /><br>
<sub>Data Source: <a href="http://compuboxonline.com/" target="_blank">CompuBox</a></sub>

Setting aside the head-to-head comparison I wanted to visualize the performances side-by-side. The benefit of splitting the fighter inputs from each other is to combine jabs and power punches for a single fighter (again per round). Plotting the two-feature data points, with distinguishing colors and markers, could allow for a more complete view of the fighters' round performances. Unfortunately we lose the connection with the other fighter's contributing performance in the same round. 

I could have added distinguishing colors/markers for each round but that would have been too much of a CF. [FN: Or chart junk as Edward Tufte more politely calls it.] Instead I decided to meet the need halfway. We already know this is a fight of two halves so I distinguished the markers for fighter by color, again red v. blue, and rounds by shape, circle (1st half of bout) v. square (2nd half), to  to help if you were see how each fighter did in the respective halves of the bout. 

having come to the end of basic exploratory visual analysis I switched my attention to learning and prediction. This was a tough thing to ask due to the small number of examples. I partly mitigated this like reading three instances of each round, one for the decision of each judge. With the punch that's as features and the judge decisions as labels I applied several quick techniques to see what if anything popped out.

I applied bagging, random forest, and K and N. The results for each of the above confirmed A deepening appreciation for how close the rounds were, or rather the fight as a whole. What I was hoping to find where anomalies in the round statistics that one of these techniques would pick up on and then result in the significantly different result. that might have suggested that a round or two that was more similar to one fighters better performance over another was "unfairly" given to the other. Unfortunately from a point of view of a "gotcha" piece I was not able to determine such a thing having happened.

scores

jab/power scatter w 1st & 2nd half distinguishing markers (circles v crosses)

Bagging

Random Forest // feature importance, top three

kNN

No good b/c of p>n/curse of dimensionality: 3D a disaster (with 3 most important RF features) kMeans... but based on this feature set kMeans split the rounds 6-6

kMeans2: run 2k analysis across all 12 just for kicks to see split 

I thought it was a bit fishy that Ward won five rounds straight and unanimously from the beginning of the second half of the bout. Then we see the numbers and it is clear that precision was very high for those rounds. This analysis looks at raw numbers as punch outputs only differentiated by jab or power punch. We have not looked at nor is there as yet an adequate way of measuring "pain" [link: Clubber Lang, https://www.youtube.com/watch?v=lSPNQ82Sq4E]. Having said as much, you can imagine that being given the impression that when one fighter throws and he's consistently connecting (+40%) he is in control.

A second pass confirms what most of our eyes saw while adding a bit of nuance (perhaps).


## Notes

Twelve rounds, one knockdown, cat & mouse, cobra & mongoose, nip and tuck, clichés baby!


