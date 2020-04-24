---
layout: single
title: In search for a bug tracking system 
date: 2010-04-30 10:32
categories: Development
---
I'm about to start a new development project with a new group and we needed some sort of bug tracking system to coordinate all our efforts.  Previously I have used <a href="http://www.mantisbt.org/">www.mantisbt.org/</a> but its messy and I don't like the layout at all.

<strong>Requirements</strong>
<ul>
	<li>Installs on a LAMP system (MySQL, PHP, ect..) - Easy to install, I am lazy and I want to do as little work as possible</li>
	<li>Self hosted - Paranoia keeps me from using anyone else server.</li>
	<li>Web interface  - Need somewhere to submit a ticket.</li>
	<li>Notification - The user that submitted the ticket needs to be notified when we add a comment.</li>
	<li>Roll and category based access control - I don't want security based tickets visible to the public</li>
	<li>Required fields: Department/Category, Status, Priority, issue, steps to reproduce, Attached files.</li>
</ul>
<strong>Nice to haves </strong>
<ul>
	<li>Free or cheap -</li>
	<li>Email interface - I would be nice if users could submit and comment on tickets via email instead of having to log in to the web interface.</li>
	<li>Integrates with SVN - Some way of telling the user what version of the code this ticket was resolved in.</li>
	<li>The ability to add custom fields.</li>
</ul>
<strong>Different Bug tracking systems out there </strong>
<ul>
	<li><a href="http://www.redmine.org/">Redmine</a> - Written in Ruby on rails and will not run out of the box on a LAMP system.</li>
	<li><a href="http://www.bugzilla.org/">Bugzilla</a> - Mature, its been around for years and used by many different projects. IT scales increadably well up to extreamly large projects such as <a href="https://bugzilla.mozilla.org/">Mozilla's bug tracking system</a></li>
	<li><a href="http://trac.edgewall.org/">Trac </a>- I really like how minimalist it is. Written in python and uses MySQL for a database.</li>
</ul>
In the end I went with Trac because how how easy it was to install and its minimalist feel.
