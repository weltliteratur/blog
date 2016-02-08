---
title: Weltliteratur Blog
layout: default
date: 2016-02-08
---


{% for post in site.posts limit:5 %}
<h1 class="entry-title">
  <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
</h1>
<p class="blogdate">{{ post.date | date: "%d %B %Y" }}</p>
<div>{{ post.content |truncatehtml | truncatewords: 60 }}</div>
{% endfor %}
