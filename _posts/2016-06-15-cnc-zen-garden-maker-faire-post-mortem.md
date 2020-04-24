---
layout: single
title: CNC Zen Garden - Vancouver Maker Faire 2016 Post Mortem
date: '2016-06-15 00:01'
categories: uncategorized
---
This is a post mortem of the version of the cnc zen garden that I took to the [Vancouver Mini Maker Faire 2016](http://makerfaire.ca/). 

During the faire I discovered many issues with the machine. Most of these issues I was able to resolve during the faire or at least patch until the end of the faire. Despite all these issues the machine ran through the faire and I learned a lot. 

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image02.png)

## Issues in this version

### 1) RAMPs board regulator was not properly installed
When I arrived at maker faire and plugged in my power supply the power supply shut down. I borrowed another power supply from a friend at the faire and tried again with the same result. At this point I suspected that there was a short in my [RAMPS board](http://reprap.org/wiki/RAMPS_1.4). 

I separated the RAMPs board from the [arduino mega](https://www.arduino.cc/en/Main/ArduinoBoardMega) and found that the through hole component still had its leads attached. I the leads were touching each other and the arduino mega on the bottom side. I snipped the leads and the RAMPS board started working. 

I suspect that the board got compressed while in transit to maker faire causing the leads to touch and short the board. This would explain why I didn't have this issue with the RAMPs board while on my desk at home. 

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image05.png)

### 2) Belt on from the towers is at an angle to the Y carriage
The belt on coming from each of the towers to the Y carriage was at a slight angle. When the Y carriage got close to one of the towers the angle of the belt increased and caused the motors to work harder and consume more current. 

When the motors consumed more current than the steppers were setup to allow, the motors would skip steps and the plotter would become unaligned. 

I increased the steppers motors current limit from 0.3 to 0.7 to resolve this issue. 

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image08.png)

### 3) Stepper motors going into thermal shutdown.

I increased the stepper motors current to help reduce the skipped steps caused by the bad angle from the towers to the Y carriage. This caused the stepper motors to heat up and eventually go into thermal shutdown. They were hot to touch. 

I added a small 12v fan to blow air across the heatsinks on the stepper motor drivers and remove some of the heat. This dramatically reduced the temperature of the stepper motor drivers and I never got a thermal shutdown again. 

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image03.png)

### 4) Belt tensioning

I did not build in a way to tension the belts easily. Instead I used cable ties connected to the X carriage. Getting the tension just right was impossible. I need to cut and reapply the cable ties several times throughout the event. 

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image11.png)

### 5) Belt tensioning under movement

When the X carriage was moving left or right this caused slack in one or the belts along the Y axis.  Since there was no springs to tighten up the belts not under tension this caused them to sometimes skip steps when tension was reapplied. 

A simple tension spring would have resolved this issue. 

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image09.png)


### 6) Missed steps near towers made limit switches useless

I designed all my patterns with the assumption that I could home the machine using a pair of limit switches. Homing the machine with the limit switches would have given me absolute coordinate of the x carriage.

Since the machine was losing steps as it got closer to the towers. I could not trust the assumed location of the machine when it got close to the towers. The missed steps sometimes causes the X carriage to crash into the towers or the Y carriages. 

I ended up rewriting all my patterns to use the center as a starting location instead of using the limit switches.  I would recenter the X carriage in the center of the working area then turn on the machine and teleport to the center of the work area, then start the patterns. This was not ideal but it worked for most of the faire. 

### 7) No bearings for the towers or carriages

I didn’t used bearing for pulley in the towers, instead I used a smooth 8mm bolt. Eventually the pulleys fused with the bolts and started to rub against the acrylic towers. The extra friction made the motors work harder and causes a high pitch squealing noise that annoyed everyone around me. 

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image01.png)



### 8) Towers windows were not big enough and the belts rubbed

The windows in the towers that allowed the belts to connect to the pulleys, were too small and the belts rubbed against the acrylic. This didn’t cause too much of an issue but I suspect that over time it would reduce the lifespan of the belts. 

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image06.png)


### 9) The belts crossed over and touched each other causing friction
This is one of the common problems with a CoreXY system. It can be solved by moving the belts to different z heights so they don’t touch each other. In my design the touched and caused friction. 

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image10.png)

### 10) Towers were not placed square to each other

The towers were not perfectly square. This caused compression of the X rods when the carriage came close to one of the sides. This often caused missed steps. 

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image07.png)


## Things that worked
Even with all the issues with this version there was some things that worked well. 

### 1) Stilts

The stilts that I used to offset the working area worked well. They allowed me to lift the working area box off the top of the machine and show people how the machine worked. This also allowed me to review and repair the issues with the machine. 

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image01.png)

### 2) The working area

The working area is a [RIBBA photo](http://www.ikea.com/ca/en/catalog/products/90301621/) frame from ikea. I removed the back of the photo frame and put the glass face down. The glass bottom allowed light from within the machine to shine through the sand where the ball bearing had cleared. This created a very nice effect that can be seen in this video. 

<blockquote class="instagram-media" data-instgrm-captioned data-instgrm-version="7" style=" background:#FFF; border:0; border-radius:3px; box-shadow:0 0 1px 0 rgba(0,0,0,0.5),0 1px 10px 0 rgba(0,0,0,0.15); margin: 1px; max-width:658px; padding:0; width:99.375%; width:-webkit-calc(100% - 2px); width:calc(100% - 2px);"><div style="padding:8px;"> <div style=" background:#F8F8F8; line-height:0; margin-top:40px; padding:50.0% 0; text-align:center; width:100%;"> <div style=" background:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACwAAAAsCAMAAAApWqozAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAMUExURczMzPf399fX1+bm5mzY9AMAAADiSURBVDjLvZXbEsMgCES5/P8/t9FuRVCRmU73JWlzosgSIIZURCjo/ad+EQJJB4Hv8BFt+IDpQoCx1wjOSBFhh2XssxEIYn3ulI/6MNReE07UIWJEv8UEOWDS88LY97kqyTliJKKtuYBbruAyVh5wOHiXmpi5we58Ek028czwyuQdLKPG1Bkb4NnM+VeAnfHqn1k4+GPT6uGQcvu2h2OVuIf/gWUFyy8OWEpdyZSa3aVCqpVoVvzZZ2VTnn2wU8qzVjDDetO90GSy9mVLqtgYSy231MxrY6I2gGqjrTY0L8fxCxfCBbhWrsYYAAAAAElFTkSuQmCC); display:block; height:44px; margin:0 auto -44px; position:relative; top:-22px; width:44px;"></div></div> <p style=" margin:8px 0 0 0; padding:0 4px;"> <a href="https://www.instagram.com/p/BGYexS9g5Up/" style=" color:#000; font-family:Arial,sans-serif; font-size:14px; font-style:normal; font-weight:normal; line-height:17px; text-decoration:none; word-wrap:break-word;" target="_blank">I added LED&#39;s to the #CNCZenGarden. It&#39;s working pretty well. I can seem to get the limit switches working. Made for @makerfaire_van #vmmf. . .  #sand #cnc #art #interactiveart #projects #motion #movingart #patterns #msgnets #maker #marble #ballbearing</a></p> <p style=" color:#c9c8cd; font-family:Arial,sans-serif; font-size:14px; line-height:17px; margin-bottom:0; margin-top:8px; overflow:hidden; padding:8px 0 7px; text-align:center; text-overflow:ellipsis; white-space:nowrap;">A video posted by Steven Smethurst (@funvill) on <time style=" font-family:Arial,sans-serif; font-size:14px; line-height:17px;" datetime="2016-06-08T05:55:15+00:00">Jun 7, 2016 at 10:55pm PDT</time></p></div></blockquote>
<script async defer src="//platform.instagram.com/en_US/embeds.js"></script>

[https://www.instagram.com/p/BGYexS9g5Up/?taken-by=funvill](https://www.instagram.com/p/BGYexS9g5Up/?taken-by=funvill)

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image04.png)


### 3) Viewing area 

With the working area raised above the rest of the machine this allowed a small window for people to see how the machine worked. This had a side effect of causing a crowd to form around the machine as everyone took their turn to see what was going on. A crowd draws an even larger crowd. 

![zen garden]({{site.baseurl}}/public/uploads/zen_garden_image12.png)


## Conclusion

This project was a great learning experience on how a basic CNC works and the issues that can happen. The deadline of the [vancouver mini maker faire](http://makerfaire.ca/) kept me working on this project even when I ran into frustrations and problems.

It was a fun project. 
