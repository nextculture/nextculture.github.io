---
layout: single
title: Raspberry PI as a FM transmitter 
date: 2013-03-26 20:28
categories: RaspberryPI
tags: c fm RaspberryPI RaspberryPI transmitter
---
<img class="alignright size-medium wp-image-3216" alt="pi_fm_gpio" src="/public/uploads/2013/03/pi_fm_gpio-300x225.jpg" width="300" height="225" />

A few weeks ago I found this tutorial on make magazine <a href="http://www.icrobotics.co.uk/wiki/index.php/Turning_the_Raspberry_Pi_Into_an_FM_Transmitter">Turning the Raspberry Pi Into an FM Transmitter</a> by <a href="http://blog.codeclub.org.uk/blog/brief/">Code Club pihack</a>.

It uses the hardware on the raspberry pi that is actually meant to generate spread-spectrum clock signals on the GPIO pins to output FM Radio energy. This means that all you need to do to turn the Raspberry-Pi into a (ridiculously powerful) FM Transmitter is to plug in a wire as the antenna (as little as 20cm will do) into GPIO pin 4 and run the code posted below.

<strong>Instructions </strong>
<ol>
	<li>SFTP the <em>pifm.c</em> and <em>sound.wav</em> files on to your Raspberry PI.
<ul>
	<li>You will need to enable SHH to SFTP a file on your Raspberry PI</li>
</ul>
</li>
	<li>From the SHH terminal window, compile the pifm.c for your distro of linux. By default <em>gcc</em> will produce a <em>a.out</em> file as the compiled program.
<pre>gcc -lm -std=c99 pifm.c</pre>
</li>
	<li>Run the output. You must run the application as an administrator (sudo) because this application uses direct memory management to access the GPIO pins.
<pre>sudo ./a.out sound.wav</pre>
</li>
</ol>
