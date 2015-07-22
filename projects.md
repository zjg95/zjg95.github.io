---
layout: page
permalink: /projects/
---

## Projects

#### Welcome to my projects page! Here you will find projects I have worked on during my time at UTCS. 

****

<div class="posts">
  {% for post in site.projects %}
    <article class="post">

      <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>

      <div class="entry">
        {{ post.excerpt }}
      </div>

      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
    </article>
  {% endfor %}
</div>