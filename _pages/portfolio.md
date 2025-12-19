---
title: "Portfolio"
layout: single
permalink: /portfolio/
---

{% assign items = site.portfolio | sort: "date" | reverse %}

<div class="grid__wrapper">
  {% for item in items %}
    <div class="grid__item">
      <article class="archive__item">
        <h2 class="archive__item-title">
          <a href="{{ item.url }}">{{ item.title }}</a>
        </h2>
        <p class="archive__item-excerpt">{{ item.excerpt }}</p>
      </article>
    </div>
  {% endfor %}
</div>
