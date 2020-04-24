---
layout: single
title: Working with Open Data, Maps and data.gov.bc.ca
date: 2013-01-06 20:43
categories: Development maps opendata
tags: bathymetric Canada Development  maps opendata
---
This weekend I have been playing with more <a href="/lasers-and-vancouver-opendata/">Open Data and Maps</a> using <a href="http://mapbox.com/tilemill/">TileMill</a>. Specifically I been trying to make a <a href="http://en.wikipedia.org/wiki/Bathymetric_chart">Bathymetric map</a> of the <a href="http://en.wikipedia.org/wiki/Salish_Sea">Salish Sea</a> (BC Coastal waters)
<blockquote>A <strong>bathymetric</strong> chart is the submerged equivalent of an above-water topographic map. Bathymetric charts are designed to present accurate, measurable description and visual presentation of the submerged terrain. In an ideal case, the joining of a bathymetric chart and topographic map of the same scale and projection of the same geographic area would be seamless. The only difference would be that the values begin increasing after crossing the zero at the designated sea level datum. Thus the topographic map's mountains have the greatest values while the bathymetric chart's greatest depths have the greatest values. Simply put, the bathymetric chart is intended to show the land if overlying waters were removed in exactly the same manner as the topographic map.
<strong>Source</strong>: <a href="http://en.wikipedia.org/wiki/Bathymetric_chart">http://en.wikipedia.org/wiki/Bathymetric_chart</a></blockquote>
I have been struggling to find Bathymetric data that covers both Canada and USA coastal regions for the Salish Sea. The USA data is easy to find and highly detailed but finding data that matches up with Canadian data has been next to impossible. Even finding data was difficult in the first place.

I was able to fine some low detail layers for <a href="http://www.naturalearthdata.com/downloads/10m-physical-vectors/">0 Meters and 200 Meter</a> for North America from <a href="http://naturalearthdata.com">naturalearthdata.com</a>  that are useful for plotting out the major elements.

I also found some highly detailed coastal layers from <a href="http://data.vancouver.ca/datacatalogue/index.htm">Vancouver Open Data</a> catalog that I used for the finer details around Vancouver.

Next I added <a href="http://www.data.gov.bc.ca/dbc/search/detail.page?ms=url%3Aapps.gov.bc.ca&amp;recorduid=173523&amp;title=Coastal%20BC%20Bathymetry">Coastal BC Bathymetry</a> data from <a href="http://www.data.gov.bc.ca/dbc/index.page?">DataBC</a> but the files did not import in to TileMill correctly, and the "<em>Depth</em>" column got corrupted. Super annoying as it was the main column I was interested in. I had to spend a few hours learning about <a href="http://en.wikipedia.org/wiki/Shapefile">.shp and .dbf files</a> and was eventually able to edit the file to make it work sort of.

<a href="/public/uploads/2013/01/BCMap-1024x719.png"><img class="size-thumbnail wp-image-3138 alignleft" alt="BCMap" src="/public/uploads/2013/01/BCMap-150x150.png" width="150" height="150" /></a>BC Open Data catalog is weird in that I had to add the data to a shopping card, then "check out" the data with my email address and wait for a link to arrive in my email. The link came quickly taking at most 25mins. I still found the process strange as most of the other open data sites let me download it directly.

Currently I have only included the Canadian data as Its been exceedingly difficult to match it up with the US data.

This map still needs a lot of work to get it right. I am expecting to have to do a lot of optimization in <a href="http://inkscape.org/">InkScape</a> afterwards. Each colored layer will be a different layer of plywood  and stacked on top of each other glued in to place with "Ground level" layer being the top visible layer. I am still debating if I should leave all the little islands on the map as they will dramatically add to the complexity of the map.

<a href="/public/uploads/2013/01/bc_waterways-1024x842.png"><img class="size-thumbnail wp-image-3136 alignright" alt="bc_waterways" src="/public/uploads/2013/01/bc_waterways-150x150.png" width="150" height="150" /></a>I want to add some complexity to the top "<em>ground level</em>" layer so its not just a normal sheet. I was thinking about adding rivers and lakes to the top layer to add some details. I found the <a href="http://www.data.gov.bc.ca/dbc/search/detail.page?ms=url%3Aapps.gov.bc.ca&amp;recorduid=173918&amp;title=WSA%20-%20WATER%20POLYGON%20FEATURES%20(1:50K)">river data</a> on DataBC website.

<a href="/public/uploads/2013/01/lowermainland_water-1024x769.png"><img class="size-thumbnail wp-image-3137 alignleft" alt="lowermainland_water" src="/public/uploads/2013/01/lowermainland_water-150x150.png" width="150" height="150" /></a>The river data looks beautiful but to complex and there doesn't seem to be a way of differentiating between rivers and streams.

&nbsp;

&nbsp;
