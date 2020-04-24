---
layout: single
title: Cakephp - Using the same view for multiple controler functions 
date: 2009-11-19 12:05
categories: Development
tags: cakephp controler php render snippit template Development
---
<strong>Question:</strong>
I have a Cakephp project the controller has several different methods.

<code>function Index()
function IndexAuthor()</code>

And I want to use the same 'view' (or template, Index.ctp) for both of the methods of the control.

<strong>Answer:</strong>

You're looking for <a href="http://book.cakephp.org/view/428/render">Controller::render()</a>.
<code>function IndexAuthor() {
$this-&gt;autoRender = false ;
$this-&gt;render('/stories/admin_index');
}</code>

Source: <a href="http://stackoverflow.com/questions/1753585/cakephp-same-view-for-multiple-functions">http://stackoverflow.com/questions/1753585/cakephp-same-view-for-multiple-functions</a>
