# Introduction to Docker

_Captured: 2018-03-02 at 20:27 from [dzone.com](https://dzone.com/articles/introduction-to-docker-1?edition=365216&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-02)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

In the last couple of years, there has been lot of excitement about Docker and many big & small companies have moved toward Docker and have incorporated it as part of their DevOps application deployment process. As part of this blog, I would like to introduce Docker and provide a synopsis on:

  * Challenges faced by IT companies before Docker

  * The Matrix from Hell

  * Containers & Evolution of Docker from containers

  * VM vs Containers

  * Docker & its architecture

  * Solution: How Docker helps in mitigating the challenges faced earlier

## **What is the Challenge?**

As depicted in the picture below, maintaining multiple technology stacks across multiple environments was a nightmare earlier. On top of this, one has to also worry about migrating to a different technology, upgrades, etc., which not only makes it more complex, but completely nonviable to support without having huge impact of CTO and BAU operations.

![Image title](https://crunchytechbytz.files.wordpress.com/2018/01/whatisthechallenge.jpg?w=825)

## **The Matrix From Hell**

If you Google "Matrix from Hell," I am sure you will find lot of articles on how Docker solves the matrix from hell quandary.

So what precisely is the matrix from hell? In simple words, it is the challenge of packaging any application, irrespective of language/frameworks/dependencies, so that it can run on any cloud, irrespective of the underlying OS/hardware/infrastructure.

![Matrix From Hell](https://crunchytechbytz.files.wordpress.com/2018/01/matrixfromhell.jpg?w=825)

> _Matrix From Hell_

## **Solution: Intermodal Shipping Container**

![Intermodal Shipping Container](https://crunchytechbytz.files.wordpress.com/2018/01/sjippingcontainer.jpg?w=825)

> _Intermodal Shipping Container_

## **Solution: Why It Works: Separation of Concerns**

The introduction of Docker helped in the eliminating of this matrix, by isolating the worries of developers and administrators. Developers can focus on bundling applications and dependencies as containers, without agonizing over underlying hardware/infrastructure. Administrators/DevOps team can concentrate on managing containers, without agonizing over the contents of those containers.

![Separation of Concerns](https://crunchytechbytz.files.wordpress.com/2018/01/separationofconcerns.jpg?w=825)

> _Separation of Concerns_

## **Solution: Benefits for Developers & Administrators**

## ![](https://crunchytechbytz.files.wordpress.com/2018/01/benfits.jpg?w=825)

> _What is Docker?_

Docker is an open platform for developing, shipping & running distributed applications, whether on laptops, data center VMs or cloud. Docker provides the ability to package and run an application in a loosely isolated environment called a container. The Docker Platform consists of multiple product/tools, including the Docker Engine, Images, Containers, and Hub, among others.

![](https://crunchytechbytz.files.wordpress.com/2018/01/docker.jpg?w=825)

The Docker platform is the only container platform to build, secure and manage the widest array of applications from development to production both on premises and in the cloud.

## **Docker Architecture**

![Docker Architecture](https://crunchytechbytz.files.wordpress.com/2018/01/dockerarchitecture.jpg?w=825)

> _Docker Architecture_

## **Docker Images, Containers & Registries **

**Images**
**Containers**
**Registries**

An image is a static representation of the app or service and its configuration and dependencies.
Container is runtime object or representation of an image.
An image is a static representation of the app or service and its configuration and dependencies

An image is an instance of a container. When an image is started, it gives running container of an image.
Containers are lightweight & portable encapsulation of an environment where applications are run
A Docker image is built up from a series of layers 

A Docker image is built up from a series of layers, allowing a minimal amount of data to be sent when transferring images over network.
Command - **_"docker ps"_** only outputs running containers
Images are stored in a registry 

Images are stored in a registry such as docker hub
When a docker image is run using command "**_docker run"_** it creates a container from that instance.

Images are created with the "**_build_**" command
Containers can be run in either active or detached mode.

Local images can be listed by running command - **_docker images_**

Filesystem changes made in a container do not affect the image

## **VM vs. Containers**

![VM vs Containers](https://crunchytechbytz.files.wordpress.com/2018/01/vmvscontainers.jpg?w=825)

> _VM vs Containers_

## **Solution: Docker Eliminates the Matrix From Hell**

Docker solved the matrix from hell by decoupling the application from the underlying operating system and hardware. It did this by packaging all dependencies inside Docker containers, including the OS. This makes Docker containers "portable", i.e. they can run on any cloud or machine without the dreaded "it works on this machine" problems.

![](https://crunchytechbytz.files.wordpress.com/2018/01/solution-matrixfromhell1.png?w=825)

> _Solution: From Waterfall to DevOps_

In one of the studies, it is estimated by Gartner that more than 50% of new workloads will be deployed into containers in atleast one stage of the application life cycle in the year of 2018.

Also, I have presented below some of the facts from RighScale 2017 State of the Cloud report. This is simply to underscore that Docker is causing the most imperative change in application deployment process.

![](https://crunchytechbytz.files.wordpress.com/2018/01/rightscale.jpg?w=825)

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Topics:

cloud ,docker ,containers ,matrix from hell ,intermodal shipping container ,docker architecture ,vm
