---
layout: custom-page
title: News
permalink: /news/
---

<div class="news-archive">
  <h2>Game Development News & Updates</h2>
  <p>Stay up to date with the latest news about Crimson Crisis and other projects.</p>
  
  {% assign news_posts = site.posts | where_exp: "post", "post.categories contains 'news'" %}
  {% if news_posts.size == 0 %}
    {% assign news_posts = site.posts %}
  {% endif %}
  
  {% for post in news_posts %}
    <article class="news-archive-item">
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
  .news-archive {
    margin-top: 2rem;
  }

  .news-archive-item {
    margin-bottom: 2rem;
    padding-bottom: 2rem;
    border-bottom: 1px solid #e0e0e0;
  }

  .news-archive-item:last-child {
    border-bottom: none;
  }

  .news-archive-item h3 {
    margin-bottom: 0.5rem;
  }

  .post-excerpt {
    margin-top: 0.5rem;
    color: #666;
  }
</style>