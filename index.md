---
layout: home
---

<div class="posts">
    {% for post in site.posts %}
      <article>
      <h3><a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h3>
        <span class="post-date meta">{{ post.date | date: "%b %-d, %Y" }}</span>
      </article>
    {% endfor %}
  </div>
