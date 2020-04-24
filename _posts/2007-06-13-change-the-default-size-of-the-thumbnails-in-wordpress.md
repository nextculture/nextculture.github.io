---
layout: single
title: Resize thumbnails in Wordpress
date: 2007-06-13 23:08
categories: Tips Development
---
I get asked this question lot, how to change the default size of the thumbnail that wordpress creates when you upload an image. There are two different ways of doing it depending on what version of your Wordpress you have installed.

<strong>If you have Wordpress prior to 2.1</strong>
Open <em>/wp-admin/inline-uploading.php</em> and look for the following code:
<code>if ( $imagedata['width'] &gt; 128 &amp;&amp; $imagedata['width'] &gt;= $imagedata['height'] * 4 / 3 )
$thumb = wp_create_thumbnail($file, 128);
elseif ( $imagedata['height'] &gt; 96 )
$thumb = wp_create_thumbnail($file, 96);</code>

The default max size is 128 x 96. You can change these numbers to whatever you like, although you must keep the proper aspect ratio (4 / 3).
For example, to double the size of the thumbnails, replace 128 with 256, and 96 with 192. Be sure to change both sets of numbers - they are each listed in the code twice.

<strong>Instructions for WordPress 2.1 or 2.2 and later</strong>
Open <em>/wp-admin/admin-functions.php</em> and look for the following code:
<code>$max_side = apply_filters( 'wp_thumbnail_max_side_length', 128, $attachment_id, $file );</code>

This works a bit differently than earlier versions of WordPress. The number specified here (128 by default) is the maximum size of either dimension. You can still just change this to whatever number you like though.
