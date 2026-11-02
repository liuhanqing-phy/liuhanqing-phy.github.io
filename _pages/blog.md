---
layout: page
permalink: /blog/
title: Blog
nav: true
nav_title: blog
nav_order: 3
---

<ul class="personal-post-list">
{% for post in site.posts %}
  <li>
    <span class="post-date">{{ post.date | date: '%b %Y' }}</span>
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    <p>{{ post.description }}</p>
  </li>
{% endfor %}
</ul>
