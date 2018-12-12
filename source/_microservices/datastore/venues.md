---
layout: default
title: Venues
parent: Data Store
grand_parent: Microservices
nav_order: 3
permalink: microservices/datastore/venues
---

# Venues

## Structure

| Column      | Type          | Comment |
|-------------|---------------|---------|
| id          | char(36)      |         |
| service_id  | char(36)      |         |
| provider_id | char(36) NULL |         |
| name        | varchar(255)  |         |
| address     | varchar(255)  |         |
| details     | varchar(255)  |         |
| created     | datetime      |         |
| updated     | datetime      |         |
| flagged     | tinyint(1)    |         |
