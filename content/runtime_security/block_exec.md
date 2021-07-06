+++
title = "Block Container Exec"
date = 2020-06-16T19:01:12-04:00
weight = 10
chapter = true
pre = "<b></b>"
+++

## Block Container Exec
The easiest way to gain access to a running container and executing commands against it is ```kubectl exec``` 
Attackers with permissions could run ```kubectl exec``` to execute malicious code and compromise resources within a cluster.

Aqua has a security control that prevents an attacker from gaining any form of shell access to running containers. 

```shell
kubectl exec -it <pod_name> bash
```

As you can see Aqua blocks this attempt successfully.
![block-exec](/images/runtime_security/block-exec.png)

Let's go ahead and remove this security control for the runtime policy so that we can move on to Drift Prevention.

Navigate to ```Policies``` > ```Runtime Policies``` > ```Aqua default runtime policy``` and remove the control for ```Block Container Exec```.
![remove-exec](/images/runtime_security/remove-exec.png)

We can also add a new control to block a certain executable ```date```
![block-date](/images/runtime_security/block-date.png)
