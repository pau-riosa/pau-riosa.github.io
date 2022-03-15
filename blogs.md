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
                  src="./assets/images/image-from-rawpixel-id-560462-jpeg.jpg"
                  width="100%"
                  />
            </div>
        </div>
        <div class="card__body">
          <h1>{{post.title}}</h1>
          <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Sequi
          perferendis molestiae non nemo doloribus. Doloremque, nihil! At
          ea atque quidem!
          </p>
        </div>
        <div class="card__footer">
          <div class="user">
            <img
                src="./assets/images/profile-picture.png"
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

