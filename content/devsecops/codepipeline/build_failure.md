---
title: "Non-compliant build"
date: 2018-10-03T10:14:32-07:00
draft: false
weight: 3
---


Open [CodePipeline in the Management Console](https://console.aws.amazon.com/codesuite/codepipeline/pipelines). You will see a CodePipeline that starts with **aqua-devsecops**. Click the link to view the details.

Once you are on the details page for the specific CodePipeline, you can see that a new CodePipeline has already been triggered. 
Notice the pipeline fails during the Build phase because of the Aqua scanner step with a Build error below, in the CodeBuild Phase details. 
![Build failure](/images/devsecops/build-failed-new.png)

You can also check out the **Phase Details** in the CodeBuild project to see that the Aqua scanner step has failed.
![Build phase error](/images/devsecops/build-phase-new.png)


Aqua scanner generates a report from the automated scan which is saved as an aqua.html artifact in the CodePipeline artifact location. This can be retrieved by clicking on **Build details** tab in the CodeBuild console and scrolling to the **Artifacts** section.
![Artifact location](/images/devsecops/artifact-location-new.png)

Click on the **Artifacts upload location**, download the zipped artifact file and extract the **aqua.html** file. Aqua provides an HTML output outlining the root cause of pipeline failure based on the assurance policies you defined previously.
![CodePipeline artifact 1](/images/devsecops/aqua-ci-artifact1-new.png)

Clicking on the **Vulnerabilities** tab also shows the various vulnerabilities that were detected in the image, and whether a fix is available.
![CodePipeline artifact 2](/images/devsecops/aqua-ci-artifact2-new.png)
{{% children showhidden="false" %}}

You can also go to the **Aqua Console** and view the details of the non-compliant image.
![CI/CD scan](/images/devsecops/ci-cd-scan-new.png)

