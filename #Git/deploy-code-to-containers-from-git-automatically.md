# Deploy Code to Containers From Git Automatically

_Captured: 2017-04-28 at 09:00 from [dzone.com](https://dzone.com/articles/deploy-code-to-containers-from-git-automatically-1?edition=292935&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-27)_

[MongoDB Atlas is a database as a service that makes it easy to deploy, manage, and scale MongoDB](https://dzone.com/go?i=193126&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad). So you can focus on innovation, not operations. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=193126&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad).

There is a number of options to deploy your source code from a Git repo to containers including a redeploy of the whole container, instant redeploy via volumes, or the "git clone" approach. However, when it comes to automation of this process and moving to continuous deployment, many developers can face the complexity, as they need to know how to properly combine all the application components with the required interconnection points.

Specifically, in the containers world, you have to manage builds of your stack images dealing with the extra complexity of the CI/CD pipeline. And the whole containers redeploy may not be the best approach if you do frequent commits without configuration changes in the operating system, application server stack, or its dependencies.

![github ci cd](http://blog.jelastic.com/wp-content/uploads/2017/04/GitHub-GitLab.png)

To ease deployment automation, Jelastic prepared a special dedicated Git-Push-Deploy package for code delivery into the preliminarily built container images. This package implements a number of configurations to set up the automatic deployment of committed changes within your Git application source repository to the cloud, making them available for further testing with minimal delays.

## Git-Push-Deploy Specifics

The Git-Push-Deploy package can be integrated with GitHub and GitLab repositories. It is developed for automatic delivery of updates within your **Java**, **PHP**, **Ruby**, **Node.js**, and **Python** application sources and can be applied to the following certified stack templates:

  * _Java_ - Tomcat 6/7/8/9, TomEE, GlassFish 3/4, Jetty 6/8/9, WildFly 8/9/10, JBoss AS 7, Spring Boot 1.x
  * _PHP_ - Apache 2.4, NGINX 1.10
  * _Ruby _- Apache 2.4, NGINX 1.10
  * _Node.js_ - Node.js 0.x-6.x
  * _Python_ - Apache 2.4

The workflow depends on the programming language used in your project:

* _for Java-based projects_, the package initiates the creation of a separate environment with a Maven build node, which will be responsible for interaction with remote Git repository, triggering your application builds and their deployment to the application server.
* _for PHP/Ruby/Node.js/Python applications_, the package sets up a pipeline for project deployment directly to the ROOT context on a web server (here, consider that Ruby app servers are supplied with a deployment mode instead of a context within the dashboard, though the actual project location is the same).

This deployment automation package is compatible with Jelastic PaaS of the 4.9.5 version and higher. To review and compare available hosting platforms with a particular Jelastic version, refer to the Jelastic Cloud Union Catalog.

## Repository Pre-Configurations

For a proper add-on installation, you'll need to provide a _Personal API Token_ for your Git account. This enables the package to set up a webhook for the corresponding repository, which will initiate application redeployment each time a change is contributed to its code.

So let's generate one. Follow the instructions below according to the used Git VCS, i.e. either GitHub or GitLab.

## **Generating Access Token on GitHub**

To get your [personal access token](https://github.com/blog/1509-personal-api-tokens) for your GitHub account, navigate to the **Settings > Personal access tokens** and click the **Generate new token** button.

![node js app deployment automation](http://blog.jelastic.com/wp-content/uploads/2017/04/Generating-Access-Token-on-GitHub.png)

In the opened page, specify the **Token description** and select the **_repo_** and **_admin:repo_hook_** scopes. Click **Generate token** at the bottom of the page.

![github auto deploy](http://blog.jelastic.com/wp-content/uploads/2017/04/Token-description.png)

Once redirected, copy and save the shown access token anywhere else (as it can't be viewed again after you leave this page).

![ruby continuous deployment](http://blog.jelastic.com/wp-content/uploads/2017/04/personal-access-tokens.png)

After this is accomplished, proceed to the _Install Git-Push-Deploy Package_ section further along in this article.

## **Generating Access Tokens on GitLab**

To generate a [personal access token](https://docs.gitlab.com/ee/api/README.html#personal-access-tokens) on GitLab, enter your account **Settings **and switch to the **_Access Tokens_** tab.

Here, specify the optional token **Name**, its **Expiry** date (which can be left blank) and tick the **api** permission scope.

![python app deployment automation](http://blog.jelastic.com/wp-content/uploads/2017/04/Generating-Access-Token-on-GitLab.png)

Click the **Create Personal Access Token** button.

In the opened page, copy and temporarily store your access token value anywhere else (as you won't be able to see it again after leaving this page).

![github ci cd php](http://blog.jelastic.com/wp-content/uploads/2017/04/Create-Personal-Access-Token.png)

> _Now, you are ready for package installation._

## Extra Pre-Configurations for Java Projects

If running a Java-based project, you need to preliminarily ensure its proper interaction with the Maven build node by adding a special Project Object Model ([POM](https://maven.apache.org/guides/introduction/introduction-to-the-pom.html)) file to its structure.

So, create a **_pom.xml_** file in your project repository root, with the following content as an obligatory basis:

Where optional values are:

  * _groupId_ - group of a project (e.g. company name).
  * _artifactId_ - name of a project.
  * _version_ - your application version.

All the rest of parameters should be left unchanged. You can check how it should be done in [our sample](https://github.com/jelastic/HelloWorld-CI-CD/blob/master/pom.xml).

## Install Git-Push-Deploy Package

Git-Push-Deploy package is an add-on, so it can be installed only on top of an environment. We have prepared two separate environments with **Tomcat** and **Apache-PHP **application servers to show the workflow for different programming languages.

If you are going to use a previously created environment, note that the package will overwrite the application deployed to the **_ROOT_** context. So to keep your already deployed application, move it to the custom context. We recommend creating a new environment and then proceeding to the installation:

1\. Click the **Import** button on the top pane of the dashboard and insert a **_manifest.jps_** link for Git-Push-Deploy project within the opened **URL** tab:

_https://github.com/jelastic-jps/git-push-deploy/blob/master/manifest.jps_

![ruby application deployment automation](http://blog.jelastic.com/wp-content/uploads/2017/04/Install-Git-Push-Deploy-Package.png)

Click **Import** to continue.

2\. In the opened frame, specify the following details about your repository and target environment:

  * **_Git Repo URL_** - HTTPS link to your application repo (either _.git_ or of a common view). You can fork our sample [Hello World](https://github.com/jelastic/HelloWorld-CI-CD) application to test the flow.
  * **_Branch_** - a project branch to be used.
  * **_User_** - enter your Git account login.
  * **_Token_** - specify the access token you've previously created for webhook generation.
  * **_Environment name_** - choose an environment to which your application will be deployed.
  * **_Nodes _**- application server name (is fetched automatically upon selecting the environment).
![java continuous deployment](http://blog.jelastic.com/wp-content/uploads/2017/04/GitHubGitLab-addon.png)

Click **Install** to continue.

3\. Wait a minute for Jelastic to fetch your application sources from GitHub and configure webhook for continuous deployment.

![php github auto deploy](http://blog.jelastic.com/wp-content/uploads/2017/04/Git-Push-addon.png)

**Close** the notification frame when installation is finished.

4\. Depending on a project type, the result will be the following:

* for **Java-based** infrastructure, you'll see a new environment appear on your dashboard with a **_Maven_** build node inside; it will build and deploy your application to the _ROOT_ context on a web server each time the source code is updated  
![application ci/cd automation](http://blog.jelastic.com/wp-content/uploads/2017/04/Git-push-Java-project.png)

**Pay attention** that it might take some time for Maven to compile a project (though the package installation itself has already finished), so you need to wait a few minutes before launching it. The current progress of this operation can be tracked in real time via **_vcs_update_** log file on Maven:

![jps automation git push](http://blog.jelastic.com/wp-content/uploads/2017/04/vcs_update-log-file.png)

* for **PHP-based** infrastructure (and the rest of supported languages), your application will be deployed directly to the chosen server _ROOT._

Herewith, consider that the similar _Projects_ section for **Ruby** application servers provides information on used deployment mode (_development _by default) instead of a context, whilst actual app location refers to server root as well.

To start your application, click on **Open in browser** next to your web server.

![node js continuous deployment	](http://blog.jelastic.com/wp-content/uploads/2017/04/hello-world-jelastic.png)

That's it! Now a new version of your application is automatically delivered to the application server upon each commit to a repository.

## Redeployment Policies for Different Stacks

The table below lists behavior of different application servers after receiving the updated code.

Stack Name Policy

Tomcat 6
Restart

Tomcat 7
Restart

Tomcat 8
Restart

Tomcat 9
Restart

TomEE
Restart

GlassFish 3
Hot Redeploy via Server API

GlassFish 4
Hot Redeploy via Server API

GlassFish 5
Hot Redeploy via Server API

Jetty 6
Restart

Jetty 8
Restart

Jetty 9
Restart

JBoss 7
Restart

Wildfly 8
Restart

Wildfly 9
Restart

Wildfly 10
Restart

Railo
Restart

SpringBoot
Restart

Apache-PHP
[Advanced ZDT](https://docs.jelastic.com/php-zero-downtime-deploy)

Nginx-PHP
[Advanced ZDT](https://docs.jelastic.com/php-zero-downtime-deploy)

Apache-Ruby
Graceful Reload

Nginx-Ruby
Graceful Reload

NodeJS
Restart

Python
Restart

To eliminate possible application downtime for a server with _Restart_ update policy, scale it out to be run over multiple containers. In this case, the required updates will be applied to the instances sequentially, with a 30-second delay by default.

## Test Automated Deploy From Git

And now let's check how this process actually works. Make some minor adjustment to the code in a repo and ensure everything is automated:

1\. Click **Edit this file** for some item within your project repository and **Commit changes** to it - for example, we'll modify the text at our HelloWorld start page.

![github continuous deployment](http://blog.jelastic.com/wp-content/uploads/2017/04/Test-Automated-Deploy-from-Git.png)

2\. As a result, the appropriate webhook will be triggered to deploy the made changes into your hosting environment - refer to the repository **Settings > Webhooks** section for the details.

![python continuous deployment	](http://blog.jelastic.com/wp-content/uploads/2017/04/recent-deliveries-git-push.png)

Upon clicking on this string you'll see the list of **Recent Deliveries**, initiated by the webhook, and the result of their execution.

3\. As the last checkpoint, return back to your application page and refresh it (whilst remembering that it may take an extra minute for Maven to build and deploy your Java-based project).

![java app deployment automation](http://blog.jelastic.com/wp-content/uploads/2017/04/git-push-hello-world.png)

That's it! As you can see, the modifications were successfully applied, so the solution works as intended.

Simply update your code, make commits as you usually do, and all the changes will be pushed to your Jelastic environment automatically. No need to switch between processes or make manual updates eliminates human errors and accelerates time to market for your application.

MongoDB Atlas is [the best way to run MongoDB on AWS](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad) -- highly secure by default, highly available, and fully elastic. [Get started free](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad). Brought to you in partnership with [MongoDB.](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad)
