---
layout: single
title: Introduction to Home automation with the Raspberry Pi - Sunday November 24th 2013
date: 2013-11-07 23:22
categories: Projects  RaspberryPI
---
<strong>Who:</strong>
VHS members only, become a member and join us!
<a href="http://vancouver.hackspace.ca/wp/membership">http://vancouver.hackspace.ca/wp/membership</a>

Bottomed lined: <a href="http://abluestar.com/">Steven Smethurst</a>

RVSP on <a href="https://plus.google.com/u/0/events/cjjqunp7nflsoqtuafkuhre2dms">Google+</a>, <a href="https://www.facebook.com/events/420902668011729/">Facebook</a>

<strong>Cost:</strong>
Free for VHS members

<img class="alignright size-medium wp-image-2614" title="raspberry_pi_logo1" alt="" src="http://vancouver.hackspace.ca/wp/wp-content/uploads/2013/11/raspberry_pi_logo1-246x300.png" width="246" height="300" />

<strong>Where:</strong>
VHS 270 East 1st (The Bunker)

<strong>When:</strong>
Sunday November 24th 2013 1 pm till 5pm or when ever we are done.

<strong>What:</strong>
In this workshop we will be using a Raspberry PI to read sensors (inputs), store their vales in a database for historical trending and turn relays (outputs) on and off when a sensor value goes outside of a certain range. There will be a small amount of very basic python programming in this workshop. Example code will be provided and even if you have never programmed before you should be able to get the basic example running.

In this workshop you will be building a system that will turn on a light if the door is open or motion is detected in an area. We will be recording the current temperature to a database and if the temperature goes outside of a range a fan will be turned on to reduce the temperature.

Before this workshop you should have your Raspberry PI loaded with an OS and have the latest version of <a href="/getting-started-with-your-raspberry-pi/">Adafruite WebIDE running</a>. It will also help considerably if you record your Raspberry PI MAC address and HostName on a scrap of paper before the workshop.

<span style="text-decoration: underline;"><strong><a href="http://vancouver.hackspace.ca/wp/wp-content/uploads/2013/11/2013-11-02-17.20.48.jpg"><img class="alignright size-medium wp-image-2613" title="2013-11-02 17.20.48" alt="" src="http://vancouver.hackspace.ca/wp/wp-content/uploads/2013/11/2013-11-02-17.20.48-300x225.jpg" width="300" height="225" /></a>Hardware is NOT provided by VHS!!!</strong></span>
<strong>All the hardware</strong> can be purchased locally at <a href="http://www.leeselectronic.com">Lee's Electronics</a>  (4522 Main Street). Tell them your a VHS member to receive a small discount. Or you can order all the hardware from adafruit.com they also have many other interesting components. Note there are Raspberry PIs available in the VHS vending machine at the space. If you buy your components from DealExtream expect them to take 6 weeks to be delivered. If you are unable to source all the components join us anyways VHS can lend you some parts for the workshop.

<strong>Parts list</strong>
<ul>
	<li><a href="http://www.raspberrypi.org/">Raspberry PI</a>
<ul>
	<li>$50 in the vending machine at VHS (Thanks Dan)</li>
	<li><a href="https://www.adafruit.com/products/998">$40 from Adafruit</a></li>
</ul>
</li>
	<li>Pi Cobbler Breakout + Cable for Raspberry Pi
<ul>
	<li><a href="https://www.adafruit.com/products/914">$8 from Adafruit</a></li>
</ul>
</li>
	<li>Sensors (inputs)
<ul>
	<li>One Wire Digital Temperature Sensor - <a href="http://www.maximintegrated.com/datasheet/index.mvp/id/2812">DS18B20</a>
<ul>
	<li><a href="http://dx.com/p/1-wire-temperature-and-humidity-sensor-142cm-143515">$2.50 at Deal Extream</a></li>
	<li><a href="http://www.adafruit.com/products/381">$10 from AdaFruit</a></li>
</ul>
</li>
	<li>Simple on and off switch (any switch will do)</li>
	<li>Magnetic door switch (Provided by VHS for a donation)
<ul>
	<li><a href="http://www.adafruit.com/products/375">$4 from Adafruit</a></li>
</ul>
</li>
	<li>PIR (motion) sensor
<ul>
	<li><a href="http://www.adafruit.com/products/189">$10 from AdaFruit</a></li>
</ul>
</li>
</ul>
</li>
	<li><a href="http://vancouver.hackspace.ca/wp/wp-content/uploads/2013/11/2013-11-02-14.10.56.jpg"><img class="alignright size-thumbnail wp-image-2616" title="2013-11-02 14.10.56" alt="" src="http://vancouver.hackspace.ca/wp/wp-content/uploads/2013/11/2013-11-02-14.10.56-150x150.jpg" width="150" height="150" /></a>Outputs
<ul>
	<li>Replay breakout board (5V input)
<ul>
	<li><a href="http://dx.com/p/4-ch-12v-power-relay-module-red-blue-173827">$7.20 from Deal Extream</a></li>
	<li><a href=" http://www.adafruit.com/products/268">$26 from AdaFruit</a> <strong>(highly suggested) </strong></li>
</ul>
</li>
	<li>Standard wall outlet
<ul>
	<li><a href="http://www.homedepot.com/p/Leviton-15-Amp-Duplex-Outlet-White-R52-05320-00W/202066670?N=c33a%3FNs%3DP_REP_PRC_MODE%257C0#.UnWNjvnbNMQ">$1 from Homedepot</a></li>
</ul>
</li>
</ul>
</li>
</ul>
If you would like to get started early we will be following these tutorials provided by Adafruit in this workshop
<ul>
	<li><a href="http://learn.adafruit.com/webide/installation">WebIDE</a></li>
	<li><a href="http://learn.adafruit.com/adafruits-raspberry-pi-lesson-11-ds18b20-temperature-sensing">DS18B20 tempture sensor</a></li>
	<li><a href="http://learn.adafruit.com/adafruits-raspberry-pi-lesson-12-sensing-movement">PID motion sensor and magnetic door switch</a></li>
	<li><a href="http://learn.adafruit.com/dht-humidity-sensing-on-raspberry-pi-with-gdocs-logging/connecting-to-google-docs">Using Google docs as a database for sensor data</a></li>
	<li><a href="http://learn.adafruit.com/send-raspberry-pi-data-to-cosm/necessary-packages">Using Cosm as a database for sensor data</a>, <a href="https://github.com/petervizi/python-eeml">better version of the EEML libary</a>, <a href="http://lxml.de/installation.html">installing lxml</a></li>
	<li><a href="http://learn.adafruit.com/adafruits-raspberry-pi-lesson-13-power-control">Relays</a></li>
</ul>
