---
layout: single
title: Your daily WTF
date: 2008-07-11 14:26
categories: Development Tips
---
I found this today while doing code review.

it was ment to be a sleep timer...
I just about shit a brick when I saw this.
<blockquote>
<pre>for(int i=0; i&lt;PAUSE_LENGTH; i++)
{
i++;
}</pre>
</blockquote>
