---
layout: default
title: Data Store
parent: Microservices
nav_order: 3
permalink: microservices/datastore
---
# Data store microservice

Stores and retrieves the data of the directory of service.

Contains data for:

- **Providers**
- **Services**
- **Eligibility**
- **Cost options**
- **Events**, including attending info
- **Contacts**
- **Venues**
- **Taxonomy**, including
  - category
  - function
  - type
  - deliverable type
  - tag

## Repository

Code for the DoS Data Store microservice is in the [https://github.com/LBHackney-IT/DoS-data-store-service](https://github.com/LBHackney-IT/DoS-data-store-service) repository.

## Functionality

This service provide the following functionality:

* Creation of production and development databases
* Migration handler for database updates
* Model and Object definitions
