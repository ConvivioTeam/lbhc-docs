---
layout: default
title: Event Sourcing
parent: Event Stream
grand_parent: Microservices
nav_order: 1
permalink: microservices/eventstream/eventsourcing
---

# Event Sourcing: Consuming and Publishing Events

Each microservice will need to source events from the event stream.

If an app is built with Laravel, as most of the microservices will be, then it will need to use a library to work with the Kafka-powered event stream.

## PHP Kafka libraries

This project looks like it could be a useful driver to add to a Laravel Lumen microservice:

- Kafka Queue driver for Laravel: [https://github.com/rapideinternet/laravel-queue-kafka](https://github.com/rapideinternet/laravel-queue-kafka)

**Supported versions of Laravel**
Tested on: [5.4, 5.5, 5.6, 5.7]

### Alternatives

See also:

- [https://github.com/arquivei/laravel-kafka-queue-connector](https://github.com/arquivei/laravel-kafka-queue-connector)
- [https://github.com/Superbalist/php-pubsub-kafka](https://github.com/Superbalist/php-pubsub-kafka)