---
layout: default
title: Contacts
parent: Data Store
grand_parent: Microservices
nav_order: 3
permalink: microservices/datastore/contacts
---

# Contacts

## Structure

| Column          | Type              | Comment |
|-----------------|-------------------|---------|
| id              | char(36)          |         |
| url             | varchar(255) NULL |         |
| email           | varchar(255)      |         |
| name            | varchar(255)      |         |
| position        | varchar(255) NULL |         |
| social_facebook | varchar(255) NULL |         |
| social_twitter  | varchar(255) NULL |         |
| phonenumber     | varchar(255) NULL |         |
| created         | datetime          |         |
| updated         | datetime          |         |
| flagged         | tinyint(1)        |         |
