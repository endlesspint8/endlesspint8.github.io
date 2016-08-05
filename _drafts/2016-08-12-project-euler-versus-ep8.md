---
layout: post
title: When you come to a fork in the road, keep moving
subtitle: How Many Different Routes to RnH?
---

## A common enough conversation: where do you wanna meet up?

Every other week or so I like to grab a pint with a friend of mine and catch up. Hopefully you too have someone you can share stupid and serious ideas with. Someone who appreciates your sensibility and opinion. Most importantly, someone who can hold an interesting coversation, be occassionally irreverant, and have a laugh over a good beer. 

In New York there are a ton of options for grabbing a good pint, especially with the rotating taps at most self-respecting places. If you work in the city odds are you're either in Midtown or the Financial District. If you enjoy good beer, and less of a bustling afterwork crowd, chances are you won't stick around long in these neighborhoods, unless you're with your work collegues and kicking back a few, unwilling to be the douche that makes everyone else accomodate his beer snobbish palatte by going to some less than office-convenient bar. Don't be that guy. At least have some finesse and teach people slowly about what good beer is and entice them that way over time. Make it seem like it's their decision to go to "that bar with the weird but delicious beers".[1]

Depending on the choice of bar, and this is determined by a litany of considerations: convenience to work/home, newness of establishment, grub, and of course beer selection, there is then the logistical matter of getting your ass from the office chair to the bar stool. Subways usually (nearly always, really) play a role and then there is the most time honored New York means of travel, walking. Tourist or resident, you can't help notice the importance and etiquete of walking in the city[http://www.travelandleisure.com/slideshows/walking-in-new-york-city]. 

I like to play a game called "Shark Walk" where if you stop moving you "die". The goal is to get from A to B without waiting at a light. Besides jaywalking, also a NYC tradition, and running to beat traffic, preferably avoided,[2] your best bet is knowing your options, staying alert to traffic lights, and minding your pace. It's always preferable to "pick it up" a bit or lay back with the pace to standing at a corner waiting for car traffic to pass. And this is not jogging, so running in place does not count.[3]

This game is applicable to lunch hour walks, taking a stroll (can you say _flaneur_?[4]), or making your way from the subway stop to the delicious pint waiting for you at your watering hole of choice. If you want to keep moving and give yourself the impression that you've got some little bit of control in this mad city[kendrick link] then know your options, which brings us back to the topic at hand. How many ways are there of getting from here, thirsty, to there, imbibing?

## A Simple Example (credit to the MTA)

Two blocks away: straight line

Two blocks away: L-shape

Despite <a href="http://www.citylab.com/commute/2016/07/a-new-map-of-new-yorks-subway-deserts/491156/" target="_blank">subway deserts</a>, that you can <a href="http://nymag.com/selectall/2016/08/this-subway-game-turned-me-into-a-tinpot-robert-moses.html" target="_blank">attempt to alleviate</a>, the MTA covers NYC reasonably well. 

Assume you're on the Sixth Avenue line and get off at 34th for the purposes of getting a drink at Rattle and hum, that places you
two blocks away (let's ignore the difference in avenues and streets, since it won't matter either way in our scenarios) which requires you to go east and south, in either order. Since both options are available you have two routes to getting there.

Now if you're two blocks up the Avenue (35th & 5th Ave) from your destination, the same number of blocks (again not in actual distance), you only have one choice, walk downtown.

Inuitively being off of a straight line provides alternate ways of getting to the same destination and this is especially clear in the
city, or an area of the city, that is laid out like a Cartesian plane (we will be ignoring bisecting streets and avenues, such as Broadway).

Second intuition when it comes to a straight line, it doesn't matter how far out you extend it, the most direct way of getting to the
destination remains the same; you have one best option,  you actually have a best option. Straight ahead.

## More Options the Farther Away

Three blocks: straight line
Four blocks: straight line
Four blocks: 2x2

Final intuition, the more blocks between you and the bar in a grid layout, the more options. Four blocks away, in a 3x1 fashion starting on 36th and Park and still aiming for Rattle 'n Hum you have no less than four ways of getting there (either taking park or fifth all the way down or walking west on either 35th or 34th and continuing down fifth). The options increase if you happen to be in a 2 x 2 grid; again still the same four blocks. Can you envision in your minds eye how many ways you can walk from 35th and 7th to 33rd and fifth? I'll give you a second. It's six this time. 

## Mr. Euler, I Presume

This is where Mr. Euler comes into the picture. The canonical set of mathematical problems posted on <a href="https://projecteuler.net/" target="_blank">Project Euler</a> challenging you to apply math concepts and computer programming is the spring board for this thought exercise. <a href="https://projecteuler.net/problem=15" target="_blank">One of these problems</a> deals with <a href="https://en.wikipedia.org/wiki/Lattice_path" target="_blank">Lattice paths</a>. Remembering nothing beyond my fourth-grade math but intuiting there's got to be a systematic way of solving this mystery I go first for a visual representation. 

## To the Bar!

I take the origin coordinate (0,0) and branch out to see how the numbers expand looking for a pattern. This is easy enough to do with the 1x1 and 2x2 grid but begins to present problems at 3x3. I rush to develop the last of these trees, am sloppy without realizing it and then spend 30 minutes attempting to find a pattern to an incomplete "solution". Upon returning to my sketches, and revisiting my steps, I realize my error. 

**insert photo**

I correct the path count and redo it from scratch on the other side of the page to confirm the result. Convinced of the correct next path count I try again to find a mathematical pattern. Nothing doing, I figure more numbers of paths would help but do not necessarily trust myself to come out with the correct path count for the 4x4 grid. Had I been at this corner before? Couldn't keep it straight in my head and it was like the scene from Inception where <a href="https://www.youtube.com/watch?v=x9hBWnh_O6A" target="_blank">the city folds in on itself</a> (or an <a href="http://www.mcescher.com/gallery/recognition-success/convex-and-concave/" target="_blank">Escher</a>). What's a fool to do? 

How about building an equally foolish function, but one that knows how to keep count? Done. 

**insert function**

Now armed with path counts for square grids from 1 to 4 blocks I sense that the mysteries of the solution are shortly to be revealed. After another half hour it's clear the revelation will be taking its time and may require another visual representation, this time listing out the number of paths available at each corner of the grid. I start simply and build up, taking my time and hoping that my deliberate attention will clue me into following the right direction. And what do you freaking know? By the time I expand from the 2x2 to the 3x3 I'm seeing a possibility. Having the next path count, 4x4, allows me to know what to look for and does validate the pattern further. As soon as this next step returns the right number I expand my efforts from a sheet of paper, to an Excel sheet, and finally to a slightly smarter function.

**insert function**

Initially I had focused on just one branch of paths, knowing the number could be doubled to reflect the paths branching in the alternate direction. In creating my Excel grid the whole numbers jump out at me and I realize that closer look returns the number I require with no additional arithmetic, even one keepable by my fourth grade skills.

We now have two simple and elegant ways of calculating the paths. It's not likely you'll need all of these options but they're helpful in keeping you free and flexible in your walks to the bar. Just remember to be careful on your way back. After a little alcohol these numerous options have a way of making themselves feel present, creating confusion for you and then we do have to worry about walking in any of the four directions [provide foreshadow earlier].

1st & 1st, <a href="https://www.youtube.com/watch?v=bb9IA-914Xw" target="_blank">nexus of the universe</a>

## ...

<br />

--- 

## Invisible Cities (<a href="https://www.goodreads.com/work/quotes/68476-le-citt-invisibili" target="_blank">quotes</a>)

> “Futures not achieved are only branches of the past: dead branches.” 
--- 
> “Elsewhere is a negative mirror. The traveler recognizes the little that is his, discovering the much he has not had and will never have.”
--- 
> “You take delight not in a city's seven or seventy wonders, but in the answer it gives to a question of yours.” 
> --- 
> “Memory's images, once they are fixed in words, are erased," Polo said. "Perhaps I am afraid of losing Venice all at once, if I speak of it, or perhaps, speaking of other cities, I have already lost it, little by little.” 
> “The city is redundant: it repeats itself so that something will stick in the mind.
[…]
Memory is redundant: it repeats signs so that the city can begin to exist.” 
> “An invisible landscape conditions the visible one” 

> “Thus the city repeats its life, identical, shifting up and down on its empty chessboard."

> “The city does not consist of this, but of relationships between the measurements of its space and the events of its past:” 

> “The traveler recognizes the little that is his, discovering the much he has not had and will never have.” 

> "they must admit that all their calculations were wrong and their figures are unable to describe the heavens"

> "he sees someone in a square living a life or an instant that could be his; he could now be in that man’s place, if he had stopped in time, long ago; or if, long ago, at a crossroads, instead of taking one road he had taken the opposite one"

Doubt of ever reaching the bar.
> “Desires are already memories.” 




## ...

<br />

--- 

**Notes**

see: binomials; pascal's triangle; ... <br />
[1] What's more important in the end: the credit or the beer? <br />
[2] And never a good look. <br />
[3] Ibid. <br />
[4] See: Paris Spleen[link needed] <br />
[5]

https://bl.ocks.org/mbostock/1b64ec067fcfc51e7471d944f51f1611
