---
layout: post
title: Did you tap that?
subtitle: NYE Weekend Kegs (2017)
tags: ["", ""]
shortlink: 
twitimg: 
---

## What's Popping?

<iframe width="100%" height="520" frameborder="0" src="https://endlesspint8.carto.com/viz/cbc6c4b4-d801-11e6-be5f-0e3ebc282e83/embed_map" allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>

It’s not just champagne that’s bubbling up on New Year’s Eve. Craft beer has classed up the joint so much that beer ain’t just for breakfast [AM Ale link] anymore. With so many styles and producers to choose from you’ll undoubtedly be able to find a perfect pour to go with that midnight chime and kiss.

I was curious to get an idea how prevalent this potential phenomenon was. Enter social media, specifically Twitter. Though much to my dismay from previous work on Twitter data most accounts do not activate geocoding or provide location information [FN: Can’t blame ‘em. I don’t do it either.]. This has limited my previous analyses but proved to be less of an issue this time around. 

A curious thing about bars, they’re in the business of making money. One of the best ways of getting money is having a place to collect it (I know, one piece of breaking news after another). It behooves bars to provide information on where you can go to give them your money, namely a physical location [FN: In fact, most of the bars analyzed did not have their geo-position set either but they did provide their address or city location in text format. You know, for us humans not interested in pulling data and trying to do something with it.]. 

Among the accounts I follow I realized a prime candidate for scratching my itch, Digital Pour [link Twitter]. This account posts statuses regarding the tapping of kegs at specific bars [FN: In the majority of instances we are also given a third piece of info, the kicked keg, which we will ignore in this piece.]. Nearly all of these bars have Twitter accounts of their own. You can imagine an establishment as “tech forward” to use the DP board system [link] to also have a social presence. 

Having a suitable target identified I pulled the New Year's Eve weekend statuses from Digital Pour, identified the bars, grabbed their Twitter profiles, along with their addresses, geocoded these addresses in Google Maps API and also pulled their UTC offset for good measure (to be more consistent since this is a feature that is spotty coming out of Twitter). The resulting bars were then uploaded to CARTO for Geo visualization. Voilà.

Feelings? Some relief and a small sense of accomplishment for jumping through all the hoops. Also a bit of disappointment for there being far fewer bars using and posting their Digital Pour info than I expected. This will not preclude future analysis though. Stay tuned.


## Snapshot Look


<img src="/gallery/2017/digitalpour-nye/intensity.png" alt="intensity" align="middle" width="800" /><br>
<sub>Data Source: <a href="" target="_blank">Twitter</a></sub>

<img src="/gallery/2017/digitalpour-nye/cluster_chart2.png" alt="cluster_chart" align="middle" width="800" /><br>
<sub>Data Source: <a href="" target="_blank">Twitter</a></sub>

<img src="/gallery/2017/digitalpour-nye/heatmap.png" alt="heatmap" align="middle" width="800" /><br>
<sub>Data Source: <a href="" target="_blank">Twitter</a></sub>
