+++
title = "Creating an Amazon EKS cluster"
date = 2020-06-16T19:01:12-04:00
weight = 5
chapter = false
pre = "<b></b>"
+++

Amazon Elastic Kubernetes Service (Amazon EKS) is a fully managed Kubernetes service, trusted to run the most sensitive and mission critical applications because of its security, reliability, and scalability. 

{{% notice note %}}
If you are running this workshop at an AWS hosted event, a 3 node cluster with the name "eksworkshop-eksctl" will be pre-created for you. Please skip cluster creation step listed below.
{{% /notice %}}



## EKS Cluster creation
```shell
CLUSTER="aqua-<name>"
```

```shell
eksctl create cluster --name ${CLUSTER} --region ${AWS_REGION} --zones ${AWS_REGION}a,${AWS_REGION}b
```

{{% notice info %}}
Launching EKS and all the dependencies will take approximately 15 minutes
{{% /notice %}}





## Verify the cluster
#### Test the cluster:

Get cluster Name and Region:

```bash
eksctl get clusters
```

Update kubeconfig:
```bash
aws eks update-kubeconfig --name <CLUSTER_NAME> --region <REGION>
```

Confirm your nodes:
```bash
kubectl get nodes # if we see our 3 nodes, we know we have authenticated correctly
```

#### Export the Worker Role Name for use throughout the workshop:

```bash
STACK_NAME=$(eksctl get nodegroup --cluster $CLUSTER -o json | jq -r '.[].StackName')
ROLE_NAME=$(aws cloudformation describe-stack-resources --stack-name $STACK_NAME | jq -r '.StackResources[] | select(.ResourceType=="AWS::IAM::Role") | .PhysicalResourceId')
echo "export ROLE_NAME=${ROLE_NAME}" | tee -a ~/.bash_profile
```

#### Congratulations!

You now have a fully working Amazon EKS Cluster that is ready to use!
