---
layout: post
title: Spence/Garcia
subtitle: What Were the Odds of That?
tags: ["boxing", "", ""]
shortlink: 
twitimg: 
image: http://endlesspint.com/gallery/2019/boxing/spence_act_v_exp.png
sideof: []
---

## A Whoopin' Happened, but How?

What does domination look like? There are many ways to the same label and this weekend we saw one approach. The larger man, Spence, used his mind in combination with his physical advantages to never allow the smaller, but still great fighter to get settled. If the domination were not apparent enough from watching the bout the numbers bear out the one-sided affair in stark terms. By contrasting the fight night stats against the respective fighters’ previously recorded punch stat performances, and taking some liberties with probability distributions, we see how each was impacted by the presence of the other in the ring, by how much, and who (just guess) to a larger degree. 

### Expected Punch Output Based on Previous Fighter Averages
<img src="/gallery/2019/boxing/poi_dist.png" alt="poi_dist" align="middle" width="100%" /><br />
<sub>Code @[nbviewer](https://nbviewer.jupyter.org/github/endlesspint8/endlesspint8.github.io/blob/master/code/spence_garcia/spence_garcia.ipynb)</sub>

Looking at activity first we see that Spence had it and Garcia did not. Spence’s output with the lead left jab was in most rounds, and for the fight overall, out of proportion to what might have been expected from his previous averages. His low connect rate hardly mattered when it came to effectiveness. 

**SPENCE**

Punches | Chance of Actual Punch Count or Greater by Round | For the Fight
--- | --- | ---
total | [0.9912, 0.882, 0.0963, 0.0015, 0.005, 0.0001, 0.2386, 0.0, 0.0, 0.0, 0.0, 0.0] | 18.5%
jabs | [0.093, 0.0245, 0.0001, 0.0, 0.0, 0.0, 0.0009, 0.0, 0.0, 0.0, 0.011, 0.2537] | 3.2%
power | [1.0, 1.0, 0.9827, 0.8285, 0.9537, 0.1682, 0.9959, 0.0747, 0.0, 0.0, 0.0, 0.0] | 50%

**GARCIA**

Punches | Chance of Actual Punch Count or Greater by Round | For the Fight
--- | --- | ---
total | [1.0, 1.0, 0.9997, 0.9969, 0.9615, 0.9309, 1.0, 0.9615, 0.9992, 0.1232, 1.0, 0.9713]  | 91%
jabs | [1.0, 0.9999, 0.9971, 0.9905, 0.9981, 0.995, 1.0, 0.9725, 0.9981, 0.9089, 1.0, 0.9991]  | 98.8%
power | [1.0, 0.927, 0.978, 0.927, 0.283, 0.283, 0.8865, 0.6958, 0.927, 0.0008, 0.978, 0.283]  | 68%


We see Spence using a remarkable work rate, specifically with the jab, to dampen Garcias’ offense in both output and accuracy. Though Spence himself was not particularly precise overall he leveraged his activity to tamp down Garcia and place himself in advantageous positions to deliver and land a substantial number of power shots. 

### What's a Bomb Without a Missile System?

<img src="/gallery/2019/boxing/spence_act_v_exp.png" alt="spence_act_v_exp" align="middle" width="100%" /><br />
<sub>Code @[nbviewer](https://nbviewer.jupyter.org/github/endlesspint8/endlesspint8.github.io/blob/master/code/spence_garcia/spence_garcia.ipynb)</sub>

**95 percent range for Spence total**: 	 341  -  401
 * Spence total actually landed: 	 345
 * prob of landing this Spence total count or less: 4%
 
**95 percent range for Spence jabs**: 	 103  -  141
 * Spence jabs actually landed: 	 108
 * prob of landing this Spence jabs count or less: 7%
 
**95 percent range for Spence power**: 	 202  -  243
 * Spence power actually landed: 	 237
 * prob of landing this Spence power count or less: 90%


<img src="/gallery/2019/boxing/garcia_act_v_exp.png" alt="garcia_act_v_exp" align="middle" width="100%" /><br />
<sub>Code @[nbviewer](https://nbviewer.jupyter.org/github/endlesspint8/endlesspint8.github.io/blob/master/code/spence_garcia/spence_garcia.ipynb)</sub>


**95 percent range for Garcia total**: 	 103  -  138
 * Garcia total actually landed: 	 75
 * prob of landing this Garcia total count or less: 0%
 
**95 percent range for Garcia jabs**: 	 29  -  49
 * Garcia jabs actually landed: 	 21
 * prob of landing this Garcia jabs count or less: 0%
 
**95 percent range for Garcia power**: 	 80  -  107
 * Garcia power actually landed: 	 54
 * prob of landing this Garcia power count or less: 0%
