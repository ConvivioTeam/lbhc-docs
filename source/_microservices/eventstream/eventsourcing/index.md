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

## Event Sourcing and Laravel Queues

Laravel has an effective system for managing [queues](https://laravel.com/docs/master/queues) so Lumen, based on Laravel, can use the queue API.

### Running the Queue Worker

{: .fs-2 }
(excerpt from Laravel queue docs on [running the queue worker](https://laravel.com/docs/master/queues#running-the-queue-worker))

Laravel includes a queue worker that will process new jobs as they are pushed onto the queue. You may run the worker using the queue:work Artisan command. Note that once the  queue:work command has started, it will continue to run until it is manually stopped or you close your terminal:

```
$ php artisan queue:work
```

{: .alert .alert-primary }
To keep the `queue:work` process running permanently in the background, you should use a process monitor such as [Supervisor](https://laravel.com/docs/master/queues#supervisor-configuration) to ensure that the queue worker does not stop running.

## PHP + Kafka Libraries

This project looks like it could be a useful driver to add to a Laravel Lumen microservice:

- Kafka Queue driver for Laravel: [https://github.com/rapideinternet/laravel-queue-kafka](https://github.com/rapideinternet/laravel-queue-kafka)

**Supported versions of Laravel**
Tested on: [5.4, 5.5, 5.6, 5.7]

### Alternatives

See also:

- [https://github.com/arquivei/laravel-kafka-queue-connector](https://github.com/arquivei/laravel-kafka-queue-connector)
- [https://github.com/Superbalist/php-pubsub-kafka](https://github.com/Superbalist/php-pubsub-kafka)