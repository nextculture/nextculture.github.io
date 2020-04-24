---
layout: single
title: RPXnow and Windows live ID, problems signing out
date: 2010-01-23 13:23
categories: Development
tags: Microsoft OpenID Rants RPXnow windows
---
<strong>The problem </strong>

I am using <a href="https://rpxnow.com/">RPXnow</a> to help simplify the OpenID login system on one of my sites <a href="http://www.everydayfiction.com/">EveryDayFiction.com</a>. It works great for all OpenID providers but <em><strong>Windows Live ID</strong></em>. The users can login with Windows Live ID but when they try to logout of Hotmail or MSN or anything else that uses Windows Live ID they get the following error messages.

Super scary to most users.

<a href="/public/uploads/2010/01/RPXnow_WindowsLifeID_Cantsignout.png"><img class="aligncenter size-full wp-image-856" title="RPXnow Windows Live ID Cant sign out" src="/public/uploads/2010/01/RPXnow_WindowsLifeID_Cantsignout.png" alt="" width="801" height="412" /></a>

After a few <em><strong>DAYS</strong>!</em> of trouble shooting I found this support issues on Google groups.
<a href="http://groups.google.com/group/rpx-developers/browse_thread/thread/3d0d1ffde84a4c4b/041b1830f4d68393?lnk=gst&amp;q=windows+live+id,+sign+out#041b1830f4d68393">http://groups.google.com/group/rpx-developers/browse_thread/thread/3d0d1ffde84a4c4b/041b1830f4d68393?lnk=gst&amp;q=windows+live+id,+sign+out#041b1830f4d68393</a>
<blockquote>Hi All,
Windows Live users are getting warnings whenever they sign out from Hotmail or Bing. The warnings state that Windows Live was unable to sign out of "https://login.getsatisfaction.com/liveid/return", as well as "https://signin.rpxnow.com/liveid/return".

Does RPX support the Windows Live signout protocol? It's documented  here:
http://msdn.microsoft.com/en-us/library/bb676640.aspx

Users are getting really confused and blaming us for not allowing them to log out of Hotmail.
Thanks!
christian.</blockquote>
With this response from RPXnow support.
<blockquote># Does RPX support the Windows Live signout protocol?
The short answer is, "no."
The long answer is that RPX can't support Windows Live signout, because in order to support it, the relying party site itself would  need to expose a sign-out API to RPX.  Otherwise, signout of RPX has no meaning; we cannot guarantee that the user is signed out of anything at all.
We get occasional direct messages from integrators about this problem, and it's very unfortunate.  We could fake it and support the sign-out by issuing the appropriate responses to Windows Live, but then we'd be violating the requirements of the document you mentioned.
I'm sorry I can't be more helpful!

--
Jonathan Daugherty
Software Engineer
JanRain, Inc.</blockquote>
So in other words there is no seamless solution to this problem if you are using RPXnow and Windows live ID.

All the user has to do is click '<strong><em>done</em></strong>' instead of '<strong><em>Try again</em></strong>' and they will be logout of Windows Live ID, but most users don't. Very frustrating, How does Microsoft expect people to start adopting OpenID if they add extra hoops for people to jump thou that are specific for there system.
