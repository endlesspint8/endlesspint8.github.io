---
layout: post
title: Still Razor Thin
subtitle: Three Data Approaches to a Controversial Decision
tags: ["KovalevWard", "dataviz"]
shortlink: http://bit.ly/KovWrdep
twitimg: 
---

## Round Features v. Judges' Cards

Having looked at how Twitter folk saw the fight we now turn our attention to the ringside judges' take. Additionally, we will take a look at the fight numbers to get a better idea of _what_ people were seeing.

first the numbers, Compubox

Twelve rounds, one knockdown, cat & mouse, cobra & mongoose, nip and tuck, clichés baby!

The data is built up out of two primary features: jabs and power punches. These numbers are combined, for total punch output, and broken down into thrown and connected hits, for percentages. We will take all of these criteria into consideration and review.

Below is a head-to-head graphical representation by round of jabs, power, and total punches. The top row shows the actual counts for each of the aforementioned measures. The second row shows the same data as percentages. In each of the charts I have provided a 45-degree line to help provide a visual cue when one fighter is outperforming the other for any specific round.

These two rows appear to tell slightly different stories. In the first we see a nearly balanced fight, depending on how you favor jabs versus power shots. The second row tells a much more partisan tale. Here we see that Ward holds a definitive advantage.

Taking a look at this data in another way I identified each round with the judges' scores. There were eight rounds that were unanimously agreed upon, three for Kovalev and five in Ward's favor, and four that were split. I replotted the data points with colors to identify the judges' take on the fighters' performance.

With the added context of the official score cards you might say that Ward was favored in more active rounds, most likely due to his more acurate punches. Beyond that I am a bit hard pressed to distinguish how the split rounds should be distributed. Nothing in particular jumps out. The fact that Kovalev had a knockdown in one of the rounds doesn't exactly help matters. That round, when your default, he's going to be opening round and typically one where the punch numbers will be hard to generalize to other rounds.

Setting aside the head-to-head comparison I wanted to visualize the performance side-by-side. The benefit of splitting the fighter inputs from each other is to combine jobs and power punches for single fighter, again per round. By plotting the two feature Data points on the same graph with distinguishing colors and markers we can see a more complete view of the fighters round performances that we unfortunately lose the connection with the other fighters contributing performance in the same round. I could've added colors to distinguish the multiple rounds but that would've been too much of a CF or more politely chart junk as Edward tufty calls it. Instead I decided to meet the need halfway. We already know this is a fight of two halves. So I've distinguished the fighter markers to help if you were see how each fighter did in the respective halves of the bout. 

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




