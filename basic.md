---
layout: default
title: Basic Customize
folder: basic
permalink: /basic/
---
<h1 class="page-title">{{ page.title }}</h1>

基本的なカスタマイズ

{% for collection in site.collections %}
  {% if collection.label == page.folder %}
    {% assign groups = collection.docs | group_by: "part" %}
  {% endif %}
{% endfor %}

{% for group in groups %}
  <h2 id="{{ group.name }}">{{ group.name }}</h2>
  <ul>
  {% for item in group.items %}
    <li class="post-list-by-part">
      <a href="{{ item.url | relative_url }}">{{ item.title }}</a>
      <time datetime="{{ page.date | date_to_xmlschema }}">{{ item.date | date: "%Y-%m-%d" }}</time>
    </li>
  {% endfor %}
  </ul>
{% endfor %}