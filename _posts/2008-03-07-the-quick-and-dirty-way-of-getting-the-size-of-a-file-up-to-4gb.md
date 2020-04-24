---
layout: single
title: The quick and dirty way of getting the size of a file up to 4GB.
date: 2008-03-07 15:23
categories: Tips
tags: c code snippet Tips
---
I'm often surprised how many times this question has come up by beginner programmers.
How do you tell the size of a file in win32?

This method will fail on files greater then 4GB, and its slower then other methods but it quick and easy as long as you are not dealing with files greater then 4gb.
<pre>FILE * h_file = NULL ;
if( h_file = fopen( h_file, "rb" )  != NULL ) {
	fseek(h_file, 0, SEEK_END);
	long file_size = ftell(h_file);
	fclose( h_file );
}</pre>
