---
layout: single
title: Host gator has bad security and sucks.
date: 2012-08-29 21:56
categories: Rants
tags: hosting passwords rant Rants security support Development webdev
---
I had a bad experience with <a href="http://www.hostgator.com/">HostGator</a> the other day. I had forgot the password to HostGators billing system and went though their password recovery function. The password recovery system emailed me my password in plain text instead of a link to reset the password.

This means that HostGator stores its users passwords as plain text in their database instead of using a <a href="http://en.wikipedia.org/wiki/Salt_(cryptography)">salted hash</a> (The standard practice on the web today) . This also means that If/When Hostgator gets hacked like so many other secure companies have in the past and their user database gets stolen. The hackers will have access to your password, username, and billing information. All the information that they will need to attempt to log in to other systems or charge your account with purchases that you did not make.

I contacted HostGator's support and had the following conversation with them <a href="/public/uploads/2012/08/hostgator_chat.txt">Hostgator_chat</a>. Leaving me even more concerned as they know about the problem and choose not to fix it.

After searching HostGator's own site I found this page <a href="http://support.hostgator.com/articles/pre-sales-policies/security-abuse/how-can-i-prevent-hacking">How can I prevent hacking?</a> where HostGator suggests to its own users that they don't store passwords as plain text.
<blockquote>"Don't write down your passwords or <strong>save them in a plain text</strong> file."</blockquote>
I highly suggest that you use a <a href="https://www.grc.com/passwords.htm">random password generator</a> when assigning a password to your HostGator Billing account. Sooner or later they will get hacked and your password will be in the hands of some criminals.
