---
layout: single
title: How to make a CMinMaxAvg class 
date: 2008-06-06 13:21
categories: Development Tips
---
I got asked how to create a simple averaging class.
If you where feeling smart you could enhance this class in to a template class for a object that has the =,+,&gt;,&lt; operator. But I'm feeling lazy today.
<pre>class CMinMaxAvg
{
private :
int	m_count;
int	m_total;
int	m_min;
int	m_max;
public:

CMinMaxAvg() {
m_count = 0 ;
m_total = 0 ;
m_min   = 0 ;
m_max   = 0 ;
}

void add( int iNum ) {
if( m_count == 0 ) {
SetMax( iNum, true ) ;
SetMin( iNum, true );
}        SetMax( iNum, false );
SetMin( iNum, false );
m_count ++;
m_total += iNum ;
}

void SetMax( int iNum, bool force=true ) {
if( m_max &lt; iNum || force ) {
m_max = iNum ;
}
}

void SetMin( int iNum, bool force=true ) {
if( m_min &gt; iNum || force) {
m_min = iNum ;
}
}

float GetAvg( ) {
return (float)m_total/(float)m_count ;
}

int GetMax() {
return m_max ;
}

int GetMin() {
return m_min ;
}
};</pre>
