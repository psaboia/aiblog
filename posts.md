---
layout: page
title: All Posts
permalink: /posts/
---

<div class="posts-list">
  {%- if site.posts.size > 0 -%}
    <ul class="post-list">
      {%- for post in site.posts -%}
      <li>
        {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        <span class="post-meta">{{ post.date | date: date_format }}</span>
        <h3>
          <a class="post-link" href="{{ post.url | relative_url }}">
            {{ post.title | escape }}
          </a>
        </h3>
        {%- if post.excerpt -%}
          {{ post.excerpt }}
        {%- endif -%}
      </li>
      {%- endfor -%}
    </ul>
  {%- endif -%}
</div>

<style>
.posts-list {
  margin-top: 30px;
}

.post-list {
  list-style: none;
  padding: 0;
}

.post-list li {
  margin-bottom: 30px;
  border-bottom: 1px solid #e8e8e8;
  padding-bottom: 20px;
}

.post-list li:last-child {
  border-bottom: none;
}

.post-meta {
  font-size: 14px;
  color: #828282;
}

.post-link {
  display: block;
  font-size: 24px;
  margin: 5px 0;
  color: #2a7ae2;
  text-decoration: none;
}

.post-link:hover {
  text-decoration: underline;
}
</style> 