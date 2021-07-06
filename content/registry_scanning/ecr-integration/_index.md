+++
title = "ECR Integration"
date = 2020-06-16T19:01:12-04:00
weight = 30
chapter = true
pre = "<b></b>"
+++


## Enable the ECR integration
Enabling the integration is a quick one-step configuration. This allows you to automatically scan ECR images for vulnerabilities, check their security status and apply image assurance policies to ensure that only approved images are allowed to run.

![ECR integration](/images/ecr-scanning/add-ecr-int.png)

The wizard takes in following details:
* Registry Type
* AWS Region
* Access delegation Role

For access delegation, add the Role ARN for the CodePipeline by running the following command and inputting the ARN in the wizard. 
```bash
aws iam get-role --role-name AquaWorkshopCodeBuildKubectlRole --output text --query 'Role.Arn'
```
![ECR registry](/images/ecr-scanning/register-ecr.png)

Once you have added the information, click on **Test Connection** to verify connectivity. 
![test connectivity](/images/ecr-scanning/test-connection.png)

You can also click on **Registry Configuration** to enable automatic scanning instead of on-demand.

And finally click on **Save** to add the integration.