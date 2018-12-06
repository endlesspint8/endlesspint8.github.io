---
layout: post
title: Simulating HBO Greatest Fighter of All Time Tournament
subtitle: Had Boxing Once (tear)
tags: ["boxing", "ELO", "simulation"]
shortlink: 
image: http://endlesspint.com/gallery/2018/boxing/rebracket.gif
---


I was fortunate to be introduced to boxing at a young age and at a great time for quality of fighters, broadcasts, and storylines. The network that played the oversized roll in this introduction was HBO. Decades down the line I was fully indoctrinated to its brand. Though I could be critical at times, having not lost all sense of individual preference and autonomy I never questioned where the best quality fights and fighters would be. I was hardly the only one. A couple of generations grew up taking the network as the standard bearer for granted. 

## Such Sweet Sorrow

Naturally, it was bittersweet to [read about HBO deciding to move away from its boxing programming](http://www.espn.com/boxing/story/_/id/24814171/hbo-drop-boxing-coverage-end-2018). Bitter because I had grown up on many of the fights from the late (very late) 80s to the present day. Bitter because I have fond memories of spending Saturday evenings amongst my father and his friends, well past my bedtime, watching the fights as the adults talked shit, drank, smoked entirely too many cigarettes for both themselves and their surrounding children, and made small side bets. Over the years these adults would be replaced by my generation. And even though for most of my youth I never wanted children paradoxically I looked forward to passing along the experience to a new generation, minus the second-hand smoke, but no less of the shit talking and drinking. Bitter because I grew up with many of the announcers and reporters on the telecasts who had such of an oversized influence on my boxing sensibilities. Bitter because sports mean more when you are younger but even in adulthood the stories of the fighters remained inspiring. Bitter because now I almost certainly will never be able to attend a Las Vegas HBO pay-per-view bout (though I did catch one at MSG). 

Sweet for all the same reasons, and sweet also because the HBO quality and quantity fight fans had been spoiled by and accustomed to no longer persisted. What had been for nearly two decades Showtime’s [Gobots](link) to HBO’s [Transformers](link) had been gradually reversing itself, judging exclusively by the amount of money and airtime spent the switch was complete (though something about the second status network can never be shaken for me). Rather than continue limping along the network pulled the plug on a tremendous career; a lesson worth passing along to actual boxers. 

Part of growing up is being confronted, and dealing with, change. Change can rock us to the core depending on its severity and our maturity. Rather than being a preteen seeing his parents break up I am simply a grown man witnessing a fading light being turned off. 

Change confronts us with uncertainty and that is much of what I feel regarding the immediate future of boxing, specifically in America. Change can also be exciting and very much necessary. Change is many things and ever present (Heraclitus!). 

## Let’s Get Ready to… 

As if by intention, or simply due to the trend of declining fights and the need to remind fans of its deep legacy, or just simple coincidence, the [HBO boxing podcast did a multipart series]([link) on a fantasy tournament to crown the greatest fighter ever to appear on the network. This was a multi-generational, cross weight class, in-their-prime imaginary set of bouts. The tournament consisted of 32 fighters across four brackets, each region named in honor of a long time HBO announcer. Fighters had been pre-seeded and placed into brackets for a single illumination showdown where fan votes would determine the one to advance. Many matchups were close, some were blowouts, there was one overarching dark horse (Tyson) that in retrospect makes a ton of sense when considering the popular nature of determining winners, but at the end of the day, most top seeds prevailed, and the final saw two classic, all-time talents, Ali and Leonard with the former being crowned, appropriately, the greatest. 

<img src="/gallery/2018/boxing/hbo-the-final-round.png" alt="hbo-the-final-round" align="middle" width="75%" /><br />
<sub><b>Data Source</b>: <a href="http://www.insidehboboxing.com/inside/2018/7/12/hbo-greatest-fighter-of-all-time-tournament-the-final-round" target="_blank">HBO</a>, <em>HBO Greatest Fighter of All Time Tournament: The Final Round</em> [Accessed: October 2018]

With HBO hanging up the gloves I wished to hold onto the memories a while longer. I did so by digging a bit deeper into the tournament, the fighters, and projecting additional. By leveraging voter preferences as a proxy for head-to-head winning probabilities it was possible to generate fighter ratings (see [reverse ELO](link)). Once “The Greatest” was given an appropriately high ELO rating it was only a matter of trickling the results/ratings back down to the first rounds.

<img src="/gallery/2018/boxing/grid_RevELO.PNG" alt="grid_RevELO" align="middle" width="100%" /><br />

<img src="/gallery/2018/boxing/grid_RevELO2.PNG" alt="grid_RevELO2" align="middle" width="100%" /><br />




As soon as each fighter had an ELO rating it was trivial to create expected win results for all match ups, regardless if they had happened in the original tournament or were even possible should voters have decided differently. 

The first curiosity to be scratched was what the results would have been if the tournament had been run thousands of times over, who else would win and how often. Unsurprisingly Ali came out on top but there were a few shakeups due to the determined ratings. 

<img src="/gallery/2018/boxing/hbo_10k_sim.PNG" alt="grid_RevELO2" align="middle" width="100%" /><br />


The second bit of intrigue was to see what the same simulation would show once fighters had been reseeded by rating. Sorting fighters in descending order of rating determined revised seeding, with new matchups created by [snaking the order of the seeds](notebook link).

<img src="/gallery/2018/boxing/rebracket.gif" alt="rebracket gif" align="middle" width="50%" /><br />

Below is an image of how the new seeding looked and would play out if the results were straight chalk.

<img src="/gallery/2018/boxing/ep8-the-final-round-chalk.png" alt="ep8-the-final-round-chalk" align="middle" width="100%" /><br />

Predictably the stronger rated fighters benefited from softer matchups early on, boosting their overall wins the first couple of rounds. The reverse was inevitably true for the higher seeds. The win share became more divergent with fewer fighters garnering the majority of wins. 

<img src="/gallery/2018/boxing/hbo_10k_sim2.PNG" alt="grid_RevELO2" align="middle" width="100%" /><br />

<img src="/gallery/2018/boxing/hbo_10k_sim2_comp.PNG" alt="grid_RevELO2" align="middle" width="100%" /><br />

In both instances of these two tournament iterations one crucial aspect was set aside, the updating of ELO ratings. This missing piece was added in to address the final angle of interest, how would fighters perform, and fare, given multiple opportunities and a chance to benefit/suffer from accumulated results. Some guard rails had to be introduced to avoid ridiculous results, most notably placing ceilings (3000) and floors (ELO – 200, rounded down) on a fighter’s ELO rating. 


