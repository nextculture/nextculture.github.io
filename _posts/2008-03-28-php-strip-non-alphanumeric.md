---
layout: single
title: PHP strip non alphanumeric
date: 2008-03-28 21:43
categories: Tips Development
---
On <a href="http://www.everydayfiction.com/">EveryDayFiction.com</a>, in the titles of the posts our editors insisted on including a non alphanumeric character.
The little dot that separates the title from the author. This causes havoc with a lot of my scripts and is really freaking annoying.

This handy little function strips all the non  alphanumeric character from the string.
<blockquote>function strip_non_alnum($str) {
$str = preg_replace('~^(\s*)(.*?)(\s*)$~m', "\\2", $str);
$str = ereg_replace("[^[:alnum:] ]","",$str);
return $str ;
}</blockquote>
