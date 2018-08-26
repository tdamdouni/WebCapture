# Containers - The Perfect Solution for Running Microservices

_Captured: 2018-06-06 at 21:38 from [dzone.com](https://dzone.com/articles/containers-the-perfect-solution-for-running-micros?edition=376267&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=microservices%202018-05-09)_

Learn the Benefits and Principles of [Microservices Architecture for the Enterprise](https://dzone.com/go?i=291431&u=https%3A%2F%2Ftransform.ca.com%2FAPI-microservice-architecture-for-the-enterprise.html%3Fcid%3DNA-DSP-API-AEL-000195-00001674-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dmicroservices_api_acquire%26utm_content%3Dna_eb1-microservice-arch-ent-ddc-preroll%26mrm%3D)

A container image is a lightweight executable package of a piece of software that will always run the same, regardless of the environment you are using it with. The series of videos presented below will explain the basic and advanced principles of using containers, as well as various technologies and services around it.

## Introduction to Containers

In this video series, we will understand the story behind containers and what drives the need for it. We will know why companies moved from traditional solution architecture to microservices and how this made containers the perfect solution for running them. We will get a quick intro to clear up some definitions, tools, and keywords related to this ecosystem; for example, we will understand the difference between VMs, containers and Hyper-V containers, why we prefer containers over VMs, and when the VM is better. We will understand the difference between containers and images and know the lifecycle of creating a new image and why I do things like adding more layers to the base image, push that to container images registry on the cloud, then pull that from the registry to anywhere to have a new container. We will also understand different technologies and services around containers, like Docker, Docker Swarm, Kubernetes, Azure Container Services (ACS), Azure Container Registry, etc.

We will see how to create a Linux machine on Azure, remotely connect to it using Git bash, and PuTTY, how to install Docker, display all the images that exist on the machine, pull a new image from Docker Hub, run and stop a container, display running containers, and many others. We will see also the same steps on Windows with Docker.

## 1- Microservices and Containers: What and Why?

This is the first video in this series. We will understand the story behind containers and what drives the need for it. We will know why companies moved from traditional solution architecture to microservices and how this made containers the perfect solution for running them. We will get a quick intro to clear up some definitions, tools, and keywords related to this ecosystem; for example, we will understand the difference between VMs, containers and Hyper-V containers, why we prefer containers over VMs, and when the VM is better. We will understand the difference between containers and images and know the lifecycle of creating a new image and why I do things like adding more layers to the base image, push that to container images registry on the cloud, then pull that from the registry to anywhere to have a new container. We will also understand different technologies and services around containers, like Docker, Docker Swarm, Kubernetes, Azure Container Services (ACS), Azure Container Registry, etc.

## 2- Create a Linux VM on Azure and Establish a Remote Connection

In this video, we will see how to create Linux machine on Azure. We will select the Ubuntu server and remotely connect to it using Git bash and PuTTY, and we will see how to test that our connection is established using the `sudo` command.

## 3- Working With Docker on Linux

In this video, we will start working with containers using Docker, so first, we will get more familiar with some Linux commands like `sudo` and `sudo bash`, understanding the difference between apt-get and Yum, installing and uninstalling Docker, pulling images from Docker-Hub, running containers with `docker run`, listing all the running containers in the machine with `docker ps`, seeing all the containers from the host machine using process tree or `pstree`, and much more.

## 4- Creating a Windows VM on Azure and Working With Docker

In this video, we will see how to create Windows virtual machines on Azure. I will use a Windows 10 machine, connect remotely to it using a remote desktop, and installing Docker for Windows in Linux mode. We will see how to verify that Docker installation succeeded and fix some errors. We will also pull a Docker hello-world image from Docker Hub and run a container from it, and also pull a SQL Express image as well as nginx. We will also run many containers from the same images and see how we can verify that, and much more.

### **Commands in the Linux Video**

`$ sudo`

**Clean screen:**

`$ Reset or clear`

Type docker without sudo and without installing docker:

`$ docker`

Install docker:

`$ sudo apt-get update && sudo apt-get install -y docker.io`

Now type docker again:

`$ docker`

List all images of docker:

`$ docker images`

"Got permission denied;" now we understand we need to use sudo with every command as we don't have permission without sudo, so let's list all images of docker using sudo.

List all images of docker:

`$ sudo docker images`

Type sudo bash so we don't need to type sudo with each command:

`$ sudo bash`

Type exit to exit from the root user:

`# exit`

sudo allows users to run programs with the security privileges of another user (normally the superuser, or root). bash starts a new bash shell. So, sudo bash starts a new bash shell with the security privilege of root user.

Run a hello world image to know we are working correctly:

`$ sudo docker run hello-world`

Uninstall Docker then install Docker again:

`$ sudo apt-get remove docker docker-engine docker.io`

Try to see Docker help:

`$ sudo docker run -help`

Type docker ps (process) to see all running images (no images running):

`$ sudo docker ps`

Go to [Docker hub](https://hub.docker.com/explore/). Select the nginx image and see the pull command. Pull this image from Docker hub:

`$ sudo docker pull nginx`

List Docker images:

`$ sudo docker images`

Run the container of nginx image:

`$ sudo docker run nginx`

From another PuTTy see Docker process, you should see now nginx container is running:

`$ sudo docker ps`

On the root, access the process tree, you should see the running container and what is inside:

`$ sudo pstree`

Stop the container by type docker stop and give the container ID which you can get from Docker images:

`$ sudo docker stop ee3434341`

### **Commands in the Windows Video**

Type docker ps (process) to see all running images  
docker ps

Go to [Docker hub](https://hub.docker.com/explore/).

Select nginx image and see the pull command. Pull this image from Docker hub:

`docker pull nginx`

List Docker images:

`docker images`

Run the container of the nginx image:

`docker run nginx`

See now that the nginx container is running:

`docker ps`

Microservices for the Enterprise eBook: [Get Your Copy Here](https://dzone.com/go?i=291432&u=http%3A%2F%2Ftransform.ca.com%2FAPI-microservice-architecture-for-the-enterprise.html%3Fcid%3DNA-DSP-API-AEL-000195-00001674-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dmicroservices_api_acquire%26utm_content%3Dna_eb2-microservice-arch-ent-ddc-postroll%26mrm%3D)

Topics:

microservices ,video ,containers ,linux ,azure ,docker ,tutorial
