---
layout: single
title: Raspberry PI and the GPIO pins
date: 2013-02-03 20:35
categories: Arduino RaspberryPI
tags: Arduino cosm DataLogger Development HomeAutomation RaspberryPI
---
This week I have been playing with the <a href="http://www.raspberrypi.org/">Rapberry PI</a>, <a href="http://www.python.org/">Python</a> and the <a href="http://pypi.python.org/pypi/RPi.GPIO">Python GPIO pins library</a>.

<strong>Software</strong>

<img class="size-medium wp-image-3155 alignleft" alt="WebIDE" src="/public/uploads/2013/02/WebIDE-300x235.png" width="300" height="235" />

I started by formatting a SD Card with the <a href="http://www.raspberrypi.org/downloads">Raspbian "
wheezy"</a> (2012-12-16) image from <a href="http://www.raspberrypi.org/">Raspberry PI's website</a>. I followed this tutorial on <a href="http://learn.adafruit.com/adafruit-raspberry-pi-lesson-1-preparing-and-sd-card-for-your-raspberry-pi">how to set up the Raspberry PI</a> for the first time.

I then <a href="http://learn.adafruit.com/adafruits-raspberry-pi-lesson-6-using-ssh">enabled SSH</a> so I don't have to attache a monitor, keyboard or mouse to the Raspberry PI. Since my main box is a Windows machine I downloaded and installed <a href="http://www.putty.org/">PuTTY</a> to use as my SSH client.

Once I was connected to the RPI via SSH, <a href="http://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/">I updated the OS and all of its packages</a> to the latest versions, by running the following command.
<pre>sudo apt-get update</pre>
<em>Note:  This command may take a long time to complete depending on how out of date your system is. </em>

Next I installed the <a href="http://learn.adafruit.com/webide">Raspberry Pi WebIDE</a> from <a href="http://learn.adafruit.com/webide">adafruit.com</a>. The Web IDE allows you to create Python programs from your webbrowser directly on the Raspberry PI. The WebIDE has a few nice features like a debugger and visualizer and auto version control via <a href="https://bitbucket.org/">bitbucket</a>.

I also installed the "<a href="http://packages.python.org/distribute/easy_install.html">easy_install</a>", "<a href="http://pypi.python.org/pypi/pip">python-pip</a>" and "<a href="http://www.eeml.org/">EEML - markup language</a>" and other python packages that I wanted to use.
<pre>$ sudo easy_install -U distribute
$ sudo apt-get install python-pip
$ wget -O geekman-python-eeml.tar.gz https://github.com/geekman/python-eeml/tarball/master
$ tar zxvf geekman-python-eeml.tar.gz
$ cd geekman-python-eeml*
$ sudo python setup.py install</pre>
<strong>Hardware </strong>

<a href="/public/uploads/2013/02/2013-01-31-23.07.11.jpg"><img class="size-medium wp-image-3153 alignright" alt="Home made Raspberry PI GPIO ribbon cable" src="/public/uploads/2013/02/2013-01-31-23.07.11-225x300.jpg" width="225" height="300" /></a>The Raspberry PI has a 26pin mail connector that connects to its GPIO pins. These ribbon cables and breakout boards can be found on <a href="http://www.adafruit.com/products/862">adafruit.com</a> ($2.95) and <a href="https://www.sparkfun.com/products/11489">Sparkfun</a> ($2.95)

You can also make your own. <a href="http://www.raspberrypi.org/archives/1404">Hardware lesson with Gert: make your own ribbon cable connector</a>.

<a href="http://vancouver.hackspace.ca/wp/">Vancouver Hackspace</a> (VHS) just happen to have a bunch of the 26 pin press connector and I was able to make a few cables.

<strong> Source code </strong>

Since I am using <a href="https://bitbucket.org/">bitbucket</a> <a href="https://github.com/funvill/RaspberryPIExamples/tree/master/examples">all my source code is public</a>. I created a few learning scripts to understand how the GPIO pins work on the Raspberry PI. The first script I made was a simple <a href="https://bitbucket.org/funvill/my-pi-projects/src/d0ebc27c2dd1/examples/Blinky.py?at=master">blinking LED</a>, just like the <a href="https://gist.github.com/anonymous/4728721">arduino blinking LED script</a>. Next was to read the <a href="https://bitbucket.org/funvill/my-pi-projects/src/d0ebc27c2dd1/examples/DigitalRead.py?at=master">current state of a switch</a> and print the results to the screen.

This image was tremendously helpful in figuring out what pins go where<em id="__mceDel"><a href="/public/uploads/2013/02/Raspberry-Pi-GPIO-Layout-Revision-1-e1347664808358.png"><img class="alignnone size-medium wp-image-3157" alt="Raspberry-Pi-GPIO-Layout-Revision-1-e1347664808358" src="/public/uploads/2013/02/Raspberry-Pi-GPIO-Layout-Revision-1-e1347664808358-300x141.png" width="300" height="141" /></a></em>

Next I followed <a href="http://learn.adafruit.com/send-raspberry-pi-data-to-cosm/overview">Send Raspberry Pi Data to COSM</a> from <a href="http://learn.adafruit.com">adafruit.com</a>. I <a href="https://bitbucket.org/funvill/my-pi-projects/src/d0ebc27c2dd1/examples/cosm.py?at=master">changed the tutorial</a>  to read a digital pin (as the Raspberry PI does not have any analog pins) that I connected to a <a href="https://cosm.com/feeds/102208">magnetic read switch for my front door</a>.

<a href="/public/uploads/2013/02/0.png"><img class="alignnone size-medium wp-image-3159" alt="0" src="/public/uploads/2013/02/0-300x102.png" width="300" height="102" /></a>

&nbsp;

The GPIO pins on the Raspberry PI are pretty easy to use with the python libary. Its too bad there are no analog pins. I can add <a href="http://en.wikipedia.org/wiki/Analog-to-digital_converter">AtoD converters</a> or interface the <a href="http://www.raspberrypi.org/archives/1171">Raspberry PI with an Arduino</a> to add some analog pins.

More to come.
