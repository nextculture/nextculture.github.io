---
layout: single
title: How to check your MAC address of your network cards
date: 2007-02-19 09:00
categories: Tips
---
How to check your MAC address of your network cards
1) Open a command prompt (Windows Start button-&gt; Run -&gt; Type "cmd" )
2) Type "ipconfig /all"

Your MAC address are defined as "Physical Address" and should be a 6x 2 HEX charter string.
For example: '00-03-0D-12-00-00'
It should look something simlare to this.
<code>
Windows IP Configuration
Host Name . . . . . . . . . . . . : XXXXXXX
Primary Dns Suffix  . . . . . . . :
Node Type . . . . . . . . . . . . : Broadcast
IP Routing Enabled. . . . . . . . : No
WINS Proxy Enabled. . . . . . . . : No
<u> Ethernet adapter Local Area Connection:</u>
Connection-specific DNS Suffix  . :
Description . . . . . . . . . . . .: SiS 900-Based PCI Fast Ethernet Adapter
<strong> Physical Address</strong>. . . . . . . . . : 00-03-0D-12-00-00
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 192.168.1.106
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.1.1
DHCP Server . . . . . . . . . . . : 192.168.1.1
DNS Servers . . . . . . . . . . . : 4.2.2.2
4.2.2.3
Lease Obtained. . . . . . . . . . : Wednesday, April 25, 2007 9:34:31 AM
Lease Expires . . . . . . . . . . : Thursday, April 26, 2007 9:34:31 AM
<u> Ethernet adapter Wireless Network Connection 2:</u>
Media State . . . . . . . . . . . : Media disconnected
Description . . . . . . . . . . . : 802.11g MiniPCI Wireless Network Adapter
<strong> Physical Address</strong>. . . . . . . . . : 00-0C-76-CA-00-00
</code>
