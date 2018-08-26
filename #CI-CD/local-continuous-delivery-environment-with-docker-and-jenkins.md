# Local Continuous Delivery Environment With Docker and Jenkins

_Captured: 2018-06-18 at 07:11 from [dzone.com](https://dzone.com/articles/local-continuous-delivery-environment-with-docker?edition=382200&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-17)_

![](https://piotrminkowski.files.wordpress.com/2018/06/art-docker-1.png?w=670&h=262)

## 1\. Running Jenkins Master

We will use the latest Jenkins **LTS** image. Jenkins Web Dashboard is exposed on port **38080**. Slave agents may connect to the master on the default **50000** JNLP (Java Web Start) port.

After starting, you have to execute the command `docker logs jenkins` in order to obtain an initial admin password. Find the following fragment in the logs, copy your generated password and paste it in the Jenkins start page available at _<http://192.168.99.100:38080>_.

![](https://piotrminkowski.files.wordpress.com/2018/06/art-docker-2.png?w=547&h=62)

We have to install some Jenkins plugins to be able to check out the project from the Git repository, build application from the source code using Maven, and finally, build and push a Docker image to a private registry. Here's a list of required plugins:

  * [Maven Integration Plugin](https://wiki.jenkins.io/display/JENKINS/Maven+Project+Plugin) \- this plugin provides advanced integration for Maven 2/3.
  * [Pipeline Plugin](https://wiki.jenkins.io/display/JENKINS/Pipeline+Plugin) \- this is a suite of plugins that allows you to create continuous delivery pipelines as a code and run them in Jenkins.
  * [Docker Pipeline Plugin](https://wiki.jenkins.io/display/JENKINS/Docker+Pipeline+Plugin) \- this plugin allows you to build and use Docker containers from pipelines.

## 2\. Building the Jenkins Slave

Pipelines are usually run on a different machine than the machine with the master node. Moreover, we need to have the Docker engine installed on that slave machine to be able to build Docker images. Although there are some ready Docker images with Docker-in-Docker and Jenkins client agent, I have never found the image with JDK, Maven, Git, and Docker installed. These are the most commonly used tools when building images for your microservices, so it is definitely worth it to have such an image with a Jenkins image prepared.

Here's the Dockerfile with the Jenkins **Docker-in-Docker** slave with **Git**, **Maven**, and **OpenJDK** installed. I used Docker-in-Docker as a base image **(1)**. We can override some properties when running our container. You will probably have to override the default Jenkins master address **(2)** and slave secret key **(3)**. The rest of the parameters are optional, but you can even decide to use an external Docker daemon by overriding the `DOCKER_HOST` environment variable. We also download and install Maven **(4)** and create a user with special sudo rights for running Docker **(5)**. Finally, we run the `entrypoint.sh` script, which starts the Docker daemon and Jenkins agent **(6)**.

Here's the script `entrypoint.sh`.

The source code with the image definition is available on GitHub. You can clone the [repository](https://github.com/piomin/jenkins-slave-dind-jnlp.git), build the image, and start the container using the following commands.

Building it is just an optional step because the image is already available on my Docker Hub account.

![](https://piotrminkowski.files.wordpress.com/2018/06/art-docker-3.png?w=840)

## 3\. Enabling Docker-in-Docker Slave

To add a new slave node, you need to navigate to _Manage Jenkins_ -> _Manage Nodes_ -> _New Node_. Then, define a permanent node with the name parameter filled. The most suitable name is default name declared inside the Docker image definition - **dind-node**. You also have to set the remote root directory, which should be equal to the path defined inside the container for the `JENKINS_HOME` environment variable. In my case, it is `/home/jenkins`. The slave node should be launched via Java Web Start (JNLP).

![](https://piotrminkowski.files.wordpress.com/2018/06/art-docker-4.png?w=598&h=203)

The new node is visible on the list of nodes as disabled. You should click it in order to obtain its secret key.

![](https://piotrminkowski.files.wordpress.com/2018/06/art-docker-5.png?w=840)

Finally, you may run your slave container using the following command containing the secret copied from the node's panel in Jenkins Web Dashboard.

If everything went according to plan, you should see the enabled node `dind-node` in the node's list.

![](https://piotrminkowski.files.wordpress.com/2018/06/art-docker-6.png?w=840)

> _4. Setting Up the Docker Private Registry_

After deploying the Jenkins master and slave, there is one last required element in the architecture that has to be launched -- the private Docker registry. Because we will access it remotely (from the Docker-in-Docker container), we have to configure a secure TLS/SSL connection. To achieve it, we should first generate a TLS certificate and key. We can use the **openssl** tool for it. We begin by generating a private key.

Then, we should generate a certificate request file (CSR) by executing the following command.

Finally, we can generate a self-signed SSL certificate that is valid for one year using the openssl command as shown below.

Don't forget to remove the passphrase from your private key.

You should copy the generated `.key` and `.crt` files to your Docker machine. After that, you may run the Docker registry using the following command.

If a registry has been successfully started, you should able to access it over HTTPS by calling the address _<https://192.168.99.100:5000/v2/_catalog>_ from your web browser.

## 5\. Creating the Application Dockerfile

The sample application's source code is available on GitHub in the repository [sample-spring-microservices-new](https://github.com/piomin/sample-spring-microservices-new.git). There are some modules with microservices. Each of them has a Dockerfile created in the root directory. Here's a typical Dockerfile for our microservice built on top of Spring Boot.

## 6\. Building the Pipeline Through Jenkinsfile

This step is the most important phase of our exercise. We will prepare pipeline definition, which combines together all the currently discussed tools and solutions. This pipeline definition is a part of every sample application source code. The change in Jenkinsfile is treated the same as a change in the source code responsible for implementing business logic.

Every pipeline is divided into **stages**. Every stage defines a subset of tasks performed through the entire pipeline. We can select the **node**, which is responsible for executing the pipeline's steps, or leave it empty to allow random selection of the node. Because we have already prepared a dedicated node with Docker, we force the pipeline to be built with that node. In the first stage, called Checkout, we pull the source code from the Git repository **(1)**. Then we build an application binary using the Maven command **(2)**. Once the fat JAR file has been prepared, we may proceed to build the application's Docker image **(3)**. We use methods provided by the Docker Pipeline Plugin. Finally, we push the Docker image with the fat JAR file to a secure private Docker registry **(4)**. Such an image may be accessed by any machine that has Docker installed and has access to our Docker registry. Here's the full code of the Jenkinsfile prepared for the module `config-service`.

## 7\. Creating the Pipeline in Jenkins Web Dashboard

After preparing the application's source code, Dockerfile, and Jenkinsfile, the only thing left is to create the pipeline using the Jenkins UI. We need to select _New Item_ -> _Pipeline_ and type the name of our first Jenkins pipeline. Then, go to the _Configure_ panel and select _Pipeline script from SCM_ in the _Pipeline_ section. In the following form, we should fill in the address of the Git repository, user credentials, and location of the Jenkinsfile.

![](https://piotrminkowski.files.wordpress.com/2018/06/art-docker-7.png?w=658&h=268)

## 8\. Configure GitLab WebHook (Optional)

If you run GitLab locally using its Docker image, you will be able to configure a webhook, which triggers a run of your pipeline after pushing changes to the Git repository. To run GitLab using Docker, execute the following command.

Before configuring the webhook in the GitLab Dashboard, we need to enable this feature for the Jenkins pipeline. To achieve it, we should first install the [GitLab Plugin](https://wiki.jenkins.io/display/JENKINS/GitLab+Plugin).

Then, you should come back to the pipeline's configuration panel and enable the GitLab build trigger. After that, the webhook will be available for our sample pipeline, called **config-service-pipeline** under the URL _<http://192.168.99.100:38080/project/config-service-pipeline> _as shown in the following picture.

![](https://piotrminkowski.files.wordpress.com/2018/06/art-docker-9.png?w=617&h=176)

Before proceeding to configuration of the webhook in the GitLab Dashboard, you should retrieve your Jenkins user API token. To achieve it, go to the profile panel, select _Configure,_ and click the button _Show API Token_.

To add a new WebHook for your Git repository, you need to go to the section _Settings_ -> _Integrations_ and then fill the URL field with the webhook address copied from the Jenkins pipeline. Then paste Jenkins user API token into field _Secret Token_. Leave the _Push events_ checkbox selected.

![](https://piotrminkowski.files.wordpress.com/2018/06/art-docker-11.png?w=565&h=256)

## 9\. Running the Pipeline

Now, we may finally run our pipeline. If you use a GitLab Docker container as a Git repository platform, you just have to push changes in the source code. Otherwise, you have to manually start the build of the pipeline. The first build will take a few minutes because Maven has to download dependencies required for building an application. If everything ends with success, you should see the following result on your pipeline dashboard.

![](https://piotrminkowski.files.wordpress.com/2018/06/art-docker-13.png?w=628&h=145)

You can check out the list of images stored in your private Docker registry by calling the following HTTP API endpoint in your web browser: _<https://192.168.99.100:5000/v2/_catalog>_.
