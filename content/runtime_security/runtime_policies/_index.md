+++
title = "Configuring Runtime Policy"
date = 2020-06-16T19:01:12-04:00
weight = 8
chapter = true
pre = "<b></b>"
+++

## Configure Runtime policy in Aqua


### Runtime Policy
A runtime policy has three parts:

* Scope — You can create a blanket policy that can be applied to the entire environment. You can also use granular scoping mechanisms based on image attributes, container attributes, or even Kubernetes constructs like pods, deployments, etc.
* Enforcement Mode — You can apply the policy in an Audit mode for current state assessment of your environment, which allows you to perform discovery and provides deeper insight into cloud-native workloads. Switch to the Enforcement mode for actively blocking or enforcing the specified policies.
* Controls — These are security-related tests that are conducted by the Aqua Enforcer while the workload is running.

#### Update the default runtime policy in Aqua Console
In the Aqua Platform console, go to the Policies tab on the left and select Runtime Policies. In the screen that appears, select 'Aqua default runtime policy' of type Container.

![runtime policy](/images/runtime_security/runtime-policy.png)

Once inside the policy, add the security controls indicated below. 

![runtime criteria](/images/runtime_security/sec-controls.png)

Set the policy to Enforcement Mode

![runtime enforce](/images/runtime_security/enforce.png)

Click on ```Save``` to save your work.