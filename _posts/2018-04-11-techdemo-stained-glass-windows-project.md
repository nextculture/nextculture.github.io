---
layout: single
title: Tech Demo - Stained glass windows project
date: '2018-04-11 00:01'
categories: 
    - projects
    - stain glass windows 
tags: techdemo paper tape acrylic laser 
---

This post is part of a series on the [stained glass windows project](/projects/2018-stained-glass-window). 

When starting a new project, I tend to create a series of tech demos of all the different techniques that I am planning on using in the project. This helps me find out what works and what doesn't. 

Below are some of the design questions that I wanted to solve while working on the tech demo.

### How to attach the semi-transparent white acrylic inlay into the black border acrylic. 

My first thought was to use [Methylene chloride](https://en.wikipedia.org/wiki/Dichloromethane)  (acrylic glue). The issue with methylene chloride is that the parts have to be butted up to each other with no room for a gap. I could not guarantee that the laser cutter that I was using had tight enough tolerances that would prevent a gap from forming. Methylene chloride can also discolor acrylic and leave blotches or water marks that would be very visible when the light shines through the white acrylic. 

<img src="/public/uploads/stainglasswindow_segments.png" alt="Segments"/>

I thought about sandwiching the center plate between two clear plates of acrylic. This would be very expensive as each plate would need 4 layers of acrylic. Semi-transparent white inlay, Black borders, and two transparent sheets. 

I ended up with the low tech method of using clear packing tape stretch across the entire plate on the inside. This worked quite well. 

<img src="/public/uploads/stainglasswindow_tape.png" alt="tape"/>

### Dividers between the different segments in the design. 

Each segment of the design has a individually addressable LED. I needed a way to prevent the light from one LED from bleeding into the segment of a neighboring LED. 

My first idea was to use the laser cutter to create slotted dividers between each segment. This would have taken a bunch of time to design and I wanted to rapidly iterate on different designs. 

I decided to use a bunch of card stock I had on hand then tapping the cardstock together. This left imperfections in the dividers as the card stock got crinkled or deformed. The black borders helped hide the imperfections in the dividers. 

<img src="/public/uploads/stainglasswindow_dividers.png" alt="Dividers"/>

### Finding the right height for the dividers that prevented LED hotspots

An LED hotspot is when the light from the LED does not diffuse, and you can see single points that are brighter than others. 

<img src="/public/uploads/stainglasswindow_hotspots.png" alt="led_array_from_led_strips"/>

One of the simplest ways to solve this problem, is to increase the distance from the LED to the diffusing panel. Finding the optional distance that doesn’t make your project's profile too thick is always a challenge. Normally this comes down to trial an error. A good rule of thumb is twice the distance from the next closest LED. 

Another solution is to add a wax paper as a diffusing material. I find that this doesn’t alway produce uniform results and I tend to avoid it. 

In my case, most of the sections in my panels are 20 mm apart from each other. After a bit of trial and error I ended up using a divider with the height of 30 mm. 

### Positioning the LEDs in the segments

I need to layout the LEDs so that I could map and change the color of each segment independently. 

I could have made a sheet of LED strips and map the LEDs to each segment. This would allow me to have multiple LEDs per segment when the segment were larger. 

<img src="/public/uploads/led_array_from_led_strips.jpg" alt="led_array_from_led_strips"/>

The issue is that many of the LEDS wouldn't add value. LEDs under the dividers or in the corners of the segments. Mapping each segment would also take a lot of time. 

Instead I used "Square" style LEDs that have mounting flanges built into them. 

<img src="/public/uploads/led_pixels_square-profile.jpg" alt="Square LEDs"/>

Then created a backplane for these LEDS to be mounted on. The backplane has a series of 11.5mm holes that aline with the in the center of each of the different segments. The issue with this choice is that it requires another sheet of acrylic behind dividers. This adds to the cost of this project. 

<img src="/public/uploads/stainglasswindow_ledmount.png" alt="LED mount"/>

### Results 

This was the results of the first tech demo. I am reasonably happy with the way this one came out. I discovered that the spacing between the segments could be a lot smaller. In this tech demo I used 10 mm spacing. In later designs I shrunk the spacing down to 3mm. 

<blockquote class="instagram-media" data-instgrm-permalink="https://www.instagram.com/p/Bha3XUBloLC/" data-instgrm-version="8" style=" background:#FFF; border:0; border-radius:3px; box-shadow:0 0 1px 0 rgba(0,0,0,0.5),0 1px 10px 0 rgba(0,0,0,0.15); margin: 1px; max-width:658px; padding:0; width:99.375%; width:-webkit-calc(100% - 2px); width:calc(100% - 2px);"><div style="padding:8px;"> <div style=" background:#F8F8F8; line-height:0; margin-top:40px; padding:50.0% 0; text-align:center; width:100%;"> <div style=" background:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACwAAAAsCAMAAAApWqozAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAMUExURczMzPf399fX1+bm5mzY9AMAAADiSURBVDjLvZXbEsMgCES5/P8/t9FuRVCRmU73JWlzosgSIIZURCjo/ad+EQJJB4Hv8BFt+IDpQoCx1wjOSBFhh2XssxEIYn3ulI/6MNReE07UIWJEv8UEOWDS88LY97kqyTliJKKtuYBbruAyVh5wOHiXmpi5we58Ek028czwyuQdLKPG1Bkb4NnM+VeAnfHqn1k4+GPT6uGQcvu2h2OVuIf/gWUFyy8OWEpdyZSa3aVCqpVoVvzZZ2VTnn2wU8qzVjDDetO90GSy9mVLqtgYSy231MxrY6I2gGqjrTY0L8fxCxfCBbhWrsYYAAAAAElFTkSuQmCC); display:block; height:44px; margin:0 auto -44px; position:relative; top:-22px; width:44px;"></div></div><p style=" color:#c9c8cd; font-family:Arial,sans-serif; font-size:14px; line-height:17px; margin-bottom:0; margin-top:8px; overflow:hidden; padding:8px 0 7px; text-align:center; text-overflow:ellipsis; white-space:nowrap;"><a href="https://www.instagram.com/p/Bha3XUBloLC/" style=" color:#c9c8cd; font-family:Arial,sans-serif; font-size:14px; font-style:normal; font-weight:normal; line-height:17px; text-decoration:none;" target="_blank">A post shared by Steven Smethurst (@funvill)</a> on <time style=" font-family:Arial,sans-serif; font-size:14px; line-height:17px;" datetime="2018-04-11T06:17:35+00:00">Apr 10, 2018 at 11:17pm PDT</time></p></div></blockquote> <script async defer src="//www.instagram.com/embed.js"></script>


