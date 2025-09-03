---
layout: default
title: 標籤
permalink: /tags/
---

<h1>標籤</h1>

<ul>
{% for t in site.tags %}
  <li>
    <a href="#{{ t[0] | slugify }}">{{ t[0] }}</a> ({{ t[1].size }})
  </li>
{% endfor %}
</ul>

<hr/>

{% for t in site.tags %}
  <h2 id="{{ t[0] | slugify }}">{{ t[0] }}</h2>
  <ul>
    {% for p in t[1] %}
      <li>
        <a href="{{ p.url | relative_url }}">{{ p.title }}</a>
        <small>— {{ p.date | date: "%Y-%m-%d" }}</small>
      </li>
    {% endfor %}
  </ul>
{% endfor %}
