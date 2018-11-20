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

![Directory of services process model design](/assets/images/microservices/dos-process-model-v0.2.png)

## Microservices and Event Streaming

### Further reading

#### Videos

- Guido Schmutz, Oracle Code 2018 — [Building Event Driven MicroServices with Apache Kafka](https://www.youtube.com/watch?v=llgU1UqL2JQ)
- Chris Richardson, DockerCon 2016 — [Microservices + Events + Docker = A Perfect Trio](https://www.youtube.com/watch?v=sSm2dRarhPo)

#### Blogs

- ThoughtWorks — [Scaling Microservices with an Event Stream](https://www.thoughtworks.com/insights/blog/scaling-microservices-event-stream)
- Capital One Tech — [Event-Streaming: An Additional Architectural Style to Supplement API Design](https://medium.com/capital-one-tech/event-streaming-an-additional-architectural-style-to-supplement-api-design-703c4f801722)