---
layout: single
title: Reporting the system stats of a Raspberry PI to COSM with python 
date: 2013-03-27 00:05
categories: RaspberryPI
---
<a href="https://cosm.com/">COSM</a> is a online data store of sensor data for the <a href="http://en.wikipedia.org/wiki/Internet_of_Things">internet of things</a>. You can use Cosm to store sensor data (light, temp, heat, etc...) from your internet enabled device (<a href="http://www.arduino.cc/">Arduino</a>, <a href="http://www.raspberrypi.org/">Raspberry PI</a>, etc) online and produce pretty graphs of the values as they change. Recently <a href="http://www.chipkin.com/">Chipkin Automation Systems</a> (The company I work for) <a href="http://www.chipkin.com/bacnet-ipmstp-to-cosm-data-logger/">added COSM as one of the supported drivers</a> on their <a href="http://www.chipkin.com/products/cas-gateways/">CAS Gateway device</a>.

This got me to thinking of how I could track system stats from my <a href="http://www.raspberrypi.org/">Raspberry PI</a> with <a href="http://www.python.org/">python</a> and record the stats on COSM.

I have written about sending data to COSM with a Raspberry PI before in my <a href="/raspberry-pi-and-the-gpio-pins/">Raspberry PI and the GPIO pins</a> post.  Adafruit also has a great tutorial on this as well <a href="http://learn.adafruit.com/send-raspberry-pi-data-to-cosm/overview">Send Raspberry Pi Data to COSM</a>.

This code snippet will <a href="https://gist.github.com/funvill/5252169">get the system stats (CPU, Ram, Disk Space) from the Raspberry PI</a>, We can then send these values to COSM. I then added in the eeml class to talk to the COSM servers. I also added reading a light sensor that is connected to an Arduino talking pyfirmata.

<a href="https://github.com/funvill/RaspberryPIExamples/blob/master/examples/datalogger.py">Full source code can be found on my github account.</a>

<a href="https://cosm.com/v2/feeds/120539/"><img class="aligncenter" alt="Light graph" src="https://api.cosm.com/v2/feeds/120539/datastreams/RoomTemperature.png?width=730&amp;height=250&amp;colour=%23f15a24&amp;duration=1week&amp;title=Temperature%20in%20Chipkin's%20Office&amp;show_axis_labels=true&amp;detailed_grid=true&amp;scale=auto" width="500" height="250" /></a>

&nbsp;

&nbsp;

&nbsp;
