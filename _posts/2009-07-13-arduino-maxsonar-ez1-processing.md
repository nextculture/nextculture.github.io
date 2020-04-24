---
layout: single
title: Arduino + Maxsonar EZ1 + Processing 
date: 2009-07-13 14:08
categories: Arduino Development
tags: Arduino csv Development GUI MaxSonarEZ1 Processing visualization
---
After resolving my user error with the Maxsonar EZ1 with the help of <em>Bob Gross</em> I moved on to visulizing the data captured. Captuing the output of from the Arduino with Hyper ternimal as a CSV file and importing it in to Excel worked, but I was looking for something more advanced. After a little <a href="http://en.wikipedia.org/wiki/Google_(verb)">google</a> (The verb <strong>to google</strong> (also spelled <strong>to Google</strong>) refers to using the Google search engine to obtain information on the Web.) I found a simlare project <a href=" http://creativetechnology.eu/wordpress/?p=299">Arduino + Processing: range finder</a> that worked but didn't look as nice as I wanted.

So I rewrote the code to use arc instead of lines, Change the hue of the arc depending on how close the object is and CSV instead of a proprietary format. It looks much better if you ask me.

<img class="aligncenter size-full wp-image-764" title="example" src="/public/uploads/2009/07/example.gif" alt="example" width="646" height="506" />

Source code: <a href="http://www.abluestar.com/dev/arduino/snippets/range_finder_001_%5b2009Jul13_14-01-14%5d.zip">/dev/arduino/snippets/range_finder_001_[2009Jul13_14-01-14].zip</a>
