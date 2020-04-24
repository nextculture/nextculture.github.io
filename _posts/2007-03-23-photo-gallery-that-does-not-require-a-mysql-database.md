---
layout: single
title: Photo Gallery that does not require a MySql database 
date: 2007-03-23 15:12
categories: Development
---
A while ago I was looking for a truly upload and go photo gallery one that does require a database. I found an abandoned PHP project called Simple PHP gallery by Paul Griffin.

No database required, automatically generates thumbnails,  auto generates gallery layout based off of file structior, a truly upload and go photo gallery. It was almost perfect only missing a few "nice to have" mod_rewrite and comments, file upload, and IPCT data.

After a little searching on Google I found that other people had made improvements to this package such as <a href="http://www.quirm.net/category.php?id=14" aiotarget="false" aiotitle="Enhanced Simple PHP Gallery and">Enhanced Simple PHP Gallery</a> and <a href="http://memory.org/point.b/open.source/">Espg v2</a> that alowed for mod_rewrite, comments.

I took the eSPG project and altered its source code and added the ability to read the <a href="http://www.abluestar.com/utilities/ephpg_iptc/">IPCT titles</a>, a pretty easy mod that you can read about and download <a href="http://www.abluestar.com/utilities/ephpg_iptc/">Enhanced Simple PHP Gallery IPTC mod</a>

The website for original developer of this project has been shut down. I have mirrored of the original project that you can download. <a href="http://www.abluestar.com/utilities/ephpg_iptc/espg_1_72_iptc.zip">eSPG with IPCT mod</a>

<strong>Features</strong>
<ul>
	<li>No Database required</li>
	<li>Upload and go</li>
	<li>Easy install (just upload the files in the zip)</li>
	<li>Automatically generates thumbnails</li>
	<li>Automatically generates gallery structure from file structure</li>
</ul>
<strong>Minimum Requirements</strong>
<ul>
	<li>     PHP 4.0 or better</li>
	<li>     GD Library, 1.0 or better</li>
</ul>
<strong> Recommended Requirements</strong>
<ul>
	<li>     PHP 4.0 or better</li>
	<li>     GD Library, 2.0 or better</li>
	<li>     File write permission for PHP</li>
	<li>     mod_rewrite</li>
</ul>
