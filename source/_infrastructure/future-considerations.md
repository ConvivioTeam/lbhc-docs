---
layout: default
title: Future Considerations
parent: Infrastructure
nav_order: 2
---
# Future Considerations

## Kubernetes

With the microservice architecture inherently built into the project it makes sense to use a container orchestration system like [Kubernetes](https://kubernetes.io/).

Each component of the application has been built with the idea of scaling in mind so K8s is a perfect tool for deploying the containerised parts of the application. Special consideration should be given to persistent data such as the Data Store. Currently the Data Store storage (AWS RDS) but this could be brought into K8s if needed.

## Helm

Because K8s is quite complex to get an application up and running Helm was created to provide an abstraction layer. Building a Helm chart would be a great way of documenting and deploying K8s in production.

## Kubernetes on EKS

AWS now supports Kubernetes on their cloud platform however it isn't available in London yet so while it would be good to keep all components with the same provider it's out of scope until it support the UK.

## Further Reading

[Deploy your first scaleable PHP/MySQL Web application in Kubernetes
](https://medium.com/devopslinks/deploy-your-first-scaleable-php-mysql-web-application-in-kubernetes-33ed7ab66595)

[Learning Kubernetes on EKS by Doing Part 1— Setting Up EKS](https://medium.com/devopslinks/learning-kubernetes-by-doing-part-1-setting-up-eks-in-aws-50dcf7a76247)
