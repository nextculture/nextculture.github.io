---
layout: single
title: RGB LED POV Globe - Status update and mechanical issues
date: 2011-06-12 15:27
categories: Arduino Development  Projects 
---
This project has somewhat hit a road block and with 12 days left before <a href="http://makerfaire.ca/">Maker Faire</a> I'm starting to panic. This leaves me with ~4 good working days left. Here is my current stats.

<strong>Editor and Simulator</strong>

At <a href="http://www.burningman.com/">burning man</a> 2010 I saw the <a href="http://cwd.co.uk/illuminatrix/index.php">Illuminatrix</a> made by <a href="http://www.cwd.co.uk/">Ben Delarre</a>. A RGB LED color grid that was programmable from a <a href="http://www.cwd.co.uk/illuminatrix/edit.php">JavaScript editor</a> that he made. I was impressed when I saw it at burning man and contacted him early after I started this project to see if I could use his editor for my project. Not only did he let me use the editor but he said that he would change it so it would work specifically with<a href="http://cwd.co.uk/hbd5000/index.php"> my globe project</a>. A week later and I had my own HBD5000 page on his website with an editor, simulator and a few example animations. Amazing Ben Delarre is awesome.

<strong>Example animations:</strong>
Click the images to see a simulation.

<a href="http://cwd.co.uk/hbd5000/view.php?id=10"><img class="alignnone size-medium wp-image-1514" title="hbd5000_eg2" src="/public/uploads/2011/06/hbd5000_eg2-300x297.png" alt="" width="180" height="178" /></a> <a href="http://cwd.co.uk/hbd5000/view.php?id=3"><img class="alignnone size-medium wp-image-1515" title="hbd5000_eg3" src="/public/uploads/2011/06/hbd5000_eg3-300x294.png" alt="" width="180" height="176" /></a> <a href="http://cwd.co.uk/hbd5000/view.php?id=9"><img class="alignnone size-medium wp-image-1516" title="hbd5000_eg9" src="/public/uploads/2011/06/hbd5000_eg9-300x294.png" alt="" width="180" height="176" /></a>

Please <a href="http://cwd.co.uk/hbd5000/edit.php">generate your own animations</a> with the editor. We need more animations!

<strong>Software</strong>

Software is basically done, I'm still having problems steaming frames at full speed over bluetooth, but half frame rate is works great. On the Arduino Mega I can buffer ~19 full color frames and the Arduino uno I can buffer ~10 full frames. As I am displaying the frames to the users I can stream in new frames over bluetooth. The whole system works pretty well and with so little time left I probably won't be changing it anytime soon.

<strong>The Mechanical </strong>

The first wheel I made was a 6 foot monstrosity of bent tube stock. While I was doing my testing it was a little unbalanced and bent under the stress. As soon as it bent even a little the problem got exasperated and by the time I was able to shut it down the whole ring was bent out of shape and unrecoverable. It was an expensive and time consuming mistake. Luckily I was not running it at full speed or it could have sheared off its hinge and hurt someone as it flew though the air.

At this point I decided to shrink my project down from a 6 foot tall ring to the biggest bicycle rim that I could find. The bicycle rim is already sturdy enforced with the spokes, light and balanced. The project is smaller but much safer.

I drilled some holes in the rim for wires to run though and buffered the LEDs with expanding foam. Its not pretty but it works surprisingly well.

<a href="/public/uploads/2011/06/IMG_3351.jpg"><img class="alignnone size-thumbnail wp-image-1520" title="IMG_3351" src="/public/uploads/2011/06/IMG_3351-150x150.jpg" alt="" width="150" height="150" /></a> <a href="/public/uploads/2011/06/IMG_3354.jpg"><img class="alignnone size-thumbnail wp-image-1521" title="IMG_3354" src="/public/uploads/2011/06/IMG_3354-150x150.jpg" alt="" width="150" height="150" /></a> <a href="/public/uploads/2011/06/IMG_3412.jpg"><img class="alignnone size-thumbnail wp-image-1523" title="IMG_3412" src="/public/uploads/2011/06/IMG_3412-150x150.jpg" alt="" width="150" height="150" /></a>

Next I secured the Led boards, wires and the controller boards to the spokes of the bicycle rim. These components will be spinning at great speeds so I took extra care to make sure that they won't be going anywhere.

<a href="/public/uploads/2011/06/IMG_3415.jpg"><img class="alignnone size-thumbnail wp-image-1524" title="IMG_3415" src="/public/uploads/2011/06/IMG_3415-150x150.jpg" alt="" width="150" height="150" /></a> <a href="/public/uploads/2011/06/IMG_3416.jpg"><img class="alignnone size-thumbnail wp-image-1525" title="IMG_3416" src="/public/uploads/2011/06/IMG_3416-150x150.jpg" alt="" width="150" height="150" /></a> <a href="/public/uploads/2011/06/IMG_3417.jpg"><img class="alignnone size-thumbnail wp-image-1526" title="IMG_3417" src="/public/uploads/2011/06/IMG_3417-150x150.jpg" alt="" width="150" height="150" /></a>

Next I attached the bolts to a tuning fork like mount that <em><a href="http://atechodyssey.blogspot.com/">Arthur Hazleden</a></em> a fellow <a href="http://vancouver.hackspace.ca/wp/">Vancouver Hackspace</a> member made for me.

<a href="/public/uploads/2011/06/IMG_3419.jpg"><img class="alignnone size-thumbnail wp-image-1528" title="IMG_3419" src="/public/uploads/2011/06/IMG_3419-150x150.jpg" alt="" width="150" height="150" /></a> <a href="/public/uploads/2011/06/IMG_3421.jpg"><img class="alignnone size-thumbnail wp-image-1529" title="IMG_3421" src="/public/uploads/2011/06/IMG_3421-150x150.jpg" alt="" width="150" height="150" /></a>

Next I made a box out of wood with two pillows bolted to a center brace. A pillow is ball baring mount that should let the center shaft spin freely while saying in position.

<a href="/public/uploads/2011/06/IMG_3425.jpg"><img class="alignnone size-thumbnail wp-image-1531" title="IMG_3425" src="/public/uploads/2011/06/IMG_3425-150x150.jpg" alt="" width="150" height="150" /></a> <a href="/public/uploads/2011/06/IMG_3426.jpg"><img class="alignnone size-thumbnail wp-image-1532" title="IMG_3426" src="/public/uploads/2011/06/IMG_3426-150x150.jpg" alt="" width="150" height="150" /></a> <a href="/public/uploads/2011/06/IMG_3427.jpg"><img class="alignnone size-thumbnail wp-image-1533" title="IMG_3427" src="/public/uploads/2011/06/IMG_3427-150x150.jpg" alt="" width="150" height="150" /></a> <a href="/public/uploads/2011/06/IMG_3428.jpg"><img class="alignnone size-thumbnail wp-image-1534" title="IMG_3428" src="/public/uploads/2011/06/IMG_3428-150x150.jpg" alt="" width="150" height="150" /></a> <a href="/public/uploads/2011/06/IMG_3429.jpg"><img class="alignnone size-thumbnail wp-image-1535" title="IMG_3429" src="/public/uploads/2011/06/IMG_3429-150x150.jpg" alt="" width="150" height="150" /></a>

In this video/pictures you can see the LEDs lit up. I used a C Camp to keep the wheel from falling over. Ignore the voices in the background they are from the scary ally behind Vancouver Hackspace.

<a href="/public/uploads/2011/06/IMG_3433.jpg"><img class="alignnone size-thumbnail wp-image-1537" title="IMG_3433" src="/public/uploads/2011/06/IMG_3433-150x150.jpg" alt="" width="150" height="150" /></a> <a href="/public/uploads/2011/06/IMG_3434.jpg"><img class="alignnone size-thumbnail wp-image-1538" title="IMG_3434" src="/public/uploads/2011/06/IMG_3434-150x150.jpg" alt="" width="150" height="150" /></a> <a href="/public/uploads/2011/06/IMG_3436.jpg"><img class="alignnone size-thumbnail wp-image-1539" title="IMG_3436" src="/public/uploads/2011/06/IMG_3436-150x150.jpg" alt="" width="150" height="150" /></a>

<iframe width="425" height="349" src="http://www.youtube.com/embed/z-efDKEh8uU" frameborder="0" allowfullscreen></iframe>

<strong>Power</strong>

I used a <a href="http://electronics.stackexchange.com/questions/14757/powering-leds-with-a-computers-power-supply">standard computer power supply</a> to power all the LEDs and electronics on the wheel. This works really well and I suggest it for anyone that is powering large amounts of LEDs. The power supply comes with both 5v and 3.3v rails. A common computer power supply also filters and smooths out the current before passing it on to the LEDs.

There is a simple trick for <a href="http://www.techpowerup.com/articles/other/22">turning on a PC's power supply without a PC</a>. Basically you need to short the green {PS_ON} pin with any of the black wires {COM} on the power supply.
<a href="/public/uploads/2011/06/psconnshort.gif"><img class="alignnone size-full wp-image-1540" title="psconnshort" src="/public/uploads/2011/06/psconnshort.gif" alt="" width="147" height="220" /></a>

I am using a 3 connection slip ring to transfer power from the stationary base and power supply to the rotating wheel. There are lots of industrial slip rings available online but they are pretty expensive. You can make your own <a href="http://www.instructables.com/id/Flying-Fan/#step1">slip ring</a> but with something so important to this project I decided to buy one.

<strong>Safety at Maker Faire </strong>

Because of my previous mishap with the larger ring, and because the ring is spinning so fast the good people at Vancouver mini Maker Faire had valid concerns about the safety of this project. The code name of this project probably didn't help much either. HBD5000 = <strong>H</strong>ippy <strong>B</strong>all of <strong>D</strong>eath 5000.

I decided to encase the spinning parts of my project with <a href="http://en.wikipedia.org/wiki/Polyethylene_terephthalate">Polyethylene terephthalate</a> aka PET-G or better known as the stuff that pop bottles are made from. Its has a few good properties that plexi glass doesn't. Its easy to mode in to shape, it bends and warps instead of shattering, and most importantly its cheap.

They also connected me with <a href="http://toptekkies.com/">Farrell Segall</a> who has successfully created a few different POV projects that he plans to bring to Vancouver Maker faire this year. We met up at the Vancouver Hackspace and he showed me his impressive POV projects as well as some other very interesting projects that he is working on. He suggested that I make a mount at the top of the POV with a pillow so that the Ring won't be able to wobble too much. Great idea!

With the top mount and the PET-G even if this project does spin honorably out of control it shouldn't hurt anyone.

<strong>Issues </strong>
<ul>
	<li>The bluetooh receiver broke while I was mounting it to the Arduino board. Ordered another one and it should be here 2 days before Maker Faire. If it does not get here in time I will pre program the POV with a single image and use that to demo it.</li>
	<li>I have no welding skills and i'm reliant on others to do the welds that I need for this project.</li>
	<li>I have burnt out two used motors testing this project. I have purchased a bran new motor for Maker faire but if it burns out on site I will not be able to replace it.</li>
	<li>Spinning speed, there is a controversy on what speed I should spin the ring at. Its safer at slower speeds but I will get less frame rate. The POV is not spinning yet so I can not test it at different speeds.</li>
</ul>
<strong>Whats left to do </strong>
<ul>
	<li>Add the top mount for safety</li>
	<li>Add the PET-G container for safety</li>
	<li>Get it spinning</li>
	<li>Mount the power supply</li>
	<li>Add the slip ring to transfer power to the wheel.</li>
</ul>
&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;
