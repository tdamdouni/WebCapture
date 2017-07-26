# Create a Continuous Deployment Pipeline with Node.js and Jenkins

_Captured: 2017-05-07 at 19:19 from [dzone.com](https://dzone.com/articles/create-a-continuous-deployment-pipeline-with-nodej)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Previously I had written about [using Jenkins for continuous deployment of Java applications](https://blog.couchbase.com/create-a-continuous-deployment-pipeline-with-jenkins-and-java/), inspired by a keynote demonstration that I had developed for [Couchbase Connect 2016](https://youtu.be/Bq8zkcbnRac?t=26m25s). I understand that Java isn't the only popular development technology that exists right now. Node.js is a very popular technology and a perfect candidate to be plugged into a continuous deployment pipeline using Jenkins.

We're going to see how to continuously deploy a Node.js application with [Jenkins](https://jenkins.io/) based on changes made to a GitHub repository. So let's figure out the plan here. We're going to be using an already existing Node.js repository that I had [uploaded to GitHub](https://github.com/couchbaselabs/restful-angularjs-nodejs) a while back. When changes are made to this repository, Jenkins will build the application and deploy or run the application. Because of the nature of Node.js, the build process will consist of making sure the NPM modules are present.

## The Requirements

There are a few software requirements that must be met in order to be successful with this guide. They are as follows:

Since this is a Node.js pipeline, of course, we'll need it installed. However, since Jenkins is a Java application, we'll also need Java installed. My sample application does use Couchbase, but that won't be the focus of this guide. However, if you're using the same application I am, you'll need Couchbase Server installed. All software listed should reside on the same host. In a production environment, you will probably want them dispersed across multiple machines.

## Installing and Configuring Couchbase Server as the NoSQL Database

At this point, you should have already downloaded Couchbase Server. After installing it and configuring it, you'll need to create a Bucket called `restful-sample` and that Bucket should have a primary index. For instructions on configuring Couchbase and getting this Bucket created, check out a [previous tutorial](https://www.thepolyglotdeveloper.com/2015/10/create-a-full-stack-app-using-node-js-couchbase-server/) I wrote on the subject. It is actually the tutorial that went with creating this Couchbase, Express Framework, Angular, and Node.js (CEAN) stack application. With Couchbase ready to go, we can focus on configuring Jenkins and creating our workflow.

## Configuring Jenkins with the Necessary Plugins

You should have already downloaded Jenkins by now. If you haven't, go ahead and obtain the WAR file from the Jenkins website. To start Jenkins, execute the following command from your Command Prompt or Terminal:

This will make Jenkins accessible from a web browser at `http://localhost:8080` . Upon first launch, you'll be placed in a configuration wizard.

![](http://blog.couchbase.com/wp-content/uploads/2017/03/jenkins-config-1.png)

> _Jenkins Configuration Part 1_

The first screen in this configuration wizard will ask you for the password that Jenkins generates. Find it in the location presented on the screen. The second screen will ask you which plugins you'd like to install.

![](http://blog.couchbase.com/wp-content/uploads/2017/03/jenkins-config-2.png)

> _Jenkins Configuration Part 2_

For now, we're going to install the suggested plugins. We'll be installing extra plugins later. The third screen will ask us to create our first administrative user. Technically, the generated password you're using is an administrative user, but you may want to create a new one.

![](http://blog.couchbase.com/wp-content/uploads/2017/03/jenkins-config-3.png)

> _Jenkins Configuration Part 3_

After you create a user, Jenkins is ready to go. However, we are going to need another plugin and it can vary depending on how we wish to build and deploy the Node.js application. From the main Jenkins screen, choose "Manage Jenkins" to see a list of administration options.

![](http://blog.couchbase.com/wp-content/uploads/2017/03/jenkins-manage.png)

> _Manage Jenkins_

What we care about is managing the available plugins. After choosing "Manage Plugins" we want to search for and install a plugin by the name of Post-Build Script.

![](http://blog.couchbase.com/wp-content/uploads/2017/03/jenkins-postbuildscript-plugin.png)

> _Install Jenkins Post-Build Script Plugin_

This plugin allows us to execute shell commands or scripts after the build stage has completed. In this example we'll be building and deploying to the same host, we can run everything locally via shell commands. In a production environment, you might want to use the SSH plugin to migrate the code to a remote server and run it there. With the plugins available, let's create our continuous deployment workflow for Node.js in Jenkins.

## Creating a Jenkins Continuous Deployment Workflow for Node.js

Just to reiterate, our goal here is to create a workflow that will pull a project from GitHub, build it by installing all the dependencies, and deploy it by running it on a server, in this case, our local machine. Start by creating a new item, otherwise known as a new job or workflow.

![](http://blog.couchbase.com/wp-content/uploads/2017/03/jenkins-nodejs-freestyle-project.png)

> _Jenkins Node.js Freestyle Project_

We're going to be creating a Freestyle Project, but you can give it any name you want. There are three things that need to be done on the next screen. The source of our workspace will come from GitHub. In your own project it can come from elsewhere, but for this one, we need to define our source control information.

![](http://blog.couchbase.com/wp-content/uploads/2017/03/jenkins-nodejs-source-control.png)

> _Jenkins Node.js Source Control_

The GitHub project is one that I had previously created and written about, like mentioned before. The project can be found at:

Now in a production environment, you'll probably want to set up GitHub hooks to trigger the job process, but since this is all on localhost, GitHub won't allow it. Instead, we'll be triggering the job manually.

![](http://blog.couchbase.com/wp-content/uploads/2017/03/jenkins-nodejs-build.png)

> _Jenkins Node.js Build Step_

After configuring the source control section we'll need to configure the build step. For Node.js, building only consists of installing dependencies, but you could easily have unit testing and other testing in this step as well. In my [previous Java example](https://blog.couchbase.com/create-a-continuous-deployment-pipeline-with-jenkins-and-java/), the build step had a little more to it. In this Node.js example we have the following:

Finally, we get to define what happens after the project is built.

![](http://blog.couchbase.com/wp-content/uploads/2017/03/jenkins-nodejs-postbuild.png)

> _Jenkins Node.js Post Build Step_

In this example, we will be deploying the application locally on our machine. Probably not the case in your production scenario. So you'll notice in our post-build step we have the following commands:

Before starting the application we are stopping any already running instance of it. Once stopped we can start the new version. However, where do these `stop` and `start` tasks come from?

The above was taken from the GitHub project's package.json file. Each task starts and stops a `forever` script for Node.js. Go ahead and try to run the job choosing Build Now from the list of options. It should obtain the project, install the dependencies, and make the project available at `http://localhost:3000` . Just make sure Couchbase Server is running for this project- otherwise, you'll get errors.

You just saw how to use Jenkins to continuously deploy your Node.js applications based on changes that have been made in GitHub. A similar version of this guide was created for Java applications called, [Create a Continuous Deployment Pipeline with Jenkins and Java](https://blog.couchbase.com/create-a-continuous-deployment-pipeline-with-jenkins-and-java/), which is worth reviewing if you're a Java developer.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).

### Like This Article? Read More From DZone
