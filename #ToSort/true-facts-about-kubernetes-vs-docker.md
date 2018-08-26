# True Facts About Kubernetes vs. Docker

_Captured: 2018-08-07 at 19:12 from [dzone.com](https://dzone.com/articles/true-facts-about-kubernetes-vs-docker-itsyndicate?edition=385338&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-08-07)_

See why enterprise app developers love Cloud Foundry. [Download](https://dzone.com/go?i=295426&u=https%3A%2F%2Fwww.cloudfoundry.org%2Fcf-user-report-2018%2F%3Futm_source%3Ddzone%26utm_medium%3Dpaid%26utm_campaign%3Dleadgen) the 2018 User Survey for a snapshot of Cloud Foundry users' deployments and productivity.

## Understanding Docker and Kubernetes: Container Orchestration

In the last few years, containers have changed the face of software development and deployment. As a result, anyone working in the DevOps space sooner or later will come across the "Kubernetes vs Docker" discussion. The conversation might be perplexing at first as Docker and Kubernetes are not direct competitors. As we'll find out, the discussion should be more geared towards "Kubernetes vs Docker Swarm".

However, for any DevOps practitioner, it's important to understand the ins and outs of Docker and Kubernetes. Both technologies are improving rapidly and changing DevOps practices. So a good understanding of where these technologies stand will help you gain a competitive advantage for your business.

## Docker and the Rise of Containers

Containers are lightweight executable packages that run as a stand-alone software. They contain all the necessary components like code, runtime, system tools, libraries, and configuration settings to execute consistently.

Docker is an open platform for containers. It's not the first of its kind. Container platforms have been around since the 1970s. Their development can be traced back to the chroot system call in Unix. In the early 2000s, the development of the FreeBSD Jails and Linux Servers led to the [Linux Containers (LXCs) ](https://linuxcontainers.org/) in 2008. Docker emerged in the container space in around 2013 and became an instant success. The reason was Docker made it simple to run containers; you can see the simplicity of Docker usage by reading this article which describes [Top Docker commands](https://itsyndicate.org/blog/docker-commands-any-docker-expert-must-know/) and how to use them. With Docker, developers could start, stop and destroy containers easily. The low learning curve and ease-of-use made it a staple in the software development process.

Initially, due to security concerns, IT operations teams weren't enthusiastic about using containers in production. At the time, they were already using Virtual Machines (VMs). But unlike VMs, the kernel of the host machine is shared among the containers. So the risk of taking down the host machine through a container is higher. Using this vulnerability, hackers can easily launch Denial of Service (DoS) and other forms of attacks. Also, containers are created from common images and teams were wary about using bad images that might put the whole production pipeline at risk.

Despite the concerns from production teams, Docker kept gaining momentum because it made life easier for developers. As the technology matured, the Docker open source community placed more emphasis on resolving the security concerns. Soon Docker containers started to show up in production environments.

## Kubernetes and the Need for Container Orchestration

The journey of Kubernetes started independently of Docker. Around 2003, Google created the Borg System to deal with its growing cluster management problems. It was an internal tool. In mid-2014, Google introduced Kubernetes as an open-source version of the Borg System. Soon Microsoft, RedHat, IBM, and Docker joined to support the Kubernetes community.

Kubernetes is a container orchestration solution. When developers are dealing with a handful of containers in a development environment, managing the services isn't a big deal. But when the application is deployed to a production environment and there are hundreds or thousands of containers and services, the management tasks become complex. Kubernetes simplifies the container management problem for large-scale deployments.

In a Kubernetes environment, developers create their applications using the concept of pods. Pods are containers clustered together that work like single units. These pods are deployed to the Kubernetes master node along with the configuration requirements like the number of pods and the network settings. The master node manages the worker nodes. After the pods are deployed, it's the responsibility of the master node to keep track of the containers. Suppose a container gets stuck on one of the worker nodes. The master will spin up a new container and destroy the rogue one. Kubernetes makes container management and orchestration easy for the production team.

## Understanding the Intersection of Kubernetes and Docker

From the above discussion, it should be evident that Docker containers are managed using Kubernetes. So there shouldn't be any "Docker vs. Kubernetes" discussion. But Docker has a product called Docker Swarm. It's a clustering and scheduling tool. It's kind of similar to Kubernetes, so anyone who is looking into container orchestration tools should look into "Kubernetes vs. Docker Swarm" comparisons.

Due to the popularity of Docker, a lot of development teams start container orchestration using Docker Swarm. It seems like the natural next step. It is easy to learn, and Kubernetes has a steeper learning curve. But it is getting easier to learn it using [Minikube](https://kubernetes.io/docs/setup/minikube/), a tool to run a single node Kubernetes cluster.

Another important factor is that Kubernetes has a stronger community than Docker Swarm and all the major cloud providers are supporting it. Amazon AWS has started [Amazon Elastic Container Service for Kubernetes (Amazon EKS)](https://aws.amazon.com/eks/), Google Cloud has [Kubernetes Engine](https://cloud.google.com/kubernetes-engine/), and Microsoft Azure has [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/en-us/services/kubernetes-service/). So it seems for the moment, major market forces are betting on Kubernetes as a container orchestration solution.

## Key Trends in Docker and Kubernetes

DevOps teams who are managing Docker and Kubernetes environments should keep an eye on these key trends:

  * **Use of Microservices:** Microservices architecture is one of the big contributors to the rise of container use. In this architecture, applications are broken into smaller and independent services. Containers are a natural fit for supporting these kinds of applications in a production environment. So expect to support more microservices-based applications that use Docker and Kubernetes.
  * **Increase in Multi-cloud Environments:** Enterprises are getting nervous about using single- cloud solutions. So they are seeking out multi-cloud environments to have more options and decrease dependency on a single vendor. It means DevOps teams have to have the skills necessary to run Docker and Kubernetes in multi-cloud environments which will bring new challenges.
  * **Growing support for Docker and Kubernetes:** Both Docker and Kubernetes have strong communities behind them. [Docker Hub](https://hub.docker.com/) has an active user base that regularly updates images for various applications. Kubernetes is also enjoying a strong support from both the open source community and big companies like Amazon, Google, Microsoft, and IBM. So Docker and Kubernetes are going to become more common in both enterprises and small businesses.

##  Final Thoughts

Instead of "Kubernetes vs. Docker," the discussion should concentrate on "Kubernetes vs. Docker Swarm." Both of these technologies have important roles to play in today's software landscape. Docker containers improve the development process and Kubernetes container orchestration improves the deployment process. DevOps teams can harness the power of these technologies to build more robust continuous integration and continuous delivery (CI/CD) pipelines for faster and more reliable software development cycles.

Cloud Foundry saves app developers $100K and 10 weeks on average per development cycle. [Download](https://dzone.com/go?i=295427&u=https%3A%2F%2Fwww.cloudfoundry.org%2Fcf-user-report-2018%2F%3Futm_source%3Ddzone%26utm_medium%3Dpaid%26utm_campaign%3Dleadgen) the 2018 User Survey for a snapshot of Cloud Foundry users' deployments and productivity. Find out what people love about the industry standard cloud application platform.

Topics:

kubernetes ,docker ,container orchestration ,devops ,comparison ,cloud
