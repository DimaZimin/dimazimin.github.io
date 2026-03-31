---
layout: page
title: Photos
permalink: /photos/
---
<ul class="post-list">
  {% for post in site.photos %}
    <li>
        <span class="post-meta">{{ post.date | date: "%B %-d, %Y" }}</span>
        <h3>
            <a class="post-link" href="{{ post.url }}">
                {{ post.title }}
            </a>
        </h3>
    </li>
    {% endfor %}
</ul>