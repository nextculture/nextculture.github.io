---
layout: single
title: C++ name mangling hell
date: 2008-11-09 09:00
categories: Development Tips
---
I found this post on Experts exchange about <a href="http://www.experts-exchange.com/Programming/System/Windows__Programming/MFC/Q_21865192.html ">C++ name mangling hell</a>. I have run in to this problems a few times, it drives me nuts as I always forget about it when trying to use LoadLibrary and GetProcAddress.
<blockquote><code>#ifdef FIRSTINDLL_EXPORTS
#define FIRSTINDLL_API extern "C" __declspec(dllexport)
#else
#define FIRSTINDLL_API extern "C" __declspec(dllimport)
#endif</code>

// Exported function.
FIRSTINDLL_API const char* const FirstGetBuf(USHORT Num);

Otherwise the exported function will end up as
<code>FirstGetBuf@US&amp;NP</code></blockquote>
In c++ they try to make all the functions have unquie names by adding a hash of something to the end of the exported function "US&amp;NF" this works really well for creating unquie function names but it makes it impossable to use GetProcAddress. So we have to Extern C all the functions so they show up as C function instead of C++ functions.
