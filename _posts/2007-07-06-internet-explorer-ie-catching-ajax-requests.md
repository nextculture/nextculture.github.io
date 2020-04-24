---
layout: single
title: Internet explorer (IE) caching AJAX requests.
date: 2007-07-06 13:14
categories: Development  Projects  Development
---
The project was to create a status web page that showed the temperature of a room. The temperature of the room changes rapidly and I wanted the changes to appear on the page without my users having to click refresh every time they wanted an updated value.The ideal solution was AJAX.
I would use a bit of JavaScript to query anther page for the temperature of a room and refresh a div on the status page every n seconds.

It worked fine in FireFox and opera but when I tried it in Internet Explorer (IE) I found that the value never refreshed.
Example:  <a href="http://www.abluestar.com/dev/web/ajax/temperature/">http://www.abluestar.com/dev/web/ajax/temperature/</a>

It turns out that Internet explorer loves to cache everything even when it&quot;s told that the data has expired. IE is happy to shows you the catches version.

The first thing I tried was to set the Last-Modified, Date, Cache-Control headers so that it shouldn&quot;t cache anything. Of course Internet Explorer ignored these settings.

Then as a good internet enabled programmer I searched the internet for a solution and came across this page <a href="http://www.enja.org/david/?p=25">Ajax IE caching issue</a>. His solution was to use a POST instead of a GET to retrieve the data but it didn&quot;t work for me

After a bit of smashing my head up against the wall, cursing the devil that is internet explorer I finely found a working solution.
Added a parameter to the end of the URL with the time in Sec&quot;s

So instead of requesting <a href="http://www.abluestar.com/dev/web/ajax/temperature/value.php">value.php</a> I request <a href="http://www.abluestar.com/dev/web/ajax/temperature/value.php?ms=34908900">value.php?s=1828399595</a>. It worked flawlessly
Example:  <a href="http://www.abluestar.com/dev/web/ajax/temperature/index2.htm">http://www.abluestar.com/dev/web/ajax/temperature/index2.htm</a>

<code>
&lt;html&gt;
&lt;head&gt;
&lt;title&gt;Temperature&lt;/title&gt;
&lt;script type="text/javascript"&gt;
function GetXmlHttpObject() {
var objXMLHttp=null
if (window.XMLHttpRequest) {
objXMLHttp=new XMLHttpRequest()
} else if (window.ActiveXObject) {
objXMLHttp=new ActiveXObject("Microsoft.XMLHTTP")
}
return objXMLHttp
}
function RefreshData() {
// Get The value span
var value_span = document.getElementById("temperature_a") ;
if( value_span == null ) {
return ;
}
// Get XmlHttp Object
var xmlhttp=GetXmlHttpObject();
if (xmlhttp==null) {
alert ("Browser does not support HTTP Request")
return ;
}
// Create the request
xmlhttp.open("POST", "value.php" + "?ms=" + new Date().getTime() , true);
xmlhttp.onreadystatechange=function() {
if (xmlhttp.readyState==4) {
if( xmlhttp.status==200 ) {
value_span.innerHTML = xmlhttp.responseText ;
} else {
// Error
value_span.innerHTML = 'Error loading data. Error=' + xmlhttp.status ;
}
}
}
// Set the request
try {
xmlhttp.send(null);
}
catch (E) { }
// Set a timer to call this function again in 1 sec
timerID = self.setTimeout("RefreshData( );", 1000 )
}
&lt;/script&gt;
&lt;/head&gt;
&lt;body onload='RefreshData();' &gt;
&lt;strong&gt;Temperature:&lt;/strong&gt; &lt;span id='temperature_a'&gt;Loading&lt;/span&gt;
&lt;/body&gt;
&lt;/html&gt;
</code>
