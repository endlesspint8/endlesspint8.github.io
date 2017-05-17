---
layout: post
title: Branching out
subtitle: One Twig at a Time
tags: ["D3", "BeerVis"]
shortlink: http://bit.ly/ep8D3noob
image: http://endlesspint.com/gallery/2016/usb_d3_posneg.PNG
---

While it is not clear if anyone cares to go on looking at the percentage change of brewery counts over time (<a href="https://www.youtube.com/watch?v=8T2l15bKMZk" target="_blank">crickets!</a>) I am not ready to give it up. At least not yet, but this is likely the last word on the matter for a while. It is good to follow through on what you start and I certainly want to be a good influence on my future nephews/nieces. Additionally, there is the self-serving reason of being able to reuse this visualization work in future posts and that's some non-negligible motivation. That's right little nephews, be lazy-efficient. Create, refine, and reuse: don't be a sisyphean programmer.<sup id="a1">[1](#f1)</sup>

The other motivation is to work with <a href="https://d3js.org/" target="_blank">D3</a> more (hey look, <a href="http://www.nytimes.com/interactive/2014/12/27/upshot/mapping-the-paths-to-the-nfl-playoffs.html?_r=0" target="_blank">The New York Times uses it!</a>). Most of the visualizations I create on the job are either in other programs or static (or on local servers, which is effectively the same thing where this site is concerned).<sup id="a2">[2](#f2)</sup> I need to expand my toolkit for this site.

> "The lessons you are meant to learn are in your work." -<a href="http://browse.nypl.org/iii/encore/search/C__Sart%20and%20fear__Orightresult__U?lang=eng" target="_blank">Art & Fear</a>, David Bayles & Ted Orland

I am going to show several variations of the visualization below, both to fill up space (lazy-effective) and to walk through the data transformations. Ask yourself which are easier to read or more importantly, which are most effective in getting across the information of the underlying numbers. 

<style>

.bar {
  fill: steelblue;
}

.bar:hover {
  fill: brown;
}

.axis {
  font: 8px sans-serif;
}

.axis path,
.axis line {
  fill: none;
  stroke: #000;
  shape-rendering: crispEdges;
}

.x.axis path {
  display: none;
}

.line {
  fill: none;
  stroke: orange;
  stroke-width: 2.5px;
}

</style>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>

var margin = {top: 20, right: 20, bottom: 30, left: 40},
    width = 864 - margin.left - margin.right,
    height = 450 - margin.top - margin.bottom;

var x = d3.scale.ordinal()
    .rangeRoundBands([0, width], .1);

var y = d3.scale.linear()
    .range([height, 0]);

var xAxis = d3.svg.axis()
    .scale(x)
    .orient("bottom");

var yAxis = d3.svg.axis()
    .scale(y)
    .orient("left")
    .ticks(10);

var line_5yr = d3.svg.line()
    .x(function(d) { return x(d.year) + x.rangeBand()/2; })
    .y(function(d) { return y(+d.total); })
    .interpolate("basis");

d3.csv("/datasets/usb/brwComp.csv", type, function(error, data) {
  if (error) throw error;

  x.domain(data.map(function(d) { return +d.year; }));
  y.domain([0, d3.max(data, function(d) { return +d.total; })]);

  console.log(data.total);
  
  var svg = d3.select("div#samesame").append("svg")
    .attr("width", width + margin.left + margin.right)
    .attr("height", height + margin.top + margin.bottom)
  .append("g")
    .attr("transform", "translate(" + margin.left + "," + margin.top + ")");

  svg.append("g")
      .attr("class", "x axis")
      .attr("transform", "translate(0," + height + ")")
      .call(xAxis)
    .selectAll("text")
      .attr("y", 0)
      .attr("x", 9)
      .attr("dy", ".35em")
      .attr("transform", "rotate(90)")
      .style("text-anchor", "start");

  svg.append("g")
      .attr("class", "y axis")
      .call(yAxis)
    .append("text")
      .attr("transform", "rotate(0)")
      .attr("x", width/2)
      .attr("y", 6)
      .attr("dy", ".71em")
      .style("text-anchor", "end")
      .text("US Brewery Count");

  svg.selectAll(".bar")
      .data(data)
    .enter().append("rect")
      .attr("class", "bar")
      .attr("x", function(d) { return x(d.year); })
      .attr("width", x.rangeBand())
      .attr("y", function(d) { return y(d.total); })
      .attr("height", function(d) { return height - y(d.total); });

  svg.append("path")
      .datum(data)
      .attr("class", "line")
      .attr("d", line_5yr);
});

function type(d) {
  d.total = +d.total;
  return d;
}

</script>
<div id="samesame"></div>

<sub>Data Source: <a href="http://www.beerinstitute.org/" target="_blank">Beer Institute</a></sub>

First off, if you can read this it means you either didn't bang your head hard enough against the screen or you haven't read the previous posts. The chart above, in one form or another, has made a cameo in three successive pieces. It's included hear for context. A closer chart of what I was hoping to present is below.

<iframe src="http://endlesspint.com/gallery/usb_d3_posneg.html" width="960" height="500" marginwidth="0" marginheight="0" scrolling="no" frameBorder="0"></iframe>

<sub>Data Source: <a href="http://www.beerinstitute.org/" target="_blank">Beer Institute</a></sub>

Shout out to the internets in general and to the coding resources specifically,<sup id="a3">[3](#f1)</sup> but I needed more time to get this in the shape I was hoping for. However, my new commitment to "ship" something keeps me from holding back.

> “The show doesn’t go on because it’s ready; it goes on because it’s 11:30.” -<a href="http://www.goodreads.com/quotes/370068-the-show-doesn-t-go-on-because-it-s-ready-it-goes" target="_blank">Lorne Michaels</a>


Excuses aside, let's focus on the positives and take-aways:

1. Though nothing spectacular, in the first vis we have an interactive element when hovering our mouse over the bars. We can build on this!
2. Though ugly, the second vis succeeds in highlighting the percentage change for each year. Kudos.
3. D3 is frustrating in the beginning; `console.log()` is your friend.

**Items For Future Consideration**

- Implement "better" plot elements: title, legend, axis labels, etc.
- Use hover tool-tips to provide additional, granular, information, eg. place mouse on bar, get `year` and `brewery count`.
- Once again, split by macro/micro breweries. Though that was not the focus here it is worth mentioned again. 
- Create a plot similar to <a href="http://bl.ocks.org/slnader/9452976" target="_blank">this</a> (sadly no Public License).

<br>

---

**Notes**

<b id="f1">1</b> ... Or whatever you'll be doing in the future; which, <a href="https://www.youtube.com/watch?v=7Pq-S557XQU" target="_blank">if things continue along certain trends</a>, may be whatever the robots leave for us; that may be <a href="https://en.wikiquote.org/wiki/Talk:John_Maynard_Keynes#.22The_government_should_pay_people_to_dig_holes_in_the_ground_and_then_fill_them_up..22" target="_blank">ditch digging</a>, in which case you won't be able to avoid being a bit sisyphean; the upside is you probably won't be a "sisyphean" word-using sissy. [↩](#a1) <br>
<b id="f2">2</b> No need to bore the less data interested reader: Python (matplotlib, seaborn, bokeh) & R (ggplot, Shiny), mostly. [↩](#a2) <br>
<b id="f3">3</b> Special mention to <a href="http://bl.ocks.org/mbostock" target="_blank">Mike Bostock</a> and the resources he's provided under Public License. His lifted code is obvious here. Also to <a href="http://www.nicksuch.com/2014/03/26/d3-sample/" target="_blank">Nick Such's post</a> regarding use of `<iframe>` and `<div id="example">`, both implemented in this post. [↩](#a3) <br>
