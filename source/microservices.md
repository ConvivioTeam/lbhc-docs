---
layout: default
title: Microservices
permalink: /microservices/
nav_order: 2
---
# Microservices

A list of the microservices in the system.

<ul>
{% assign microservices = site.microservices %}
    {% for page in microservices %}
    <li><a href="{{ page.url }}">{{ page.title }}</a></li>
    {% endfor %}
</ul>