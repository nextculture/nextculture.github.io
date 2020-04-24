---
layout: single
title: CakePHP - Search bar 
date: 2009-12-09 14:16
categories: Development
Tags: cakephp search 
---
This code snippet will create a search box that uses can use to search for text in the database.
The control creates a query to search certain fields of published stories

<strong>View or layout:</strong>
<code>&lt;?php
echo $form-&gt;create('Stories', array('url' =&gt; array('action' =&gt; 'index')));
echo $form-&gt;input('search_text', array('label' =&gt; false));
echo $form-&gt;end('Search');
?&gt;</code>

<strong>Controler:</strong>
<code>&lt;?php
function admin_index( )
{
$conditions = array( 'Story.terms !=' =&gt; '0' ) ;
if( isset( $this-&gt;data['Stories']['search_text'] )  )
{
$this-&gt;set('title', ' Search "'. $this-&gt;data['Stories']['search_text'] .'"' );
$conditions = array(
'Story.published' =&gt; '1',
'or' =&gt; array(
'Story.title LIKE'    =&gt; '%' . $this-&gt;data['Stories']['search_text'] . '%',
'Author.name LIKE'    =&gt; '%' . $this-&gt;data['Stories']['search_text'] . '%'
));
} </code>

<code> </code>

<code> $data = $this-&gt;paginate( 'Story', $conditions);
$this-&gt;set('data', $data );
}
?&gt;</code>
