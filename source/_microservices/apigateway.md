---
layout: default
title: API Gateway
parent: Microservices
nav_order: 2
permalink: microservices/apigateway
---
# API Gateway microservice

The API Gateway microservice provides the interface from the public internet into the Directory of Services system. Its main function is handle RESTful requests from outside the system, pass the request (and associated data, as appropriate) into the event stream, and then consume appropriate response(s) in the event stream and handle sending that back in the HTTP reponse.

Endpoints are designed to be simple and easy to understand following a standard design pattern:

* Endpoints should be plural e.g. ```providers```
* Each endpoint must support GET POST and PUT requests
* When returning data from the response it should contain the full data object including any updates

## Repository

Code for the DoS API Gateway microservice is in the [https://github.com/LBHackney-IT/DoS-api-gateway](https://github.com/LBHackney-IT/DoS-api-gateway) repository.

## API Spec doc

View the spec at [SwaggerHub](https://app.swaggerhub.com/apis-docs/LBHC/lbh-co_l_directory_of_services_gateway_api/1.0.0)

View the raw spec document at [https://github.com/LBHackney-IT/DoS-api-gateway/blob/master/docs/api/api-gateway.openapi.yml](https://github.com/LBHackney-IT/DoS-api-gateway/blob/master/docs/api/api-gateway.openapi.yml)
