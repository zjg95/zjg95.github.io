---
layout: page
permalink: /projects/
---

## Projects

#### Welcome to my projects page! Here you will find projects I have worked on during my time at UTCS. 

<div class="posts">
  {% for post in site.posts %}
    <article class="post">

      <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>

      <div class="entry">
        {{ post.excerpt }}
      </div>

      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
    </article>
  {% endfor %}
</div>

****

### GoTDB

![an image alt text]({{ site.baseurl }}/images/gotdb.png "an image title")

****

### PuzzlePals

![an image alt text]({{ site.baseurl }}/images/puzzlepals1.png "an image title")

****

### Tic-Tac-Toe

![an image alt text]({{ site.baseurl }}/images/tictactoe1.png "an image title")