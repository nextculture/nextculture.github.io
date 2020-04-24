---
layout: single
title: Leap Year post!
date: 2008-02-29 14:47
categories: uncategorized
---
February 29 is a date that only occurs once every four years, and is called leap day. This day is added to the calendar in leap years as a corrective measure, because the earth does not orbit around the sun in precisely 365.000 days.
The chance of being born on leap year day is about 1 in 1,500, there are about 4 million people worldwide with February 29 as there birthday.

This is the algorithm that I used to determine if a given year is a leap year or not. I'm not sure where I got it from but it comes in handy when creating calendar applications.
<blockquote> if (year % 4 == 0) &amp;&amp; ((year % 100 != 0) or (year % 400 == 0))
then leap
else no_leap</blockquote>
I'm sure there are more interesting things about leap years that I don't know.
I suggest that you check out <a href="http://en.wikipedia.org/">wikipedia.org</a> page on <a href="http://en.wikipedia.org/wiki/Leap_year">Leap_year</a>
