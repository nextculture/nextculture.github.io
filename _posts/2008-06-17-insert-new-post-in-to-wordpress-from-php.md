---
layout: single
title: Insert new post in to wordpress from php
date: 2008-06-17 22:52
categories: Tips Development
---
This code snippet should let you add a new post to your wordpress database 2.5.1 

<code>require_once('wp-config.php');

//&nbsp;create&nbsp;post&nbsp;object
class&nbsp;wm_mypost&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;var&nbsp;$post_title;
&nbsp;&nbsp;&nbsp;&nbsp;var&nbsp;$post_content;
&nbsp;&nbsp;&nbsp;&nbsp;var&nbsp;$post_status;&nbsp;&nbsp;&nbsp;&nbsp;/*&nbsp;publish,&nbsp;private&nbsp;*/
&nbsp;&nbsp;&nbsp;&nbsp;var&nbsp;$post_author;&nbsp;&nbsp;&nbsp;&nbsp;/*&nbsp;author&nbsp;user&nbsp;id&nbsp;(optional)&nbsp;*/
&nbsp;&nbsp;&nbsp;&nbsp;var&nbsp;$post_name;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/*&nbsp;slug&nbsp;(optional)&nbsp;*/
&nbsp;&nbsp;&nbsp;&nbsp;var&nbsp;$post_type;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/*&nbsp;'page'&nbsp;or&nbsp;'post'&nbsp;(optional,&nbsp;defaults&nbsp;to&nbsp;'post')&nbsp;*/
&nbsp;&nbsp;&nbsp;&nbsp;var&nbsp;$comment_status;&nbsp;/*&nbsp;open&nbsp;or&nbsp;closed&nbsp;for&nbsp;commenting&nbsp;(optional)&nbsp;*/
&nbsp;&nbsp;&nbsp;&nbsp;var&nbsp;$post_category&nbsp;;&nbsp;
}

//&nbsp;initialize&nbsp;post&nbsp;object
$wm_mypost&nbsp;=&nbsp;new&nbsp;wm_mypost();
$wm_mypost->post_title&nbsp;&nbsp;&nbsp;&nbsp;=&nbsp;&quot;Title2&nbsp;&quot;.&nbsp;date(&nbsp;'r'&nbsp;);
$wm_mypost->post_content&nbsp;&nbsp;=&nbsp;&quot;content3&quot;;
$wm_mypost->post_status&nbsp;&nbsp;&nbsp;=&nbsp;'publish';&nbsp;
$wm_mypost->post_author&nbsp;&nbsp;&nbsp;=&nbsp;1;

//&nbsp;Catagorys
$post_category&nbsp;=&nbsp;split(&quot;,&quot;&nbsp;,&nbsp;&quot;one&quot;);
foreach($post_category&nbsp;as&nbsp;$key=>$val)&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;$post_category[$key]&nbsp;=&nbsp;get_cat_ID($val);
}
$wm_mypost->post_category&nbsp;=&nbsp;&nbsp;$post_category&nbsp;;&nbsp;

//&nbsp;Optional;&nbsp;uncomment&nbsp;as&nbsp;needed
//&nbsp;$wm_mypost->post_type&nbsp;=&nbsp;'page';
//&nbsp;$wm_mypost->comment_status&nbsp;=&nbsp;'closed';

//&nbsp;feed&nbsp;object&nbsp;to&nbsp;wp_insert_post
$post_ID&nbsp;=&nbsp;wp_insert_post($wm_mypost);
echo&nbsp;date(&nbsp;'r'&nbsp;)&nbsp;.&nbsp;&quot;\n&quot;;
echo&nbsp;&quot;post_ID:&quot;.&nbsp;$post_ID&nbsp;.&nbsp;&quot;\n&quot;;&nbsp;</code>
