---
layout: page
title: endlesspint
subtitle: Positive/Negative Percentage Change of US Breweries (1887-2012)
tags: [code, US Breweries]
---

<style>

.bar--positive {
  fill: steelblue;
}

.bar--negative {
  fill: brown;
}

.axis text {
  font: 10px sans-serif;
}

.axis path,
.axis line {
  fill: none;
  stroke: #000;
  shape-rendering: crispEdges;
}

</style>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>

var margin = {top: 20, right: 30, bottom: 40, left: 30},
    width = 960 - margin.left - margin.right,
    height = 500 - margin.top - margin.bottom;

var x = d3.scale.linear()
    .range([0, width]);

var y = d3.scale.ordinal()
    .rangeRoundBands([0, height], 0.1);

var xAxis = d3.svg.axis()
    .scale(x)
    .orient("bottom");

var yAxis = d3.svg.axis()
    .scale(y)
    .orient("left")
    .tickSize(6, 0);


d3.csv("/datasets/usb/brwComp.csv", type, function(error, data) {
  x.domain(d3.extent(data, function(d) { return d.perChgTot; })).nice();
  y.domain(data.map(function(d) { return d.year; }));

  var svg = d3.select("div#percent").append("svg")
    .attr("width", width + margin.left + margin.right)
    .attr("height", height + margin.top + margin.bottom)
  .append("g")
    .attr("transform", "translate(" + margin.left + "," + margin.top + ")");
    
  svg.selectAll(".bar")
      .data(data)
    .enter().append("rect")
      .attr("class", function(d) { return "bar bar--" + (d.perChgTot < 0 ? "negative" : "positive"); })
      .attr("x", function(d) { return x(Math.min(0, d.perChgTot)); })
      .attr("y", function(d) { return y(d.year); })
      .attr("width", function(d) { return Math.abs(x(d.perChgTot) - x(0)); })
      .attr("height", y.rangeBand());

  svg.append("g")
      .attr("class", "x axis")
      .attr("transform", "translate(0," + height + ")")
      .call(xAxis);

  var tickNegative = svg.append("g")
      .attr("class", "y axis")
      .attr("transform", "translate(" + x(0) + ",0)")
      .call(yAxis)
    .selectAll(".tick")
    .filter(function(d, i) { return data[i].value < 0; });

  tickNegative.select("line")
      .attr("x2", 6);

  tickNegative.select("text")
      .attr("x", 9)
      .style("text-anchor", "start");
});

function type(d) {
  d.perChgTot = +d.perChgTot;
  return d;
}

</script>
<div id="percent"></div>

<sub>Data Source: <a href="http://www.beerinstitute.org/" target="_blank">Beer Institute</a></sub>
