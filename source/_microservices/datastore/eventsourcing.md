---
layout: default
title: Data Store
parent: Data Store
has_children: false
nav_order: 3
permalink: microservices/datastore/eventsourcing
---

# Data store: event sourcing

The Data Store microservice is built with [Laravel Lumen](https://lumen.laravel.com). It is a small PHP application.

The data store microservice uses [Laravel queues in Lumen](https://lumen.laravel.com/docs/5.7/queues) to source jobs from the [event store microservice]({% link _microservices/eventstream/index.md %}).

