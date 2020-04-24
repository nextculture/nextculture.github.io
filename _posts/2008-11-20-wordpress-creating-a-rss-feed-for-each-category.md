---
layout: single
title: Wordpress, Creating a RSS feed for each category.
date: 2008-11-20 12:04
categories: Tips
---
Have you ever wanted to create a RSS feed just for a perpendicular category in wordpress?

Say for example that you run an artiest website like my friend <a href="http://www.camilladerrico.com/blog/">Camilla d'Errico</a>. You want to send your users updates about upcoming shows but you don't want to send them all the status updates and other blog posts.  Well we can create a separate RSS feed just for the news posts. And if we where so inclined we could also create a mailing list (via <a href="http://www.feedburner.com/">feedburner</a>) that our users could subscribe to just for the news.

Well your in luck because wordpress already does it for you.
You just need to know the syntax

<code>&lt;blog url&gt;/?feed=rss2&amp;cat=&lt;Catagory ID&gt;
eg. <a href="http://www.camilladerrico.com/blog/?feed=rss2&amp;cat=16">http://www.camilladerrico.com/blog/?feed=rss2&amp;cat=16</a></code>

It works in Wordpress 2.6.3
