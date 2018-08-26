# Continuous Deployment Through Jenkins

_Captured: 2018-08-24 at 08:13 from [dzone.com](https://dzone.com/articles/continuous-deployment-through-jenkins?edition=387225&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-23)_

Easily enforce open source policies in real time and reduce MTTRs from six weeks to six seconds with the Sonatype Nexus Platform. See for yourself - [Free Vulnerability Scanner.](https://dzone.com/go?i=290455&u=https%3A%2F%2Fwww.sonatype.com%2Fsoftware-bill-of-materials%3Futm_campaign%3Ddzone%252520-%252520AHC%26utm_source%3DDZone%252520-%252520AHC%2525202018%26utm_medium%3DDZone%252520-%252520AHC%2525202018)

Releasing software isn't an art, but it is an engineering discipline. Continuous deployment can be thought of as an extension to continuous integration, which lets us catch defects earlier.

In this article on continuous deployment, we will go through the following topics:

  * What Is Continuous Deployment?
  * Continuous Delivery vs. Continuous Deployment
  * Case Study of Continuous Deployment
  * Benefits of Continuous Deployment
  * Hands-On

So, before we deep-dive into continuous deployment, let me brief you on DevOps first!

## **What Is Continuous Deployment? **

Continuous deployment is an approach to releasing software on production servers continuously in an automated fashion. So, once code passes through all the stages of compiling the source code, validating the source code, reviewing the code, performing unit and integration testing, and packaging the application continuously, it will then be deployed onto the test servers to perform user acceptance tests. Once that is done, the software will be deployed onto the production servers for release. This is said to becontinuous deployment.

Often, people get confused between the terms continuous delivery and continuous deployment, so let me clarify it for you.

## **Continuous Delivery vs. Continuous Deployment **

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/06/Asset-18.png)

Continuous delivery does not involve deployment to production for every change that occurs. You just need to ensure that the code is always in a deployable state so you can deploy it easily whenever you want.

On the other hand, continuous deployment requires every change to be deployed automatically, without human intervention.

So, as you can see in the diagram above, once the continuous integration stages are completed, the newly built application is automatically deployed to production; this is continuous deployment. On the other hand, if we automate everything but decide to require human approval in order to proceed with the deployment of the new version, then we are taking into account continuous delivery. The difference is very subtle, but it has enormous implications, making each technique appropriate for various situations.

Now that you have an understanding of continuous deployment, let's see a case study.

## **Linkedln's Case Study of Continuous Deployment**

LinkedIn is an employment-oriented service that is mainly used for professional networking. LinkedIn's prior system before implementing Continuous Deployment was more traditional.

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/07/Linkedln-Master-Branch_DevOps.png)

The system included various branches diverging from a single trunk developed in a parallel manner. A developer would write big batches of code for various features and then wait for this feature branch to be merged into the trunk, i.e. the master branch.

Once the feature was merged into the master branch, it had to be tested again to make sure that it did not break any other code of a different feature.

Since this system included several batches of code written in isolation by various teams then merged into a single branch, this system was known as a feature branch system. This kind of system limited the scope and number of features, thus slowing down the company's development lifecycle.

Looking at the above conditions, Linkedln decided to move from its traditional feature-based development lifecycle to continuous deployment. This required migrating the old code and building automated tools to make the new system work, halting Linkedln's development for months.

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/07/Linkedln-Use-case-for-DevOps.png)

LinkedIn's framework after using continuous deployment includes developers writing code in tidy, distinct chunks and checking each chunk into the trunk shared amongst all LinkedIn developers. The newly-added code is then subjected to a series of automated tests to remove bugs.

Once the code passes the tests, it is merged into the trunk and listed out in a system that shows managers what features are ready to go live on the site or in newer versions of LinkedIn's apps.

Now, let me continue this discussion by telling you the basic benefits of continuous deployment.

## **Benefits of Continuous Deployment**

  * **Speed** -- Development does not pause for releases so code is developed really fast.
  * **Security** -- Releases are less risky, as before releasing, testing is performed, and all bugs are resolved.
  * **Continuous Improvements** -- Continuous deployment supports continuous improvements which are visible to customers.

## Hands-On

**Problem Statement:** Deploy an application in headless mode through Jenkins server, using Selenium test files.

**Solution: **Follow the steps below to deploy the application in headless mode.

**Step 1:** Open your Eclipse IDE and create a Maven Project. To create a Maven project, go to File -> New -> Maven Project. In the dialog box that opens up, mention the Group Id and the Artifact Id and then click on Finish.

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/07/Picture1.png)

**Step 2:** Once you create your Maven project, include the code of Selenium app in the main Java file and make sure you have inserted the argument to deploy it in headless mode.

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/07/App-1.png)

> _Step 3: Include the required dependencies in the pom.xml file._

**Step 4:** After this, your project is ready to run. Since we want to run it in headless mode, we have to deploy this application in the Jenkins Server.

**Step 5:** So, you have to export your project as a JAR file. To do that, go to File -> Export -> choose Runnable JAR file. After that, click on "Next."

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/07/app-config.png)

**Step 7:** After you export your project as a JAR file, you have to push it to a GitHub repository. To push it to the GitHub repository, create a new repository in your GitHub account. To do that, go to the Repositories tab and choose the option "New."

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/07/new-rep-1.png)

After that, mention the repository name, and choose if you wish your project to be private or public. Then, click on "Create Repository."

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/07/Github-rep.png)

> _Step 8: To push your project to this repository, follow the below steps:_

**Step 9:** Once the JAR file has been pushed to the local repository, you have to create a new Job in the Jenkins server. To do that, open your Jenkins Dashboard, and then go to New Item -> Type in the item name -> Click on OK.

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/07/jenkinsproject-1.png)

**Step 10:** Once your job is created, click on the job and go to configure option. Go to the Source Code Management tab -> Choose Git -> Mention the Repository URL.

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/07/git.png)

After that, go to the "Build" tab and choose the option "Execute shell." In this. mention the path of the jar file in your Jenkins.

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/07/jar-1.png)

> _Once you're done with the above two steps, save the changes._

![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2018/07/ouput.png)

Since it is continuous deployment, this program can be deployed by any person working in the team and the others can only see the output when something has been changed. They will not know who has deployed it directly onto the production servers.

But, if you run the same project in Eclipse, it will run on the browsers, which we don't want in our case, as in Jenkins, we cannot open other browsers!

Automate open source governance at scale across the entire software supply chain with the Nexus Platform. [Learn more.](https://dzone.com/go?i=290456&u=https%3A%2F%2Fwww.sonatype.com%2Fwp-enforce-open-source-policies-with-confidence)
