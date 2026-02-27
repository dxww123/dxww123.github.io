---
layout: page
title: 归档
permalink: /archive/
---

<ul class="archive-list">
  {% for post in site.posts %}
    <li class="archive-item">
      <span class="archive-date">{{ post.date | date: "%Y-%m-%d" }}</span>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      {% if post.tags %}
        <span class="post-tags">
          {% for tag in post.tags %}
            <span class="tag">#{{ tag }}</span>
          {% endfor %}
        </span>
      {% endif %}
    </li>
  {% endfor %}
</ul>

{% if site.posts.size == 0 %}
  <p style="text-align: center; color: #999; padding: 50px 0;">
    还没有文章，快来写第一篇吧！
  </p>
{% endif %}
