---
layout: single
title: Raspberry PI - Start up questions
date: 2012-06-17 19:23
categories: Development Projects RaspberryPI Tips
---
<a href="/public/uploads/2012/06/Raspberry-Pi-Logo.jpg"><img class="alignright size-thumbnail wp-image-2774" title="Raspberry-Pi-Logo" src="/public/uploads/2012/06/Raspberry-Pi-Logo-150x150.jpg" alt="" width="150" height="150" /></a>I got my new shinny <a href="http://www.raspberrypi.org/">Raspberry PI</a> a few days ago, and got some time to play with it today. I am a windows guy by default and this is my first adventure in to the world of Linux. While getting everything started it up I ran in to these questions.

<strong>[Q] I have a 700 mA USB power supply but my Raspberry PI keeps turning off randomly, Why? </strong>
<strong>[A]</strong> 700 mA is the absolute minimum, Once I switched to a 1500 mA power supply I had a lot less problems with random restarts.

<strong>[Q] My keyboard is not working when plugged directly in to the main board, Why? </strong>
<strong>[A]</strong>  The main board is only capable of producing 100 mA per channel over the USB, my keyboard draws 500 mA (more then I would have expected, cheap Chinese gear). The Raspberry PI disabled that port and the keyboard would not function. I found a self powered USB hub to power the keyboard and mouse off of and that seemed to resolve this problem. <a href="http://elinux.org/R-Pi_Troubleshooting#Keyboard_.2F_Mouse_.2F_Input_Devices">R-Pi does not respond to key presses</a>

<strong>[Q] Okay, I got my Raspberry PI to boot, What is the default username and password? </strong>
<strong>[A] </strong>The default username and password can be found on the <a href="http://www.raspberrypi.org/downloads">download page</a> for the Raspberry PI OS.<strong> Username:</strong> pi <strong>Password:</strong> raspberry

<strong>[Q] Now that I am logged in how to I get the desktop to show?</strong>
<strong> [A]</strong> You need to launch a desktop environment, (Debian "
squeeze") comes with X Windows. You can start it by typing "startx" in the command prompt.

<strong>[Q] With the default firmware (Debian "
squeeze"), The keyboard is set to British formatted keyboard, and I would like it to be set to US formatted key board. How do I do this? </strong>
<strong>[A]</strong> From the terminal window
<blockquote>- Type 'sudo su' then press =enter]
- Run 'dpkg-reconfigure locales' and changing from en_GB.UTF-8 to en_US.UTF-8 (or whatever country setting you need).
- Run 'dpkg-reconfigure keyboard-configuration' and change the keyboard to USA PC104 (again, change as needed).
- Reboot.</blockquote>
<a href="http://www.raspberrypi.org/phpBB3/viewtopic.php?f=27&amp;t=6907">Remapping the Keyboard</a>

&nbsp;
