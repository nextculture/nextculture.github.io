---
layout: single
title: SQL Injection License Plate
date: 2011-10-11 19:10
categories: uncategorized
---
<a href="/public/uploads/2011/10/for_traffic_cameras.jpg"><img class="size-medium wp-image-2248 alignright" title="for_traffic_cameras" src="/public/uploads/2011/10/for_traffic_cameras-300x225.jpg" alt="" width="300" height="225" /></a> One clever hacker realized that recent speed traps use cameras that automatically register your speed, take a picture of you license plate, and then use character recognition to translate you license plate number into something they can use as a lookup within the DMV database. With this in mind, he changed his license plate number to
<blockquote>('ZU 0666', 0, 0); Drop Database Table.</blockquote>
If the DMV uses this string of characters in their database lookup it has a good chance of deleting all of the database records containing his actual license plate number, ZU 0666. This has got to be 10 out of 10 on the creativity scale, and once again showing the importance of knowing what SQL injection and <a href="http://xkcd.com/327/">little Bobby tables</a> is all about.

Source: <a href="http://gizmodo.com/5498412/sql-injection-license-plate-hopes-to-foil-euro-traffic-cameras">SQL Injection license plate hopes to foil euro traffic cameras</a>
