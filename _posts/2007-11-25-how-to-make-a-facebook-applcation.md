---
layout: single
title: How to make a facebook applcation.
date: 2007-11-25 18:02
categories: Development
---
We are going to build a simple <a href="http://www.facebook.com/">facebook</a> application to demonstrate how to use the Facebook API.

<strong>Requirements:</strong>
<ul>
	<li>Basic knowledge of <a href="http://www.php.net/">php</a></li>
	<li>A webserver running php5 that is open to the internet.</li>
	<li>A facebook account (<a href="https://www.facebook.com/r.php">sign up</a>)</li>
</ul>
<strong>Directions</strong>
<ol>
	<li>Add the developers application to your facebook account.
Goto: <a href="http://www.facebook.com/developers/">http://www.facebook.com/developers/</a> and add the developers application to your account.
<img src="/public/uploads/2007/11/adddevlopers.png" />After you sugsefuly add the devlopers application you should see the devlopers icon on the left sidebar.
<img src="/public/uploads/2007/11/adddevlopers2.png" /></li>
	<li>Create a new application
Goto: <a href="http://www.facebook.com/developers/editapp.php?new">http://www.facebook.com/developers/editapp.php?new</a>
<ol>
	<li>Application Name: for our app, we put 'Comp1920 Application'</li>
	<li>Check the Terms of service box.</li>
	<li>Click on the Optional Fields link - this will bring up more options.</li>
	<li>Support E-mail: your Facebook contact email may be filled in automatically, but you might not want to give out your personal email to everyone who adds your app! You do have to put a valid email address that you can check, however.</li>
	<li>Callback Url: for our app, we put 'http://www.abluestar.com/dev/facebook/' - you should put something DIFFERENT - in particular, you should put the url of the directory on your server where you will create your application.</li>
	<li>Canvas Page URL: http://apps.facebook.com/: for our app, we put 'comp1920tutorialapp' - you must put in a different name.</li>
	<li>Use Iframe: keep this setting.</li>
	<li>Application Type: leave this set to 'Website'.</li>
	<li>Can your application be added to Facebook: set to 'yes' - this will bring up more options.</li>
	<li>TOS URL: you can leave this blank.</li>
	<li>Post-Add Url: for our app, we put 'http://apps.facebook.com/comp1920tutorialapp/' -- you should put something DIFFERENT - in particular, you should put your full canvas page url.</li>
	<li>Default FBML: type in the text 'hello'.</li>
	<li>Leave everything else under Installation Options blank.</li>
	<li>Side Nav Url: for our app, we put 'http://apps.facebook.com/comp1920tutorialapp/' -- you should put something DIFFERENT - in particular, you should put your canvas page url here as well.</li>
	<li>Leave everything else under Integration Points blank.</li>
</ol>
All the fields are described in detail on the <a href="http://developers.facebook.com/documentation.php">Facebook documentations wiki</a>.

<img src="/public/uploads/2007/11/popfriends.png" />

We have created out first Facebook application.
People will be able to add this application to there accounts but it will not do anything just yet.</li>
	<li>Download the Facebook php5 API
GoTo: <a href="http://developers.facebook.com/resources.php">http://developers.facebook.com/resources.php</a>
Extract it to a folder on your local computer.</li>
	<li>Create a basic Facebook Application with the Facebook php5 API
<ol>
	<li>Download and edit Step1.php with your faviorite php editor. (I suggest and use <a href="http://notepad-plus.sourceforge.net/uk/site.htm">notepad++</a>)<code></code>// Include the Facebook php API
// The API can be downloaded from facebook's website. http://developers.facebook.com/resources.php
require_once 'facebook.php';// These are settings that are given to you when you register your applcation.
// ToDo: Change these setting to match the ones found on your
//		 My Applcation page http://www.facebook.com/developers/apps.php
$appapikey = '[your api_key]';
$appsecret = '[your secret]';

// Create an instance of the facebook class.
$facebook = new Facebook($appapikey, $appsecret);

// attempt to log in to facebook
// We will attemp to log in as the current user,
$user = $facebook-&gt;require_login();

// The call back url for all internal links on this page.
$appcallbackurl = 'http://www.abluestar.com/dev/facebook/';

// catch the exception that gets thrown if the cookie has an invalid session_key in it
try {
if (!$facebook-&gt;api_client-&gt;users_isAppAdded()) {
$facebook-&gt;redirect($facebook-&gt;get_add_url());
}
} catch (Exception $ex) {
// this will clear cookies for your application and
// redirect them to a login prompt
$facebook-&gt;set_user(null, null);
$facebook-&gt;redirect($appcallbackurl);
die( "can not load facebook class" );
}

// Print the users number.
echo "hello $user";</li>
</ol>
</li>
	<li>Upload the Facebook API and step1.php to your webserver.</li>
	<li>Add the application to your own Facebook account to test it.
Goto your applications Canvas page: <a href="http://apps.facebook.com/comp1920tutorialapp/">http://apps.facebook.com/comp1920tutorialapp/</a>
Add your application to your Facebook account.
<img src="/public/uploads/2007/11/addapplcation.png" /></li>
	<li>Browse to your applications page
Goto your applications Canvas page: <a href="http://apps.facebook.com/comp1920tutorialapp/">http://apps.facebook.com/comp1920tutorialapp/</a>
<img src="/public/uploads/2007/11/done.png" /></li>
</ol>
You have made your first working Facebook Application.
In the next article we will be adding some functionality to the application to make it useful and describing how it all works.
