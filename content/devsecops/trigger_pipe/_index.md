---
title: "Trigger a new release"
date: 2018-10-03T10:14:32-07:00
draft: false
weight: 18
---

In order for the build to succeed, we can go to the **Aqua Console** and modify the **Assurance policy** that we created [previously](/devsecops/assurance).
![Modify assurance](/images/devsecops/modify-assurance.png)

Once you have modified the policy go back to the [CodePipeline in the Management Console](https://console.aws.amazon.com/codesuite/codepipeline/pipelines). On the details page for our CodePipeline, click on **Release Change** to trigger a new pipeline. 
![Trigger pipeline](/images/devsecops/trigger-pipeline.png)

Notice this time, the pipeline succeeds. 
![Build success](/images/devsecops/build-success.png)

Since the pipeline has succeeded, the application also has been successfully deployed to the Amazon EKS cluster. Check out the output of the following command in the Cloud9 IDE
```shell
kubectl get pods
```

![kubectl output](/images/devsecops/kubectl.png)

You can also check out in the **Aqua Console** that the application has also been deployed, by clicking on Risk Explorer.
![application](/images/devsecops/risk-explorer.png)


