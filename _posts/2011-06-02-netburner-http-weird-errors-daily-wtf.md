---
layout: single
title: Netburner http weird errors - Daily WTF
date: 2011-06-02 11:33
categories: Development Rants
---
<strong>Daily WTF</strong>

<a href="/public/uploads/2011/06/netburner-logo.gif"><img class="alignright size-full wp-image-1505" title="netburner-logo" src="/public/uploads/2011/06/netburner-logo.gif" alt="" width="200" height="93" /></a>I got these weird errors while attempting to compile a Netburner project with NbEclipse. The project included the HTTP driver as well as some custom generated pages. After bashing my head against the wall for an hour I figure out what caused these errors. Because the HTTP driver has been loaded you are required to have a file in the <em>/http/index.html</em> folder to get NbEclipse to compile.
<blockquote>C:\dev\nburn\lib\NetBurner.a(httpinternal.o): In function `BaseDoHead':
C:\release\nburn\system/httpinternal.cpp:431: undefined reference to `default_page'
C:\dev\nburn\lib\NetBurner.a(httpinternal.o): In function `BaseDoGet':
C:\release\nburn\system/httpinternal.cpp:395: undefined reference to `default_page'
C:\dev\nburn\lib\NetBurner.a(htmldecomp.o): In function `SendHtml(int, char*, int, char const*)':
C:\release\nburn\system/htmldecomp.cpp:176: undefined reference to `html_table'
C:\release\nburn\system/htmldecomp.cpp:180: undefined reference to `html_table'
C:\dev\nburn\lib\NetBurner.a(htmldecomp.o): In function `GetRecordFromName(char*)':
C:\release\nburn\system/htmldecomp.cpp:88: undefined reference to `file_record'
C:\dev\nburn\lib\NetBurner.a(htmldecomp.o): In function `SendHtml(int, char*, int, char const*)':
C:\release\nburn\system/htmldecomp.cpp:143: undefined reference to `DoHtmlFunction(int, char const*, unsigned short)'
C:\dev\nburn\lib\NetBurner.a(htmldecomp.o): In function `GetRecordFromName(char*)':
C:\release\nburn\system/htmldecomp.cpp:86: undefined reference to `n_file_record'
C:\release\nburn\system/htmldecomp.cpp:95: undefined reference to `file_record'
C:\release\nburn\system/htmldecomp.cpp:86: undefined reference to `file_record'
C:\release\nburn\system/htmldecomp.cpp:95: undefined reference to `file_record'</blockquote>
