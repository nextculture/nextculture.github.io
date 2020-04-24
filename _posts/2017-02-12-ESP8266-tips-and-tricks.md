---
layout: single
title: ESP8266 Tips
date: '2017-02-12 00:01'
categories: uncategorized
---

Last updated: 2017 Feb 12th 

This is a list of tips and tricks for the [ESP8266](https://en.wikipedia.org/wiki/ESP8266) module. I will update this page as I learn more about these chips. Pull requests are appreciated.

## Communities
Where to look for help and support. 

- [ESP Community forums](http://www.esp8266.com/viewforum.php?f=25) 
- [Gitter for ESP8266](https://gitter.im/esp8266/Arduino) - A group chat for the ESP8266 and the Arduino libary. 
- [Stackoverflow](https://stackoverflow.com/questions/tagged/esp8266), and [electronics.stackexchange](https://electronics.stackexchange.com/questions/tagged/esp8266) are great for asking questions. 

## Documtation 

- [Debugging ESP8266 Arduino](https://github.com/esp8266/Arduino/blob/master/doc/Troubleshooting/debugging.md) - Instruction on how to set up the Arduino IDE to debug the ESP8266 Arduino libary. 

### Youtube 

- [Andreas Spiess](https://www.youtube.com/playlist?list=PL3XBzmAj53Rlu3Byy_GkqG6b-nwEpWku0) ESP8266 series. - Great youtube series of videos about the ESP8266. Highly suggested

## Libaries 

- [ESP8266 Arduino Libary](https://github.com/esp8266/Arduino)
- [WiFiManager](https://github.com/tzapu/WiFiManager) - ESP8266 WiFi Connection manager with fallback web configuration portal
- [WIZ Ethernet Library](https://github.com/funvill/WIZ_Ethernet_Library) - A fork of the WIZ_Ethernet_Library that supports Wiznet 550io Ethernet board. (Created by me)

## Power consumption 

- Under normal operation the ESP8266 chip consumes around 70mA at 3.3v with spikes of 300mA. These spikes are really anying while building a power supply. A 1000-2200uF cap and reduce these spikes. Source: [#47 Power Saving with ESP8266](https://www.youtube.com/watch?v=6SdyImetbp8). 
- The ESP.deepSleep() function doesn't work unless there is a delay of 100 after this command. 
  
  ~~~~
  ESP.deepSleep(1000*10000*3, WAKE_RF_DEFAULT) ; 
  delay(100); 
  ~~~~
  
- In deep sleep the ESP consumes around 0.06mA

