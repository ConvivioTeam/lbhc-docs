---
layout: default
title: CI/CD Pipeline
parent: Infrastructure
nav_order: 2
---
# CI/CD Pipeline

CI and CD is provided by [Jenkins](https://jenkins.io/).

Each job is configured using [Jenkins Declarative Pipelines](https://jenkins.io/doc/book/pipeline/syntax/).

Pipeline files should be contained within the services repo to allow developers to modify the build process if required.