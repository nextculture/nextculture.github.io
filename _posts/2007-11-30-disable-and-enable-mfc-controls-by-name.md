---
layout: single
title: Disable and Enable MFC controls by name 
date: 2007-11-30 12:25
categories: Development Tips
---
I use this snippet all the time to disable/enable, hide/show, move MFC controls.

<code>
// Enables and disables an MFC control by name
void CCILikeChease::EnableControl( int iControl, bool enable )
{
// Enable Control
</code><code>     </code><code>CWnd* wnd_control = (CWnd*)( GetDlgItem( iControl ) );
</code><code>     </code><code> if( wnd_control != NULL ) {
</code><code>     </code><code>     </code><code> wnd_control-&gt;EnableWindow( enable ) ;
</code><code>     </code><code> }
}
void CNetworkDlg::HideControl( int iControl, bool show )
{
</code><code>     </code><code> // Hide the Control
</code><code>     </code><code> CWnd* wnd_control = (CWnd*)( GetDlgItem( iControl ) );
</code><code>     </code><code> if( wnd_control != NULL ) {
</code><code>     </code><code>     </code><code> if(  show ) {
</code><code>     </code><code>     </code><code>     </code><code> wnd_control-&gt;ShowWindow( SW_SHOW ) ;
</code><code>     </code><code>     </code><code> } else {
</code><code>     </code><code>     </code><code>     </code><code> wnd_control-&gt;ShowWindow( SW_HIDE ) ;
</code><code>     </code><code>     </code><code>}
</code><code>     </code><code> }
}
void CNetworkDlg::MoveControl( int iControl, int top, int left, int sizex, int sizey  )
{
</code><code>     </code><code> // Move the control
</code><code>     </code><code> CWnd* wnd_control = (CWnd*)( GetDlgItem( iControl ) );
</code><code>     </code><code> if( wnd_control != NULL ) {
</code><code>     </code><code>     </code><code> LPRECT lpRect = new RECT ;
</code><code>     </code><code>     </code><code> wnd_control-&gt;GetClientRect( lpRect ) ;
</code><code>     </code><code> </code><code>     </code><code>lpRect-&gt;top		= top;
</code><code>     </code><code>     </code><code> lpRect-&gt;left	= left;
</code><code>     </code><code>     </code><code> if( sizex &gt; 0 || sizey &gt; 0 ) {
</code><code>     </code><code>     </code><code>     </code><code> lpRect-&gt;right   = sizex + left ;
</code><code>     </code><code>     </code><code>     </code><code> lpRect-&gt;bottom  = sizey + top;
</code><code>     </code><code>     </code><code> }
</code><code>     </code><code>     </code><code> wnd_control-&gt;MoveWindow( lpRect ) ;
</code><code>     </code><code>     </code><code> delete lpRect ;
</code><code>     </code><code> }
}
</code>
