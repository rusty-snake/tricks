# Tips & Tricks

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>


Questions? <https://github.com/rusty-snake/tricks/discussions>
