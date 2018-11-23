---
layout: default
title: Scraper
parent: Microservices
nav_order: 3
permalink: microservices/scraper
---

# Scraper Microservice

The scraper microservice pulls in data from external data sources. It is built with a plugin architecture, so that scapers or crawlers for a variety of external sources can be created.

Once data has been scraped, it should be put into the system [event stream](./eventstream) to create or update entries in the [data store](./datastore).

{% include_relative include-plugins.md %}

{% include_relative include-event-sourcing.md %}

## Repository

Code for the DoS Scraper microservice is in the [https://github.com/LBHackney-IT/DoS-scraper-service](https://github.com/LBHackney-IT/DoS-scraper-service) repository.
