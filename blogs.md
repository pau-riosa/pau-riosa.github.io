---
layout: blog 
title: Blogs 
---

<section>
  {% include navigation.html %}
  <div class="container-layout">
    <div class="blog-item"> 
    {% for post in site.posts %}
          <a href="{{post.url}}">
      <div class="card">
        <div class="card__header">
            <div class="module lr">
              <img
                  src="{{ root_url }}{{ post.image_path }}"
                  width="100%"
                  />
                  {{ post.image }}
            </div>
        </div>
        <div class="card__body">
          <h1>{{post.title}}</h1>
          <p class="truncate">
          {{ post.keywords }} 
          </p>
        </div>
        <div class="card__footer">
          <div class="user">
            <img
                src="{{ root_url }}/assets/images/profile-picture.png"
                alt="user__image"
                class="user__image"
                width="45"
                height="45"
                />
            <div class="user__info">
              <h5>{{ post.author }}</h5>
              <small>{{ post.date | date: "%-d %B %Y" }}</small>
            </div>
          </div>
        </div>
      </div>
          </a>
        {% endfor %}
    </div>
  </div>
  {% include footer.html %}
</section>

