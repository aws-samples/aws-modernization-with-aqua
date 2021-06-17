+++
title = "Scanning an image"
date = 2020-06-16T19:01:12-04:00
weight = 30
chapter = true
pre = "<b></b>"
+++

## Registering an image with Aqua
Once you have successfully enabled the integration you can easily add and scan images from the registry. Aqua provides an easier way to search for the right repositories in the registry for adding images. 

In the Aqua console, go to the ```Images``` tab and click on ```Add Image```. Select the ECR registry in the dropdown and search for **ecr**. You will see the ECR registry pop up up and you can click on it and add the relevant images by selecting the tags.
![ECR integration](/images/ecr-scanning/add-img.png)

As soon as you click on ```Add image```, it will be added to the Scan queue. Select Scan Queue to check the progress of the image scan.
![ECR registry](/images/ecr-scanning/scan-queue.png)

Once the scan is completed, Aqua generates a comprehensive report of all the security risks found, and includes detailed and actionable information of the various vulnerabilities, malware, and any embedded sensitive data in the image.
![Image scan](/images/ecr-scanning/image-scan.png)

Now that the image is registered with Aqua, any subsequent pods using that image will not be blocked, and will spin up successfully.



