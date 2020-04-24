---
layout: single
title: Disable Windows low disk space warning
date: 2007-03-04 16:18
categories: Tips
---
I've had it up to my eyeballs with the nagging Windows low disk space warning and offers from my helpful operating system to clean up the <em>junk </em>I have lying around. If you have a drive or two that remains constantly on the edge of full for good reason, you probably share my sentiment.

I went looking for a solution, and I found a few. Most of them involved lengthy descriptions of how to navigate the registry <em>just </em>to add the "NoLowDiskSpaceChecks" key. Here's a much easier solution; one command line you can cut and paste into any open command prompt window.
<textarea style="width: 450px; height: 60px">regini HKEY_CURRENT_USERSoftwareMicrosoftWindowsCurrentVersionPoliciesExplorer "NoLowDiskSpaceChecks" = REG_DWORD</textarea>
