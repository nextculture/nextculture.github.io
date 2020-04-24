---
layout: single
title: Wordpress robots.txt
date: 2007-06-09 09:00
categories: Tips Development
---
Recently Daily blog tips ran an <a href="http://www.dailyblogtips.com/collection-of-robotstxt-files/">article about Robots.txt</a> files. The article gives examples of other major websites and there robots.txt files but fails to mention the reason behind each rule.

I am going to run thou my robots.txt file and describe each and every rule.
Hopefully by the end of this article you will have a better understanding of the robots.txt file.

<a href="http://www.abluestar.com/robots.txt">http://www.abluestar.com/robots.txt</a>
<pre>
sitemap: http://www.abluestar.com/sitemap.xml

User-agent:  *
Disallow: /img/
Disallow: /blog/wp-admin/
Disallow: /blog/wp-includes/
Disallow: /blog/category/
Disallow: /blog/feed/

User-agent: duggmirror
Disallow: /</pre>
<strong>Line 01: 'sitemap: http://www.abluestar.com/sitemap.xml'</strong>
I included a link to my site map, this is for Google Site map utility. Google Site map utility lets you define your site map in your robots.tst file or on there webmasters configuration page. I use both just incase.

<strong>Line 02: 'User-agent:  *'</strong>
This tell search engines that the following rules apply to all robots and everyone should follow it.

<strong> Line 03: 'Disallow: /img/'</strong>
This line tells the search engines that I don't want them to index my /img/ folder. The folder mainly contains pictures of my family and friends. There is no reason for robots to search this directory, infact I don't want pictures of my family showing up randomly on the internet.

<strong>Line 04: 'Disallow: /blog/wp-admin/'
Line 05: 'Disallow: /blog/wp-includes/'</strong>
These two lines tell robots to say out of the Wordpress softwares application data, most of these files are password protected and there is no reason for a robot to go here.

<strong>Line 06: 'Disallow: /blog/category/'
Line 07: 'Disallow: /blog/feed/'</strong>
These two lines are important for SEO. Most search engines will penalize you for duplicate content (Content that appears in more the once place at a time). Your category pages and RSS feed is all duplicate content, copies of your psts. To prevent search engines from penalizing my site I ask them not to index these pages. This reduces the amount of duplicate pages that the search engine will fine.

<strong>Line 08: 'User-agent: duggmirror'
Line 09: 'Disallow: /'</strong>
These two lines tells a specific robot <a href="http://www.duggmirror.com/">duggmirror robot</a> that I don't want them indexing any of my site. The duggmirror is used by digg.com to make copies of your website before posting it on digg. On slow servers this is a good idea it prevents your site from falling over because of the massive amount of traffic that these social bookmark sites can produce. Instead of the traffic going to your site it goes to this mirror site and everone gets a chance to see your content. Sounds like a good thing right?.. The problem is that you don't get the traffic, your ads don't get clicked on and you cant see the traffic stats. I host this site on a server that can take all the traffic that digg/fark/slashdot/stumble upon can thou at it so there is no reason for someone else to mirror my site, so I disable this robot from crawling any of my site.

I hope you found this article useful, if you have any suggestions for other rules that might be handy.
Feel free to comment.
