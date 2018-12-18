---
layout: default
title: Data Store
parent: Microservices
has_children: true
nav_order: 3
permalink: microservices/datastore
---
# Data store microservice

Stores and retrieves the data of the directory of service.

Contains data for:

- **[Providers](/microservices/datastore/providers)**
- **[Services](/microservices/datastore/services)**
- **[Eligibility](/microservices/datastore/eligibilities)**
- **[Cost options](/microservices/datastore/costoptions)**
- **[Events](/microservices/datastore/events)**
- **[Contacts](/microservices/datastore/contacts)**
- **[Venues](/microservices/datastore/venues)**
- **[Taxonomy](/microservices/datastore/taxonomy)**
- **[Taxonomy Reference](/microservices/datastore/taxonomy_ref)**

## Repository

Code for the DoS Data Store microservice is in the [https://github.com/LBHackney-IT/DoS-data-store-service](https://github.com/LBHackney-IT/DoS-data-store-service) repository.

## Functionality

This service provide the following functionality:

* Creation of production and development databases
* Migration handler for database updates
* Model and Object definitions

## Build and Deployment

[Drone CI](https://drone.io/) is used to build and push the Docker image to Amazon ECR. It can be access [here](https://drone.hc-dos.co.uk).

The database build and migration service has the following workflow:

1. Database changes are made to the app and pushed to ```master```
2. Drone CI builds the docker image
3. Drone CI pushes the docker image to AWS ECR

Future work:

* Expand CI pipeline to deploy to ECS and run database migrations
* Validation of any changes to the database
* Reporting of any changes to the database
