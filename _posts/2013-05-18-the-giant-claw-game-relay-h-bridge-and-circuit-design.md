---
layout: single
title: The Giant Claw Game! - Relay H-Bridge and Circuit Design
date: 2013-05-18 13:33
categories: Projects
---
Over the week I worked on the Relay H Bridge,  software and circuit diagrams for this project. Only 1 more week till it needs to be done.

<strong>Relay H Bridge </strong>

After finding out that my <a href="/the-giant-claw-game-the-controls-system/">L298 H Bridge</a> was not powerful enough to operate my gantry motors last week, I switched over to use a Relay H Bridge. The advantages of using a relay instead of the L298 is that the relay can take a lot more current but the switching frequency is much slower (~40 hz)
<table>
<tbody>
<tr>
<th>IN1 (IN3)</th>
<th>IN2 (IN4)</th>
<th>DIRECTION</th>
</tr>
<tr>
<td>1</td>
<td>0</td>
<td>Forward</td>
</tr>
<tr>
<td>0</td>
<td>1</td>
<td>Reverse</td>
</tr>
<tr>
<td>1</td>
<td>1</td>
<td>Motor stop</td>
</tr>
<tr>
<td>0</td>
<td>0</td>
<td>Motor stop</td>
</tr>
</tbody>
</table>
<a href="/public/uploads/2013/05/arduino-a-4-canali-5v-relay-modulo-di-scheda-di-espansione_kmunaz13430945734694.jpg"><img class="alignnone size-full wp-image-3302" alt="Relay H Bridge" src="/public/uploads/2013/05/arduino-a-4-canali-5v-relay-modulo-di-scheda-di-espansione_kmunaz13430945734694.jpg" width="587" height="785" /></a>

Image source: <a href="http://nvhs.wordpress.com/project/catspberry/motor-controller/">http://nvhs.wordpress.com/project/catspberry/motor-controller/</a>

<strong>Circuit Design</strong>

I don't have much experience with circuit design but I think this makes sense. I built it with <a href="https://www.circuitlab.com">circuitlab.com</a> and online circuit designer.

<strong> <a href="/public/uploads/2013/05/big-claw-game1.png"><img class="alignnone size-medium wp-image-3303" alt="big-claw-game circuit " src="/public/uploads/2013/05/big-claw-game1-300x282.png" width="300" height="282" /></a></strong>

&nbsp;

<strong>Arduino Software </strong>

The code for the <a href="http://www.arduino.cc/">Arduino</a> is pretty strait forward. Move the claw around until the fire button is pressed, then drop the claw and pick up a toy and bring it back to the start location. The source code for the <a href="https://github.com/funvill/TheGiantClawGame/blob/master/ClawGame/ClawGame.ino">The Giant Claw Game</a> can be found on my <a href="https://github.com/funvill/">GitHub account</a>.

<em id="__mceDel"> </em>

&nbsp;

&nbsp;

&nbsp;
