---
layout: single
title: NiceDog nano php web framework
date: 2012-07-28 02:01
categories: Development
tags: code coding frameworks php Tips web Development webdev
---
Last week I started on a simple web app that only has three pages. After I got the prototype working I wanted to clean up the code and switch over to using a more robust framework. Normally I would use something like <a href="http://cakephp.org/">CakePHP</a> (PHP MVC framework). But since this web app is so small and didn't need all the extra power that CakePHP provided I decided the CakePHP is probably overkill. I did a quick google search and found a nano php web framework called <a href="https://github.com/bastos/nicedog">NiceDog</a>. Its a single file, very light, framework similar to <a href="http://webpy.org/">web.py</a> for python.

After playing around with the source code for a while I found a few bugs with the system. The tutorial also didn't include a example project to download and try out. So I fixed some of the bugs and created the example code.

<a href="/public/uploads/2012/07/nicedog_20120728_024604.zip">nicedog_update</a>

<strong>NiceDog nano php web framework example code. </strong>
<pre>&lt;?php
/**
* Created by: Steven Smethurst
* Created on: 28 July 2012
*
* A example file for NiceDog php nano web framework found https://github.com/bastos/nicedog
*/
require 'NiceDog.php';
R('')-&gt;controller('Test')-&gt;action('index')-&gt;on('GET');
R('foo')-&gt;controller('Test')-&gt;action('update')-&gt;on('GET');
R('tag/(?P&lt;tag&gt;[-\w]+)')-&gt;controller('Test')-&gt;action('p_tag')-&gt;on('GET');

class Test extends C{

public function index(){
echo 'Hello world';
}
public function foo(){
echo "bar";
}
public function p_tag($tag){
$this-&gt;tag = $tag;
echo $this-&gt;render('views/index.php');
}
}

// This is the error page.
function r404() {
echo "Error: 404 Page not found";
}

run();
?&gt;</pre>
In the end I decided against using this framework as it has obviously not been toughly tested enough for production and the lack of support from the community.
