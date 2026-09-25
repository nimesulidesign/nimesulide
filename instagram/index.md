---
layout: default
title: "Archivio Instagram"
---

# 📸 Archivio Instagram

Qui trovi l'archivio completo dei post recuperati da Instagram:

<style>
  .insta-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 16px;
    padding: 0;
    list-style: none;
    margin-top: 20px;
  }
  .insta-card {
    border: 1px solid #e1e4e8;
    border-radius: 8px;
    overflow: hidden;
    background: #fff;
    transition: transform 0.2s, box-shadow 0.2s;
  }
  .insta-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  }
  .insta-card a {
    text-decoration: none;
    color: #24292e;
    display: block;
  }
  .insta-card img {
    width: 100%;
    height: 160px;
    object-fit: cover;
    display: block;
    background-color: #f6f8fa;
  }
  .insta-title {
    padding: 8px 10px;
    font-size: 0.85em;
    font-weight: 600;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    text-align: center;
  }
</style>

<ul class="insta-grid">
{% for page in site.pages %}
  {% if page.path contains 'instagram/' and page.path != 'instagram/index.md' %}
    <li class="insta-card">
      <a href="{{ page.url | relative_url }}">
        {% if page.image %}
          <img src="{{ page.image | relative_url }}" alt="{{ page.title }}">
        {% elsif page.cover %}
          <img src="{{ page.cover | relative_url }}" alt="{{ page.title }}">
        {% else %}
          <img src="{{ '/media/404.jpg' | relative_url }}" alt="{{ page.title }}">
        {% endif %}
        <div class="insta-title">{{ page.title | default: page.name }}</div>
      </a>
    </li>
  {% endif %}
{% endfor %}
</ul>
