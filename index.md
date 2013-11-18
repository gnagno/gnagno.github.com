---
layout: page
title: GnagnoSoft
tagline: Supporting tagline
---
{% include JB/setup %}

{% for post in site.posts %}
  <h3>
    <a href="{{ post.url }}">{{ post.title }}</a>
  </h3>
  <p>{{ post.excerpt }}</p>
  <p>Published: {{ post.date | date: '%B' }} {{ post.date | date: '%d' }} {{ post.date | date: '%Y' }}</p>
<hr />
{% endfor %}

