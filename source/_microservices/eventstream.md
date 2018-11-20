---
layout: default
title: Event Stream
parent: Microservices
nav_order: 2
---
# Event Stream Microservice

The event stream is the heart of the microservice ecosystem.

Built on [Apache Kafka](https://kafka.apache.org/), the event stream allows each microservice to function independently of the next, simply waiting for an appropriate event in the event stream to trigger an action. Once it has completed its action, if appropriate, it may put an event back into the event stream to trigger a downstream or dependent microservice.

This sequence allows microservices to function without causing dependency failures. I.e. a failure in one microservice should not be allowed cause the whole system to fail or to cause cascading errors.

Each microservice will need to include an event sourcing sub-system to respond to relevant events in the event stream for the microservice.

There are many code libraries available for interacting with Apache Kafka.

## Microservices and Event Streaming

### Further reading

#### Videos

- Guido Schmutz, Oracle Code 2018 — [Building Event Driven MicroServices with Apache Kafka](https://www.youtube.com/watch?v=llgU1UqL2JQ)
- Chris Richardson, DockerCon 2016 — [Microservices + Events + Docker = A Perfect Trio](https://www.youtube.com/watch?v=sSm2dRarhPo)

#### Blogs

- ThoughtWorks — [Scaling Microservices with an Event Stream](https://www.thoughtworks.com/insights/blog/scaling-microservices-event-stream)
- Capital One Tech — [Event-Streaming: An Additional Architectural Style to Supplement API Design](https://medium.com/capital-one-tech/event-streaming-an-additional-architectural-style-to-supplement-api-design-703c4f801722)