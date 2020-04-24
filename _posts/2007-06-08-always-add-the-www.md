---
layout: single
title: Always add the www
date: 2007-06-08 09:00
categories: Tips Development
---
When creating a new website you want to create as little duplicate content as possible. Most host let your users access your website from either the <em>http://abluestar.com</em> or the www version <em>http://www.abluestar.com</em>. This can be dramaticly reduce your site's Page rank because is that most search engines see the 'www' and the 'non www' version as two different websites and Googles's Page rank is split between the two sites. Instead of getting a solid PR4 you get two measly PR2 sites.

<strong>There is a solution</strong>
You can force your users browser to redirect to the www version with a Mod Rewrite script.

<strong>Directions </strong>
<ol>
	<li>Create a new file called <em>.htaccess</em></li>
	<li>Copy and past the snippet below in to the file.
<blockquote> RewriteEngine on
RewriteBase /
# Always add the www
RewriteCond %{HTTP_HOST} !^www.abluestar.com$
RewriteRule ^.*$ http://www.abluestar.com%{REQUEST_URI} [R=301,L]</blockquote>
</li>
	<li>Replace 'abluestar.com' with your domain (replace in two locations)</li>
	<li>Upload the file to your base directory on your web server.</li>
</ol>
The next time your users try to browse to your non 'www' version of your website they will be automatically forwarded to you  www version.
