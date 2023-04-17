---
title: "Configuring Assurance policy"
date: 2018-10-03T10:14:32-07:00
draft: false
weight: 12
---


Earlier in the workshop, you deployed the Aqua platform on the Amazon EKS cluster. One of the most notable and versatile Aqua components are the Enforcers. They are deployed as a Kubernetes DaemonSet on the EKS cluster and are responsible for the auto-discovery of assets, as well as enforcement of the policies defined in the Aqua Console.

## Configure Assurance policy in Aqua

### Static scanning with Aqua
Aqua Platform scans all build artifacts to generate a comprehensive report describing the image layers, package versions installed, the vulnerabilities found, and fixes, if any.

Aqua scans can also track the provenance of the images and code that make up your application, and evaluate them along with the overall security posture of the application. After the scan, Aqua provides actionable security advice based on a structured decision workflow: Remediate, Mitigate, or Accept.

### Assurance policy and compliance criteria
Once the images are scanned and the risk assessment is completed, you must decide whether the images are safe enough to run in production; in other words, they are in compliance. Assurance policies allow you to create a compliance gate, to make sure only clean artifacts are generated and allowed in the production environment.

It’s easy to create a sound assurance policy, in accordance with security best practices, by combining the various security controls provided by Aqua Platform.

#### Update the default assurance policy in Aqua Console
In the Aqua Platform console, go to the Policies tab on the left and select Assurance Policies. In the screen that appears, select Default policy of type Image.

![assurance policy](/images/devsecops/assurance-new.png)

Once inside the policy, add the security controls indicated below. 

Click on ```Save``` to save your work.

![assurance criteria](/images/devsecops/sec-controls-new.png)

For Aqua to serve as a security hook in the build pipeline, ensure the Fail Aqua step in CI/CD under Actions is checked. This causes AWS CodePipeline to fail if the image does not comply with the controls set in this policy. 

If you choose to uncheck the Fail the Aqua step in CI/CD field, then Aqua does not fail the build, but marks the image as non-compliant.

![actions](/images/devsecops/actions-new.png)


{{% children showhidden="false" %}}

