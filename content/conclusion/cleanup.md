---
title: "Cleanup"
draft: false
weight: 15
---

## Cleanup

To remove the Aqua deployment and the Amazon EKS cluster, run the following commands inside the AWS Cloud9 IDE:

```shell
kubectl delete ns aqua
eksctl delete cluster --name=$CLUSTER --region=$AWS_REGION
```

Thank you!
