# Docker Commands for Development to Deployment

_Captured: 2017-08-25 at 14:18 from [dzone.com](https://dzone.com/articles/docker-commands-for-development-to-deployment?edition=319415&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202017-08-25)_

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

The objective of this article to understand the end to end flow of container development to deployment in the target environment and list the Docker commands needed for every action.

## 1\. Introduction

The overall process consists of developing a container image with your code, dependent software, and configurations, running and testing the container in a development environment, publishing the container image into Docker Hub, and finally, deploying the Docker image and running the container in the target environment. This article assumes that you have installed Docker engine in the development and target environment. Please refer to [6.3](https://docs.docker.com/engine/installation/) for installation instructions.

## 2\. Develop Container Image

To build the container image, we have to create a dockerfile which will contain all the necessary information. Please refer [here](https://nodejs.org/en/docs/guides/nodejs-docker-webapp/) to develop the dockerfile.

### 2.1 Build Docker Container

This command will take the Dockerfile present in your current directory. If you have the dockerfile in a different name and different location, we can use -f flag to specify the docker file name. The "docker build" command will build the container image in the name specified with "-t" flag.

### ![01-DockerBuild](https://techietweak.files.wordpress.com/2017/08/01-dockerbuild.jpg?w=705)

### 2.2 Docker Image Naming Convention

You can provide any name to a Docker container, when you run locally. It could be as simple as "myApp" as shown above. But if you want to publish the image into Docker Hub, there is a specific naming convention to be followed. This convention helps the Docker tools to publish the container image into right namespace and repository.

The format:

NameSpace/Repository:Version

So, I build the docker image using the above convention:

We can also use the "docker tag" command to create an image from an existing image. The "docker tag" command is explained below.

### 2.3 List All Images in the Docker

## ![02-DockerImagesList](https://techietweak.files.wordpress.com/2017/08/02-dockerimageslist1.jpg?w=705)

## 3\. Run the Container

### 3.1 Start the Docker Container

Use the "docker run" command to start the Docker container.

![03-DockerRun](https://techietweak.files.wordpress.com/2017/08/03-dockerrun1.jpg?w=705)

The "-d" option runs the container in the detached mode, so that the container continues to run, even if the terminal is closed.

The "-p" command used to map the ports. In this example, "-p 8080:8080" the first port number is the port used the Docker host. The second port number is used by the Docker container. As per this command, all the traffic comes to the Docker host port, will be forwarded to the Docker container port.

### 3.2 Check Current Running Containers

![07-DockerPS](https://techietweak.files.wordpress.com/2017/08/07-dockerps.jpg?w=705)

From the above output, we can see that a Docker container is running in the name of "trusting_snyder."

To list all the containers irrespective of the states, use the "-a" switch.

### 3.3 Show the Console Logs of the Running Container

![08-dockerlogs](https://techietweak.files.wordpress.com/2017/08/08-dockerlogs.jpg?w=705)

> _ContainerName can be found with the "docker ps" command._

### 3.4 Log into the Container

The above command will prompt you with "bash" shell of the container.

![09-dockerlogin](https://techietweak.files.wordpress.com/2017/08/09-dockerlogin.jpg?w=705)

### 3.5 Stop the Running Container

### ![11-DockerStop](https://techietweak.files.wordpress.com/2017/08/11-dockerstop.jpg?w=705)

> _3.6 Remove the Container Image From Docker_

Find the imageId of the container using the command "docker images" or "docker images -a."

![11-DockerRMIImages](https://techietweak.files.wordpress.com/2017/08/11-dockerrmiimages.jpg?w=705)

> _The above command will forcefully delete the given image._

### 3.7 Clean Up Your Docker/Delete All Container Images in the Local Docker

## 4\. Publish the Container Image

The Docker container images can be published to your local dockyard or the public Docker hub. The process and commands are the same for both. To publish your Docker image in the Docker Hub, first create your namespace and repository at <http://hub.docker.com>.

I have used my namespace "saravasu" and the repository "techietweak" for this exercise.

![00-dockerhubRepo](https://techietweak.files.wordpress.com/2017/08/00-dockerhubrepo.jpg?w=705)

### 4.1 Log Into Docker Hub

If you want to log into your local repository, please provide the URL. If a URL is not specified, then this command will log into Docker Hub.

### ![04-DockerLogin](https://techietweak.files.wordpress.com/2017/08/04-dockerlogin.jpg?w=705)

### 4.2 Tag the Container Image

To push the Docker container image into Docker Hub, it must be tagged in a specific format: <Namespace>/<Repository>:<Version>. If you don't specify the version, it will be taken as "default." In the below command, I am tagging the image:

### 4.3 Push the Docker Image Into Docker Hub

### ![10-DockerPushToDockerHub](https://techietweak.files.wordpress.com/2017/08/10-dockerpushtodockerhub.jpg?w=705)

> _4.4 Check the Container Images in Docker Hub_

Now log into your Docker Hub account and check for the images in the respective repository.

![05-dockerhubimages](https://techietweak.files.wordpress.com/2017/08/05-dockerhubimages1.jpg?w=705)

## 5 Deploy the Container

### 5.1 Pull the Docker Container Image

Login into Docker Hub from the host machine in the target environment and pull the container image from Docker Hub. If you want to pull it from your private dockyard, use the command "$docker login <hostname>" to specify the hostname of the private dockyard.

The above command will log into <https://hub.docker.com>, since the host name is not specified.

![12-dockerPull](https://techietweak.files.wordpress.com/2017/08/12-dockerpull.jpg?w=705)

### 5.2 Check the Image

The docker pull command downloaded the container image from the Docker Hub. We can validate the same by using the "docker images" command.

![06-DockerPull-Images](https://techietweak.files.wordpress.com/2017/08/06-dockerpull-images1.jpg?w=705)

### 5.3 Run the Container

Now we can run the Docker container in the same way we ran it in the development environment and test it in the same way we have done before.

## ![13-dockerTargetRun](https://techietweak.files.wordpress.com/2017/08/13-dockertargetrun.jpg?w=705)

The docker run command starts the container. To validate it, we can use the "docker ps" command. Docker has created a new container and it is running in the name of "naughty_lewin."

As we see above, the Docker engine provides a random name to the running container, but this could be a problem in automation, so it is always good to specify a name we want to refer. This can be achieved by using the "-name" parameter.

![14-dockerRunNamedContainer](https://techietweak.files.wordpress.com/2017/08/14-dockerrunnamedcontainer.jpg?w=705)

## 6\. Summary

This article captures the flow and necessary commands to develop a container image, run it in the local environment, publish the image to Docker Hub, and run the container in the target environment. Further study and detailed documentation are available on the Docker website [refer to 6.1].

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).
