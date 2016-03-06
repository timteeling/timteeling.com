---
layout: page
title: Thoughts
permalink: /thoughts/
slug: thoughts
---


<div class="posts">
  {% for post in site.posts %}
    <article>
    <h4 class="nomb"><a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h4>
      <p class="post-date meta">{{ post.date | date: "%b %-d, %Y" }}</p>
    </article>
  {% endfor %}
</div>
