---
layout: default
title: Tags
permalink: /tags/
---
{% assign rawtags = "" %}
{% for post in site.posts %}
{% assign ttags = post.tags | join:'|' | append:'|' %}
{% assign rawtags = rawtags | append:ttags %}
{% endfor %}
{% assign rawtags = rawtags | split:'|' | sort %}
{% assign tags = "" %}
{% for tag in rawtags %}
{% if tag != "" %}
{% if tags == "" %}
{% assign tags = tag | split:'|' %}
{% endif %}
{% unless tags contains tag %}
{% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' %}
{% endunless %}
{% endif %}
{% endfor %}
{% for tag in tags %}
{% endfor %}
{% for tag in tags %}
<article>
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
</article>
{% endfor %}
