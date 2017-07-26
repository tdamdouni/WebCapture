# The Ultimate DevOps Tools Ecosystem Tutorial, Part V: Release

_Captured: 2017-02-15 at 04:22 from [dzone.com](https://dzone.com/articles/the-ultimate-devops-tools-ecosystem-tutorial-part-4?edition=268944&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-14)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

We've arrived at part 5 of our "Ultimate DevOps Tools Ecosystem Tutorial" blog series. This series is covering the top DevOps and development process tools, divided into five stages: Plan, Develop, Test, Release, and Operate. You can see the complete infographic here:

![devops tools ecosystem infographic](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/DevOps-Infographic-v1.4%20690x690.png)

In [part 1](https://www.blazemeter.com/blog/ultimate-devops-tools-ecosystem-tutorial-part-1?utm_source=BM&utm_medium=BM_blog&utm_campaign=ultimate-devops-tools-ecosystem-tutorial-part5) of the series, we introduced the DevOps work cycle. In part 2, we covered the [Plan](https://www.blazemeter.com/blog/ultimate-devops-tools-ecosystem-tutorial-part-2-planning?utm_source=BM&utm_medium=BM_blog&utm_campaign=ultimate-devops-tools-ecosystem-tutorial-part5) stage. In part 3, we went over the [Develop](https://www.blazemeter.com/blog/ultimate-devops-tools-ecosystem-tutorial-part-3-developing?utm_source=BM&utm_medium=BM_blog&utm_campaign=ultimate-devops-tools-ecosystem-tutorial-part5) stage. In part 4, we explained the [Test](https://www.blazemeter.com/blog/ultimate-devops-tools-ecosystem-tutorial-part-4-testing?utm_source=BM&utm_medium=BM_blog&utm_campaign=ultimate-devops-tools-ecosystem-tutorial-part5) stage. This time, we will dive into the Release stage.

The Release stage takes place through all the layers of the infrastructure and the company. It includes deployment tools, containers, and release tools, as well as configuration management and Cloud foundation for scalability. The release stage takes us from code to working product.

Here are some of the top tools for the release stage.

## Configuration Management: Chef, Puppet, and Ansible

Configuration management lays the groundwork for the app and its dependencies, by tracking and updating information about hardware and software. It can also be used for continuous deployment strategies by automatically distributing changes.

[Chef](https://www.chef.io/), [Puppet](https://puppet.com/), and [Ansible](https://www.ansible.com/) are three similar tools that help you build strong and automated infrastructure by IT automation that operates and deploys your infrastructure.

![ansible](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/ansible.svg)

### **Which One Should You Choose?**

  * In Chef and Puppet, the language/DSL is more flexible than Ansible's YAML files. But, it's hard to manage multi-DC masters and replication. In addition, these systems need to manage another PKI (public key infrastructure), unlike Ansible which uses an existing infrastructure. This makes the infrastructure management more complex.
  * Ansible can run ad-hoc commands, it enables simple reading and writing using YAML files, it's agentless, and the PKI is already there if you have ssh access to the machines. However, in Ansible, YAML files are strict and prone to indentation errors.

In general, for all config management tools, every change has to run dynamically on the servers, but they might break at runtime. The solution for the runtime issue is immutable infrastructure, so read on to the next section: containers.

## Container Runtimes and Orchestrators: Docker, rkt (Rocket), Kubernetes, and Nomad

Containers are tools that assist keeping releases organized, by delivering the changes in an isolated structure. Once, releasing required sending a code in a separate file that needed to be uploaded to the server. Today, with containers, developers can prepare a container image that contains all the needed dependencies. The container image is distributed to developers and to QA, who don't need to install anything but can use it straight from the dev laptop to production.

Container runtimes are tools that run the containers on a single machine. Orchestrators run containers on clusters through the runtimes. Container runtimes and orchestrators help you eliminate the need for single-purpose machines (called pets). Instead, a cluster of machines is treated as one giant machine, thus using the full capacity of your machines. All you need to know is how much compute/disk you need to run your app, and the framework will do the rest to distribute your app and make it available somewhere in the cluster. In any case, you need to add capacity to the cluster you just add new machines.

[Docker](https://www.docker.com/) and [rkt](https://github.com/coreos/rkt) are both runtime tools for containers. They leverage Linux kernel features such as CGroups and namespaces, for achieving isolation, security and resource management (CPU, memory, etc.). In addition, they are both very useful for building immutable infrastructure and for pushing the artifacts to a central repository (registry). With them, you build once and run anywhere. Finally, they enable wrapping the application and its dependencies into the same container, with the config mgmt scheme the organization used to separate dependencies (ops) from the app (dev). This ensures scalability of code since the image is immutable and runs the same way, whether it's one container or 200 containers.

![docker containers](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/docker.svg)

### **Which One Should You Choose?**

  * Docker and Rocket have very similar features, even though Docker is more mainstream and it has a large supporting open-source community.
  * Rocket pushes to standardize containers, while Docker keep breaking APIs compatibility with each version as it tries to build its own platform.

[Kubernetes](https://kubernetes.io/) is by far the largest distributed computing framework, i.e orchestrator. It orchestrates containers and helps interconnect containers across machines and hosts. It includes secret, config management, deployments and service discovery.

[Nomad](https://www.nomadproject.io/) is an orchestrator that is a scheduler. It can schedule and distribute binaries, jars and containers for managing the workload across a cluster of machines. Nomad compares to the Kubernetes scheduler (which is a part of the complete Kubernetes framework). All of the Hashicorp (Nomad's creators) tools stand in their own right, but can also be tied together. With Nomad you can achieve service discovery mechanism by attaching a [consul.io cluster](https://www.consul.io/). For secret management, you will need [Vault](https://www.vaultproject.io/).

  * Both tools are very strong and there is no clear choice.
  * Kubernetes is supported by a strong open-source community. However, unlike Nomad or any other orchestrator, Kubernetes supports containers-only infrastructure, whether it's Docker, rkt (by CoreOS), or Hyper through its CRI interface. This means that every process has to be in containers.

## Cloud Infrastructure: AWS, Google Cloud, and Microsoft Azure

Cloud infrastructure platforms offer infrastructure as a service. They enable compute, i.e., virtual machines and database services, as well as storage and availability. Through their infrastructure developers and teams can develop, provide services and manage and store their code, products, and applications. One of their main advantages is that they enable companies to lease compute that had to be purchased in the past. This enables companies that grow or diminish to scale according to their needs, without an in-house DevOps engineer.

[AWS (Amazon Web Services)](https://aws.amazon.com/), [Google Cloud](https://cloud.google.com/), and [Microsoft Azure](https://azure.microsoft.com/en-us/) are the largest and most stable cloud infrastructure platforms. AWS is the leading provider that invented the market and has the largest market share, but both Google Cloud and Microsoft Azure are making progress and leveling the playing field when it comes to features and abilities.

### **Which One Should You Choose?**

  * AWS has the most functionalities.
  * Google Cloud is rapidly improving the number of its features and has the most user-friendly interface.
  * Microsoft Azure is improving the number of its features as well as its reliability and stability, their geographical reach is the widest and they have the most special certifications.

We're almost done with the cycle! Next time we will go over the last phase: Operate. Stay tuned!

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
