+++
title = "Module 1: DevSecOps"
weight = 4
chapter = true
pre = "<b></b>"
+++

# Module 1: DevSecOps

DevSecOps, sometimes called security as code, integrates security best practices into a DevOps pipeline instead of bolting them on at the end. It’s a new security paradigm that can evolve with fast-changing security requirements.

![Title Image](/images/devsecops/devsecops-arch.png)

##  Instrumenting DevSecOps using Aqua and AWS CodePipeline
Due to their immutable nature, container workloads are most likely an output of a CI/CD pipeline, where code flows only in one direction: from artifacts to full-fledged workloads running in production. DevSecOps aligns with the Shift Left movement and incorporates Security as a first-class citizen in your DevOps workflows, to uncover security issues at the inception of the application.
To help us in this regard, we use AWS CodePipeline. It automates the build, test, and deploy phases of your release process every time there's a code change, based on the release model you define. 

The build phase is the best time to reduce the attack surface as there is less complexity and interdependency involved. We approach Aqua has the most powerful and accurate scanner out there that weeds out bad configuration, embedded secrets and vulnerabilities with the least number of false positives, making sure that you are starting with a secure foundation right out the gate.


## Learning Objective
* Integrating with AWS CodePipeline for scanning artifacts
* Understand the scan report and remediation advice
* Deploying clean artifacts to Amazon EKS
