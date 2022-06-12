---
title: The Art of Computer Programming
layout: page
---

Notes and posts for me as I work through my 3 volumes of TAOCP. If this works out then volume 4 would be a pending purchase.

<ul>
{% for tag in site.tags %}
    {% assign t = tag | first %}
    {% assign posts = tag | last %}
    {% for post in posts %}
        {% if post.tags contains "taocp" %}
        <li>
            <a href="{{ post.url }}">{{ post.title }}</a>{% endif %}
        </li>
    {% endfor%}
{% endfor %}
</ul>