---
layout: post
title: Why are there no brothers on the wall?
subtitle: Forget the Images, Let's Own the Wall 
tags: ["ParallelSets", "D3"]
shortlink: http://bit.ly/prplxd3
twitimg: pic.twitter.com/nqGsQDvTWQ
image: http://endlesspint.com/gallery/2017/beer-prplxd/wheel_spin.gif
sideof: ["Bubble chart", "http://eepurl.com/cj8urH", "of beer style features."]
---

## Motivation 
 
I am a boxing fan, someone who appreciates beer, and a lover of books. I could not tell you why it has taken me such an inexcusably long time to do a piece on books. Maybe I'm just fashionably late, even to my own party. This comes as no surprise to myself or anyone who knows me. ‘Better late than never’ will be my next tattoo, if i ever get around to it. Be that as it may we are here now.
 
An intuitive analysis of books would deal with something text or natural language related but I am leaving that for another time. Instead I am going to do a simple feature analysis of certain titles. Two separate influences got me started down this path. The first is the Jason Davies parallel set visualization I have appropriated below. The second, which came about in search of a data set to use the vis on, and in the reverse order of how a conscientious data scientist would behave, is <a href="https://www.outofprintclothing.com/" target="_blank">Out of Print</a> clothing, a company that primarily sells t-shirts emblazoned with excellent book covers, both in writing quality and cover art. This potential data source got me going even more so than the visualization. 
 
I love books, beer, and boxing. Somewhere in there, and certainly not far behind, is my fondness for t-shirts. In fact, I love mixing t-shirts with these other areas of interest, so you bet your ass I have brewery t-shirts and shirts from this company.<sup id="a1">[1](#f1)</sup> I don't have any boxing shirts at the moment, maybe that's also something I'll end up getting around to, just like this piece. <a href="https://www.rootsoffight.com/collections/mike-tyson" target="_blank">Iron Mike, anyone</a>?

https://www.flickr.com/photos/rvthomas67/ Russell Thomas
 
Like many late 20th century males I have too many of these cultural indicators, though I have cut back and I'm only holding onto the essentials. The shirts are comfortable and fit well, the titles are top shelf, and the covers selected are of eye-catching designs that translate well to many accessories, clothing included, t-shirts specifically. 

## Deliberate consumption
 
I prefer to only wear the shirts of books I've read, and only the shirts of breweries I've been to. The desire to have a more intimate relationship with a book or brewery than just the image or idea of the thing rests behind this decision. It is very easy to glom on to the most salient features or the ones served up to us. However, every time we take things at face value we abdicate a bit of her own authority to others. Much of this is inevitable. For instance I am not going to go back myself and verify all of the research findings in a certain field. I rely on the scientific method, the scientific community, and the peer review process. Other subjects are not as well grounded but yet we, in our better moments, attempt to identify trustworthy authorities in a given field and defer to their judgment. 

Occasionally, either through interest or expert training, we can delve a bit deeper ourselves and develop a more than passing judgment, we can be the aforementioned authorities through developing our subject matter expertise. I would like nothing more but to continue along this path with respect to books, beer, and boxing. I wish the same for others, though of course not for necessarily the same subjects but topics of their choosing.
 
I wanted to see how the Out of Print t-shirt collection stacked up on several categories and realized I could easily do such a thing, thereby scratching a few itches: web scraping, visualization, and a little analysis. Like a good bookworm I collect more than I can possibly read. This used to be physical, then it switched to digital, but like the t-shirts I'm cutting back. 

With a visualization in hand and an appealing target it was now a matter of deciding on the actual features to map onto. In keeping with the <a href="https://www.kaggle.com/c/titanic" target="_blank">Titanic data set</a>, which this is based on, I also limited my exploration to four <a href="https://stats.stackexchange.com/questions/206/what-is-the-difference-between-discrete-data-and-continuous-data" target="_blank">categorical dimensions</a>. Perhaps it is the identity politics in the air, the national retrenchment we are seeing around the globe, or just a hangover from the 90’s political correct movement but whatever the influence I settled on identifying the dead old white guys.

## Pivot TIME
 
I realize this is a sensitive topic for a variety of reasons across an uneven spectrum of validity. I do not wish to get more embroiled in the topic than I am already stupidity doing. Thus I will limit the best I can the dumb things I say. Even so, the decision to proceed is my own. It might be unfair to make the same decision for another, including the Out of Print clothing company, since I am not looking to single out anyone player, I just happened to be familiar with one company’s connection to books in particular. As such I decided to find a different data source, one that could and has taken its lumps. 
 
Back in the dark days of the early 21st century, all the way back in 2005, when magazines were still mostly physical items, a little publication called TIME put out a list of <a href="http://entertainment.time.com/2005/10/16/all-time-100-novels/" target="_blank">the top 100 English-language novels of the 20th century</a>. Not quite the entire 20th century but starting in 1923, the year the publication got started, incidentally leaving off Ulysses from the list, and a little into the new millennium up until the list was published.
 
As opposed to the generic clickbait and superficial listicles of their current website this collection actually had substance.<sup id="a2">[2](#f2)</sup> Whatever happened to this outlet, CNN also? I remember looking up with reverence to these sources of information. Then again I was a teenager. Perhaps my reading comprehension went up but I have a sneaking suspicion they more than met me halfway. A bit sad really. Then again, what can you expect? These sources of temporary information don't really, and shouldn't be relied on to, bring the wisdom to the fore. That is what books are for and just like that we are back.
 
Switching to the TIME booklist was actually a boon to the data collection process. We are not talking about large data sets in any case but there are different degrees of workable or friendly data sets. Out of Print provides only the book titles of the shirts it sells. No author name and no publication date. Those are crucial pieces of information in determining the novelist’s characteristics.

## Definition of Features
 
Let's define the categories in order so as to be clear about what is being tabulated. 
 
D - Shit, I guess the transhumance or religious folk can get on me about this and I suppose this may turn out to be the touches the ball topics. For our purposes and author would be considered pushing daisies if they were deceased at the time of the creation of the list (2005). [Princess Bride]

<img src="/gallery/2017/books/dowgs/TIME100_percAlive2.PNG" alt="TIME100_alive" /><br />
<sub>Data Source: <a href="http://entertainment.time.com/2005/10/16/all-time-100-novels/" target="_blank">TIME Magazine</a></sub>
 
O - Every few years we hear Y is the new X but using commonsense and the influences from nip tuck, Louis CK, and even The Bard himself as guides, I have settled on 45 as a compromise. Any author over 45 at the time of the book and questions publication would be categorized as "old". Finally, the dead. [Louis CK]

<img src="/gallery/2017/books/dowgs/TIME100_median.PNG" alt="TIME100_median" /><br />
<sub>Data Source: <a href="http://entertainment.time.com/2005/10/16/all-time-100-novels/" target="_blank">TIME Magazine</a></sub>
 
W - You can make a more easy argument about the social construction of race that even sex, right? yet once again I'm going to go out with my commonsense understanding and how I might describe the respective writers: black dude, white chick, Hispanic guy. Make sense? I think you get the idea [Mo’nique (// Race is a sensitive and moving target (Domino) ) & Chris Rock]

<img src="/gallery/2017/books/dowgs/TIME100_demo.PNG" alt="TIME100_demo" /><br />
<sub>Data Source: <a href="http://entertainment.time.com/2005/10/16/all-time-100-novels/" target="_blank">TIME Magazine</a></sub>	
 
G - The sex of the novelist, with all due respect to any future claims by transhumant and or transgender persons of the future, remain a binary description.. 
 

 
## Data, What it is and is not
  
[gist link for wiki pull; include screen shot of wiki donation]
 
Data is an important step toward a better understanding of a subject. Setting aside concerns about measuring tools, inherent biases, what can and cannot be reduced to data, and other <a href="https://mitpress.mit.edu/books/raw-data-oxymoron" target="_blank">raw data oxymorons</a>, analytic models can be viewed through a four stage process. This framework can help better orient what specifically is being presented and what can reasonably be expected to be done. It is worthwhile to keep this analytical framework in mind when looking at the data in this piece. 
 
The framework looks to the use of data as <a href="http://leadtime.com/blog/data-analytics-101-descriptive-diagnostic-predictive-and-prescriptive" target="_blank">descriptive, diagnostic, predictive, and/or prescriptive</a>. Descriptive models lay out _what_ happened. Diagnostic models detail causes or _why_ it happened. Predictive models outline probabilities of what _will_ happen. Prescriptive models provide suggestions on _what to do_. What we have here, as far as the data is concerned, is the first step, descriptive. Though the least sophisticated of the data analytic models it is a critical first step. How things worked out to get to this situation or what to do concretely is outside the purview of this data set and any conjectures would be speculative without additional sources and references, narrative or numeric.
 
 <iframe src="http://endlesspint.com/gallery/2017/books/dowgs/Parallel Sets_TIME100.html" width="1152" height="720" marginwidth="0" marginheight="0" scrolling="no" frameBorder="0"></iframe>
 
## List This
 
What is the point of having lists? Is it that we cannot help ourselves as humans to weigh, measure, and tabulate things? Certainly that is part of it and I know I feel the pull. Aside from books I enjoy talking boxing, about who could beat who, who should be considered better than another fighter, and so on (ad nauseam, my lady would add). Pre-fight prognostications are tantalizingly interesting and post bout breakdowns are also welcome and appreciated. List creation no doubt has to do with our drive for meaning and understanding, two complimentary though not identical things. 
 
Lists offer structure, a set of criteria, and an ordering or ranking. They help to clarify a topic as well as offer suggestions for further exploration on the items we are not as familiar with. They offer the promise of a shortcut, a sure fire way of getting to the heart of the matter. Read these books, drink these beers, visit these countries, try these foods, play these games, etc. Do these few essential things and you will have understood something on a deeper level. 
 
Lists also say much by what they leave out. We can divine the interests, influences, and biases of a person or group from a list. At times we feel compelled to dismiss someone out of hand for a perceived flawed list, less often but more rewarding are the opportunities to elevate our opinion of someone who successfully challenges our preconceived notions and even (hopefully) changes our mind on a policy, athlete, or book. The person who can do this has destabilized our earlier foundations. Even if we feel no strong allegiance to the items, the fact of our re-ordering them has made us question our certainty, on however small a scale. This is a good thing. Rare is the topic that can be resolved without dispute and rarer still is our ability to stay interested in such topics. I believe I speak not just for myself when I say that it is the constant resorting that brings the most growth and nuance to our understanding (and appreciation) of a subject.
 
I have used the TIME list as a resource when I have run out of inspiration or side interests. I have yet to be steered wrong though there have been occasions when I have been ill prepared for certain titles. This was usually a matter of time constraints on my part and sometimes due to a mismatch in book style and personal temperament. Some books have been put down before completion. A surprising number of these have been revisited and completed. 
 
I come to the list for a bit of purchase. There is so much to choose from it can be quite helpful to have a place to stand on and scan the surroundings. This is helpful even if you disagree with the resource. You have at least delineated a set of items you wish to consider or exclude. From here you can appraise the criteria that makes the most sense to you. This is a sort of unsupervised learning [link] on a personal and human level. You identify books you are interested in, without judgments or preconceived notions, and with a good number in hand you take a look to see what similarities or themes emerge among them, if any. Perhaps you have discovered an interest in World War I history, Harlem Renaissance fiction, or existentialist philosophy [links]. Whatever it may be you now have some categories to work with: to group like titles together, see where they fit with respect to each other and the larger cannon. Now you can delve deeper and take a step closer to becoming that subject matter expert, that authority. But you have to get in there and do the work. Simply looking at the list is a false exercise.
 
## Content v Image
 
The demographics are disappointingly disproportionate. One might even add predictably so. After all human history is studded with instances of inclusiveness that are the exception rather than the rule. Yet I would advise against the knee-jerk reaction of tearing down the images presented for no other reason then the disparity in the numbers. We should discard these images, and better yet replace them, on the basis of excellence, backed by an intimacy with the works.
 
[Biases, cultural or otherwise, are important for us to be aware of and acknowledge. Their ramifications have hard implications now and moving into the future as they become imbedded into our institutions and with increasing frequency into the machines and algorithms we will be depending on moving forward. These biases may be picked up from within language itself and the data sets we create to the detriment of already vulnerable populations. ]
 
We would all be better served in dealing with the substance and putting the images in perspective, because while we argue about what is on the wall we may be overlooking who owns the wall and controls the framing. Arguably the numbers are a symptom more than a root cause. If we are going to be more concerned about ownership of the wall we can take encouragement from the education numbers related to women and horrified by the incarceration disparities [the Atlantic video]. Let’s target facts on the ground, not books on a list. 
 
## Deliberate & Detailed Criticism
 
 
Again I do not care to dispute this list’s specific standards one way or another but it does entice me to seek out the voices I am not hearing from and have also been highly regarded. The disparities should attract our attention and perhaps receive extra interest to make sure we hear the voices of the underrepresented. 
 
[this offers another opportunity to insert a bit of data talk: exploration v exploitation]
 
I have routinely made a conscious effort to read non-DOWG authors. On occasion the differences have been negligible but more often than not I have been confronted by a different sensibility than the more commonly available one. I believe these experiences benefit anyone who exposes themselves to them, challenging the regular everyday presentation of reality. We take in our common cultural settings by default, very often never noticing the default we encounter as a choice. A choice that has oftentimes been made ahead of time by others and that we live with unreflectively, like fish in water [DFW link], oblivious to our own surroundings.
 
 
<br>

---

**Notes**

<b id="f1">1</b> I have bought about 10 of these shirts over the years. I don't have stock and I am not paid to endorse them (yet?!) but I recommend them without reservation and in case you're on the fence, please know that they also give to charity. Basically this company rocks. [↩](#a1) <br>
<b id="f2">2</b> The average American reads X books a year. That's not overly impressive but if you applied that rate to these books you could find worse ways of enlightening yourself for (a couple of) Y decades. [↩](#a2) <br>
<b id="f3">3</b> . [↩](#a3) <br>
