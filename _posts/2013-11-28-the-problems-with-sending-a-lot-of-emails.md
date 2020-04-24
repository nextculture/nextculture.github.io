---
layout: single
title: The problems with sending a lot of emails.
date: 2013-11-28 21:20
categories: Rants
---
One of my side projects is a daily fiction magazines called <a href="http://www.everydayfiction.com/">EveryDayFiction.com</a>. We take user submitted stories of 1000 words or less. Give feedback on every submitted story, select the best stories, and publish a new story each and every day. We even pay our authors! We have been operating since 2007 and we have published 2500+ stories.
<h3><strong>We send a lot of emails </strong></h3>
We have 6,000+ email subscribers and we are growing by about ~100 new subscribers every month. Everyday we send all our subscribers a new story via email. On average we are sending ~2,190,000 email a month (6000 subscribers * 365 days = 2,190,000 emails) that is a lot of emails!
<h3><strong>We are a good guy!</strong></h3>
We make it hard to subscribe to our mailing list, and easy to unsubscribe. We do this to ensure that you actually want one of our stories in your inbox and to help reduce the amount of people that mark our emails as spam.

To subscribe you have to enter your email address into a clearly defined subscription box on our website. We send you an email to confirm that you actually want this email (<a href="http://kb.mailchimp.com/article/how-does-confirmed-optin-or-double-optin-work">double opt in</a>) and to confirm your email address. This prevents someone from subscribing their friends and family on their behalf. At the bottom of every one of our email in NORMAL SIZE FONT is a link to unsubscribe. It only takes one click to unsubscribe.
<h3><strong>Sending that much email is hard or expensive</strong></h3>
To send the new stories to our email subscribers we have two options.
<h4><strong>Send the email our selfs </strong></h4>
We could send the emails our selfs from our own servers. This option is cheap as it just costs us bandwidth, but is has many draw backs.

If enough people mark our emails as spam in a short period then <a href="http://www.spamhaus.org/">automatic spam prevention robots</a> (more good guys) may black list our domain or server as a spammer. Once you are on the blacklist its very hard to get off that list, Many email clients (google, hotmail, outlook, etc...) use this list to help reduce spam. If you are on this list your email goes directly in to the spam folder or gets deleted unread.

Most web hosts also have limits on the amount of emails that you can send from their hosts to also prevent spam. <a href="https://www.dreamhost.com/">Dreamhost</a> (one of our old hosts) has <a href="http://wiki.dreamhost.com/index.php/Smtp-quota">a limit of 100 emails per hour</a>. If we wanted to send our subscribers the daily stories each morning it would take ~60 hrs (6000/100). Media temple (another old host) has <a href="https://kb.mediatemple.net/questions/66/Outgoing+Email+Limitations#gs">a limit of 500 emails an hour</a> or 12hrs. Other hosts have very similar limits.

We would also have to store all of our subscribers email address on our own server. This isn't such a big deal until your server is hacked and someone steals your mailing list. Then they starts sending spam emails to all of your subscribers and your subscribers get mad at you for giving our their email address.
<h4><strong>Send emails from a third party </strong></h4>
This is what we are currently doing. When you subscribe to our mailing list you are actually sending your email address to a trusted third party. (In this case Feedburner, aka Google) When we publish a new story we send a copy of this story to Feedburner and they send the story to all of the subscribers.

Feedburner and Mailchimp have a lot of experience and a relationship with the automatic spam prevention robots and email black lists providers. They ensure that their servers and domains do not get black listed, and do other good things to prevent your email from getting marked as spam.

Their servers are set up to send email and don't have the same limits as dreamhost or other web hosts have. They also have dedicated staff to ensuring the security of your email subscription list. So you don't have to worry about security as much.

But they are also very expensive and the free options are disappearing.

Feedburner while free, has many other problems with it and no support to turn to when things go wrong. They are also <a href="http://adsenseforfeeds.blogspot.ca/">slowly shutting down their service</a> leaving us without any good free options.

Sending ~6000 emails every morning from MailChimp, it would cost around ~<a href="http://mailchimp.com/pricing/b/growing-business/">$75 per month for 5,800-10,000 subscribers</a>. This is a cost that we just can't afford to pay at this moment. Other email services like MailChimp cost about the same amount or more.
<h3>Plea for help</h3>
How do you send a email to a large subscription base daily on the cheap?
