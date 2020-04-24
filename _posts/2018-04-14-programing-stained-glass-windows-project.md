---
layout: single
title: Programing - Stained glass windows project
date: '2018-04-14 00:01'
categories: 
    - projects
    - stain glass windows 
---

This post is part of a series on the [stained glass windows project](/projects/2018-stained-glass-window). 

In this project I am using a [Wemos ESP8266](/hardware-stained-glass-windows-project) development board. This board supports [micro python](https://docs.micropython.org/en/latest/esp8266/esp8266/tutorial/index.html), C/C++ and the Arduino variant of C/C++ via [ESP8266 core for Arduino](https://github.com/esp8266/Arduino). I decided to go with the ESP8266 core for Arduino because I was able to get it up and running quickly and I already had the tool chain set up for it. 

I been using [FastLED](https://github.com/FastLED/FastLED) for the last few projects over the more common [Adafruit_NeoPixel](https://github.com/adafruit/Adafruit_NeoPixel) library. FastLED uses less memory, more compatibility with different hardware and leds, actively [maintained and updated](https://github.com/FastLED/FastLED/commits/master), build in gamma and color correction, faster math and memory functions like HSV2RGB, [Good comunity](https://plus.google.com/communities/109127054924227823508), [Good documtation](https://github.com/FastLED/FastLED/wiki) 

For each pattern, I create a legend image that shows the offset of each LED. This gives me a good reference making it easier to make patterns. 

<img src="/public/uploads/stainglasswindow_legend.png" alt="Legend" />

Then I created a series of sets for each different geometry within the pattern.

For example: Star #1 = 3,4,9,14,13,10,3. Star #4 = 27,28,31,38,37,32. Cube #5=15,16,20. Cube #8=24,25,33 

<img src="/public/uploads/stainglasswindow_legend_SubSet.png" alt="legend_SubSet" />

Next I create a series of function for each type of pattern. The functions take a set of offsets, the transition speed, the color pallet as parameters. These parameters are randomized each time the function is called and should produce a different pattern each time the panel is started up. Theoretically there should be in the order of 65 million different patterns, but realistically there is only a few hundred visibly different patterns for each panel 

All the panels share the same code base with a different series of sets. As I made more patterns all the panels should get more and more interesting. 

All of the source code for the panels can be found on my github. [StainGlassLaserPatterns](https://github.com/funvill/StainGlassLaserPatterns) 
