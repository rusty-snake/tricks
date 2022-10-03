---
layout: default
---

# Tips & Tricks

<p>
  {% for post in site.posts %}
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
  {% endfor %}
</p>

Questions? <https://github.com/rusty-snake/tricks/discussions>
