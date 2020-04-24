---
layout: single
title: Raspberry PI controlling an Arduino via the pyfirmata protocol 
date: 2013-02-10 21:30
categories: Development  RaspberryPI Tips
---
The <a href="http://reviews.cnet.co.uk/desktops/25-fun-things-to-do-with-a-raspberry-pi-50009851/">Raspberry PI is good for a lot of things</a> from <a href="http://www.engadget.com/2012/09/13/supercomputer-built-from-raspberry-pi-and-lego/">computer clusters</a> to <a href="http://www.instructables.com/id/Raspberry-Pi-GPIO-home-automation/">home automation</a> but its missing a few things such as a <a href="http://learn.adafruit.com/adding-a-real-time-clock-to-raspberry-pi/overview">real time clock</a>, terminal/barrel power connector, or  Analog pins.  The Arduino has analog pins that can be read by the USB virtual serial port from the Raspberry PI.

<img class="alignright size-medium wp-image-3168" alt="2013-02-10 21.31.34" src="/public/uploads/2013/02/2013-02-10-21.31.34-300x225.jpg" width="300" height="225" />

In <a href="http://ex.ploit.ws/themagpi/The_MagPi_issue_7.pdf">MagPI issue 7</a>, has a great article on using the firmata protocol to communicate between   Arduino and the Raspberry PI.

<strong>Requirements</strong>
<ul>
	<li>A <a href="http://www.raspberrypi.org/">raspberry PI</a></li>
	<li>A <a href="http://www.arduino.cc/">Arduino</a></li>
	<li><a href="https://www.sparkfun.com/products/512">USB Cable A to B</a></li>
	<li><a href="https://github.com/tino/pyFirmata">pyFirmata</a> python library (<a href="https://readthedocs.org/projects/pyfirmata/">documentation</a>)</li>
</ul>
<strong>Install and setup </strong>
<ol>
	<li><a href="http://learn.adafruit.com/adafruits-raspberry-pi-lesson-6-using-ssh">Enable SSH on the Raspberry PI</a></li>
	<li>Install <a href="http://learn.adafruit.com/webide/overview">Adafruit Learning System Raspberry Pi WebIDE</a></li>
	<li>Get the required packages:
<pre>sudo apt-get install python-serial mercurial</pre>
</li>
	<li>Install pyFirmata
<pre>sudo apt-get install python-serial mercurial
hg clone https://bitbucket.org/tino/pyfirmata
cd pyfirmata
sudo python setup.py install
cd .. ; sudo rm -r pyfirmata</pre>
</li>
</ol>
<strong>Source code </strong>

<a href="https://gist.github.com/anonymous/4752636">Read analog pin 1</a>
<pre>import pyfirmata

# Create a new board, specifying serial port
board = pyfirmata.Arduino('/dev/ttyACM0')

# start an iterator thread so that serial buffer doesn't overflow
it = pyfirmata.util.Iterator(board)
it.start()

# set up pins
pin0=board.get_pin('a:0:i')             # A0 Input      (LM35)
pin3=board.get_pin('d:3:p')             # D3 PWM Output (LED)

# IMPORTANT! discard first reads until A0 gets something valid
while pin0.read() is None:
    pass

while True : 
  print "PWM: " + str( pin0.read() ) 
	board.pass_time(1)                  # pause 1 second

board.exit()<span style="font-size: 16px;"> </span></pre>
