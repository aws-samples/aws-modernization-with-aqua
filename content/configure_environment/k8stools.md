---
title: "Install Kubernetes Tools"
chapter: false
weight: 15
---

Amazon EKS clusters require kubectl and kubelet binaries and the aws-cli or aws-iam-authenticator
binary to allow IAM authentication for your Kubernetes cluster.

{{% notice tip %}}
In this workshop we will give you the commands to download the Linux
binaries. If you are running Mac OSX / Windows, please [see the official EKS docs
for the download links.](https://docs.aws.amazon.com/eks/latest/userguide/getting-started.html)
{{% /notice %}}

#### Install kubectl


{{% notice note %}}
In this workshop we will be using Kubernetes v1.21. You must use a kubectl version that is within one minor version difference of your Amazon EKS cluster control plane. For example, a 1.21 kubectl client works with Kubernetes 1.20, 1.21, and 1.22 clusters.
{{% /notice %}}

```bash
sudo curl --silent --location -o /usr/local/bin/kubectl \
  https://s3.us-west-2.amazonaws.com/amazon-eks/1.21.2/2021-07-05/bin/linux/amd64/kubectl

sudo chmod +x /usr/local/bin/kubectl
```

#### Update awscli

Upgrade AWS CLI according to guidance in [AWS documentation](https://docs.aws.amazon.com/cli/latest/userguide/install-linux.html).

```bash
sudo pip install --upgrade awscli && hash -r
```

#### Install jq, envsubst (from GNU gettext utilities) and bash-completion

```bash
sudo yum -y install jq gettext bash-completion moreutils
```


#### Verify the binaries are in the path and executable

```bash
for command in kubectl jq aws
  do
    which $command &>/dev/null && echo "$command in path" || echo "$command NOT FOUND"
  done
```

#### Enable kubectl bash_completion

```bash
kubectl completion bash >>  ~/.bash_completion
. /etc/profile.d/bash_completion.sh
. ~/.bash_completion
```

