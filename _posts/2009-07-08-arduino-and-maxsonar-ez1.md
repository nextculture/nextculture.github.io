---
layout: single
title: ARDUINO and MaxSonar EZ1
date: 2009-07-08 10:51
categories: Arduino Development
tags: Arduino Development MaxSonarEZ0 MaxSonarEZ1 robots sensor source
---
<strong>Update: 13 July 2009, Resolved with the help of <em>Bob Gross. User error</em> see notes below.</strong>

<hr />I found a <a href="http://www.maxbotix.com/">MAX Sonar EZ1</a> sensor at my local electronics store and decided to try it out. The selling features of this sensor for me was
<ul>
	<li>Cheap (&lt; $20), and immediately available, (impulse buy)</li>
	<li>Analog and serial pins, with documentation, oh how I love documentation on electronic parts.</li>
	<li>Operated on 5v, the arduino has a 5V Pin making it as easy as can be to hook it up to the board.</li>
	<li>Mounting holes.</li>
</ul>
I mounted the sensor on an €˜L&quot; bracket and pointed it at a wall about 36 inches away. I connected the GRD, 5V, Analog pin to my Arduino chip and started reading data. After playing around with it for a while, I found it hard to get reliable data from this sensor.

Took in 100 readings getting results anywhere from 50-255, unreliable data. I searched Google and found a few other people using this sensor with the Arduino. <a href="http://www.arduino.cc/cgi-bin/yabb2/YaBB.pl?num=1226321702">http://www.arduino.cc/cgi-bin/yabb2/YaBB.pl?num=1226321702</a>

Apparently these  range finders (less then $100) are notorious for giving spiked reading every once in a while. So all data read from these sensors should be averaged over ~10 or more readings for better accuracy. <span style="text-decoration: line-through;">Also grounding the unused pins can sometimes help.</span>

So I grounded all my unused analog pin (<em>this is where I made my miss take, see below</em>) and changed my code to find the average over 100 readings as the result. Then tested the results for 10k times and found the results to be wildly different between each session.

After a few more hours of playing around with it I gave up. I considered connected to the serial pins but decide it was more work then it was worth. It could be that this particular sensor was damaged <span style="text-decoration: line-through;">or it could be the brand</span>, either way it didn&quot;t work out for me.

I have included my source code for your reference.

<a href="http://www.abluestar.com/dev/arduino/snippets/read_MaxSonarEZ1.c" target="_blank">dev/arduino/snippets/read_MaxSonarEZ1.c</a>

<hr />
<strong>Update (12 July 2009):</strong>
After getting contacted by <em>Bob Gross</em> of <em><a href="http://www.maxbotix.com/">MaxBotix Inc</a>. </em>I decided to give this sensor anther chance.
Using the code above I connected  analog pin 1 (NOT Pin 0) to the "AN" ping on the chip. GND to GND, +5 to 5V. <a style="text-decoration: none;" href="http://www.abluestar.com/dev/arduino/snippets/IMG_8504.JPG">Picture</a>
Uploaded the code and connected Hyper terminal capturing the output to a text file and let it run for about an ~hour poiting at the roof.
The results where variable as shown in <a href="http://www.abluestar.com/dev/arduino/snippets/ouput.txt">the output</a>.

<strong>Update (13 July 2009)</strong>

User error. Boy do I feel like an idiot today. When I grounded the analog pins (as noted above) I also connected the pin that I was using for the sensor to all the other analog pins.

I removed the grounding wire, and the connection between all the pins and got reliable results. The sensor works fine this was entirely human error. I decided to keep using the averaging code above with ~10 reads instead of 100 for speed.

My aploagies to Bob Gross and <a href="http://www.maxbotix.com/">MaxBotix Inc</a> for my error and false claims that the sensor didn't work.
Thank you for your help.
