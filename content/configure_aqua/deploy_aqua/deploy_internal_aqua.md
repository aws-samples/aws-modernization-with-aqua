+++
title = "Deploy with PostGreSQL container"
date = 2020-06-16T19:01:12-04:00
weight = 7
chapter = false
pre = "<b></b>"
+++

Launch **Aqua Enterprise** in an Amazon EKS cluster and secure your artifacts, hosts and workloads with Aqua. Well-suited for non-production deployments, it allows you to hit the ground running while providing a sneak peak into Aqua's full-blown cloud-native security capabilities.

## Deploy Aqua Enterprise Platform using containerized PostGres

Go to the AWS Cloud9 IDE and follow the steps in succession.

```shell
aquactl download all --platform eks --version 2022.4 --output-dir workshop
```

![aquactl install](/images/configure_aqua/aquactl-install-new.png)

```shell
kubectl create ns aqua
```

{{% notice info %}}
Make sure that you have the Registry login and license. For the AWS Workshop you will be provided with a username and password.
{{% /notice %}}

```shell
kubectl create secret docker-registry aqua-registry --docker-server=registry.aquasec.com --docker-username=<username> --docker-password=<password> -n aqua
```

Deploy Aqua using the following command

```shell
rm -f workshop/009-aqua-kube*
kubectl apply -f workshop/
```

![aquactl output](/images/configure_aqua/aquactl-internal-output-new.png)

Note the Aqua Console Service endpoint.

```shell
AQUA_ELB=$(kubectl get svc aqua-web --namespace aqua -o jsonpath="{.status.loadBalancer.ingress[0].hostname}")

AQUA_CONSOLE="http://$AQUA_ELB:8080"

echo $AQUA_CONSOLE
```

## Login to the Aqua Console

Open a browser and log in to the Aqua Console using the ```AQUA_CONSOLE``` URL from the above output, and create the Aqua administrator password.
![aqua console](/images/configure_aqua/aqua-console-new.png)

Once you are logged in, enter the Aqua license token from your Aqua account.

![aqua license](/images/configure_aqua/aqua-license-new.png)
