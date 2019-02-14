---
layout: default
title: Infrastructure
permalink: infrastructure
nav_order: 4
has_children: true
---
# Infrastructure

All services are hosted on Amazon Web Services (AWS).

Containers are stored in ECR. New ECRs can be requested.

The Data Store is held in RDS and is accessible through a jump host.

Any new services can be provisioned in the VPC on a private subnet accessible through the jump host.
