---
layout: single
title: Troubleshooting CakePHP
date: 2009-03-10 15:39
categories: Development
tags: bug cakephp Development php Tips
---
<p>I&quot;m just starting to learn CakePHP 1.2 and I am running in to small little problems. As I find solutions I write them down so people after me might have an easier time finding them. </p>  <p><strong>Problem:</strong></p>  <blockquote>   <p>Warning (512): Method HtmlHelper::file does not exist      <br />Warning (512): Method HtmlHelper::submit does not exist </p> </blockquote>  <p><strong>Solution: </strong></p>  <p>Those methods have been moved to the FormHelper in Cake 1.2. So you have to add the FormHelper to the $helpers array of your controller, and to use $form instead of $html. But I am not sure whether you have to modify other things in this example to make it work with Cake 1.2. I have to test it myself.</p>  <p><strong>Example:</strong></p>  <blockquote>   <p>// Bad      <br />echo $html-&gt;file('File');       <br />echo $html-&gt;submit('Upload');</p>    <p>// Good      <br />echo $form-&gt;file('File');       <br />echo $form-&gt;submit('Upload');</p></blockquote>
