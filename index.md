---
layout: home
title: Arjun Anilkumar Portfolio
---

# Featured Projects
Still tryna figure out this Jekyll thing :)

<div class="project-grid">
  {% for post in site.posts %}
    <div class="project-card">
      <a href="{{ post.url }}">
        <h3>{{ post.title }}</h3>
        <p>{{ post.excerpt | strip_html | truncatewords: 20 }}</p>
      </a>
    </div>
  {% endfor %}
</div>
