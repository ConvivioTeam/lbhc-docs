---
layout: default
title: Secrets Management
parent: Infrastructure
nav_order: 2
---
# Secrets Management

[Vault](https://www.vaultproject.io/) should be used to manage secrets it has a REST api which can be used to query secrets.

Many CI tools have built in support for Vault, this makes retrieving secrets in a build pipeline easy. The resulting images can then be securely stored on ECS.
