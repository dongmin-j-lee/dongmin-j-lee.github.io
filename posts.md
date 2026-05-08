---
layout: page
title: "Posts"
permalink: /posts/
main_nav: true
---

{% for category in site.categories %}
  {% capture cat %}{{ category | first }}{% endcapture %}
  <h2 id="{{ cat }}">{{ cat | capitalize }}</h2>
  {% if site.data.category_descriptions %}
    {% for desc in site.data.category_descriptions %}
      {% if desc.cat == cat %}
        <p class="desc"><em>{{ desc.desc }}</em></p>
      {% endif %}
    {% endfor %}
  {% endif %}
  <ul class="posts-list">
  {% for post in site.categories[cat] %}
    <li>
      <strong>
        <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </strong>
      <span class="post-date">- {{ post.date | date_to_long_string }}</span>
    </li>
  {% endfor %}
  </ul>
  {% if forloop.last == false %}<hr>{% endif %}
{% endfor %}
