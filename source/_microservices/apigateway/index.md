---
layout: default
title: API Gateway
parent: Microservices
nav_order: 2
permalink: microservices/apigateway
---
# API Gateway microservice

The API Gateway microservice provides the interface from the public internet into the Directory of Services system. Its main function is handle RESTful requests from outside the system, pass the request (and associated data, as appropriate) into the event stream, and then consume appropriate response events in the event stream and handle sending that back in the HTTP reponse.

Endpoints are designed to be simple and easy to understand following a standard design pattern:

* API Endpoints should be singular e.g. `/provider` or `/provider/{id}`.
* Each endpoint must support GET, POST and PUT requests.
* When returning data to a request, the response should contain the full data object, including any updates.

## Repository

Code for the DoS API Gateway microservice is in the [https://github.com/LBHackney-IT/DoS-api-gateway](https://github.com/LBHackney-IT/DoS-api-gateway) repository.

## Technology Platform

The Scraper microservice is built with [Laravel Lumen](https://lumen.laravel.com). It is a small PHP application.

## Event Streaming

### Event Production

API requests should (generally) result in producing an event — to create, update or retrieve an entity.

### Event Sourcing

The API Gateway sources events from the event stream for the current complete view of each entity. This is done currently using the [Laravel queue worker](https://laravel.com/docs/5.7/queues#running-the-queue-worker).

#### Caching

To accelerate responses, a local cache is included in the API Gateway microservice, using Redis to store the entity views sourced from the event stream. Following a create (POST) or update (PUT) request, the new view of an entity (e.g. a service, or service provider organisation) is returned to the event stream. The API gateway sources these entity views and stores them in a local Redis store.

This may be replaced if a faster method for retrieving events in the event stream can be created than the Laravel queue worker currently used.

## API Spec doc

View the spec at [SwaggerHub](https://app.swaggerhub.com/apis-docs/LBHC/lbh-co_l_directory_of_services_gateway_api/1.0.0)

View the raw spec document at [https://github.com/LBHackney-IT/DoS-api-gateway/blob/master/docs/api/api-gateway.openapi.yml](https://github.com/LBHackney-IT/DoS-api-gateway/blob/master/docs/api/api-gateway.openapi.yml)
