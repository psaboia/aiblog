---
layout: home
title: Welcome
---

Generative AI is not merely a tool for creating content more quickly; it represents a paradigm shift in how to approach problems and solutions in software development. 

## Recent Posts

<div class="home-posts">
  {%- if site.posts.size > 0 -%}
    <ul class="post-list">
      {%- for post in site.posts limit:5 -%}
      <li>
        {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        <span class="post-meta">{{ post.date | date: date_format }}</span>
        <h3>
          <a class="post-link" href="{{ post.url | relative_url }}">
            {{ post.title | escape }}
          </a>
        </h3>
        {%- if post.excerpt -%}
          <p class="excerpt">{{ post.excerpt }}</p>
        {%- endif -%}
      </li>
      {%- endfor -%}
    </ul>

    <p class="see-all-posts">
      <a href="{{ '/posts' | relative_url }}">See All Posts →</a>
    </p>
  {%- endif -%}
</div>

<style>
.home-posts {
  margin-top: 2rem;
}

.post-list {
  list-style: none;
  padding: 0;
}

.post-list li {
  margin-bottom: 2rem;
  padding-bottom: 1.5rem;
  border-bottom: 1px solid #e8e8e8;
}

.post-list li:last-child {
  border-bottom: none;
}

.post-meta {
  font-size: 0.9rem;
  color: #666;
}

.post-link {
  display: block;
  font-size: 1.5rem;
  margin: 0.5rem 0;
  color: #2a7ae2;
  text-decoration: none;
}

.post-link:hover {
  text-decoration: underline;
}

.excerpt {
  color: #666;
  font-size: 1rem;
  margin-top: 0.5rem;
}

.see-all-posts {
  text-align: right;
  margin-top: 2rem;
}

.see-all-posts a {
  display: inline-block;
  padding: 0.5rem 1rem;
  background-color: #f8f9fa;
  color: #2a7ae2;
  text-decoration: none;
  border-radius: 4px;
  transition: background-color 0.2s;
}

.see-all-posts a:hover {
  background-color: #e9ecef;
  text-decoration: none;
}
</style> 