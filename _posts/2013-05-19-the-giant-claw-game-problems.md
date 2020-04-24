---
layout: single
title: The Giant Claw Game! - Problems 
date: 2013-05-19 21:41
categories: Projects
---
The Giant claw game can be broken down in to a few parts. The Claw, The Joystick, The Gantry/Cube, The XY table, The Cart, Control system

<strong>The Claw </strong>

<img class="size-thumbnail wp-image-3314 alignright" style="font-size: 12px; line-height: 18px;" alt="2013-05-18 15.06.03" src="/public/uploads/2013/05/2013-05-18-15.06.03-150x150.jpg" width="150" height="150" />The claw is working and it is in pretty good shape. The claw can open and closes and pick up toys. It uses a small gear motor attached to the top. The gear motor is kind of slow and takes about 20+ seconds to fully close. I am thinking about replacing this motor with one of the drills to speed it up.

I have attached limit switches to the claw so I can tell when it is fully opened and closed. This prevents the claw from crushing the stuff animals.

Bill of materials
<ul>
	<li>2 Cherry limit switches,</li>
	<li>Terminal strip</li>
	<li>Small geared motor</li>
	<li>Motor shaft coupler</li>
	<li>Wood</li>
</ul>
<a href="/public/uploads/2013/05/2013-05-14-21.14.00.jpg"><img class="alignnone size-thumbnail wp-image-3310" alt="Claw limit switches" src="/public/uploads/2013/05/2013-05-14-21.14.00-150x150.jpg" width="150" height="150" /></a>  <a href="/public/uploads/2013/05/2013-05-18-15.05.50.jpg"><img class="alignnone size-thumbnail wp-image-3315" alt="2013-05-18 15.05.50" src="/public/uploads/2013/05/2013-05-18-15.05.50-150x150.jpg" width="150" height="150" /></a> <a href="/public/uploads/2013/05/2013-05-18-15.05.57.jpg"><img class="alignnone size-thumbnail wp-image-3316" alt="2013-05-18 15.05.57" src="/public/uploads/2013/05/2013-05-18-15.05.57-150x150.jpg" width="150" height="150" /></a>

<strong>The Joystick </strong>

<img class="size-thumbnail wp-image-3313 alignright" style="font-size: 12px; line-height: 18px;" alt="2013-05-18 15.15.19" src="/public/uploads/2013/05/2013-05-18-15.15.19-150x150.jpg" width="150" height="150" />The joystick is the simplest part of this system. It has 4 limit switches and a off the shelf  joystick that I picked up from John Jukes. All the wires lead back to a RS45 connector to make setup easier. I wanted to make this part strong in case the kids drop it and kick it around. The only thing left to do here is glue the box together.

Bill of materials
<ul>
	<li><span style="line-height: 16px;">Wood</span></li>
	<li>Arcade button</li>
	<li>5 Cherry limit switches,</li>
	<li>1 RS45 connector</li>
</ul>
<a href="/public/uploads/2013/05/2013-05-18-15.15.37.jpg"><img class="alignnone size-thumbnail wp-image-3311" alt="Joy stick" src="/public/uploads/2013/05/2013-05-18-15.15.37-150x150.jpg" width="150" height="150" /></a> <a href="/public/uploads/2013/05/2013-05-18-15.15.26.jpg"><img class="alignnone size-thumbnail wp-image-3312" alt="Joy stick wiring" src="/public/uploads/2013/05/2013-05-18-15.15.26-150x150.jpg" width="150" height="150" /></a>

<strong>The Gantry/Cube</strong>

The cube is pretty much a large wooden box made out of 2x3x8. I added trusses to the corners to make it more stable. I added the shelf to the top of the cube to allow the gantry system to ride on top of.

<a href="/public/uploads/2013/05/marquee.png"><img class="size-thumbnail wp-image-3331 alignright" alt="marquee" src="/public/uploads/2013/05/marquee-150x150.png" width="150" height="150" /></a>I would like to add a marquee banner to the top of the cube to make it look better. I am also planning on adding some fabric to the bottom so all the toys will gather in the center, making it easier for the kids to pick up a prize.

There is a lot I could do her to make it look better but I am running out of time and I may not get a chance before Breaker/Maker Faire.

Bill of materials
<ul>
	<li>16 2x3x8 wood beams.</li>
	<li>50+ 3" screws</li>
	<li>4 appliance moving wheels</li>
	<li>12 pulleys</li>
	<li>45 feet of rope.</li>
</ul>
<a href="/public/uploads/2013/05/2013-05-05-20.19.25.jpg"><img class="alignnone size-thumbnail wp-image-3319" alt="2013-05-05 20.19.25" src="/public/uploads/2013/05/2013-05-05-20.19.25-150x150.jpg" width="150" height="150" /></a> <a href="/public/uploads/2013/05/2013-05-04-11.55.31.jpg"><img class="alignnone size-thumbnail wp-image-3320" alt="2013-05-04 11.55.31" src="/public/uploads/2013/05/2013-05-04-11.55.31-150x150.jpg" width="150" height="150" /></a> <a href="/public/uploads/2013/05/2013-05-12-18.46.371.jpg"><img class="alignnone size-thumbnail wp-image-3321" alt="2013-05-12 18.46.37" src="/public/uploads/2013/05/2013-05-12-18.46.371-150x150.jpg" width="150" height="150" /></a>

<strong>The XY table</strong>

<a href="/public/uploads/2013/05/reference.png"><img class="size-thumbnail wp-image-3271 alignright" alt="CoreXY" src="/public/uploads/2013/05/reference-150x150.png" width="150" height="150" /></a>The XY table moves the claw around the cube. I decided to use the <a href="http://corexy.com/">CoreXY</a> (Cartesian Motion Platform) to do the actual movement. It works but there are many problems with it that I have not resolved yet.

<img class="size-thumbnail wp-image-3332 alignleft" style="font-size: 12px; line-height: 18px;" alt="2013-05-19 19.56.56" src="/public/uploads/2013/05/2013-05-19-19.56.56-150x150.jpg" width="150" height="150" />The biggest problems I am currently having is that the cables that I am using are slipping in the motor's pulleys. I tried using some sandpaper to rough up the pulleys to add more grip but they keep slipping.

<img class="size-thumbnail wp-image-3335 alignright" style="line-height: 18px;" alt="2013-05-19 20.06.54" src="/public/uploads/2013/05/2013-05-19-20.06.54-150x150.jpg" width="150" height="150" />

I thought about adding a <a href="http://www.wisegeek.org/what-is-an-idler-pulley.htm">idler pulley</a> but I wanted to keep everything as simple as possible and I decided to add <a href="https://en.wikipedia.org/wiki/Spring_(device)">expansion springs</a> to the cables to keep the tension on the motor pulleys. Its still slipping.

The problem also could be with the cables I am using. If the cables are too slick they will slide around in the pulleys, if the cable has too much give they will stretch under constant use. I had some <a href="http://en.wikipedia.org/wiki/Parachute_cord">parachute cord</a> (paracord) around my house and decided to use it and this might be adding to my slipping.

Another idea is to wrap the cable around the pulley twice (540 degrees). This would ensure that there is tension on the pulley but the cable might get knotted up.

I have not resolved this problem yet and I am looking for a solution.

<a href="/public/uploads/2013/05/2013-05-19-19.57.03.jpg"><img class="alignnone size-thumbnail wp-image-3333" alt="2013-05-19 19.57.03" src="/public/uploads/2013/05/2013-05-19-19.57.03-150x150.jpg" width="150" height="150" /></a> <a href="/public/uploads/2013/05/2013-05-19-19.56.26.jpg"><img class="alignnone size-thumbnail wp-image-3334" alt="2013-05-19 19.56.26" src="/public/uploads/2013/05/2013-05-19-19.56.26-150x150.jpg" width="150" height="150" /></a> <a href="/public/uploads/2013/05/220px-Paracord-Commercial-Type-III-Coil.jpg"><img class="alignnone size-thumbnail wp-image-3336" alt="220px-Paracord-Commercial-Type-III-Coil" src="/public/uploads/2013/05/220px-Paracord-Commercial-Type-III-Coil-150x150.jpg" width="150" height="150" /></a>

<strong>The Cart</strong>

I have not started this yet.

<a href="/public/uploads/2013/05/cart.png"><img class="size-medium wp-image-3340 alignright" alt="cart" src="/public/uploads/2013/05/cart-250x300.png" width="250" height="300" /></a>The cart will ride along the center column being pulled across by the cables. The card will have its own pulley on it that will be used to raise and lower the claw. Here is a crude drawing of what I was thinking about doing.

There will be one large pulley that will rise and lower the main claw. this pulley will be at the bottom attached at the center to a dowel that is free rotating in the walls of the cart... kind of hard to explain.

<strong>Control system</strong>

I am using a <a href="/the-giant-claw-game-relay-h-bridge-and-circuit-design/">relay H Bridge</a> to control the motors. Each motor needs two relays and two pins on the Arduino. There are a total of 4 motors in this system (8 pins). One each for each of the axis X, Y, Z and one more to open and close the claw.

I also used a lot of <a href="http://en.wikipedia.org/wiki/Limit_switch">limit switches</a> to tell when the claw is in a certain state.
<ul>
	<li>4x for each axis on the gantry,</li>
	<li>4x for each directions in the joystick,</li>
	<li>1x for the fire button on the joystick,</li>
	<li>2x for the min and max of the claw's teeth,</li>
	<li>1x for the pulley to know when the call is fully retracted in to the cart.</li>
</ul>
A total of 20 pins. An standard Arduino has 20 pins, just enough to control the claw. I am trying to make all the connections with RJ45 connectors for an easier set up.

The programming for the Ardunio is nice and easy and pretty much done already.

<a href="/public/uploads/2013/05/2013-05-19-20.35.43.jpg"><img class="alignnone size-thumbnail wp-image-3342" alt="8 relays " src="/public/uploads/2013/05/2013-05-19-20.35.43-150x150.jpg" width="150" height="150" /></a> <a href="/public/uploads/2013/05/2013-05-19-20.37.09.jpg"><img class="alignnone size-thumbnail wp-image-3343" alt="cherry switch " src="/public/uploads/2013/05/2013-05-19-20.37.09-150x150.jpg" width="150" height="150" /></a> <a href="/public/uploads/2013/05/2013-05-19-22.32.56.jpg"><img class="alignnone size-thumbnail wp-image-3344" alt="2013-05-19 22.32.56" src="/public/uploads/2013/05/2013-05-19-22.32.56-150x150.jpg" width="150" height="150" /></a>

&nbsp;

Still lots to do and not much time to do it.
