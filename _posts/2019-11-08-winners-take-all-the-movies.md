---
layout: post
title: Winners Take All - The Movies
subtitle: And all this for what, a puppy? 
tags: ["digressions", "bayes"]
shortlink: 
twitimg: 
image: http://endlesspint.com/gallery/2019/wta_movies/marcus-wallis-4zfacTKyZ7w-unsplash.jpg
sideof: []
---

I will be avoiding John Wick's rampage but his story ties into this investigation. A few years back I was relaxing at home, killing time, not in the mood to do anything particularly productive. I was in search of a little filler, perhaps some entertainment. I surfed the channels with just the right amount of low expectations when I stumbled across the beginning of John Wick on HBO. I let it roll having only vaguely remembered that Keanu had done another action film. I had not heard anything about it with regards to reviews, no one I knew had even mentioned it. I thought I would give it 30 minutes and move on from there once it failed to draw me in and our dear Keanu’s notoriously bad acting overshadowed the movie. To my delight this never came close to happening. Of course, the terrible acting poked out from time to time, but it never endangered crowding out the storyline, action, and mood of the movie. The action scenes were a refreshing surprise to the average mindless violence so easily found elsewhere, but beyond that it was the world of the story itself that made this random viewing such a delight. The movie depicted an underworld of honor, trust, and consequences running in parallel to the everyday lives we take for granted. In many ways, and despite its violence, perhaps because of the way the violence was used as a tool within the secret society, this world made more sense, had more order than the one we commonly know. Certainly, the strictness of the rules and the formality of the players set about to create such an order. At the same time the movie did not take itself too seriously. It was done with fun in mind and it delivered. 

The sequel extended this world and some viewers preferred it to the first. Though I believe the first movie edges its sequel, the two together signified a strong franchise. By the time JW3 rolled around I was more aware of the hype. In fact, a group of friends were passing along not entirely ironic enthusiastic remarks about the latest John Wick movie. I joked about not being able to wait for the fourth, even before the third had been released. In this age of sequels any successful film invites the opportunity for spinoffs and franchise building. A friend saw the film opening night, said it left the plot open to further exploitation, and I replied that “of course there would be a future release given that this one would rake in a couple of hundred million.” It was a number thrown out there to make a point, not win an argument, but also backed by my MSU degree.<sup id="a1">[1](#f1)</sup> As is often the case, I was left wondering how much I agreed with what I just said. What would it mean to gross $200 million, how common is this yearly, and was I talking domestic or international (obviously, whatever would bring my comment closer to the truth)? I figured I could find some of the answers on the line. Pulling together several decades’ worth of domestic movie grosses I was able to investigate the idea further.

<img src="/gallery/2019/wta_movies/wta_movies_ts.jpg" alt="wta_movies_ts" align="middle" width="100%" /><br />

Even a cursory glance at the US movie sales numbers made it clear that some rough estimate could be made. Most notably, a substantial amount of the overall gross was made in the first nights/weekend. This rings true to the hype and focus we hear about when it comes to who tops the box office and where they debuted. However, a closer look also showed that some monster sized movies also started out in limited release, with puny take-homes versus their final numbers. This was a wrinkle worth keeping in mind. A couple of ideas sprang to mind as to how to deal with it. The first option, as usual, was to do nothing. The wrinkle had been noted but would remain neglected. The second option was to drop these movies from the analysis. The thought of another “Frozen” starting out on just a handful of screens and having to predict its eventual number perhaps not worth the effort. Third, fourth, and fifth, somewhere in there and intertwined with one another, was to use this bit of information as just another variable, determine a scale for interpreting it, and comparing the resulting models. 

<img src="/gallery/2019/wta_movies/wta_movies_pareto.jpg" alt="wta_movies_pareto" align="middle" width="100%" /><br />

Each of these options had their benefits and trade-offs. Intending this as a simple analysis, and only looking to get a good rule of thumb out of it, I did not make too much of a science of it, but I did have some fun exploring the nature of the film industry these past several decades. This analysis led to some simple but informative graphs. They confirm what many of us already suspected, that movie grosses are top-heavy with a long tail. Typically, the top 23 movies take home half the total gross for any given year, leaving the other 50% to be split among the 120+ remaining releases. Moreover, some studios live in the big movie space while others feed off the remains.<sup id="a2">[2](#f2)</sup> 

<img src="/gallery/2019/wta_movies/wta_movies_top23.jpg" alt="wta_movies_top23" align="middle" width="100%" /><br />

The idea being to have a simple and interpretable model in hand I only made a few variations and tested them for effectiveness. There were a few options to click on or off, but each had at least the opening weekend gross included. Beyond that I messed around with basic Gaussian versus student-T, adding a second feature for percentile of opening day/weekend theaters versus previous year, and lastly, I did one polynomial version out of curiosity. Nothing crazy overall. The data was trained on the most recent full year (20198), testing was done on another nine years (2009 – 17) where overall grosses were in the $10 billion range, with a final check on the movies closed in 2019 (October timeframe).

<p align="center">
<img src="/gallery/2019/wta_movies/wta_movies_model_ci.jpg" alt="wta_movies_model_ci" align="middle" width="80%" /><br />
</p>  

So, beyond making my point was I also right about the $200 million? Not quite. The total take home according to my data source was just shy at $171M. On the bright side, the model used appears to be reasonably reliable given its ease of use: start with a baker’s dozen million dollars, multiply the opening week’s take by 3 and add the two together. Viola, you have yourself a solid guess at where a movie will end up. 

<p align="center">
  <b> * * * </b>
</p> 

The first installment of John Wick was a revelation, the second true to the spirit if perhaps a bit derivative, the third a self-parody of its two siblings. The film makers were no doubt giving some viewers what they wanted and more of it, primarily in the form of action sequences and choreography. The trouble is that they turned one dial up to 11 and thereby drowning out all the other elements, or nearly so. The movie is recognizable to the style and appearance of the prior two, but it is also something else. At times the action was so drawn out that it felt as if I were watching a video game; in the case of the gun scenes it was akin to viewing a first-person shooter. Watching video games, while not playing them yourself, is entertaining to a point. Soon after the limit is passed it dovetails into frustration and boredom. Ultimately you must ask yourself what the point of your viewing is. 

Truthfully, I almost turned off the movie. There was hardly a compelling reason to see it through [other than I had made it as far as I had already](link to drain pour). It is too bad that half the time devoted to ingenious ways of maiming and killing a person were not given over to plot development and additional world development. Yes, I know, I sound ridiculous making this gripe about a comic book-esq piece of work. But this is neither so farfetched a request (see intro to The Walking Dead, Volume1 for a creator's take on gore and violence<sup id="a3">[3](#f3)</sup>) nor something whose material to do just what I am lamenting were not so clearly visible. 

To recap: John Wick is being hunted and given no quarter due to his having killed a member of the underworld in a sanctuary space – a Manhattan hotel that caters to this sort of clientele, to be precise. It was not the killing itself that was the main offense but the grounds on which it took place. Once again, rules and order. The movie consists almost entirely of Wick attempting to survive disparate persons’ attempts on his life for the bounty placed on it, while he also searches out the head of the organization to ask for leniency. However, it is not only Mr. Wick who is having a bad week. Two associates who granted him a bit of grace prior to the posting of the bounty are also being relieved of their positions. The ruling against these two comes down by strict interpretation and sticking to the letter of the law (or the code in this case). While the associates could have anticipated some level of displeasure for their momentary leniency they find the sentences overly harsh. They were after all no longer assisting JW once the contract was out, they simply provided a moment of grace, going by the spirit of the law. The letter of the law versus its spirit. Grace versus rigidity. Hmmm, paging Billy Shakespeare. Thematically there is something here to work with, to play off of, but this is never given a chance to breathe, suffocated by all of the glorified video game violence. Providing one more manner of unnecessary killing. This time of the story itself.


<img src="/gallery/2019/wta_movies/wta_movies_bayes.jpg" alt="wta_movies_bayes" align="middle" width="100%" /><br />


---

**Notes**

[Preview Puppy Photo by Marcus Wallis on Unsplash](https://unsplash.com/photos/4zfacTKyZ7w)

Code @[nbviewer](https://nbviewer.jupyter.org/github/endlesspint8/endlesspint8.github.io/blob/master/code/wta_movies/ch04_wta_movies.ipynb)

<b id="f1">1</b> Making Shit Up.  [↩](#a1) <br>
<b id="f2">2</b> For a further visual representation of disparity: 

<p align="center">
<img src="/gallery/2019/wta_movies/wta_movies_lorenz.jpg" alt="wta_movies_lorenz" align="middle" width="80%" /><br />
</p>
[↩](#a2) <br>
<b id="f3">3</b> _"To me, the best zombie movies aren’t the splatter fests of gore and violence with goofy characters and tongue in cheek antics. Good zombie movies show us how messed up we are, they make us question our station in society… and our society’s station in the world. They show us gore and violence and all that cool stuff too… but there’s always an undercurrent of social commentary and thoughtfulness._

_“Give me ‘Dawn of the Dead’ over ‘Return of the Living Dad’ any day. To me zombie movies are thought provoking, dramatic fiction, on par with any Oscar worthy garbage that’s rolled out year after year. Movies that make you question the fabric of our very society are what I like. And in GOOD zombie movies… you get that by the truckload.”_ [↩](#a3) <br>

