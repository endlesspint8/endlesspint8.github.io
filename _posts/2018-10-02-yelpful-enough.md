---
layout: post
title: Yelpful Enough
subtitle: Appropriation not Always Appropriate
tags: ["mle", "seaborn", "nyc"]
shortlink: 
image: http://endlesspint.com/gallery/2018/bar-hoppin/ratings mle stars.png
sideof: 

---

## Eeny, meeny

With the cold weather behind us it is time to return to walking and claiming the city more fully.<sup id="a1">[1](#f1)</sup>  Even in traveling by subway, taxi, or bike we have more daylight and warm weather than in recent months, both encouraging us to stay out a bit (longer) between work and home. In a couple of months it will be hot enough to frequent rooftop bars, a few months further still we will once again be sliding into another frigid winter. The time is now to enjoy and appreciate our out-of-doors opportunities. Now, if those out-of-doors excursions should lead us to an indoor establishment for a delicious beer, in order to refresh and quench some thirst before proceeding further of course, so be it. However, our time is precious, the daylight is wasting away, even as we have more of it, so if we are going to be cooped up it might as well be at a worthwhile establishment. As with most things craft related, beer included, if you are gonna be consuming something make it worth the effort.

The city has a ton of options and this cuts both ways with respect to knowing and enjoying what to do. With too many choices we can actually experience less well being and so it makes sense to prioritize, better filter, the candidates. At the same time, and this will come across as ironic when the method is discussed, [we do not need to make a crazy study of the subject](https://www.psychologytoday.com/us/blog/science-choice/201506/satisficing-vs-maximizing). What follows is a comparison of very good bars, they already clear the threshold of quality beers and tick off several other relevant criteria related to location and atmosphere. As such, you would be best served walking into whichever was right across the street from you in a city as dense as NYC. Additionally, with the continually rotating taps, bottles, seasonal menu items, clientele, staff, the aforementioned weather, and your given mood and financial outlook on any particular day the preferences are liable to resort themselves. This is all to say that as a [satisficing](https://en.wikipedia.org/wiki/Satisficing) exercise you can do far worse than closing your eyes and picking one of these at random.

## But what do you really think?

At the same time we are human and we love to [compare, contrast, and complain](http://www.thehappytalent.com/blog/gossip-isnt-petty-its-a-powerful-evolutionary-tool). To that end we turn to fellow urban explorers to help enlighten us on our options, but rather than simply looking at ratings of places in isolation we will compare the relative worth of specific bars against one another. In order to do a cross-watering hole-comparison we will identify patrons with multiple bar reviews. This will allow us to use their ratings as a form of vote from which to generate a general preference scheme. With several hundred/thousand ratings across a a few dozen beer halls we can extract individual leanings and match them with others to get a general predisposition on where to grab a pint. 

<img src="/gallery/2018/bar-hoppin/ratings usr pref.png" alt="ratings usr pref" align="middle" width="100%" /><br />
<sub><b>Data Source</b>: <a href="https://www.yelp.com/search?find_desc=Beer+Bar&find_loc=New+York,+NY&start=0&sortby=review_count" target="_blank">Yelp</a>, <em>Most Reviewed NYC Beer Bars</em> [Accessed: April 2018]

There are many ways to slice data. The act of slicing is one of the key abilities of data analysts and machine learning experts. There are the data on their own, an amorphous mass that can be taken as is, whatever that may mean and entail. What you get, often times do confront, is an incoherent, inappropriate, and unhelpful collection of inputs ([The End of Theory](https://www.wired.com/2008/06/pb-theory/), be damned). Data is a choice. It is structured, captured, and shared, all intertwined within a backdrop of decisions that belie the idea of information simply falling into our laps. We are today awash in data but we are not always blessed with adequate curation, admittedly another layer between ourselves and the underlying impressions but something very much needed, along with a healthy sense of skepticism.

## Slice & dice

I sought out a simple exercise. With summer approaching and the willingness to stretch our legs further in pursuit of seeing friends, new places, and having a pint I wanted to see which among a subset of bars would be the most highly regarded. If not a ranking, which are quite boring, at least a round robin pecking order to get discussions and friendly debate going.

Desiring sufficient data to make the comparison meaningful I limited myself to the 10 most rated bars, not necessarily the 10 highest rated. This carried some logic but also drawbacks. As always when making (data) decisions it is important to be open about the choices and provide some sensible explanation for why they were taken.<sup id="a2">[2](#f2)</sup> Because the site I was using was not specifically beer (bar) related I expected to have reviewers of all sorts, craft beer drinkers, bar aficionados, barflies, and one time visitors. It did not seem appropriate or interesting to consider all ratings equally. At least not in isolation.

What was desired was an expression of the preferences among patrons who went to two or more of the bars. Choosing the top 10 most rated bars increased the chances of there being such patrons and boosting their numbers.

What we are looking for determines what we see. If you wanted a quick response to highest rated beer bar, Yelp offers that functionality, including other criteria and filters such as geographical location and how expensive an establishment is. These are helpful, wonderful and come to be seen as necessary functionalities but we can go further. There are several ways of culling data in pursuit of relevance. 

<img src="/gallery/2018/bar-hoppin/ratings mle pref.png" alt="ratings mle pref" align="middle" width="100%" /><br />
<sub><b>Data Source</b>: <a href="https://www.yelp.com/search?find_desc=Beer+Bar&find_loc=New+York,+NY&start=0&sortby=review_count" target="_blank">Yelp</a>, <em>Most Reviewed NYC Beer Bars</em> [Accessed: April 2018]

Before judging the appropriateness of multiple views, it would be worthwhile to determine what we mean by relevant. As much has already been hinted at but let us be explicit: we wish to determine the preferences of reviewers for bars, where the reviewers had visited at least two of the candidate locations. The rationale being that patrons of several, in common bars can better sort out the benefits and drawbacks of locations in relation to one another. For the purposes of identifying a top bar it would make little sense to compare it against a French bistro (if we even knew what such a comparison would entail), airport bar, fast food location, etc. It would be difficult to determine in what meaningful way one such establishment were better than another, outside of some basic necessities revolving around food safety and general hygiene. Surely, each and more of the categories that an establishment can fall into may be preferable to all the others in different contexts. We are looking to minimize the variety of contexts by sticking to a particular type of bar, reviewed by those who have the relevant experience in patronizing them (again, at least two bars). 

This simple approach has drawbacks of its own. For one, we only take NYC bars into consideration, specifically the 10 chosen. Bar experts from out of town are unlikely to have their input included unless they visited and reviewed two or more local pubs (not uncommon, however [speaking from experience]). Out of town or or not an additional drawback is only including feedback from those whose reviews include two of the chosen bars. You could have an instance where a reviewer rated one of the selected candidates and all of the bars listed 11 through 20, only to have their review filtered out. These are just two obvious ways where the expert judgement saught can be left out.<sup id="a3">[3](#f3)</sup> 

## Popular vote

<img src="/gallery/2018/bar-hoppin/ratings mle stars.png" alt="ratings mle stars" align="middle" width="100%" /><br />
<sub><b>Data Source</b>: <a href="https://www.yelp.com/search?find_desc=Beer+Bar&find_loc=New+York,+NY&start=0&sortby=review_count" target="_blank">Yelp</a>, <em>Most Reviewed NYC Beer Bars</em> [Accessed: April 2018]

With respect to the “voting” mechanism of determining the general predisposition of one bar over another we have at least two counting approaches: electoral and popular. Much like the US voting system we may expect slightly different results, e.g., two bars head-to-head may show a slight preference toward one, however, it is possible that the “winning” bar wins all of its comparisons by close margins (5 stars to 4) while having a wider disparity on the votes cast against it (3 stars versus 5). Given a close enough “race” the bars with the most user preferences may end up with the fewer stars between the two (e.g., Ginger Man and Clinton Hall). Another example of making decisions with/about data.<sup id="a4">[4](#f4)</sup> 


---

**Notes**

<b id="f1">1</b> Regardless of when this is read it seems worth mentioning, given the posting date, that this piece was initially meant to run in the May/June timeframe.  Hence the warm weather themes.  [↩](#a1) <br>
<b id="f2">2</b> Naturally, focusing on specific data means filtering and risking ending up with too few inputs, even while achieving a more appropriate scope. Example: any bar pair combo with only one common reviewer between them would skew the preferences heavily in the direction of the preferred bar. That is the case in a voter-take-all face off. Regularising the vote tally so that each bar combo in the matrix starts out with a small vote would at least dampen 100% versus 0% comparisons. [↩](#a2) <br>
<b id="f3">3</b> [The MLE approach](/2016-08-01-six-pack-project-netherlands.md#t-ij---ipa) helps highlight some of the limitations and assumptions made of data. To that end it reveals uncertainty and sheds light on possible alternatives: heuristics for choosing among several options, game theory approaches to competing interests, and the concept of satisficing versus maximizing. [↩](#a3) <br>
<b id="f4">4</b> This doesn't even scratch the surface on time frame: should votes from several years back count as much as those from last week? [↩](#a4) <br> 
