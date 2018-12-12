---
layout: default
title: Providers
parent: Data Store
grand_parent: Microservices
nav_order: 1
permalink: microservices/datastore/providers
---

# Providers

## Structure

| Column     | Type          | Comment |
|------------|---------------|---------|
| id         | char(36)      |         |
| name       | varchar(255)  |         |
| published  | tinyint(1)    |         |
| venue_id   | char(36) NULL |         |
| contact_id | char(36) NULL |         |
| created    | datetime      |         |
| updated    | datetime      |         |
| flagged    | tinyint(1)    |         |
