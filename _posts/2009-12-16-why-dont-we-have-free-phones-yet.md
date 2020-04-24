---
layout: single
title: Why don't we have free phones yet?
date: 2009-12-16 12:42
categories: Rants
tags: android Arduino  cellphone openhardware opensource phone
---
<blockquote>"Re:Should be" by <a href="http://slashdot.org/~canajin56">canajin56</a> (660655) on Wednesday December 16, @12:21PM (#<a href="http://apple.slashdot.org/comments.pl?sid=1480704&amp;cid=30459990">30459990</a>)
<blockquote>At least you guys have a choice of providers. Here in Canada, we almost have government-backed monopolies with even higher monthly bills.</blockquote>
Are you kidding? It's not like we're limited to the big 3 (Rogers, Telus, Bell), we have all sorts of other providers! There's KOODO, their ads lead me to believe they don't do all that nasty hidden fee stuff. Oh, rebranded TELUS to seem less evil? Oh, well, there's always FIDO, they make the same claims about being not as evil as Rogers in all their ads! Oh...they're owned by Rogers, to rebrand and seem less evil, too? Well, there's always Solo Mobile. Oh...same deal with Bell? Virgin Mobile? Oh, Bell again? Why do they need TWO sham fronts? My favorite customer gouging one was the guy who ran up the $60,000 monthly bill, because they sold him an "Unlimited* Data** Plan!" that didn't cover any data usage other than the phones built in browser, so all that smartphone shit that also used data was billed at dollars on the kilobyte. The best part of that was the way Telus or whoever it was was unrepentant "It's not our fault he did not fully read the contract, but out of sheer generosity we will reduce the bill to a mere 6 grand!" A close runner up is KOODO/Telus's promise of "No activation fee", while there is a cancellation fee that is due in advanced when you sign up! Sort of like Blockbusters "No late fee *cough*but-there's-a-restocking-fee-if-you-return-it-late*cough*"
Source: <a href="http://apple.slashdot.org/comments.pl?sid=1480704&amp;cid=30459990">http://apple.slashdot.org/comments.pl?sid=1480704&amp;cid=30459990</a></blockquote>
<strong>**Mostly thinking out loud**</strong>

Why don't we have free phones yet?
Well lets look in to the barriers to a free phone. Software stack (OS), Hardware (the physical phone), Cell phone network (Cell phone towers and RF frequencies).

The software is pretty much done for us now that Google has released <a href="http://www.android.com/">http://www.android.com</a>. Even before  the android there where plenty of free open source smart phone stacks.

The hardware is a little tricker, it takes a lot of effort to build a solid phone with the right feature set. But over the last few years we have seen great strides in <a href="http://en.wikipedia.org/wiki/Open_source_hardware">open hardware</a> such as <a href="http://www.arduino.cc/">http://www.arduino.cc/</a>. Everything from Servos, webcams, wind turbines, to even more complex things like Graphics cards, GPS, and multi-touch tablets.  There is even an open hardware cellphone <a href="http://en.wikipedia.org/wiki/Openmoko">Openmoko</a> (<a href="http://www.openmoko.com/freerunner.html">FreeRunner</a>) that has its own software stack. The hardware can be made with enough smart people behind it.

The network required an array of physical cell phone towers spread across the coverage area and RF frequency that the Cellphones can use to communicate with the cell phone towers (<a href="http://electronics.howstuffworks.com/cell-phone1.htm">How cell phone talk to each other</a>). The RF frequency sold by the government to the highest bidder for billions.  There is no way for an open source group or any small business to enter the field. Roadblock.

So how do we work around the cell phone networks?

<strong><span style="text-decoration: underline;">Distributed network. </span></strong>

One option is you could use short range open RF frequency and hop your signal from device to device until it found its detestation (<a href="http://en.wikipedia.org/wiki/Mesh_networking">Mesh_networking</a>). Every device on the network would be responsible for receiving message checking to see if the message was meant for them if not sending it on to the next node. After a connection is made a short route could be created to optimize the connection and a backup route in case the first rout drops off. Every time a device comes in contact with anther devices it could create a list of contacted devices and the last time they saw them. This list would help in creating routs between people. The more users on the network the better chance there is that your message would get delivered.

<strong>Problems</strong>

These are just the ones that I can think of off the top of my head. I'm sure there are many more.
<ul>
	<li><strong>Fractured networks</strong>. If two people are too far apart and there are not enugh nodes to connect them to each other they will not be able to send a message between each other.</li>
	<li><strong>Privacy</strong>. If the message has to be relayed thou many different devices there is a chance that it could be intercepted by one of these devices and read by an unintended target. Public and private key encryption should help with reducing the ability for third parties to spy on conversations but the risk is still there.</li>
	<li><strong>Battier life</strong>. Since every device would be essentially active all the time they would consume a enormous amount of power.  Think of your current cell phone and how long the battery lasts when you are talking on it. At most a battery charge would only last a day.</li>
	<li><strong>Wear and tare</strong>. Again since all the devices are talking all the time the devices would break down a lot faster then your normal cell phone. instead of years think maybe one full year. More disposable electronics means more trash in our landfills, ect...</li>
	<li><strong>DOS attack</strong>s. Since every device has the requirement to repeat message that it receives to every other devices on the network until a destination is found the system acceptable to denial of service attacks.</li>
	<li><strong>RF frequency</strong>. Collisions between two different devices talking on the same channel.</li>
</ul>
Distributed networks doesn't seem to be the right option for a free cell phone network.
