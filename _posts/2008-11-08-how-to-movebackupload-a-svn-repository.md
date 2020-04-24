---
layout: single
title: How to Move/Backup/Load a SVN repository 
date: 2008-11-08 09:00
categories: Tips
---
After the first time my computer crashed and i lost 3 months of work, I started religiously making backups of everything, dialy, weekly quarterly backups of all my data. Its become an obsession of mine, before I start a project I always make sure that there is a recovery procedure.

For source code and documents I use a SVN repository (Rev 9000+ and counting). The SVN server is running on a local server that mirrors its self to an off site backup nightly. (Just in case my house burns down)

This local server is a aging computer and needs to be replaced with brand new one, more space, raid, batter backup, ect.

I'm going to have to move the SVN repository.
I did a quick Google search and found <a href="http://svn.haxx.se/users/archive-2006-12/0424.shtml">this forum post</a>.

You will need to run this from command prompt

<code>svnadmin create NEWDIR
svnadmin dump OLDDIR &gt; mydump
ssvnadmin load NEWDIR mydump</code>

Now I can make off site DVD backups of my SVN repository directory just in case anything happens to my local SVN server, and my remote SVN server at the same time.
