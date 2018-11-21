---
layout: default
title: API Gateway
parent: Microservices
nav_order: 2
permalink: microservices/apigateway
---
# API Gateway microservice

The API Gateway microservice provides the interface from the public internet into the Directory of Services system. Its main function is handle RESTful requests from outside the system, pass the request (and associated data, as appropriate) into the event stream, and then consume appropriate response(s) in the event stream and handle sending that back in the HTTP reponse.

## Repository

Code for the DoS API Gateway microservice is in the [https://github.com/LBHackney-IT/DoS-api-gateway](https://github.com/LBHackney-IT/DoS-api-gateway) repository.

## API Spec doc

View the spec at SwaggerHub (@todo – swaggerhub link).

View the raw spec document at [https://github.com/LBHackney-IT/DoS-api-gateway/blob/master/docs/api/api-gateway.openapi.yml](https://github.com/LBHackney-IT/DoS-api-gateway/blob/master/docs/api/api-gateway.openapi.yml)
