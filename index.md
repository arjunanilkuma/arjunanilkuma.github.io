---
layout: default
---

<div class="portfolio-grid">
  {% for project in site.projects %}
    <a href="{{ project.url | relative_url }}" class="portfolio-card">
      <img src="{{ project.thumbnail | relative_url }}" alt="{{ project.title }}">
      <div class="card-info">
        <span class="year">{{ project.year }}</span>
        <span class="title">{{ project.title }}</span>
      </div>
    </a>
  {% endfor %}
</div>
