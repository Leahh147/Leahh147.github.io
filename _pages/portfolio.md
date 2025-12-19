---
title: "Portfolio"
layout: single
permalink: /portfolio/
---

{% assign items = site.portfolio | sort: "date" | reverse %}

<div class="portfolio-list">
  {% for item in items %}
    <div class="portfolio-row">

      <!-- Left: image / gif -->
      <div class="portfolio-media">
        <a href="{{ item.url }}">
          <img src="{{ item.header.teaser | relative_url }}" alt="{{ item.title }}">
        </a>
      </div>

      <!-- Right: content -->
      <div class="portfolio-content">
        <h2 class="portfolio-title">
          <a href="{{ item.url }}">{{ item.title }}</a>
        </h2>

        {% if item.institution %}
          <p class="portfolio-meta">
            <strong>{{ item.institution }}</strong> · {{ item.role }}
          </p>
        {% endif %}

        <p class="portfolio-excerpt">
          {{ item.excerpt }}
        </p>

        <div class="portfolio-links">
          {% if item.github %}
            <a href="{{ item.github }}" class="btn btn--small" target="_blank">
              GitHub
            </a>
          {% endif %}
          <a href="{{ item.url }}" class="btn btn--small btn--primary">
            Details
          </a>
        </div>
      </div>

    </div>
  {% endfor %}
</div>
