---
layout: default
title: About
---

<section class="post-section">
  {% include navigation.html %}
  <h1>Writings</h1>
  <ul class="post-list">
    {% for post in site.posts %}
    <li>
      <div class="post-item">
        <a class="post-link" href="{{ post.url }}">
          {{ post.title }}
          <span class="post-date">{{ post.date | date: "%-d %B %Y" }}</span>
        </a>
      </div>
    </li>
    {% endfor %}
  </ul>
</section>
