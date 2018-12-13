---
layout: default
title: Requirements
parent: Scraper
grand_parent: Microservices
nav_order: 1
permalink: microservices/scraper/requirements
---

# Requirements

The Scraper microservice is designed to run in a containerised enviroment based on Docker. Most of the requirements for this microservice are already contained in the Docker files in this repo, but below is an outline of the architecture of the containers in this microservice and the requirements in their build.

The scraper tool is designed to retrieve content from third-party data sources, currently via web APIs or from web pages, and then extract data from those third-party sources. The microservices therefore has package dependencies to support that.

## Laravel Lumen

The system is built with [Lumen](https://lumen.laravel.com/), a PHP microservice-oriented framework from [Laravel](https://laravel.com/).

**Current version:** 5.7

### Dependencies

Beyond the standard packages required by Lumen, the Scraper microservice depends on:

- [Guzzle HTTP request client](http://docs.guzzlephp.org/en/stable/) » guzzlehttp/guzzle ^6.3
- [Symfony CSSselector component](https://symfony.com/doc/current/components/css_selector.html) » symfony/css-selector ^4.2
- [Symfony DomCrawler component](https://symfony.com/doc/current/components/dom_crawler.html) » symfony/dom-crawler ^4.1

{: .alert .alert-primary }
**@todo:** requires Kafka integration, also. See the [event stream](../../eventstream) microservice.

- [Kafka Queue driver for Laravel](https://github.com/rapideinternet/laravel-queue-kafka) » rapide/laravel-queue-kafka ~1.0

## PHP

The system is built to run on PHP 7.2.

Current version in the Docker container: PHP Version 7.2.11

For the dependency libraries, PHP must have the following extensions installed:

- `ext-dom`
- `ext-http`
- `ext-json`

We have built a custom [PHP Docker image with support for Kafka](https://hub.docker.com/r/convivio/php-kafka/) integration via the [rdkafka PECL extension](https://pecl.php.net/package/rdkafka), which in turn needs [librdkafka](https://github.com/edenhill/librdkafka). The image also has `ext-http` installed.
