---
layout: single
title: CakePHP - Disable validation in controler 
date: 2009-12-10 14:52
categories: Development
Tags: cakephp php Tips validate
---
When upgrading an old web application to start using CakePHP but the old systems was riddled with invalid data. When the creating the CRUD system I need a way of updating this invalid data.

The following line of code will disable the validation in the controller.

<code>$this-&gt;Story-&gt;validate = array(); // Stop valadation on the story.</code>

Source: <a href="http://stackoverflow.com/questions/1766862/cakephp-save-with-a-table-where-the-primary-key-is-not-id/1767133">Cakephp Save with a table where the primary key is not €˜id&quot;</a>
