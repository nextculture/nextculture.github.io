---
layout: single
title: RGB LED POV Globe - Software
date: 2011-05-16 21:07
categories: Projects
---
<a href="/public/uploads/2011/05/IMG_3300.jpg"><img class="size-thumbnail wp-image-1481 alignright" title="IMG_3300" src="/public/uploads/2011/05/IMG_3300-150x150.jpg" alt="" width="150" height="150" /></a>I been travailing a lot the past few weeks making it hard to work on the mechanics of this project and with only 50 days left till <a href="http://makerfaire.ca/">Maker Faire</a> I am running short on time. Travailing doesn't prevent me from working on the software side of things though but it make it hard to test it. I have created this testing board to use while I finish the mechanics parts.

I created a base class (<em>CFrameBase</em>) for the frame animation then inherited from it for the algorithmic generated animations (test patterns, ect...). I also created a frame buffer class that inherited from <em>CFrameBase </em>that is basically just a big memory block that you can load via the serial port.

Next I added a <a href="http://www.sparkfun.com/products/9358">blue tooth module</a> so I could load the configurations over wireless via serial. Currently the serial can't keep up with the data rate needed to do even modest frame fate. I will probably end up loading the entire animation in to memory before I start to display it. The draw back of this is that I will only be able to show 19 frames of animation at any given time.

Next I added a <a href="http://www.sparkfun.com/products/9836">Triple Axis Accelerometer</a> (ADXL345) and a <a href="http://www.sparkfun.com/products/9990">Gyro</a> (LPR530AL Dual 300), these will help determining the position of the ring as it spins around its axis. I have tested each of these parts on its own but without the mechanics I can do real world tests. I'm adding in software to manually correct for the motors speed as well just in case.

This source code is still a work in progress but functionally its working.

<a href="/public/uploads/2011/05/HBDOS_2011-05-16_220511.zip">HBDOS_[2011-05-16_220511]</a>

[nggallery id=4]

<strong>RGB LED POV Globe</strong>
<ol>
	<li><a href="/rgb-led-pov-globe-research/">RGB LED POV Globe - Research</a><strong>
</strong></li>
	<li><a href="/rgb-led-pov-globe-%E2%80%93-research-led/">RGB LED POV Globe - Research LED</a></li>
	<li><a href="/rgb-led-pov-globe-parts-shopping/">RGB LED POV Globe</a><a href="/rgb-led-pov-globe-%E2%80%93-research-led/"> - Parts shopping</a></li>
	<li><a href="http://http//www.abluestar.com/blog/rgb-led-pov-globe-%E2%80%93-research-other-peoples-projects">RGB LED POV Globe - Research other peoples projects.</a></li>
	<li><a href="/rgb-led-pov-globe-%e2%80%93-software/">RGB LED POV Globe - Software</a></li>
</ol>
&nbsp;

&nbsp;
