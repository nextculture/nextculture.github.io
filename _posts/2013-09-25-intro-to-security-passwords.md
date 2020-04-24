---
layout: single
title: Intro to Security, Passwords 
date: 2013-09-25 21:20
categories: Uncategorized
---
<h1>Passwords</h1>
<strong>Long passwords</strong>
Longer passwords are better than random shorter passwords. The more entropy the more attempts a brute force attack will have to do to crack your password.
<ul>
	<li>Comic <a href="http://xkcd.com/936/">http://xkcd.com/936/</a></li>
	<li>Password brute force attack <a href="https://www.grc.com/haystack.htm">https://www.grc.com/haystack.htm</a></li>
</ul>
Some websites limit the size of your password (such as banks). This is bad because either they are storing your password as plain text or they are using outdated password rules.

<strong>Multi-factor authentication is awesome</strong>

Multi-factor authentication (also MFA, Two-factor authentication, TFA, T-FA or 2FA) is an approach to authentication which requires the presentation of two or more of the three authentication factors: a knowledge factor ("something only the user knows"), a possession factor ("something only the user has"), and an inheritance factor ("something only the user is"). After presentation, each factor must be validated by the other party for authentication to occur. Source: <a href="http://en.wikipedia.org/wiki/Multi-factor_authentication">http://en.wikipedia.org/wiki/Multi-factor_authentication</a>

Examples of knowledge factors are: passwords, pins, patterns
Examples of possession factor are: Atm card, cell phone (sms messages, google authenticator), usb sticks (yubikey), Smartcards, etc€¦
Examples of inference factors are: Biometrics

An ATM machine uses two factor authentication. It uses your ATM pin code (knowledge) as well as your ATM card (possession).

<strong>Different passwords on each site</strong>
You should use a different password for each and every site you use. If you use the same password on two or more sites and one of these sites get compromised, a bad guy could use your password to log in to other websites where you use the same password.

Remembering all of these different passwords on 100s of different sites is impossible. You will need a password database or a password hashing scheme.

<strong>Password hashing scheme</strong> (Less secure, not reliant on technology)
This is not secure and if possible you shouldn&quot;t do this but it is easy.

Take something about the website that is constant, like the domain name. Alter the constant, and add some salt to it. This will give you a random password for every web site but if the bad guy get a hold of your password they may be able to figure out your password scheme and use it to log in to other sites.
<ul>
	<li>You could take the first three letters of the domain of the website and add the last three letters of the domain then increment all the letters by one, then add 123 to the end.</li>
	<li>Take the domain of the website add a constant word to the end and hashing it with some salt.</li>
</ul>
<strong>Password databases</strong> (much more secure, pretty easy, use this one)
This is the best way of storing your passwords. Basically its a database of all your passwords encrypted under one master password. You can generate a different random password for each and every site you visit and you don&quot;t have to remember them.

I use Last pass (<a href="https://lastpass.com/">https://lastpass.com/</a>) as my preferred password database. It comes with a browser plug in can automatically record passwords as you type them in (an option). Its can generate good random password with any length as you create accounts on new websites. It can work off line as well as on line so you can access it from remote computers. The company that runs Lastpass can not decode your database even under subpoena. Its truly TNO (Trust no one). They also support one time passwords, Multi-factor authentication, as well as many other interesting features. Its a commercial application but has an unlimited free version and they provide documentation on their entire process. These people do it right.

Other password interesting information on passwords.
<ul>
	<li>A MD5 password lookup table <a href="http://www.tobtu.com/leaderborder.php">http://www.tobtu.com/leaderborder.php</a></li>
	<li>A MD5 encoder <a href="http://www.miraclesalad.com/webtools/md5.php">http://www.miraclesalad.com/webtools/md5.php</a></li>
</ul>
Password brute force attack <a href="https://www.grc.com/haystack.htm">https://www.grc.com/haystack.htm</a>
