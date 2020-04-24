---
layout: single
title: How to install PHPBB 3.0.1
date: 2008-06-05 22:36
categories: Development
---
This tutorial will walk you thou the steps to install <a href="http://www.phpbb.com/">PHPBB3</a> on your system.

<strong>Intro </strong>

<a href="http://www.phpbb.com/">PHPBB3</a> has become one of the more popular <a href="http://en.wikipedia.org/wiki/Comparison_of_Internet_forum_software_(PHP)">bulletin board system</a> (AKA, <a href="http://en.wikipedia.org/wiki/Bulletin_board_system">BBS</a>, or forums) available. It is used for all types of websites, from <a href="http://www.chipkin.com/forums/">corporate websites</a>, online stores, <a href="http://forum.hackedgadgets.com/">online hobby groups</a>, ect.  One of the <a href="http://www.phpbb.com/about/features/">main selling points</a> for many people that use PHPBB is the strong <a href="http://www.phpbb.com/community/">community of developers</a> developing <a href="http://www.phpbb.com/mods/">mods</a> and <a href="http://www.phpbb.com/styles/">themes</a>. PHPBB is an <a href="http://en.wikipedia.org/wiki/Open_source">open source</a> project released under (<a href="http://www.gnu.org/licenses/gpl.html">General Public License</a>) that started in 2000 by <a href="http://en.wikipedia.org/wiki/James_Atkinson_%28software_developer%29">James Atkinson</a> (now a former team member) has come a long way in the last 8 years. As PHPBB grew and became more popular and as its install base reached over 100,000 sites, it started getting targeted by <a href="http://en.wikipedia.org/wiki/Hacker">hackers</a> and <a href="http://en.wikipedia.org/wiki/Script_kiddie">script kiddies</a>. Forums would be filled with <a href="http://en.wikipedia.org/wiki/Spam_in_blogs">spam comments</a>, <a href="http://en.wikipedia.org/wiki/Adult_Web_Movie_Database">links to porn/adult sites</a>, and people trying to sell <a href="http://en.wikipedia.org/wiki/Viagra">perscription medication</a> it turned a lot of people away from PHPBB on to <a href="http://getvanilla.com/">other forum systems</a>. The newer versions of PHPBB2 and PHPBB3 made spam and <a href="http://recaptcha.net/">robot prevention</a> a major concern and the exploits that allow robots and script kiddies to make new posts have been reduced significantly.

<strong>Requirements </strong>(<a href="http://www.phpbb.com/support/documentation/3.0/quickstart/quick_requirements.php">^</a>)<strong>
</strong>
<ul>
	<li>A webserver that supports <a href="http://www.php.net/">PHP</a> ( <a href="http://www.apache.org/">apache.org</a>, <a href="http://www.lighttpd.net/">lighttpd.net</a>, ect )</li>
	<li>SQL database ( <a href="http://www.mysql.com/">mysql.com</a>, <a href="http://www.sqlite.org">sqlite.org</a> )</li>
	<li><a href="http://www.php.net/">PHP 4.3.3</a> or above</li>
</ul>
For this tutorial we will be use a <a href="http://www.apache.org/">apache.org</a> on a UNIX based web server hosted on <a href="http://www.dreamhost.com/r.cgi?78455">dreamhost.com</a> using <a href="http://www.mysql.com/">mysql.com</a> for the database.

<strong>Directions</strong>

1) Download the <a href="http://www.phpbb.com/downloads/">latest stable version of PHPBB</a> (We are using PHPBB3.0.1)
2) Extract the archive to your desktop, preserving the file tree. (C:\temp\PHPBB3)
3) Upload the contents of the archive to your web server. (/abluestar.com/temp/phpBB3/)
4) Browse to the installation page

<a href="/public/uploads/2008/06/screenshot-introduction-mozilla-firefox-3-beta-5.png"><img class="alignnone size-medium wp-image-432" title="screenshot-introduction" src="/public/uploads/2008/06/screenshot-introduction-mozilla-firefox-3-beta-5-300x170.png" alt="" width="300" height="170" /></a>

5) Click the install tab at the top of the page. Then click the "
Proceed to next step" button.

<a href="/public/uploads/2008/06/screenshot-introduction-mozilla-firefox-3-beta-5-1.png"><img class="alignnone size-medium wp-image-433" title="screenshot-introduction-mozilla-firefox-3-beta-5-1" src="/public/uploads/2008/06/screenshot-introduction-mozilla-firefox-3-beta-5-1-300x187.png" alt="" width="300" height="187" /></a>

6) On this page your system will be checked for the basic requirements.

<a href="/public/uploads/2008/06/screenshot-requirements-mozilla-firefox-3-beta-5.png"><img class="alignnone size-medium wp-image-434" title="screenshot-requirements-mozilla-firefox-3-beta-5" src="/public/uploads/2008/06/screenshot-requirements-mozilla-firefox-3-beta-5-300x187.png" alt="" width="300" height="187" /></a>

7) Enter your database settings

<a href="/public/uploads/2008/06/screenshot-mysql.png"><img class="alignnone size-medium wp-image-436" title="screenshot-mysql" src="/public/uploads/2008/06/screenshot-mysql-300x211.png" alt="" width="300" height="211" /></a>

8 ) Set up the boards administrative user

<a href="/public/uploads/2008/06/screenshot-administrator-details-mozilla-firefox-3-beta-5.png"><img class="alignnone size-medium wp-image-437" title="screenshot-administrator-details-mozilla-firefox-3-beta-5" src="/public/uploads/2008/06/screenshot-administrator-details-mozilla-firefox-3-beta-5-300x187.png" alt="" width="300" height="187" /></a>

9) Set Advanced settings. Most of these settings can be left as there defaults or changed later.

<a href="/public/uploads/2008/06/screenshot-advanced-settings-mozilla-firefox-3-beta-5.png"><img class="alignnone size-medium wp-image-438" title="screenshot-advanced-settings-mozilla-firefox-3-beta-5" src="/public/uploads/2008/06/screenshot-advanced-settings-mozilla-firefox-3-beta-5-300x187.png" alt="" width="300" height="187" /></a>

10) Create database tables. This page creates the nessary tables on your database for the forum system to store your settings.

<a href="/public/uploads/2008/06/screenshot-create-database-tables-mozilla-firefox-3-beta-5.png"><img class="alignnone size-medium wp-image-439" title="screenshot-create-database-tables-mozilla-firefox-3-beta-5" src="/public/uploads/2008/06/screenshot-create-database-tables-mozilla-firefox-3-beta-5-300x187.png" alt="" width="300" height="187" /></a>

11) Final stage, this is just a conformation page that everything has been installed correctly. You can now browse to the install directory.

12) Main page. At this stage you should delete the /install/ directory from the PHPBB3 folder.

<a href="/public/uploads/2008/06/screenshot-yourdomaincom-gco-information-mozilla-firefox-3-beta-5.png"><img class="alignnone size-medium wp-image-440" title="screenshot-yourdomaincom-gco-information-mozilla-firefox-3-beta-5" src="/public/uploads/2008/06/screenshot-yourdomaincom-gco-information-mozilla-firefox-3-beta-5-300x170.png" alt="" width="300" height="170" /></a>

13) At this point you can log in to your forums adminitation panle and configure your forums to suit your needs, but this beyond the scope of this tutorial.

<a href="/public/uploads/2008/06/screenshot-yourdomaincom-gco-user-control-panel-gco-front-page-mozilla-firefox-3-beta-5.png"><img class="alignnone size-medium wp-image-441" title="screenshot-yourdomaincom-gco-user-control-panel-gco-front-page-mozilla-firefox-3-beta-5" src="/public/uploads/2008/06/screenshot-yourdomaincom-gco-user-control-panel-gco-front-page-mozilla-firefox-3-beta-5-300x187.png" alt="" width="300" height="187" /></a>

This tutorial was written for COMP2920, Steven Smethurst, B.J. Wilson, Dennis Warren 
