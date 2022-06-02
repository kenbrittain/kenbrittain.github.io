---
title: Books
layout: page
---

Books used for reference and knowledge.

## Programming

{% assign books = site.data.books.programming | sort: "title" %}
{% include chicago.html %}

## Business

{% assign books = site.data.books.business | sort: "title" %}
{% for book in books %}
* {{book.author}} *{{book.title}}*. {{book.city}}: {{book.publisher}}, {{book.year}}. [{{book.link}}]({{book.url}})
{% endfor %}
 