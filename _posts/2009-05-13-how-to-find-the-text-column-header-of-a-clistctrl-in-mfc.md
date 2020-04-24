---
layout: single
title: How to find the text column header of a CListCtrl in MFC
date: 2009-05-13 14:58
categories: Development
tags: cpp MFC snippet Tips
---
<p>&#160;</p>  <p>How to find the text column header of a CListCtrl in MFC</p>  <blockquote>   <p>CString GetColumnName( CListCtrl * list, int nCol )     <br />{      <br />&#160;&#160;&#160; CString strNome;       <br />&#160;&#160;&#160; CHeaderCtrl* pHdr = list-&gt;GetHeaderCtrl();      <br />&#160;&#160;&#160; if ( pHdr )      <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; if ( nCol &lt; pHdr-&gt;GetItemCount() )      <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; {      <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; HDITEM hdi;      <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; hdi.mask = HDI_TEXT;      <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; hdi.pszText = strNome.GetBuffer( 256 );      <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; hdi.cchTextMax = 256;      <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; pHdr-&gt;GetItem( nCol, &amp;hdi );      <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; strNome.ReleaseBuffer();      <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; }      <br />&#160;&#160;&#160; return strNome;      <br />}</p></blockquote>
