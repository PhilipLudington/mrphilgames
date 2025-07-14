---
layout: custom-page
title: Blog
permalink: /blog/
---

<div class="blog-archive">
  {% for post in site.posts %}
    <article class="archive-item">
      <h3>
        <a class="post-link" href="{{ post.url | relative_url }}">
          {{ post.title | escape }}
        </a>
      </h3>
      <span class="post-meta">{{ post.date | date: "%B %d, %Y" }}</span>
      {% if post.excerpt %}
        <div class="post-excerpt">
          {{ post.excerpt | strip_html | truncatewords: 50 }}
        </div>
      {% endif %}
    </article>
  {% endfor %}
</div>

<style>
  .blog-archive {
    margin-top: 2rem;
  }

  .archive-item {
    margin-bottom: 2rem;
    padding-bottom: 2rem;
    border-bottom: 1px solid #e0e0e0;
  }

  .archive-item:last-child {
    border-bottom: none;
  }

  .archive-item h3 {
    margin-bottom: 0.5rem;
  }

  .post-excerpt {
    margin-top: 0.5rem;
    color: #666;
  }
</style>