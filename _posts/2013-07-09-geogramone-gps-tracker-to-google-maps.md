---
layout: single
title: GeoGramOne - GPS tracker to Google maps
date: 2013-07-09 20:27
categories: Projects
---
<a href="/public/uploads/2013/07/GeogramOneTop2.jpg"><img class="size-thumbnail wp-image-3438 alignright" alt="GeogramOneTop2" src="/public/uploads/2013/07/GeogramOneTop2-150x150.jpg" width="150" height="150" /></a>A few weeks ago I ordered a <a href="http://dsscircuits.com/geogram-one.html">GeoGramOne</a> board from <a href="http://dsscircuits.com">DSScircuits</a>. Its a Open source GPS tracker that was <a href="http://www.kickstarter.com/projects/dsscircuits/open-source-tracking-device">succefuly funded on Kickstarter</a>. The board combines a <a href="http://en.wikipedia.org/wiki/Global_Positioning_System">GPS</a>, <a href="https://en.wikipedia.org/wiki/GSM">GSM Modem</a> (cellphone), <a href="http://www.arduino.cc/">Arduino</a> (Atmega328p),  <a href="https://www.sparkfun.com/products/10617">lipo fuel gauge</a>, and 6 axis digital <a href="http://en.wikipedia.org/wiki/Accelerometer">accelerometer</a>.

With the default firmware you could send a SMS message to the device and it would reply with a SMS with its current location. It had a few other interesting features that used SMS as the transport layer for the GPS coordinates.

The board design and the firmware are all open source. This means that I can edit the firmware to do what I want it to do. Getting the GPS coordinates via SMS is great when you want to actively know where the GPS is at that exact moment. But I wanted to use this board to actively track and records the location of the GPS as it travels around. Preferably I wanted it to ping my web server with a HTTP Post every 30 secs or so.

I found the the <a href="http://www.dsscircuits.com/forum/">DSSCircuits forum</a> that some people have edited the firmware to <a href="http://www.dsscircuits.com/forum/index.php/topic,62.0.html">send UDP packets to a server</a> to get real time updates of the GSP's location using a website called <a href="http://gps-trace.com/">GPS-Trace Orange</a>.

UDP is much smaller of a payload then the HTTP POST message that I want to use, but I can't set up a UDP server on a cheap web host. It also makes it harder for other people to use the code that I make.

I made a bunch of posts on DSSCircuits and <a href="http://electronics.stackexchange.com/">electronics.stackexchange.com</a> and was able to update the code to send HTTP post messages to my web server and automatically generate a Google map of the path of the GPS over time.

The <a href="https://github.com/funvill/GeogramONE">updated version of my source code</a> can be found in my <a href="https://github.com/funvill/">github account</a>. If you run the code as is from my github your GPS will send its coordinates to my web server and your device will show up on this map.

<a href="/public/uploads/2013/07/geogramone.png"><img class="alignnone size-full wp-image-3441" alt="geogramone" src="/public/uploads/2013/07/geogramone.png" width="924" height="604" /></a>

&nbsp;
