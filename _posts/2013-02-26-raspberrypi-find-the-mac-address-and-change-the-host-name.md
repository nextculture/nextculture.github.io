---
layout: single
title: RaspberryPI - Find the MAC address and change the host name
date: 2013-02-26 16:19
categories: programing RaspberryPI snippet VHS
---
<a href="/public/uploads/2013/02/Raspi-PGB001.png"><img class="size-thumbnail wp-image-3183 alignright" alt="Raspi-PGB001" src="/public/uploads/2013/02/Raspi-PGB001-150x150.png" width="150" height="150" /></a>We have been running Raspbberry PI nights at VHS the last few weeks and they have been going really well.
<ul>
	<li><a href="http://vancouver.hackspace.ca/wp/2013/02/14/using-the-raspberry-pi-to-control-a-arduino-thursday-feb-21st-2013-730pm/">Using the Raspberry PI to control a Arduino</a></li>
	<li><a href="http://vancouver.hackspace.ca/wp/2013/02/04/raspberry-pi-python-webide-gpio-pins-blink-sketch-tuesday-feb-5th/">Raspberry PI + Python + WebIDE + GPIO pins = Blink sketch</a></li>
</ul>
We are running the Raspberry PIs headless (no keyboard or mouse, using SSH) because VHS only has one device capable of being used as a display (out projector) and asking people to bring in their monitors as well as their Raspberry PIs would be bothersome.

To run the Raspberry PI headless, we need to enable SSH and know the IP address of the Raspberry PI. Some distros like the <a href="http://learn.adafruit.com/adafruit-raspberry-pi-educational-linux-distro/occidentalis-v0-dot-2">Occidentalis</a> come with SSH enabled by default. If your distro does not have SHH enabled you can follow these instructions to enable it <a href="http://learn.adafruit.com/adafruits-raspberry-pi-lesson-6-using-ssh">Adafruits Raspberry PI Lesson 6 Using SSH</a>

When people arrive they connect their Raspberry PIs to our network and DHCP an IP address from our router. The problem is that by default all the Raspberry PIs have the same hostname and its very hard to determine what Raspberry PI has what IP address.

If you know the MAC address of your Raspberry PI it makes it a lot easier to look up the MAC address in the router IP address tables. Or better yet change the Hostname of your Raspberry PI.

<strong>How to find the MAC address of your Raspberry PI/Linux Box</strong>

The MAC address is very useful for finding the IP address of your Raspberry PI if there are other Raspberry PIs on your network with the same Hostname. I would suggest writing this on your Raspberry PI case.
<pre>ifconfig -a | grep HWaddr</pre>
This will display a list of MAC address of your network devices currently installed on your system. Eth0's MAC address should be prefixed with <span style="background-color: #ffff00;">B8:27:EB</span>.
<pre>eth0 Link encap:Ethernet HWaddr <span style="background-color: #ffff00;">b8:27:eb:a1:b2:c3</span></pre>
In this example the MAC address is <em>B8-27-EB-A1-B2-C3</em>

<strong>How to change the Host Name of your Raspberry PI/Linux box </strong>

A host name makes it easy to find the device on your network when you do not know the IP address of your Raspberry PI.
<pre>sudo nano /etc/hostname (and enter the desired name, "
CTRL+X" then "
Y" to quit) 
sudo nano /etc/hosts and replace raspberry with the hostname you chose above
sudo /etc/init.d/hostname.sh start (to enable the changes).</pre>
Instead of typing the IP address of your Rapsberry PI you can use the host name to connect to your device.
