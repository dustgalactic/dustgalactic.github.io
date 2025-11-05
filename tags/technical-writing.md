---
layout: base
title: "All posts tagged 'technical-writing'"
tag: technical-writing
---

<div class="home">
  <h1 class="page-heading">{{ page.title }}</h1>

  {% assign tagged_posts = site.posts | where_exp: "post", "post.tags contains page.tag" %}

  {%- if tagged_posts.size > 0 -%}
    <ul class="post-list">
      {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
      {%- for post in tagged_posts -%}
        <li class="post-item">
          <span class="post-meta">{{ post.date | date: date_format }}</span>
          <h3 class="post-title">
            <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
          </h3>

          {%- if site.minima.show_excerpts -%}
            <div class="post-excerpt">
              {{ post.excerpt }}
            </div>
          {%- endif -%}

          {% if post.tags and post.tags.size > 0 %}
            <div class="post-tags">
              <strong>Tags:</strong>
              {% for tag in post.tags %}
                <a class="tag-link" href="{{ '/tags/' | append: tag | relative_url }}">{{ tag }}</a>{% unless forloop.last %}, {% endunless %}
              {% endfor %}
            </div>
          {% endif %}
        </li>
      {%- endfor -%}
    </ul>
  {%- else -%}
    <p>No posts found with this tag.</p>
  {%- endif -%}
</div>
