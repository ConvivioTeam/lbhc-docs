---
layout: default
title: Services
parent: Data Store
grand_parent: Microservices
nav_order: 3
permalink: microservices/datastore/services
---

# Services

## Structure

| Column         | Type          | Comment |
|----------------|---------------|---------|
| id             | char(36)      |         |
| name           | varchar(255)  |         |
| desc           | varchar(255)  |         |
| provider_id    | char(36)      |         |
| event_id       | char(36) NULL |         |
| elegibility_id | char(36) NULL |         |
| costoption_id  | char(36) NULL |         |
| created        | datetime      |         |
| updated        | datetime      |         |
| flagged        | tinyint(1)    |         |
