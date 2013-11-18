---
layout: page
title: GnagnoSoft
tagline: Supporting tagline
---
{% include JB/setup %}

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <p>{{ post.excerpt }}</p>
      <p>Published: {{ post.date | date: '%B' }} {{ post.date | date: '%d' }} {{ post.date | date: '%Y' }}</p>
    </li>
  {% endfor %}
</ul>

