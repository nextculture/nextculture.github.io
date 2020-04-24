---
layout: single
title: How to access Facebook's data
date: 2007-11-25 20:47
categories: Development
---
In my last article I talked about how to create <a href="/how-to-make-a-facebook-applcation/">a very simple Facebook Application</a>.
We created a simple hello world application that didn't do too much besides login to the Facebook API.

In this article we are going to use the Facebook API to access you and your friends information.
We are then going to display the information a different manner then Facebook.

<strong>Requirements </strong>
<ul>
	<li>A <a href="https://www.facebook.com/r.php">Facebook account</a> with the <a href="http://www.facebook.com/developers/">developers application</a> added</li>
	<li>A <a href="/how-to-make-a-facebook-applcation/">Facebook application </a></li>
	<li>A PHP enabled web server with access to the internet.</li>
</ul>
The <a href="http://developers.facebook.com/documentation.php">Facebook API</a> is well documented.
If you want more information on any of the topics that I touch in this article is suggest that you search the Facebook API.

The Facebook API uses a <a href="http://en.wikipedia.org/wiki/Representational_State_Transfer">REST-based interface</a>. This means that Facebook method calls are made over the internet by sending HTTP GET or POST requests to the Facebook REST server.

The Facebook API has about a hundred different methods, in this tourial we will be using;
<ul>
	<li><a href="http://wiki.developers.facebook.com/index.php/Friends.get">friends.get</a> - Returns the identifiers of the current user's Facebook friends</li>
	<li><a href="http://wiki.developers.facebook.com/index.php/Friends.areFriends">friends.areFriends</a> - Returns whether or not each pair of specified users is friends with each other</li>
	<li><a href="http://wiki.developers.facebook.com/index.php/Users.getInfo">users.getInfo</a> - Returns a wide array of user-specific information for each user identifier passed, limited by the view of the current user</li>
</ul>
For a full list of all the different Facebook methods see the <a href="http://wiki.developers.facebook.com/index.php/API">Facebook API documentation</a>

<strong>Basic Application Architecture</strong>
First we need to understand how the Facebook API works.
<ol>
	<li>A browse makes a request
<ol>
	<li>A user browse to the Application canvas page
Example: <a href="http://apps.facebook.com/ninteentwenty/">http://apps.facebook.com/ninteentwenty/</a></li>
	<li>acebook looks at the call back URL associated with the application.
Example: <a href="http://www.abluestar.com/dev/facebook/">http://www.abluestar.com/dev/facebook/</a></li>
</ol>
</li>
	<li>Facebook sends a request for that call back page with the user's ID as a parameter</li>
	<li>Our webserver gets the request and builds a page for this user.
<ol>
	<li>In the process of building the response page, we can request additional information from Facebook REST server.</li>
</ol>
</li>
	<li>After the page has been built on our server its sent to Facebook</li>
	<li>Facebook serves our response to the user.</li>
</ol>
<img src="/public/uploads/2007/11/call-back.jpg" />

Most of the time the user doesn't know that a 3rd party (our server) was involved at all.
The page appears to come from Facebook its self and is embedded in to a page with an iframe.

<strong>Make a request using the Facebook API</strong>

When starting off a great place to start is the <a href="http://developers.facebook.com/tools.php">API Test Console</a>. It a tool for building requests for the Facebook Rest server.

You can select the method, call back function (most of the time left blank) and respond type (XML, PHP array, JSON).

For example if we where to select the <a href="http://wiki.developers.facebook.com/index.php/Friends.get">friends.get</a>  method and the a response type of XML.
It would query the Facebook server for a list of all the currents users friends and return the results in XML.

$friends = $facebook-&gt;api_client-&gt;friends_get();

<img src="/public/uploads/2007/11/friendsget.png" />

We could then take two of these UID (aka user IDs) and test to see if they are friends with the <a href="http://wiki.developers.facebook.com/index.php/Friends.areFriends">friends.areFriends</a> method.
In this case these two people are not friends with each other.

$friends_areFriends = $facebook-&gt;api_client-&gt;friends_areFriends( '508673161', '504464182' );

<img src="/public/uploads/2007/11/friendsarefriends.png" />

The UID is a great method for uniquely identify members but it would be nice to know who 508673161, and 504464182 are.
To do this we can use the method <a href="http://wiki.developers.facebook.com/index.php/Users.getInfo">users.getInfo</a> to get information about these users including there names.

$users_getInfo = $facebook-&gt;api_client-&gt;users_getInfo( '732945108', "name" );

<img src="/public/uploads/2007/11/usergetinfo.png" />

The test console is a great tool for testing out how methods work and how the response is formated.

Now we want to put all three of these functions together to create a application that lists all your friends common friend.
<a href="/public/uploads/2007/11/popfriends.txt">PopFriends.txt</a> demonstrates how to do this.
