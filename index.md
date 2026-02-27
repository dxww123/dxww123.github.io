---
layout: default
title: 首页
---

<div class="home">
  <h1 class="page-title">最新文章</h1>

  <ul class="post-list">
    {% for post in site.posts %}
      <li class="post-item">
        <h2>
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </h2>
        <p class="post-meta">
          <time datetime="{{ post.date | date_to_xmlschema }}">
            {{ post.date | date: "%Y年%m月%d日" }}
          </time>
          {% if post.tags %}
            <span class="post-tags">
              {% for tag in post.tags %}
                <span class="tag">#{{ tag }}</span>
              {% endfor %}
            </span>
          {% endif %}
        </p>
        <p class="post-excerpt">
          {{ post.excerpt | strip_html | truncate: 200 }}
        </p>
        <a href="{{ post.url | relative_url }}">阅读全文 &rarr;</a>
      </li>
    {% endfor %}
  </ul>

  {% if site.posts.size == 0 %}
    <p style="text-align: center; color: #999; padding: 50px 0;">
      还没有文章，快来写第一篇吧！<br>
      在 <code>_posts</code> 目录下创建你的第一篇博文。
    </p>
  {% endif %}
</div>
