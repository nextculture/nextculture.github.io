---
layout: single
title: Using a Raspberry PI with a webcam to make time lapse videos. 
date: 2013-04-13 14:38
categories: Projects RaspberryPI
---
<a href="/public/uploads/2013/04/64807.jpg"><img class="size-thumbnail wp-image-3236 alignright" alt="64807" src="/public/uploads/2013/04/64807-150x150.jpg" width="150" height="150" /></a>I have made a bunch of time lapse videos in the past with my Cannon S90 using the <a href="http://chdk.wikia.com/wiki/CHDK">CHDK</a> hacked firmware. These videos turn out great and I have very happy with the results. The problem is that I have to leave my expensive camera unattended for hours or days at a time and I am unable to use the camera while it is in use.

A few weeks ago I found a few cheap HD webcams (<a href="http://ncix.com/products/?sku=64807&amp;promoid=1371">HP HD-3110 Autofocus 720p 30FPS Widescreen Webcam</a>) on <a href="http://ncix.com/">NCIX</a>. These Webcams work with the <a href="http://www.raspberrypi.org">Raspberry PI</a> and consumes a less power then other webcams I have tested in the past.

I wrote up a little bash script that uses <a href="http://www.sanslogic.co.uk/fswebcam/">fswebcam</a> to take a picture once every 10 secs and store it on the local disk (SD Card).

<strong>Instructions </strong>
<ol>
	<li>Connect to your Raspberry PI via SSH terminal</li>
	<li>Update your Raspberry PI
<code>sudo apt-get update </code></li>
	<li>Install <a href="http://www.sanslogic.co.uk/fswebcam/">fswebcam</a>
<code>sudo apt-get install fswebcam</code></li>
	<li>Test fswebcam. This should take an image from the webcam and store it in your local directory.
<code>fswebcam -d /dev/video0 -l 10 test-fswebcam.jpeg</code></li>
	<li>Write a script for fswebcam and automate
<ol>
	<li>Open up a terminal text editor such as <em>nano</em>
<code>sudo nano timelapse.sh</code></li>
	<li>In the nano editor type the follow script
<code>#!/bin/bash
fswebcam -d /dev/video0 -l 10 test-%Y-%m-%d--%H-%M-%S.jpeg</code></li>
	<li>Use [ctrl]+[x] to save and close this file.</li>
</ol>
</li>
	<li>Change the scripts permissions to allow for execution
<code>chmod +x timelapse.sh</code></li>
	<li>Run the script
<code>./timelapse.sh</code></li>
</ol>
