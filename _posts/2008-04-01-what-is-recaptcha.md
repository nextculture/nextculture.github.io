---
layout: single
title: WHAT IS reCAPTCHA
date: 2008-04-01 14:35
categories: Development
tags: Development OCR Puzzle Development Website
---

<blockquote>
<p style="padding-top: 0px"> A <a href="http://recaptcha.net/captcha.html">CAPTCHA</a> is a program that can tell whether its user is a human or a computer. You've probably seen them €” colorful images with distorted text at the bottom of Web registration forms. CAPTCHAs are used by many websites to prevent abuse from "bots," or automated programs usually written to generate spam. No computer program can read distorted text as well as humans can, so bots cannot navigate sites protected by CAPTCHAs.</p>
 About 60 million CAPTCHAs are solved by humans around the world every day. In each case, roughly ten seconds of human time are being spent. Individually, that's not a lot of time, but in aggregate these little puzzles consume more than 150,000 hours of work each day. What if we could make positive use of this human effort? <a href="http://en.wikipedia.org/wiki/ReCAPTCHA" title="ReCAPTCHA" rel="wikipedia" target="_blank" class="zem_slink">reCAPTCHA</a> does exactly that by channeling the effort spent solving CAPTCHAs online into "reading" books.

To archive <a href="http://en.wikipedia.org/wiki/Knowledge" title="Knowledge" rel="wikipedia" target="_blank" class="zem_slink">human knowledge</a> and to make information more accessible to the world, multiple projects are currently digitizing physical books that were written before the computer age. The book pages are being photographically scanned, and then, to make them searchable, transformed into text using "Optical Character Recognition" (OCR). The transformation into text is useful because scanning a book produces images, which are difficult to store on small devices, expensive to download, and cannot be searched. The problem is that OCR is not perfect.

<center><img src="/public/uploads/2008/04/sample-ocr.gif" alt="sample-ocr.gif" /></center>
<p style="padding-top: 5px">reCAPTCHA improves the process of digitizing books by sending words that cannot be read by computers to the Web in the form of CAPTCHAs for humans to decipher. More specifically, each word that cannot be read correctly by OCR is placed on an image and used as a <a href="http://en.wikipedia.org/wiki/CAPTCHA" title="CAPTCHA" rel="wikipedia" target="_blank" class="zem_slink">CAPTCHA</a>. This is possible because most OCR programs alert you when a word cannot be read correctly.</p>
 But if a computer can't read such a CAPTCHA, how does the system know the correct answer to the puzzle? Here's how: Each new word that cannot be read correctly by OCR is given to a user in conjunction with another word for which the answer is already known. The user is then asked to read both words. If they solve the one for which the answer is known, the system assumes their answer is correct for the new one. The system then gives the new image to a number of other people to determine, with higher confidence, whether the original answer was correct.

Source: <a href="http://recaptcha.net/learnmore.html">http://recaptcha.net/learnmore.html</a></blockquote>
Supremely awesome!
