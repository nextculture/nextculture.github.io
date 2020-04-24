---
layout: single
title: CakePHP - Security.level
date: 2009-12-16 18:34
categories: Tips Development
---
I been having reports from my users that they are getting randomly logged out of my web applications. After much debugging I found that CakePHP regenerates the session on every request.
<blockquote>File: <em>core.php</em>
<code>/**
* The level of CakePHP security. The session timeout time defined
* in 'Session.timeout' is multiplied according to the settings here.
* Valid values:
*
* 'high'	Session timeout in 'Session.timeout' x 10
* 'medium'	Session timeout in 'Session.timeout' x 100
* 'low'	Session timeout in 'Session.timeout' x 300
*
* <strong>CakePHP session IDs are also regenerated between requests if
<span style="font-weight: normal;"> * </span>'Security.level' is set to 'high</strong>'.
*/
Configure::write('Security.level', 'high');</code></blockquote>
After changing the '<em>Security.level</em>' to <em>medium</em> the problem stopped happening.
