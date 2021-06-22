+++
title = "Deploying Aqua Enterprise Platform"
date = 2020-06-16T19:01:12-04:00
weight = 6
chapter = false
pre = "<b></b>"
+++

You can deploy the Aqua Enterprise Platform application in an existing Amazon EKS cluster in a separate namespace. For easier scaling and high-availability, deploy it in an Amazon EKS cluster of its own in a separate virtual private cloud (VPC).

Architected as a microservices application for self-hosting, the Aqua platform is outputted as containers in the form of Kubernetes-native deployments, tailored using Helm charts.

Aqua provides multiple deployment scenarios to best suits your needs. Follow one of the following depending on your requirements:

* [Containerized PostGreSQL](deploy_internal_aqua): Well-suited for non-production deployments
* [Managed Amazon RDS](deploy_rds_aqua): Enterprise-grade deployment with managed PostgreSQL RDS Database