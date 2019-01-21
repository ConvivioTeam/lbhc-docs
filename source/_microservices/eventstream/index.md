---
layout: default
title: Event Stream
parent: Microservices
has_children: true
nav_order: 2
permalink: microservices/eventstream
---
# Event Stream Microservice

The event stream is the heart of the microservice ecosystem.

## Overview

Built on [Apache Kafka](https://kafka.apache.org/), the event stream allows each microservice to function independently of the next, simply waiting for an appropriate event in the event stream to trigger an action.

Once it has completed its action it should put an event back into the event stream to trigger a downstream or dependent microservice. The item in the event stream should contain the *current view* of the item after the action has been taken.

This sequence gives three tangible benefits:

### 1. It explicitly supports [Command Query Responsibility Segregation (CQRS)](/microservices/systemdesign#command-query-responsibility-segregation-cqrs)

Command actions and query actions can and should function independently of each other.

- **Command actions** are sourced from events in the event stream, prompting a microservice to take action.
- Once it has completed its action, the microservice puts the *current view of the item* after the action back into the event stream.
- A **query action** then only needs to return the current view from the event stream.

### 2. Microservices only need to be able to interact with the event stream

Each microservice only needs to know how to:

1. source events from the event stream, and
2. create new events in the event stream

and do not need to know anything about the architecture of other services in the system.

This *greatly reduces complexity* in the overall system, and allows each microservice to substantially alter its features, functionality, architecture and more without fear of breaking dependent services.

### 3. It allows microservices to function without causing dependency failures

I.e. a failure in one microservice should not be allowed cause the whole system to fail or to cause cascading errors.

Each microservice will need to include an event sourcing sub-system to respond to relevant events in the event stream for the microservice.

## Architecture

The Event Stream microservice is a fairly simple system, consisting of two tools:

- **Apache Kafka**, the event stream itself;
- **Apache Zookeeper**, which maintains all the metadata about the Kafka cluster.

Read the documentation about the [event stream microservice architecture](./architecture) for more.

## Event sourcing

There are many code libraries available for interacting with Apache Kafka. Read the documentation on [event sourcing](./eventsourcing) for more.

## Further reading

We've gathered a list of materials for [further reading](./notes).
