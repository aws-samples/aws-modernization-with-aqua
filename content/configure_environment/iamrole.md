---
title: "Create an IAM role for your Workspace"
chapter: false
weight: 16
---

**If you are running this workshop at an AWS hosted event, please note that there will be an IAM role created for you. Please ignore this step if you are runnining this at an AWS hosted event.**

If you are running this workshop on your own please follow the steps below:

1. Follow [this deep link to create an IAM role with Administrator access.](https://console.aws.amazon.com/iam/home#/roles$new?step=review&commonUseCase=EC2%2BEC2&selectedUseCase=EC2&policies=arn:aws:iam::aws:policy%2FAdministratorAccess)
2. Confirm that **AWS service** and **EC2** are selected, then click **Next** to view permissions.
3. Confirm that **AdministratorAccess** is checked, then click **Next: Tags** to assign tags.
4. Take the defaults, and click **Next: Review** to review.
5. Enter **aqua-workshop-admin** for the Name, and click **Create role**.
![createrole](/images/create-role-new.png)
