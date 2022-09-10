---
layout: default
title: Tags
permalink: /tags/
---

{% for tag in tags %}
<h4 id="{{ tag | slugify }}">{{ tag }}</h4>
<ul>
  {% for post in site.posts %}
  {% if post.tags contains tag %}
  <li>
      <a href="{{ post.url | prepend: site.baseurl }}">
        {{ post.title }}
      </a>
  </li>
  {% endif %}
  {% endfor %}
</ul>
{% endfor %}
