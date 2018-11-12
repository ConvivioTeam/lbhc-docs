---
layout: default
title: Microservices
permalink: microservices
nav_order: 2
parent: Microservices
has_children: true
---
# Microservices

A list of the microservices in the system.

<ul>
{% assign microservices = site.microservices %}
    {% for page in microservices %}
    {% if page.permalink != 'microservices' %}
    <li><a href="{{ page.url | relative_url }}">{{ page.title }}</a></li>
    {% endif %}
    {% endfor %}
</ul>
