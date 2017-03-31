---
layout: default
title: 文章归档
permalink: /archive/
---

# 按时间线查看

<div>
  <blockquote>
    {% for post in site.posts %}
      <span class="post-meta">
        {{ post.date | date:"%Y-%m-%d"}}
      </span>
      <h3>
        <a href="{{ post.url }}">{{ post.title }}</a>
      </h3>
    {% endfor %}
  </blockquote>
</div>


# 按分类查看

<div>
  {% for category in site.categories %}
  <h2>{{ category | first }}
    <span class="post-meta">
      共{{ category | last | size }}篇
    </span>
  </h2>
  <blockquote>
    {% for post in category.last %}
      <span class="post-meta">
        {{ post.date | date:"%Y-%m-%d"}}
      </span>
      <h3>
        <a href="{{ post.url }}">{{ post.title }}</a>
      </h3>
    {% endfor %}
  </blockquote>
  {% endfor %}
</div>
