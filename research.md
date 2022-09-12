---
layout: articles
title: Research
type: normal
data_source: 
  research_posts
---

# Hello World

{% for item in site.research_posts %}
  <h2>{{ item.title }}</h2>
  #<p>{{ item.description }}</p>
  <p><a href="{{ item.url }}">{{ item.title }}</a></p>
{% endfor %}
