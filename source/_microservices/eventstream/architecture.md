---
layout: default
title: Event Stream Architecture
parent: Event Stream
grand_parent: Microservices
nav_order: 1
permalink: microservices/eventstream/architecture
---

# Event Stream Architecture

The Event Stream microservice is a simple system, consisting of two tools:

- **[Apache Kafka](https://kafka.apache.org/)**, the event stream itself;
- **[Apache Zookeeper](https://zookeeper.apache.org/)**, which maintains all the metadata about the Kafka cluster.

There is also a Traefik instance as reverse proxy and load balancer (_although, not sure it's actually needed since  connections to Kafka are over tcp_).