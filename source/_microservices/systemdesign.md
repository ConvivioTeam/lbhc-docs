---
layout: default
title: System Design
parent: Microservices
nav_order: 1
permalink: microservices/systemdesign
---

# System Design and Architecture

The system is designed with a loosely-coupled event-driven microservice architecture. An event stream sits at the core of the architecture as the mode of communication between services. Each microservice includes event sourcing and event creation routines.

The event stream microservice is built on [Apache Kafka](https://kafka.apache.org/).

**Design v0.2**

  ![Directory of services process model design]({{ 'assets/images/microservices/dos-process-model-v0.2.png' | relative_url }})
 