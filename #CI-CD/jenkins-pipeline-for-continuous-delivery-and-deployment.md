# Jenkins Pipeline for Continuous Delivery and Deployment

_Captured: 2017-12-15 at 17:41 from [dzone.com](https://dzone.com/articles/jenkins-pipeline-for-continuous-delivery-and-deplo?edition=342138&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202017-12-15)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

Before we show how we can apply continuous delivery and deployment using Jenkins pipeline as code, we need to refresh our mind about the difference between continuous integration, delivery, and deployment, as shown below:

![Screen Shot 2017-12-03 at 15.12.06.png](https://mromeh.files.wordpress.com/2017/12/screen-shot-2017-12-03-at-15-12-06.png)

## **Release Process and Versioning in Continuous Delivery **

Basically, I am not a big fan of the Maven release plugin for several reasons. Let's consider the principles of continuous delivery:

  * "Every build is a potential release."
  * "The team needs to eliminate manual bottlenecks."
  * "The team needs to automate wherever possible."

Current drawbacks and limitations of the Maven release method:

  * Overhead. The maven-release plugin runs three (!) full build and test cycles, manipulates the pom twice, and creates three Git revisions.
  * Not isolated. The plugin can easily get into a mess when someone else commits changes during the release build.
  * Not atomic. If something went wrong in the last step (e.g. during the artifact upload), we are facing an invalid state. We have to clean up the created Git tag, Git revisions, and fix the wrong version in the pom manually.

Let us simplify the versioning process in an efficient way within our continuous delivery model by

  * Checking out the software as it is,
  * Building, testing, and packaging it, 
  * Giving it a version so it can be uniquely identified and tractable (release step),

Version=**Major.Minor.Patch.GitCommit-Id**

  * Deploying it to an artifact repository where it can then be picked for the actual roll out on target machines, and
  * Tagging this state in SCM so it can be associated with the matching artifact.

This means:

  * Every artifact is potentially shippable, so there is no need for a dedicated release workflow anymore! 
    * The delivery pipeline is significantly simplified and automated.
    * Traceability. It's obvious which commits are included.
![Screen Shot 2017-12-03 at 15.35.41](https://mromeh.files.wordpress.com/2017/12/screen-shot-2017-12-03-at-15-35-41.png)

So how we can implement continuous delivery and a conditional continuous deployment using a Jenkins pipeline? Of course, you can add more stages based into team process, like performance tests; just added until acceptance, as production will be just the same.

We will use a Jenkins pipeline as code as it gives more power to the team to control their delivery process:

  1. When a Git commit is triggered to the development branch, it will trigger the Jenkins pipeline to checkout the code, build it, unit test it, and if all is green, it will trigger the integration test plus Sonar check for your code quality gate.
  2. If all is green, deploy to the development server using the created package from Jenkins work space, or Nexus Snapshots, if you prefer.
  3. Then, if there is a release candidate (which means a merge request to your master branch), it will do the same steps as above, plus creating the release candidate using the release versioning explained above.
  4. Push the released artifact to Nexus and do acceptance deployment and auto acceptance functional testing.
  5. Prompt to production, and if it is approved, it will be deployed into production.
  6. Of course, deployment tasks must be automated if you need continuous deployment, using an automation tools like Ansible, or other options.

Now let us explain how it will be done via Jenkins Pipeline code, as the following:

<https://gist.github.com/Romeh/257056cae1730fe0c939b9f2b1b1436a>

You can use it by creating a multi-branch project in Jenkins and marking it to use the Jenkins pipeline as code.

**References**

  1. Jenkins file with a sample app for testing the pipeline execution on GitHub: <https://github.com/Romeh/spring-boot-sample-app>

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**
