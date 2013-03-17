---
layout: page
title: Comment configurer mon Mac ?
tagline: Réflexions sur OS X, Rails, Ruby, JS le Web et iOS
---
{% include JB/setup %}

## Liste des articles

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
