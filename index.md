---
layout: home
title: "Sam.Blog"
author_profile: true
---

<h2>分類</h2>
<ul class="taxonomy__index">
  {%- assign cats = site.categories | sort -%}
  {%- for c in cats -%}
    {%- assign cat_name = c[0] -%}
    {%- capture anchor %}/categories/#{{ cat_name | slugify }}{%- endcapture -%}
    <li>
      <a href="{{ anchor | relative_url }}">
        {{ cat_name }} <span class="taxonomy__count">{{ c[1].size }}</span>
      </a>
    </li>
  {%- endfor -%}
</ul>
