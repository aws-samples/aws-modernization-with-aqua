+++
title = "Installing pre-requisites"
date = 2020-06-16T19:01:12-04:00
weight = 3
chapter = false
pre = "<b></b>"
+++

## Installing eksctl for managing Amazon EKS
```shell
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

sudo mv /tmp/eksctl /usr/local/bin

eksctl version
```

## Installing aquactl for managing Aqua operations
The interactive Aqua Security aquactl command line tool simplifies the deployment of Aqua Platform on a variety of environments, including Amazon EKS. 

```shell

curl -O https://get.aquasec.com/aquactl/v3/aquactl && chmod +x ./aquactl

./aquactl --help
```                                                 
