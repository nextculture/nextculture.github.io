---
layout: single
title: The Giant Claw Game! - The Controls System 
date: 2013-05-14 00:01
categories: Projects
tags: circuit current drill drills gear gears hbridge motors Projects pulley relay
---
Only two weeks left to get the Claw up and running ready for <a href="http://vancouver.makerfaire.ca/breaker-faire-may-25th/">Breaker Faire</a> the <a href="http://vancouver.makerfaire.ca/">Maker Faire</a> fund raiser party. I am starting to get worried that I might not get it done in time.

I have been having lots of problems this week with getting the motors working with the gantry system.
<ul>
	<li>The motors are from different vendors and move at different rates.</li>
	<li>The motors draw too much current for the motor shield to handle.</li>
	<li>The motors are hard to mount on the cube.</li>
	<li>The pulley for motors slips and I am unable to get them to move the cables.</li>
</ul>
<a href="/public/uploads/2013/05/2013-05-05-17.32.27.jpg"><img class="size-thumbnail wp-image-3288 alignright" alt="3 drill motors" src="/public/uploads/2013/05/2013-05-05-17.32.27-150x150.jpg" width="150" height="150" /></a>The motors come from old power drills that I picked up at a local flea market (<a href="http://www.welcometoeastvan.com/2011/09/binners-market-dtes/">Binners market</a>). You can pick up some pretty amazing things at this market when you look hard enough. I purchased 5 battery powered drills for $5 each, 4 of them worked.  The picture shows three of the motors taken apart with the supply voltage taped to the motors. Drill are great for finding cheap motors with a gear box and a chuck. A retail motor with a gear box would probably cost me in the range of ~$30 each. The problem with getting second hand motors is that I couldn't get all of the same type of motor. Luckily, of the four working drills two of them have relativity similar gear ratios and power requirements. Even still the minor differences between these two motors will probably cause me problems after a few hours. I think I can resolve the difference by providing different voltage to each of the motors, its not ideal but it should work.

<a href="/public/uploads/2013/05/l298.png"><img class="size-thumbnail wp-image-3291 alignleft" alt="l298" src="/public/uploads/2013/05/l298-150x150.png" width="150" height="150" /></a>I purchased two<a href="http://www.seeedstudio.com/depot/l298-dual-hbridge-motor-driver-p-284.html"> L298 Dual H-Bridge Motor Driver</a> from <a href="http://www.leeselectronic.com/">leeselectronic.com</a>. They work great and are easy to interface with, but they have a 2 amp max current limit. After experimenting with the motors I have I found that they require 1.5 Amp to starting current and probably need around 6 Amps to move the gantry around properly. Way too much current for these motor shields.

<a href="https://www.circuitlab.com/circuit/4p5cgq/big-claw-game/#menu_file_link_and_share"><img class="size-medium wp-image-3289 alignright" style="line-height: 18px;" alt="Motor controller" src="/public/uploads/2013/05/big-claw-game-300x226.png" width="300" height="226" /></a>

After doing some more research and <a href="http://electronics.stackexchange.com/questions/68706/circuit-version-of-a-simple-if-else-program">asking a few questions online</a> I decided to build a <a href="http://nvhs.wordpress.com/project/catspberry/motor-controller/">relay version</a> of a <a href="http://www.instructables.com/id/How-to-make-an-H-bridge/?ALLSTEPS">H Bridge</a> instead. The advantage of using a <a href="http://en.wikipedia.org/wiki/Relay">relay</a> is that it can take a lot more current +10 Amps but its switching frequency is much lower (~40 hz) and it costs quite a bit more ($5-10 per relay).

I designed this circuit in <a href="https://www.circuitlab.com/">circuit lab</a> (online social circuit building tool). I am planning on picking up the parts and building it tomorrow. Hopefully this will resolve the motor current problem I was having.

<a href="/public/uploads/2013/05/2013-05-12-13.59.36.jpg"><img class="size-thumbnail wp-image-3292 alignleft" alt="motor mount " src="/public/uploads/2013/05/2013-05-12-13.59.36-150x150.jpg" width="150" height="150" /></a>The next problem was how to mount the motors on to the cube. I wanted to use a hole saw and cut a circle in to a 2x4 and then attach the 2x4 to the cube. But I didn't have a hole saw so I ended up using a jig saw and a drill. The results worked but didn't look pretty. I might end up redoing this work if I can find a friend with a hole saw.

I also have to figure out a way of making pulleys for the motors that can pull the cabling and move the XY table. Normally I would have used a <a href="http://en.wikipedia.org/wiki/Toothed_belt">timing belt</a> instead of cables. The rubber teeth inside the belt would have added the grip on the pulleys that I needed. But timing belts are really expensive. The two belts that I would have needed for this project would have easily cost me more then the entire project has so far. Still trying to figure this one out.

Still lots to do but things are coming along.
