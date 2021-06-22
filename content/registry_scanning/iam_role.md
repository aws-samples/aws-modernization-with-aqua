+++
title = "Create IAM role"
date = 2020-06-16T19:01:12-04:00
weight = 5
chapter = true
pre = "<b></b>"
+++

Aqua platform uses AWS access delegation in order to connect and scan the Amazon ECR registry. 

## Obtain EKS Worker node IDs
These are used to maintain session for the assumed roles
```bash
NODES=$(kubectl get no -o json | jq -r '.items[].metadata.labels."alpha.eksctl.io/instance-id"')
NODE1=$(echo $NODES|cut -d" " -f1)
NODE2=$(echo $NODES|cut -d" " -f2)
IAM=$(eksctl get nodegroup --cluster $CLUSTER --output json| jq -r .[].NodeInstanceRoleARN | sed 's/role/assumed-role/')
```

## Create a policy for ECR access
In order for Aqua to access the ECR registry, we have to create an IAM role with a trust policy to perform ECR tasks which is restricted only to the EKS cluster nodes.
```bash
echo "{\"Version\": \"2012-10-17\", \"Statement\": [{ \"Sid\": \"VisualEditor0\", \"Effect\": \"Allow\", \"Action\": \"ecr:GetAuthorizationToken\", \"Resource\": \"*\" },{\"Sid\": \"VisualEditor1\", \"Effect\": \"Allow\", \"Action\": \"ecr:*\", \"Resource\": \"arn:aws:ecr:us-east-1:${ACCOUNT_ID}:repository/*\"}]}" > /tmp/iam-role-aqua-policy


ECR_TRUST="{ \"Version\": \"2012-10-17\", \"Statement\": [{ \"Effect\": \"Allow\", \"Principal\": { \"AWS\": \"arn:aws:iam::${ACCOUNT_ID}:root\" }, \"Action\": \"sts:AssumeRole\" },{\"Effect\": \"Allow\", \"Principal\": { \"AWS\": \"${IAM}/${NODE1}\"}, \"Action\": \"sts:AssumeRole\"}, {\"Effect\": \"Allow\", \"Principal\": { \"AWS\": \"${IAM}/${NODE2}\"}, \"Action\": \"sts:AssumeRole\"}]}"  

```


## Modify the IAM role
Once the policies are ready, it is time to update the existing **AquaWorkshopCodeBuildKubectlRole**
```bash
aws iam put-role-policy --role-name AquaWorkshopCodeBuildKubectlRole --policy-name ecr-describe --policy-document file:///tmp/iam-role-aqua-policy

aws iam update-assume-role-policy --role-name AquaWorkshopCodeBuildKubectlRole --policy-document "$ECR_TRUST"
```
