---
layout: single
title: Javascript redirect when device has restarted 
date: 2011-09-20 12:45
categories: Uncategorized
---
Over the past few months I have been building a sensor device with a embedded webserver for configuration and reporting. When a user saves a configuration to the device the device needs to be restarted before the changes come in to effect.

While the device is restarting the webserver is unreachable and the users get a blank page or 404 pages, this is bad for the users. So I created this simple script to check to see if the device has been restarted correctly then redirect the users to the correct page. This script uses <a href="http://jquery.com/">JQuery</a>

Script: <a href="/public/uploads/2011/09/refresh.txt">Redirect on reboot</a>
<code></code>
<pre>&lt;script type="text/javascript"&gt;
		function UrlExists(url) {
			var http = new XMLHttpRequest();
			http.open('HEAD', url, false);
			http.send();
			return http.status!=404;
		}

		var checkCount = 0 ; 

		function CheckServerUp(){
			checkCount++; 
			$('#status').text('Checking. ' + checkCount ) ;			
			if( checkCount &gt; 30 ) {
				$('#Error').html('The device is taking a long time to reboot, &lt;a href="/refresh2.htm"&gt;Click here to continue&lt;/a&gt;' + checkCount ) ;
			}

			if( UrlExists( "refresh2.htm" ) ) {
				$('#status').text('Device running, redirecting...') ; 
				window.location.replace( "/refresh2.htm" );				
			}
		};

		$(document).ready(function(){
			setInterval( "CheckServerUp()", 1000 );			
		});
	&lt;/script&gt;</pre>
&nbsp;
