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

It’s not just champagne that’s bubbling up on New Year’s Eve. Craft beer has classed up the joint so much that beer ain’t just for <a href="https://youtu.be/_fLtEVc3jTU" target="_blank">breakfast</a> anymore. With so many styles and producers to choose from you’ll undoubtedly be able to find a perfect pour to go with that midnight chime and kiss.

Curious to get an idea how prevalent this possible phenomenon was, and by location, I looked around for a lighthearted way to find out. Enter social media, specifically Twitter. Though much to my dismay from previous work with Twitter data most accounts do not activate geocoding or provide location information [FN: Can’t blame ‘em. I don’t do it either.]. This has limited my previous analyses but proved to be less of an issue this time around. 

A curious thing about bars, they’re in the business of making money. One of the best ways of getting money is having a place to collect it (I know, one piece of breaking news after another). It behooves bars to provide information on where you can go to give them your money, namely a physical location [FN: In fact, most of the bars analyzed did not have their geo-position set either but they did provide their address or city location in text format. You know, for us humans not interested in pulling data and trying to do something with it.]. 

Among the accounts I follow I realized a prime candidate for scratching my itch, <a href="https://twitter.com/digitalpourtaps" target="_blank">DigitalPour on Tap</a>. This account posts statuses regarding the tapping of kegs at specific bars [FN: In the majority of instances we are also given a third piece of info, the kicked keg, which we will ignore in this piece.]. Nearly all of these bars have Twitter accounts of their own. You can imagine an establishment as “tech forward” to use the <a href="http://digitalpour.com/#home" target="_blank">DigitalPour system</a> to also have a social presence. 

Having a suitable target identified I pulled the New Year's Eve weekend statuses from DigitalPour, identified the bars, grabbed their Twitter profiles, along with their addresses, geocoded these addresses in <a href="https://developers.google.com/maps/" target="_blank">Google Maps API</a> and also pulled their <a href="https://developers.google.com/maps/documentation/timezone/intro" target="_blank">time zone/UTC offset</a> for good measure (to be more inclusive since this is a feature that is spotty coming out of Twitter). The resulting bars were then uploaded to <a href="https://carto.com/" target="_blank">CARTO</a> for geo-visualization. Voilà.

## Snapshot Looks


<img src="/gallery/2017/digitalpour-nye/intensity.png" alt="intensity" align="middle" width="800" /><br>
<sub>Data Source: <a href="https://twitter.com/" target="_blank">Twitter</a></sub>

Feelings? Some relief and a small sense of accomplishment for jumping through all the hoops. Also a bit of disappointment for there being far fewer bars using and posting their Digital Pour info than I expected. This will not preclude future analysis though. Stay tuned.

<img src="/gallery/2017/digitalpour-nye/cluster_chart2.png" alt="cluster_chart" align="middle" width="800" /><br>
<sub>Data Source: <a href="https://twitter.com/" target="_blank">Twitter</a></sub>

<img src="/gallery/2017/digitalpour-nye/heatmap.png" alt="heatmap" align="middle" width="800" /><br>
<sub>Data Source: <a href="https://twitter.com/" target="_blank">Twitter</a></sub>
