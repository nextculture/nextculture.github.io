---
layout: single
title: "winnt.h(5545) : error C2146: syntax error : missing ';' before identifier 'ContextRecord'"
date: 2009-10-20 10:47
categories: Development
tags: Compile dev Development VS2008 windows
---
Anther annoying compiling error.

<strong>Compile error </strong><code>
c:\program files\microsoft sdks\windows\v6.0a\include\winnt.h(5545) : error C2146: syntax error : missing ';' before identifier 'ContextRecord'
c:\program files\microsoft sdks\windows\v6.0a\include\winnt.h(5545) : error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
c:\program files\microsoft sdks\windows\v6.0a\include\winnt.h(5545) : error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
c:\program files\microsoft sdks\windows\v6.0a\include\winnt.h(11263) : error C2065: 'PCONTEXT' : undeclared identifier
c:\program files\microsoft sdks\windows\v6.0a\include\winnt.h(11264) : error C2146: syntax error : missing ')' before identifier 'ContextRecord'
c:\program files\microsoft sdks\windows\v6.0a\include\winnt.h(11264) : warning C4229: anachronism used : modifiers on data are ignored
c:\program files\microsoft sdks\windows\v6.0a\include\winnt.h(11264) : error C2182: 'RtlCaptureContext' : illegal use of type 'void'
c:\program files\microsoft sdks\windows\v6.0a\include\winnt.h(11264) : error C2491: 'RtlCaptureContext' : definition of dllimport data not allowed
c:\program files\microsoft sdks\windows\v6.0a\include\winnt.h(11264) : error C2059: syntax error : ')'
c:\program files\microsoft sdks\windows\v6.0a\include\winnt.h(12935) : error C3861: '__readfsdword': identifier not found
</code>

<strong>Solution:</strong>
<code>#include "windows.h"</code>
