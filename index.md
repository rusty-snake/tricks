---
layout: default
---

# Tips & Tricks

{% for post in site.posts %}
<h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
{% endfor %}

Questions? <https://github.com/rusty-snake/tricks/discussions>
