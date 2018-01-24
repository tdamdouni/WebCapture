# CI/CD Pipeline Using GitHub, Docker, CircleCI, and Heroku

_Captured: 2017-12-29 at 20:26 from [dzone.com](https://dzone.com/articles/cicd-pipeline-using-github-docker-circleci-amp-her?edition=347139&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202017-12-29)_

![](http://i1.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/ci_cd_cover.png?resize=462%2C267)

This post will walk you through how to setup a **Continuous Integration** & **Continuous Deployment** (CI/CD) pipeline with **CircleCI**, **Docker** & **Heroku** easily. In the end of this tutorial, you should be able to setup your own **CI/CD** as shown in the diagram above.

This tutorial assumes that you have:

  * **Python** version 3.5 installed locally.

The source code of the application used in this demo is available on my [GitHub](https://github.com/mlabouardy/circleci-heroku-flask).

## ![](http://i1.wp.com/cdn.meme.am/instances/75611207/prepare-yourself-cicd-is-coming.jpg?w=660&ssl=1)

**1 - Heroku**

First, login in using the email address & password you used when creating your **Heroku** account:

To clone the sample application so that you have a local version of the code that you can then deploy to **Heroku**, execute the following commands in your local command shell or terminal

**Note:** in case you are using your own app, you should add the following files to your code repository:

  1. _**Procfile**_: It tells **Heroku** what commands should be run.
  2. _**requirements.txt**_: In this file, you will list the packages/dependencies that **pip** should install for you.

Create an app on **Heroku**, which prepares **Heroku** to receive your source code:

Provision a **MySQL** database add-on:

**Heroku** will automatically add a config var with the database credentials in the form of a URL. You find the config vars under the Settings tab, and click the button to " **Reveal config vars** "

![](http://i0.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/img_59e1fe5677d75.png?w=660)

> _Now deploy the application:_

![](http://i2.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/img_59e1fe96805a5.png?w=660)

Go to **Heroku Dashboard**, click on the "**Open App**" button:

![](http://i2.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/img_59e1fed740d3a.png?w=660)

> _You should see:_

![](http://i2.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/img_59e1fef2ddb57.png?w=660)

> _Note: As a handy shortcut, you can open the application as follows:_

## **2 - CircleCI**

The following sections walk through how **CI/CD** steps are configured for this application, how to run unit tests, build & push the **Docker Image** to [DockerHub](https://hub.docker.com), and how to deploy the demo application to **Heroku**:

![](http://i0.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/ci_cd.png?resize=660%2C267)

The _.circleci/config.yml_ contains **CI/CD** steps:

  * We will use **Python 3.5** as the primary container & **MySQL** for the build environment:
  * The first step of the pipeline is checking out the project:

  * To speed up the builds, we place the Python **virtualenv** into the CircleCi cache and restores cache before running **pip install**

  * **Unit Tests** requires **MySQL** database, therefore, we need to wait for the container to be ready:

  * We will install the **Docker Client**, build the **docker image** from the **Dockerfile** stored in the **GitHub** repository, and then Push the image to **DockerHub**.

  * Finally, we install **Heroku CLI** & push the changes to **Heroku**

As shown in the configuration file above, we will need to set some **environment variables**, so navigate to the Project settings:

![](http://i2.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/img_59e1ff23a0153.png?w=660)

Finally, to enable the connection to the **Heroku Git Server** from **CircleCI** we need to create an SSH Key without passphrase. Issue the following command:

Then, add the private key in the CircleCI UI SSH Permissions page with a hostname of **git.heroku.com** as follows:

![](http://i1.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/img_59e1ff4d7d1b8.png?w=660)

> _The public key is added to Heroku on the Account page:_

![](http://i1.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/img_59e1ff616336e.png?w=660)

Now every time you push changes to your **Github** repo, **CircleCI** will automatically deploy the changes to **Heroku**. Here's a passing build:

![](http://i1.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/img_59e1ff8551d21.png?w=660)

> _The CI/CD pipeline steps as described in config.yml file:_

![](http://i1.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/img_59e1ff9befff7.png?w=660)

> _The Docker Image repository on DockerHub:_

![](http://i1.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/img_59e1ffb199ab6.png?w=660)

**Heroku** last build from **CircleCI**:

![](http://i0.wp.com/www.blog.labouardy.com/wp-content/uploads/2017/10/img_59e1ffc4529e7.png?w=660)
