---
layout: single
title: The procedure entry point_except_handler4_common could not be located in the dynamic link library msvcrt.dll
date: 2008-07-22 11:57
categories: Development
---
<blockquote>The procedure entry point_except_handler4_common could not be located in the dynamic link library msvcrt.dll</blockquote>
This error is caused by a 3rd party utility or applcation overwriting your msvcrt.dll with a different version.

For example if a windows vista version of this DLL was copied on to a windows XP computer you would probably get this error.

A solution to this problem can be found in Microsofts KB
<a href="http://support.microsoft.com/kb/324762">http://support.microsoft.com/kb/324762</a>

<strong>[Edit]</strong> Charles Koontz solution seems to be helping a lot of people as well.
<blockquote><strong>Charles Koontz</strong>
If the problem appears after installing or upgrading the <em>Mozilla Firefox browser to version 3.5 (or later)</em> operating under <em>Windows XP</em>, the problem is due to a Windows Vista driver (dwmapi.dll) installed in a Windows XP OS at folder system32 by mistake (faulty install program).

Delete that dwmapi.dll file to fix the problem.

Thanks to users of the Mozilla Firefox support site.</blockquote>
