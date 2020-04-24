---
layout: single
title: RGB LED POV Globe - Research 
date: 2011-03-19 16:31
categories: projects
Tags: Arduino burningman Development electronics hardware Interesting LED makerfaire POV project research VHS
---
I have decided to create a 64x <a href="http://en.wikipedia.org/wiki/RGB_color_model">RGB</a> <a href="http://en.wikipedia.org/wiki/LED">LED</a> <a href="http://en.wikipedia.org/wiki/Persistence_of_vision">POV</a> Globe for <a href="http://vancouver.makerfaire.ca/">Maker faire</a> and <a href="http://www.burningman.com/">Buring man</a> this year. This project is a factor more complex then any other project that I have attempted before, and quite a bit more expensive.

My project will be similar to this project
<object classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000" width="425" height="350" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,40,0"><param name="src" value="http://www.youtube.com/v/4KN0xoHsUiI" /><embed type="application/x-shockwave-flash" width="425" height="350" src="http://www.youtube.com/v/4KN0xoHsUiI"></embed></object>
<a href="http://www.youtube.com/watch?v=4KN0xoHsUiI">watch?v=4KN0xoHsUiI</a>

But my project has more LEDs, it will play almost full motion video instead of a static image, and the globe will be a quite a bit larger, approximatively 1.5 - 2 meters in diameter, big enough to put a human in the center of the globe.

<a href="/public/uploads/2011/03/Mondomatrix_LEDMatrix_b_t.jpg"><img class="size-thumbnail wp-image-1352 alignright" title="Mondomatrix_LEDMatrix_b_t" src="/public/uploads/2011/03/Mondomatrix_LEDMatrix_b_t-150x150.jpg" alt="" width="150" height="150" /></a>Each of the 64x RGB LED will require 3x PWM pins for a total of 192 PWM pins. No Micro-controller has that many output pins, I know I have <a href="http://electronics.stackexchange.com/questions/11670/arm-development-board-with-lots-of-pwms">asked</a>. So you need to either create a <a href="http://www.instructables.com/id/LED-Dot-Matrix-Display/#step1">matrix of LEDs</a> or use some shift registers (SIPO). I decided to go with the shift register as is much harder to power a matrix of LEDs properly compared the shift registers.

The speed at which I an do a a full refresh <a href="http://electronics.stackexchange.com/questions/11633/pov-globe-speed-questions/11683#11683">was going to be a problem</a> as I needed to update 64x RGB LEDs (192 pins) using 12 BITs PWM 120 times a revolution, 192*12*120 = ~276480 bits per revolution. Basic old school animation frame rate is ~24 fames per sec but I would want it get the refresh rate as high as possible. ~24 fps * 276,480 bits = 6,635,520 bits per sec or  810k per sec. Thats a hell of a lot of raw data!

I found a few boards that used shift registers to expand the IO such as the <a href="http://mondomatrix.com/info/?page_id=317">MondoMatrix LEDMatrix board</a>. But because the board functions on 115.2 kbps RS485 bus, I abandoned it as it would be way too slow to update the LEDs fast enough to do video.

After researching several other boards, I decided to make my own specifically designed for this project . Who knows if I make it right I might be able to sell it as a kit. I have never built a board from scratch before but its a skill I have been meaning to learn for a while.

<img class="alignright size-thumbnail wp-image-1350" title="595_pin_diagram" src="/public/uploads/2011/03/595_pin_diagram-150x150.png" alt="" width="150" height="150" />

The most commonly used and basic, shift register is the <a href="http://www.sparkfun.com/products/733">74HC595</a>. There are lots of <a href="http://www.arduino.cc/en/Tutorial/ShiftOut">tutorials</a> and <a href="http://www.youtube.com/watch?v=5P9Gmqk5338">project</a><a href="http://code.google.com/p/bicycleledpov/"> using</a> this chip.  It has 8 output pins and can be connected in series. After asking a few questions on the <a href="http://vancouver.hackspace.ca/">Vancouver HackSpace</a> (VHS) mailing list. I was pointed at the <a href="http://www.insidegadgets.com/projects/shift-register-breakout-board/">595 Shift Ease - 74HC595 Shift Register Breakout Board</a>. An ingenious little board that lets you combine shift registers together easily to create a long series of shift registers.

I started searching for other shift register that had more output pins and better power management. I found the <a href="http://focus.ti.com/docs/prod/folders/print/tlc5947.html">TLC5947</a>. It has 24x PWM 12bit outputs, better power management, and it has a neat thermal shutdown function (Automatic shutdown at over temperature by  that turns off all output drivers). So it if ever gets too hot it turns it self off to protect it. Sounds like the perfect chip, except that it only comes as a <a href="http://en.wikipedia.org/wiki/Surface-mount_technology">surface mount chip</a> (SMT). I never done a SMT before and i have been told that they can be troublesome. One more new skill to learn.

<a href="/public/uploads/2011/03/OctoBrite-DEFILIPPI.jpg"><img class="size-thumbnail wp-image-1355 alignright" title="OctoBrite DEFILIPPI" src="/public/uploads/2011/03/OctoBrite-DEFILIPPI-150x150.jpg" alt="" width="150" height="150" /></a>Now that I found a chip that I can use to operate 192 PWM 12bit output pins I need to build a board for each of these chips. But before stared down the ugly <a href="http://www.cadsoft.de/">PCB Eagle</a> path, I searched to see what other projects where using that chip. After a little <a href="https://www.google.com/search?hl=en&amp;q=TLC5947+board">googling</a> I found the <a href="http://macetech.com/store/index.php?main_page=product_info&amp;cPath=1&amp;products_id=22">OctoBrite DEFILIPPI</a> board. Almost exactly what I was about to make with a few exceptions. The LED connections use a header instead of a 4 pin polarized connectors with common cathode. I can easily work around that but I emailed the manufacture of the board to see if they would make a change to their board for me. Waiting on their responses but even if they can't make the change I think I will still buy this board.

Next is how to power this project. 192 * ~30 mA = ~5.8 Amps at full brightness (white). Thats a hell of a lot of power and that doesn't even include the micro-controller (+200 mA)  and the motor (~1 Amp). It's not going to be too much of a problem at MakerFaire where I can connect to the grid but when I am out in the desert at burning man its another story. I will need to power this project off batteries and its going to be troublesome to say the lest. 5.8 Amps is only at full brightness and I will probably code in a brightness limiter so it uses as little power as possible to conserve on battery life and temperature of the chip.

<img class="alignright size-thumbnail wp-image-1359" title="0111879_1" src="/public/uploads/2011/03/0111879_1-150x150.jpg" alt="" width="150" height="150" />A <a href="http://goo.gl/A5LoC">100 Amp/hr deep cycle car battery</a> costs ~$250 CAN and this project could drain it in ~14hrs. So I am going to need at lest two of them and a way of charging them during the day. A ~1000 W  <a href="http://en.wikipedia.org/wiki/Solar_power">solar power</a> set up that is able to charge these batteries is going cost &gt;$2k. A <a href="http://goo.gl/hNKaU">1000 W generator</a> new is about ~$950 USD to buy but I think I could rent it for a week for a quarter of that, or beg, borrow, or steal it for much less.

Next problem is the micro-controller has to be able to handle a buffer of 810k per sec. A typical <a href="http://arduino.cc/en/Main/ArduinoBoardMega2560">Arduino Mega 2560</a> (thats the big one) has 8k of SRAM. I could use some very tricky programing methods to read the file only as it is needed but even still it would be extremely difficult if not impossible to get it working right. Ideally I would like to have a multi-threaded chip with at lest 4mb of SRAM to buffer as many of the 32k frames between refresh. <a href="http://electronics.stackexchange.com/questions/11670/arm-development-board-with-lots-of-pwms">Still working on this one</a>.

Still lots to think about but at lest some of the parts are coming together.

<strong>Item list </strong>
<ul>
	<li>Micro-controller (still researching)</li>
	<li>~$200, 10x <a href="http://macetech.com/store/index.php?main_page=product_info&amp;cPath=1&amp;products_id=22">OctoBrite DEFILIPPI</a> boards (2x spare, just incase)</li>
	<li>~$60, 100x RGB LED, viewing angle ~100, ~9400 MCD @0.59 each</li>
	<li>Physical body (still researching)</li>
	<li>~$100, Power supply ~10 Amp, 5-12v</li>
</ul>
I am hoping to spend less then $1000 on this project but i suspect that by the end it will be closer to $1500

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

<strong>
</strong>
