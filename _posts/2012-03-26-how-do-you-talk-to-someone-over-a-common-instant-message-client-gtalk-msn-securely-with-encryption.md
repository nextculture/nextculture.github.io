---
layout: single
title: How do you talk to someone over a common, instant message client (Gtalk, MSN) securely, with encryption
date: 2012-03-26 11:11
categories: Development
tags: crypto Development faq, GTalk IM Interesting security VHS
---
<a href="/public/uploads/2012/03/Encrypt_all_the_things.png"><img class="alignright size-medium wp-image-2766" title="Encrypt_all_the_things" src="/public/uploads/2012/03/Encrypt_all_the_things-300x269.png" alt="" width="300" height="269" /></a>How do you talk to someone over a common, instant message (IM) client (gtalk, MSN, ect..) securely, with encryption. This was my question when I went to the <a href="https://vancouver.hackspace.ca/wp/2012/03/01/practical-intro-to-computer-security-thursday-22nd-march-2012/">Practical intro to computer security</a> at <a href="https://vancouver.hackspace.ca">Vancouver Hackspace</a>.

<a href="http://www.cypherpunks.ca/otr/">Off the record</a> (OTR) is a plugin for most IM clients that sets up a secure connection between two computers that you can use to ensure that no one else is listing in and that you are talking to the person you intend to. The problem is that there is no OTR plugin for my perfered IM client <a href="http://www.digsby.com/">Digsby</a>. Infact there are not a lot of clients that support the OTR plug-ins. The OTR people do provide a tool kit to devlope plug-ins for other clients but thats a lot of work. <a href="/public/uploads/2012/03/PidginPortable_128.png"><img class="alignright size-full wp-image-2754" title="PidginPortable_128" src="/public/uploads/2012/03/PidginPortable_128.png" alt="" width="128" height="128" /></a>

The ORT developers suggest <a href="http://www.pidgin.im/">Pidgin</a>. A cross platform, multi protocol (MSN, GTalk, Jabber, ect..), opensource, Free, IM client that can <a href="http://portableapps.com/apps/internet/pidgin_portable">run without being installed</a>. I have looked at Pidgin before but i didn't like it as it was too plain for me. This talk gave me the opportunity to look deeper in to this application and I found that its is has <a href="http://developer.pidgin.im/wiki/ThirdPartyPlugins">many plugins</a> and themes for it that make it much more usable.

<strong>Instructions </strong>
<ol>
	<li><a href="/public/uploads/2012/03/ORT.png"><img class="alignright size-medium wp-image-2755" title="ORT" src="/public/uploads/2012/03/ORT-247x300.png" alt="" width="247" height="300" /></a>Download and install <a href="http://pidgin.im/">Pidgin </a></li>
	<li>Download and install the <a href="http://www.cypherpunks.ca/otr/index.php">OTR plugin</a></li>
	<li>Start Pidgin, from tools menu select "plugins"</li>
	<li>Select the Off The Record "OTR" plugin from the menu and click configure.</li>
	<li>Select a account on the Off the record configuration dialog and click the "Generate" button.</li>
	<li>Start a conversation with a friend that has the OTR plugin installed. You should see a new button called <a href="/public/uploads/2012/03/no-private.png"><img class="alignnone size-full wp-image-2756" title="no private" src="/public/uploads/2012/03/no-private.png" alt="" width="102" height="21" /></a></li>
	<li>Click this button and it will send your friend a message starting the secure communication.
<ul>
	<li>If your friend does not have the OTR plugin installed they will see a message that looks like this "<em>?OTR?v2? nobody@nowhere.com has requested an Off-the-Record private conversation &lt;<a href="http://otr.cypherpunks.ca/">http://otr.cyph<wbr>erpunks.ca/</wbr></a>&gt;.  However, you do not have a plugin to support that. See <a href="http://otr.cypherpunks.ca/">http://otr.cyph<wbr>erpunks.ca/</wbr></a>for more information.</em>"</li>
	<li>If your friend does have the OTR plugin installed correctly they should see a message similar to this "<em>(12:34:26 PM) The privacy status of the current conversation is now: Unverified, Conversation with __FRIENDS_NAME___ on 3/28/2012 12:34:26 PM: (12:34:26 PM) The privacy status of the current conversation is now: Unverified</em>" What this means is that the communication between you two are now encrypted but you can't be sure that your friend is who they say they are. <a href="/public/uploads/2012/03/unverified.png"><img class="alignnone size-full wp-image-2760" title="unverified" src="/public/uploads/2012/03/unverified.png" alt="" width="83" height="25" /></a></li>
</ul>
</li>
	<li>You can then verify your friends by click the unverified button and select "authenticate buddy" from the menu</li>
	<li>On this page you can ask your friend a question that only they would know.
<a href="/public/uploads/2012/03/questions.png"><img class="alignnone size-medium wp-image-2762" title="questions" src="/public/uploads/2012/03/questions-292x300.png" alt="" width="292" height="300" /></a></li>
	<li>Once you have verified that your friend is who they say they are then the icon will change to
<a href="/public/uploads/2012/03/private.png"><img class="alignnone size-full wp-image-2761" title="private" src="/public/uploads/2012/03/private.png" alt="" width="76" height="23" /></a></li>
</ol>
<div><strong>Notes:</strong></div>
<div>
<ul>
	<li>Most clients will allow for logging of the chat session, if you are using OTR this defeats the purpose of the system. You will never know if your friend is logging the conversation. This is a a possible attack/vulnerability</li>
	<li>If you are talking over GTalk you may notice that the logs show random chars for your communication. This is good this is your encrypted conversation.
<div>
<div>me:  "<em><strong>?OTR:</strong>AAIDAQAAAA</em><wbr><em>MAAAADAAAAwOP8n</em><wbr><em>7lerGtKSO/sT5C5</em><wbr><em>cC1uYPOaFsBxPge</em><wbr><em>sW1aXmmldhO510p</em><wbr><em>+k7eCw/PxWyersV</em><wbr><em>zOc5iyul3xqeHkb</em><wbr><em>Z9rlr8lP2CLYadi</em><wbr><em>1rb2sw+JneD54tE</em><wbr><em>gt/EFcT8CBZ4Jcd</em><wbr><em>yNeAI0TtsByn08g</em><wbr><em>6EkeMPSMrln56Lb</em><wbr><em>32Vl8aBdddioeiwqwDSDFsdfsekb6RqXvh</em><wbr><em>NVsLMiogBPiyRk3</em><wbr><em>UarwsJ3tUHdpWuI</em><wbr><em>sW2yv0HmAb4QWxl</em><wbr><em>VPaehNdWl9itVBv</em><wbr><em>eWawtQZaqd8eu2a</em><wbr><em>alvi9/+JSeyawAA</em><wbr><em>AAAAAAABAAAABSQ</em><wbr><em>Vb9d9BNaZAKwdVs</em><wbr><em>JQH3Wgcgeb7E3oz</em><wbr><em>MoAAAAUkIlPXeG/</em><wbr><em>HYLDXS1qC/h9epd</em><wbr><em>hBpo=</em>". Sent at 12:43 PM on Wednesday</wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></wbr></div>
</div></li>
</ul>
</div>
<strong> External links </strong>
<ul>
	<li><a href="http://encrypteverything.ca/index.php/Setting_up_OTR_to_encrypt_Instant_Messaging">Setting up OTR to encrypt Instant Messaging</a></li>
	<li><a href="http://encrypteverything.ca/">Why encrypt everything </a></li>
</ul>
