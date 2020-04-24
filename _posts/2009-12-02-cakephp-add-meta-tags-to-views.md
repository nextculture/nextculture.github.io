---
layout: single
title: Cakephp - Add meta tags to views
date: 2009-12-02 12:20
categories: Tips
---
This is how you add well formated meta tags to a cakephp views even thou the meta tags are rendered in the layout.

In the head section of your layout, add this line:
<code>&lt;?php echo $scripts_for_layout ?&gt;</code>

And in the view template you can call the meta HTML helper function to dynamticly add tags and descriptions to pages.
<code>$html-&gt;meta('keywords', 'keywords for the page goes here one two three', array('type' =&gt; 'keywords'), false);
$html-&gt;meta('description', 'The description of the page goes here, cakephp is cool', array('type' =&gt; 'description'), false);</code>

<strong>Source</strong>: <a href="http://book.cakephp.org/view/206/Inserting-Well-Formatted-elements">http://book.cakephp.org/view/206/Inserting-Well-Formatted-elements</a>
