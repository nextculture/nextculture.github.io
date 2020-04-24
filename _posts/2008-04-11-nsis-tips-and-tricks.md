---
layout: single
title: NSIS - Tips 
date: 2008-04-11 10:39
categories: Development
tags: nsis programing scripts Tips windows
---
I create a lot of windows application to make things easier for my customers. The simple act of coping a file from an email to a certain directory can become the most complicated tasks for a certain type of customer.

I use an Scriptable Install System provided by <a href="http://www.nullsoft.com/">NullSoft</a> called <a href="http://nsis.sourceforge.net/Main_Page">NSIS </a>(Nullsoft Scriptable Install System). Ita great system that just plain works. Its free, open source, and can be used for <a href="http://nsis.sourceforge.net/License">commercial products</a>, Great plugin system, Dead simple for simple things, <a href="http://nsis.sourceforge.net/Features">ect</a>.

The <a href="http://nsis.sourceforge.net/Docs/Contents.html">manual</a> has lots of examples and function documentation to help <a href="http://nsis.sourceforge.net/Download">get you started</a>.

Over the last few years of using this program I have created a library of useful little snippets of code. Free free to comment with your own.

<strong>Opening a directory</strong>
<blockquote>ExecShell "open" '"$INSTDIR"'
BringToFront</blockquote>
<strong>Registering/unregistering personal ActiveX files</strong>
<blockquote>UnRegDLL "$SYSDIR\spin32.ocx"
RegDLL "$SYSDIR\spin32.ocx"</blockquote>
<strong>Checking if a process is running</strong>
This uses the <a href="http://forums.winamp.com/showthread.php?threadid=181974">FindProcDLL::FindProc</a> plug-in (<a href="http://nsis.sourceforge.net/archive/viewpage.php?pageid=483">here</a> also):
<blockquote>StrCpy $1 "mybin.exe"
FindProcDLL::FindProc "$1"
;0   = Process was not found
;1   = Process was found
;605 = Unable to search for process
;606 = Unable to identify system type
;607 = Unsupported OS
;632 = Process name is invalid
StrCmp $R0 0 0 error
File "mybin.exe" ; Can't use a variable
Goto end
error:
MessageBox MB_OK|MB_ICONSTOP "The application $1 is currently running. Press CTRL-ALT-DEL to display the list of running processes."
Quit
end:</blockquote>
