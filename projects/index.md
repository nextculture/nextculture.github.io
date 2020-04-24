---
title: "Projects"
layout: "single"
classes: wide
---

This is a list of some of the past project that I have done. 

<ul>
{% for project in site.pages reversed %}
 {% if project.title != null %}
  {% if project.layout == "project" %}
   <li><a href="{{ project.url }}">{{ project.title }}</a> 
   {% if project.excerpt != null %}
   - {{project.excerpt}}
   {% endif %}
   </li>
  {% endif %}
 {% endif %}
{% endfor %}
</ul>