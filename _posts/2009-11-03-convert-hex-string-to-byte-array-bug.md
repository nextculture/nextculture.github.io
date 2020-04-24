---
layout: single
title: Convert HEX string to BYTE array, bug. 
date: 2009-11-03 10:20
categories: Development Tips
---
Find the bug in the following code and win a prize.
Its obvious once you find it. CSharp programmers are asked not to mock c++ in this thread. 

<pre>

#include "stdafx.h"
#include &lt;string.h&gt;
#include &lt;stdio.h&gt;

#define USHORT	unsigned short 
#define BYTE	unsigned char 

USHORT ConvertHexToBytes( 
		/* IN  */ char * hex, 
		/* IN  */ const USHORT hex_length, 
		/* OUT */ BYTE * buffer, 
		/* OUT */ const USHORT buffer_length, 
		/* IN  */ const char * delemnator = ":" )
{
	if( hex	== NULL || hex_length &lt;= 0 ||
		buffer == NULL || buffer_length &lt;= 0 )
	{
		return 0; 
	}

	char *next_token = NULL;
	USHORT iOffset = 0 ; 
	char *p = strtok_s(hex, delemnator, &next_token);
	while (p) {
		if( 1 != sscanf_s( p, "%02X", &buffer[ iOffset ] ) ) {
			break; 
		}
		iOffset++;
		if( iOffset &gt;= buffer_length ) {
			break; // No more room. 
		}
		p = strtok_s(NULL, delemnator, &next_token);
	}
	return iOffset ; 
}
</pre>
