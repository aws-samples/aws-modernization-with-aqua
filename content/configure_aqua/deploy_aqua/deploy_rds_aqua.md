+++
title = "Deploy with Amazon RDS"
date = 2020-06-16T19:01:12-04:00
weight = 9
chapter = false
pre = "<b></b>"
+++

Launch **Aqua Enterprise** platform in a new or existing EKS cluster with a enterprise-grade managed **PostgreSQL RDS Database**. Simplified deployment leveraging CloudFormation template and aquactl CLI tool for a better customer experience.

## Create an Amazon RDS Postgres database for Aqua Enterprise Platform
Aqua Enterprise Platform requires a Postgres database to store operational data such as policies, configuration data, and audit events. To provision Amazon RDS with a PostgreSQL engine option, launch this AWS CloudFormation template inside your AWS account.

### Deploy the Amazon RDS database

Click the **Launch** button to create the CloudFormation stack in the AWS Management Console.

| Launch template |  |  |
| ------ |:------:|:--------:|
| Aqua Postgres DB |  {{< cf-launch "AquaRDS.yaml" "aqua-rds" >}} | {{< cf-download "AquaRDS.yaml" >}}  |

![CFN RDS input](/images/configure_aqua/rds-cfn-input.png)

Obtain the RdsInstanceEndpoint in the AWS CloudFormation output, which you will be using in the next step.

![CFN RDS output](/images/configure_aqua/rds-cfn-output.png)

## Deploy Aqua Enterprise Platform using Amazon RDS
Go to the AWS Cloud9 IDE and follow the steps in succession.

```shell
./aquactl deploy csp 
```

{{% notice info %}}
It’s an interactive command line tool, so it prompts you to enter all the relevant options.
{{% /notice %}}

Respond to the aquactl command-line prompts shown in the figure.
These are:
* Aqua license details.
* Amazon RDS details (including Database IP or DNS URL).
* Aqua administrator password.

![aquactl output](/images/configure_aqua/aquactl-output.png)

Note the Aqua Console Service endpoint.

```shell
AQUA_ELB=$(kubectl get svc aqua-web --namespace aqua -o jsonpath="{.status.loadBalancer.ingress[0].hostname}")

AQUA_CONSOLE="http://$AQUA_ELB:8080"

echo $AQUA_CONSOLE
```

## Login to the Aqua Console
Open a browser and log in to the Aqua Console using the ```AQUA_CONSOLE``` URL from the above output, plus the Aqua administrator password.
![aqua console](/images/configure_aqua/aqua-console.png)

Once you are logged in, enter the Aqua license token from your Aqua account.

![aqua license](/images/configure_aqua/aqua-license.png)

