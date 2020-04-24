---
layout: single
title: What are mysql-bin.000001, mysql-bin.000002...
date: 2010-05-28 10:47
categories: mysql Tips Development
---
By default whenever you make a change to a <a href="http://www.mysql.com/">MySQL </a>database it creates a log of the query and stores it in a file simlare to 'mysql-bin.000001' . The MySQL database does this so that you can <a href="http://dev.mysql.com/tech-resources/articles/recovering-from-crashes.html">recover</a> or <a href="http://dev.mysql.com/doc/refman/5.0/en/replication.html">replicate a database</a>. Most applications this is a good things to have enabled just like doing regular backups.

If you want to disable MySQL from creating these binary logs
<ol>
	<li>Open "my.ini"</li>
	<li>Search for this line "<em>log-bin=mysql-bin</em>"</li>
	<li>Comment this line out "<em><strong><span style="color: #ff0000;">#</span></strong> log-bin=mysql-bin</em>"</li>
	<li>Save and restart the MySQL database</li>
</ol>
You can now safely delete these files from that directory.

For more information see <a href="http://dev.mysql.com/doc/refman/5.0/en/binary-log.html">Binary logs</a> in the <a href="dev.mysql.com">MySQL documentation</a>
