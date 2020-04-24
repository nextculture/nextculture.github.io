---
layout: single
title: Get special folders with SHGetKnownFolderPath
date: 2009-12-16 15:04
categories: Tips
---
This application will print the special folders that you should be storing your applcations data in.
UAC on Windows Vista/7 will no longer alowe you to write to files in the "C:\Program Files\" with out elevation to administrator. Instead you should be writting your settings file to the "LocalAppData" folder and your output and log file to "Documents" folder.

<strong>More information on UAC</strong>
<ul>
	<li><a href="http://en.wikipedia.org/wiki/User_Account_Control">http://en.wikipedia.org/wiki/User_Account_Control</a></li>
	<li><a href="http://windowsteamblog.com/blogs/developers/archive/2009/08/04/user-account-control-data-redirection.aspx">http://windowsteamblog.com/blogs/developers/archive/2009/08/04/user-account-control-data-redirection.aspx</a></li>
</ul>
<strong>Source code:</strong>
<blockquote><code>#include &lt;shlobj.h&gt;
void GetSpecialFolder( REFKNOWNFOLDERID rfid ) {
LPWSTR wszPath = NULL;
HRESULT hr = SHGetKnownFolderPath ( rfid, KF_FLAG_CREATE, NULL, &amp;wszPath );
if ( SUCCEEDED(hr) )
{
wprintf( _T("Path: %s\n"), wszPath );
}
}</code>

<code>int _tmain(int argc, _TCHAR* argv[])
{
GetSpecialFolder( FOLDERID_ProgramData );		// Shared program data directory for all users
GetSpecialFolder( FOLDERID_RoamingAppData );	// Per-user program data directory (roaming)
GetSpecialFolder( FOLDERID_LocalAppData  );		// Per-user program data directory (non-roaming)

</code><code>GetSpecialFolder( FOLDERID_ProgramFiles  );		// App install directory
GetSpecialFolder( FOLDERID_Documents  );		// Logs, reports, output
return 0;
}
</code></blockquote>
