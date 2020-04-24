---
layout: single
title: Programming Competition Prisoners Dilemma
date: 2012-10-25 00:01
categories: Development
tags: c code Competition contests Development experiment Games github News programming project VHS
---
I have been trying to think of a simple programming competition that we can run at the next SHHH (<a href="http://vancouver.hackspace.ca/wp/2012/10/23/super-happy-hacker-house-24-nov-11-2012-730-late/">Super Happy Hacker House</a>) at <a href="http://vancouver.hackspace.ca/wp/">the Vancouver Hackspace</a>.

<a href="http://en.wikipedia.org/wiki/ACM_International_Collegiate_Programming_Contest">ACM International Collegiate Programming Contest</a> seems like an obvious choice. I have run though these contest back in collage and they where very challenging.

Too challenging for a SHHH where would probably consuming some beers and having fun. I was hoping for one with less of a barrier to entry where people with less programming experience could at-lest join in.

A few months ago I listened to a <a href="http://www.radiolab.org">Radio Lab</a> podcast on <a href="http://www.radiolab.org/blogs/radiolab-blogland/2010/dec/14/prisoners-dilemma/">the prisoners-dilemma</a> where they describe the problem and created a competition where people could submit robots that would play this game. They went on to describe the outcome of a few of these robots, how they worked, why they worked that way. It was a interesting podcast.

<img class="alignright size-medium wp-image-2930" style="line-height: 24px; font-size: 16px;" title="PrisonersDilemma" src="/public/uploads/2012/10/PrisonersDilemma-300x167.png" alt="" width="300" height="167" />

This sounded perfect for a simple programming contest. It only had a few rules, inputs,  outputs and its very simple to teach someone. So I created a model of the system with a few example bots.
<ul>
	<li><strong>Jebus</strong> - Always cooperates.</li>
	<li><strong>Snitch</strong> - Always defects.</li>
	<li><strong>Random</strong> - Randomly makes choices.</li>
	<li><strong>Copy Cat</strong> - Starts by cooperating but then copies his opponents last move.</li>
	<li><strong>Fool Me Once</strong> - Starts by cooperating but if opponents ever defect it will defect every time after that.</li>
	<li><strong>Forgives</strong> - Starts by cooperating, if the opponents defect it will defect until the opponents cooperates twice in a row.</li>
</ul>
As you can see from the results the Snitch wins most of the single rounds since he starts by defecting first and gets a jump start on the rest of the group. But overall the Snitch does do well but not the best as he can never cooperate with anyone to reduce his sentence. The fool me once bot tends to do better as he can recover from the snitch the easiest.

Source code can be found on github <a href="https://github.com/funvill/PrisonersDilemma">funvill/PrisonersDilemma</a>

This was an interesting exercise and it was fun to program but its too simple for a programming competition. The problem is that there is only one input, output and does not allow for a variety of choices.

<strong>Other research </strong>

On stack overflow I found a programming competition for creating <a href="http://stackoverflow.com/questions/1631414/what-is-the-best-battleship-ai">the best battleship AI</a>. I also found this one produced by Google that looks amazing <a href="http://aichallenge.org/">http://aichallenge.org/</a> too bad there servers are down

More research is needed.

&nbsp;

&nbsp;
