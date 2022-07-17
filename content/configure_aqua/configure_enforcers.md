+++
title = "Configuring Enforcers for Aqua Platform"
date = 2020-06-16T19:01:12-04:00
weight = 9
chapter = false
pre = "<b></b>"
+++

Aqua takes a policy-driven approach to enforce security for remediation and compliance. To do this effectively, it uses Aqua Enforcers to monitor the runtime activity of containers, collect information about the running workloads, and enforce security based on the policies defined. Aqua provides various types of Enforcers tailored specifically to the different deployment environments.

Aqua Enforcers for Amazon EKS are deployed as a Kubernetes DaemonSet on every cluster worker node to be managed by Aqua. DaemonSets ensure all Amazon EKS cluster nodes run a copy of a pod, and allow Aqua to run a daemon on every node. Enforcement can be applied to containers, hosts, and the network activity between them in the form of firewall policies.

Check the status of the Aqua Enforcers in the Aqua Console:
![edit enforcers](/images/configure_aqua/edit-enforcer.png)

Enable additional features and set them to Enforce mode:
![check enforcers](/images/configure_aqua/check-enforcer.png)

Congratulations! You have successfully deployed and configured the Aqua Platform!

