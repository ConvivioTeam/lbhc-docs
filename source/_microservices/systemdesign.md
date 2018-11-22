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

## Loosley-coupled

### Bad, bad, not good

In a *close-coupled* microservice system design, individual microservices can call APIs on each other, making the functioning of one microservice dependent on the functioning of one or many others. A problem with an upstream microservice can cause the current microservice to fail, allowing others downstream to fail also.

### Better

*Loosely-coupling* microservices removes that dependency.

Instead, each microservice publishes events to a shared event store or event stream when it completes a task or its state changes. At the same time, the microservice subscribes to events in the event store, which may trigger it to perform actions.

This means that each transaction may take the form of a [saga](https://microservices.io/patterns/data/saga.html), a sequence of local transactions. Each local transaction updates the performs an action or updates the state of an item (such as saving to a database) and publishes a message or event to trigger the next local transaction in the saga.  Failure can be handled with a series of compensating actions that undo any changes made by preceding local transactions.

### Command Query Responsibility Segregation (CQRS)

This allows the two sets of actions to be segregated effectively into two parts: the command-side and the query-side.

**Command actions:** Create, update or delete (HTTP POST, PUT/PATCH, DELETE requests) actions, which emits events when data changes.
**Query actions:** handles queries by executing them against one or more views that are kept up to date by subscribing to the stream of events emitted when data changes.

## Design (v0.2)

### Design schematics

#### Process design

  ![Directory of services process model design]({{ 'assets/images/microservices/dos-process-model-v0.2.png' | relative_url }})
  
#### System design

  ![Directory of services system model design]({{ 'assets/images/microservices/dos-system-model-v0.1.png' | relative_url }})
