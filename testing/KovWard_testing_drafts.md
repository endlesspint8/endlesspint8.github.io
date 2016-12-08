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

Twelve rounds, one knockdown, cat & mouse, cobra & mongoose, knip and tuck, cliches baby!

The data is built up out of two primary features: jabs and power punches. These numbers are combined, for total punch output, and broken down into thrown and connected hits, for percentages. We will take all of these criteria into consideration and review.

Below is a head-to-head graphical representation by round of jabs, power, and total punches. The top row shows the actual counts for each of the aforementioned measures. The second row shows the same data as percentages. In each of the charts I have provided a 45-degree line to help provide a visual cue when one fighter is out performing the other for any specific round.

These two rows appear to tell slightly different stories. In the first we see a nearly balanced fight, depending on how you favor jabs versus power shots. The second row tells a much more partison tale. Here we see that Ward holds a definitive advantage.

Taking a look at this data in another way I identified each round with the judges' scores. There were eight rounds that were unanimously agreed upon, three for Kovalev and five in Ward's favor, and four that were split. I replotted the data points with colors to identify the judges' take on the fighters' performance.





plots/graphs

scores

simulations

No good b/c of p>n/curse of dimensionality: 3D a disaster (with 3 most important RF features) kMeans

I thought it was a bit fishy that Ward won five rounds straight and unanimously from the beginning of the second half of the bout. Then we see the numbers and it is clear that precision was very high for those rounds. This analysis looks at raw numbers as punch outputs only differentiated by jab or power punch. We have not looked at nor is there as yet an adequate way of measuring "pain" [link: Clubber Lang, https://www.youtube.com/watch?v=lSPNQ82Sq4E]. Having said as much, you can imagine that being given the impression that when one fighter throws and he's consistently connecting (+40%) he is in control.

A second pass confirms what most of our eyes saw while adding a bit of nuiance (perhaps).



