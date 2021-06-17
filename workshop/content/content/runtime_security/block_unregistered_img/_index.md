+++
title = "Unregistered Images"
date = 2020-06-16T19:01:12-04:00
weight = 9
chapter = true
pre = "<b></b>"
+++

## Unregistered Images
These are images that are not registered in the Aqua console, either via the CI/CD Pipeline or the Container Image Registries. These could be images that were pulled to a host from outside of Aqua, or before Aqua was installed on the host.

Let's try to deploy an application whose image is not registered in Aqua. Run this command to deploy nginx.
```bash
kubectl create deploy nginx --image=nginx:latest
```

This will try to deploy the nginx application, but it will fail due to our runtime policy. We can check out the error by running the following command until the status of the nginx pod reports ```RunContainerError```:
```shell
kubectl get pods -w
```

![nginx-create](/images/runtime_security/nginx-create.png)

You can describe the pod status as follows:
```shell
kubectl describe pod <name>
```

![aqua-error](/images/runtime_security/aqua-error.png)

## Registering an image with Aqua
Now let's register the Nginx image with Aqua using the console.

Navigate to the menu on the left and click on ```Images``` and add an image.
![add-img1](/images/runtime_security/add-img.png)

Select Docker Hub in the Registry drop-down and search for ```nginx``` with tag ```latest```.
![add-img2](/images/runtime_security/add-img2.png)

Wait for the image to be scanned and registered with Aqua
![img-scanned](/images/runtime_security/img-scanned.png)

Now if we create the ```nginx``` deployment again, this time it will work.
```bash
kubectl create deploy nginx --image=nginx:latest
kubectl get po -w
```
![img-registered](/images/runtime_security/img-registered.png)
