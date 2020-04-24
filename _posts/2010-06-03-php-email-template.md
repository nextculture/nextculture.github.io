---
layout: single
title: PHP email template
date: 2010-06-03 10:21
categories: Tips
tags: email php snippet template Tips
---
When I create a PHP script that has to send an email to a user I tend to use a template file for the body of the email. I load the template file in to the script then search and replace the variables that I need to before sending it to the user.

I use this template system for a few reasons.
<ul>
	<li>Easier to update in the future. I don't have to search thou all my scripts looking for the body of an email instead I can just update the template.</li>
	<li>I can use the same template for multiple emails</li>
	<li>It follows the <a href="http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller">MVC</a> pattern</li>
</ul>
One of my favorite PHP template engines is <a href="http://www.smarty.net/">http://www.smarty.net/</a> it just works. You can use it for both Email, Websites or what ever else you want. But it might be a little over kill when you want to just send one email using a template. Instead you could use something similar to this;

<code> </code>

<code> </code>

<code>
<pre><strong>SendEmail.php:</strong>
&lt;?php
$name = 'Mr Waterbottom';
$emailBody = file_get_contents( 'email_template.tpl' ) ;
$emailBody = str_replace( '__NAME__', $name, $emailBody );
// SentEmail( $email, "Email Subject", $emailBody );
echo "&lt;pre&gt;";
echo $emailBody ;
echo "&lt;/pre&gt;";
?&gt;</pre>
</code>
<pre><strong>email_template.tpl:
<span style="font-weight: normal;">Hello __NAME__</span>
<span style="font-weight: normal;">How are you doing?</span> </strong></pre>
