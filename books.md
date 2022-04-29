---
title: Books
layout: page
---

Books used for reference and knowledge.

<!-- Chicao Style Bibliographies -->
{% for book in site.data.books %}
* {{book.author}} *{{book.title}}*. {{book.city}}: {{book.publisher}}, {{book.year}}. [Amazon]({{book.amazon}}){% endfor %}
