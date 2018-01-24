# 50+ Useful Docker Tools

_Captured: 2018-01-02 at 19:23 from [dzone.com](https://dzone.com/articles/50-useful-docker-tools?edition=347150&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-02)_

Are you joining the containers revolution? Start leveraging container management using Platform9's [ultimate guide to Kubernetes deployment](https://dzone.com/go?i=243221&u=https%3A%2F%2Fget.platform9.com%2Fjzlp-kubernetes-deployment-models-the-ultimate-guide%2F).

The container ecosystem is growing and expanding faster than ever, and with so many Docker tools and services, it can feel like a daunting task just understanding the available options. Whether you're a beginner or expert, developer or DevOps engineer, SRE or platform architect, this list will be your companion guide to understanding the most popular offerings for enhancing every stage of your development pipeline with Docker.

## **Docker Tools Categories List**

  * Orchestration and Schedulers

  * Continuous Integration/Continuous Deployment (CI/CD)

  * Monitoring

  * Logging

  * Security

  * Storage/Volume Management

  * Networking

  * Service Discovery

  * Builds

  * Management

## **Orchestration and Schedulers**

## 1\. Kubernetes

Kubernetes is the defacto, most popular container orchestration engine available on the market. Initially begun as a Google project, thousands of teams use it to deploy containers in production. Google claims it runs billions of containers using Kubernetes every week.  
The tool works by grouping containers that make up an application into logical units for easy management and discovery.

**Link: **<https://kubernetes.io>

**Cost:** Free

![](https://i0.wp.com/caylent.com/wp-content/uploads/2017/11/docker-300x72.png?resize=300%2C72)

> _2. Docker Swarm_

Swarm is Docker's answer to a developer's problem of how to orchestrate and schedule containers across many servers. Swarm has been included in Docker Engine since version 1.12.0, and offers advanced features such as baked-in service discovery, load balancing, scaling, and security.

Swarm continues in Docker's tradition of focusing on simplicity and the developer experience. It is arguably easier to use than Kubernetes out of the box.

**Link: **<https://www.docker.com>

**Cost:** Free Community Edition

![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/Mesosphere-DCOS-300x110.png?resize=300%2C110)

## 3\. Mesosphere DC/OS

Mesosphere Datacenter Operating System (DC/OS) is an integrated open-source platform for data and containers built on the Apache Mesos distributed systems kernel. It is designed to treat multiple machines within a data center as one or more clusters either in the cloud or using on-premise software. DC/OS can deploy containers and manage both stateless applications and stateful workloads in the same environment.

Works with Docker Swarm and Kubernetes.

**Link: **<https://dcos.io/>

**Cost:** Mesosphere DC/OS subscription packages are based on the number of nodes (physical or virtual) in your environment.

![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/AmazonECS-300x122.png?resize=300%2C122)

> _4. Amazon ECS_

Amazon Web Services' answer to container orchestration, Amazon ECS is a highly scalable management service which allows developers to run containerized applications on EC2 instances. It is composed of multiple built-in components to enable the simple scheduling and deployment of Docker clusters, tasks, and services.

While there is no support for running containers outside of EC2, the benefits include AWS service advantages such as CloudTrail, CloudWatch, Elastic Load Balancers, etc.

**Link: **<https://aws.amazon.com/ecs/>

**Cost:** Amazon ECS comes at no additional cost. Pay only for the AWS resources (e.g. EC2 instances or EBS volumes) necessary to store and run your application.

![](https://i2.wp.com/caylent.com/wp-content/uploads/2017/11/Azure-Container-Service-ACS.png?resize=270%2C130)

## 5\. Azure Container Service (ACS)

An open-source management service optimized for use on Azure Virtual Machines, Azure Container Service provides the necessary tools to create, configure, and manage open Docker container infrastructure. It offers simplified container-based application development and deployment with support for Kubernetes, Mesospere DC/OS, or Swarm for orchestration.

Scale and orchestrate using application management tools of your choice and connect via standard API endpoints.

**Link: **<https://azure.microsoft.com/en-us/services/container-service/>

**Cost:** Pay only for the virtual machines, and associated storage and networking resources used.

## 6\. Google Container Engine (GKE)

Powered by Kubernetes, GKE can deploy, manage and scale containerized applications on Google Cloud. GKE's aim is to optimize IT team productivity by improving the management of container-based workloads. It hides both complex and simple management tasks behind easy user experience and straightforward command line tools.

Kubernetes is the backbone of GKE. While you don't need to learn it to use GKE, it helps if you understand the basics.

**Link: **<https://cloud.google.com/container-engine/>

**Cost:** Free for 0-5 nodes, 6+ nodes = $0.15/hr ($109.50/mo) per cluste

![](https://i0.wp.com/caylent.com/wp-content/uploads/2017/11/Cloud-Foundry%E2%80%99s-Diego-300x101.png?resize=300%2C101)

## 7\. Cloud Foundry's Diego

Cloud Foundry uses its Diego architecture to manage application containers within the 'garden' environment. Garden follows Linux's Open Container Initiative guidelines for hosting containers and is abstracted through Diego's other components. The Diego elements offer application scheduling and management capabilities through the Cloud Controller.

**Link: **<https://docs.cloudfoundry.org/concepts/diego>

**Cost:** Free

![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/Marathon.png?resize=163%2C156)

## 8\. Marathon

Marathon is a private production-grade Platform-as-a-Service (PaaS) built on Apache Mesos. The Marathon framework promises to scale Dockerized applications and expand to more nodes when necessary to increase the available resource pool. It can also act as a container orchestration tool to provide fault recovery for containerized workloads. Marathon automatically handles hardware or software failures and ensures that an application is "always on."

**Link: **<https://mesosphere.github.io/marathon/>

**Cost:** Free

![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/HashiCorp-Nomad-300x87.png?resize=300%2C87)

## 9\. HashiCorp Nomad

Supported by Linux, Mac, and Windows, Nomad is a single binary tool capable of scheduling all virtualized, containerized, and standalone applications. From a single container to a swarm of thousands, Nomad allows you to run 1 million containers across 5,000 hosts in a matter of minutes. Nomad helps improve density, at the same time as reducing costs, by efficiently allocating more applications on fewer servers.

**Link: **<https://www.nomadproject.io/>

**Cost:** Free

## 10\. Helios

Helios began as Spotify's internal tool for ensuring hundreds of microservices work effectively across several thousand servers. It is capable deploying and managing containers at scale and is equipped with an API based on HTTP as well as a command-line client.

Helios does not need a specific network topology; it merely requires a ZooKeeper cluster and a JVM on the machines which the tool will run on. It is available as an open-source project.

**Link: **<https://github.com/spotify/helios>

**Cost:** Free

![](https://i0.wp.com/caylent.com/wp-content/uploads/2017/11/Rancher-300x44.png?resize=409%2C60)

## 11\. Rancher

Not just a container orchestrator, but a complete container management platform for operating Docker in production. RancherOS is a container-based operating system (OS) that is capable of many infrastructure services such as global and local load balancing, multi-host networking, and volume snapshots. Rancher integrates native Docker management capabilities such as Docker Machine and Swarm.

**Link:**<http://rancher.com/>

**Cost:** Free

## 12\. Nebula

Nebula is a new open source project created for Docker orchestration and designed to manage massive clusters at scale. The tool achieves this by scaling each project component out as far as required. The project's aim is to act as Docker orchestrator for IoT devices as well as for distributed services such as CDN or edge computing. Nebula is capable of simultaneously updating tens of thousands of IoT devices worldwide with a single API call. Nebula aims to help devs and ops treat IoT devices just like distributed Dockerized apps.

**Link:**<http://nebula.readthedocs.io/en/latest/>

**Cost:** Free

## **Continuous Integration/Continuous Deployment (CI/CD)**

## ![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/Jenkins-300x92.png?resize=300%2C92)

13\. Jenkins

Jenkins is a leading CI tool that enables dev and ops teams to automate build and test cycles for applications. As such, it has become a tool synonymous with the DevOps movement. A self-contained Java-based program, Jenkins works right out of the box and delivers hundreds of plugins designed to integrate with other tools across your stack. The tool enables you to quickly provision build agents, deploy artifacts, then tear-down quickly.

**Cost:** Free

![](https://i0.wp.com/caylent.com/wp-content/uploads/2017/11/CircleCI.png?resize=206%2C206)

## 14\. CircleCI

CircleCI promises to help software teams focus on delivering value to customers rather than maintaining CI infrastructure. CircleCI improves IT team's productivity by making the CI process quicker and simpler. It integrates quickly and allows you to build and deploy immediately after signup. Debug manually via SSH and dynamically scale the number of containers at the same time when beginning a project.

**Link:**<https://circleci.com/>

**Cost:** First container is free; open source projects +3 free; additional containers $50/month (per container)

![](https://i2.wp.com/caylent.com/wp-content/uploads/2017/11/Travis-CI-300x93.png?resize=300%2C93)

## 15\. Travis CI

A free open-source CI project, Travis CI improves the efficiency of a development process by enabling the automatic building and testing of code changes. The Software-as-a-Service (Saas) platform is then capable of providing immediate feedback on the code change's success. Travis CI is also capable of automating other parts of your development process by managing deployments and notifications.

**Link: **<https://travis-ci.org/>

**Cost:** Free

![](https://i2.wp.com/caylent.com/wp-content/uploads/2017/11/CodeShip-300x56.png?resize=300%2C56)

## 16\. CodeShip

CodeShip is a fully customizable CI platform which provides native support for Docker by working with your established Docker workflows. The platform is dedicated to speed and security and works by automating your testing and deployment tasks giving you complete control over your build environment. It offers support for many other cloud platforms and orchestration tools.

**Link: **<https://codeship.com/>

**Cost:**

  * Basic: Free for 100 builds/month, pricing starts at $49/month
  * Pro: Starts at $75/month
![](https://i2.wp.com/caylent.com/wp-content/uploads/2017/11/GitLab-CI-300x248.png?resize=233%2C193)

## 17\. GitLab CI

GitLab combines CI, CD and code review to handle your entire application lifecycle. It works in conjunction with GitLab runner on Docker Engine to enable automated tests and builds of apps. Other features include activity streams, IDE, issue tracking, and repository management. GitLab CI also has a built-in container registry to scan and store Docker repositories.

**Link: **<https://about.gitlab.com/features/gitlab-ci-cd/>

**Cost:**

  * Community Edition: Free, unlimited users
  * Enterprise Edition Starter: $3.25/user/month
  * Enterprise Edition Premium: $16.59/user/month
![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/Shippable-300x75.png?resize=300%2C75)

## 18\. Shippable

Speed up software delivery with Shippable; a SaaS platform for developers that dramatically reduces the time needed to build, test and deploy code to production. Shippable is designed to be a one-stop automation platform that enables the practice of DevOps and optimizes innovation by providing complete workflow visibility. The simple plug-and-play interface means Shippable integrates easily with many other application architectures and tech stacks.

**Link: **<https://www.shippable.com/>

**Cost:**

  * Free: c4.large node, unlimited builds, 1 concurrent job
  * $25/75/150/month: c4 large/xlarge/2xlarge nodes, each concurrent job
  * Enterprise Support Add-on: Starts at $500/month

## 19\. CodeFresh

CodeFresh provides a complete toolchain with which devs can create and automate delivery pipelines. Built on Kubernetes, these Docker native CI/CD pipelines offer fast and efficient resource management with caching. CodeFresh combines an enterprise-ready registry with seamless connection and deployment to Kubernetes.

**Link: **<https://codefresh.io/>

**Cost:**

  * Free (public repos only)
  * Basic: Begins at $99/month (public & private repos)
  * Pro: $299/month, dedicated nodes with SSH

## 20\. Buddy

## ![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/Buddy-300x300.png?resize=166%2C166)

Build, test, and deploy apps in no time. Buddy is a CI/CD and user feedback platform with a friendly user interface, fast integration, and tools to make continuous deployment more efficient and productive. It supports all popular languages and frameworks including Angular, Ruby, Python, PHP/Laravel, Node.js, and .NET Core.

**Link: **<https://buddy.works/>

**Cost:**

  * Freelancer: $49/month
  * Team: $99/month
  * Software House: $199/month
  * Mega: $299/month

## 21\. Drone

An open-source CI and Deployment-as-a-service platform, Drone is built on container technology using Go and Docker. The platform requires no installation, configuration or server maintenance and it integrates seamlessly with BitBucket, Heroku, GitHub, and others to automate code building, testing, and deployment using Docker containers.

**Link: **<https://drone.io/>

**Cost:**

  * Nano: $125/month
  * Micro: $250/month
  * Mega: $500/month

## 22\. Wercker

A Docker-native CI & CD automation platform designed to help software developers build and deploy their applications and complex microservice architectures. Featuring native integration with Kubernetes, Wercker automates your deployment workflows so you can focus on building applications.

**Link: **<http://www.wercker.com/>

**Cost:** Community Edition: Free; Virtual Private Pipelines: From $350/month

## **Monitoring**

For Caylent's insight into Container Monitoring, check out our blog post on the pros and cons of [Prometheus and Grafana vs. Sysdig and Sysdig Monitor](http://caylent.com/container-monitoring-prometheus-vs-sysdig/).

## 23\. Sumo Logic

Sumo Logic is a cloud-native, log review tool that provides advanced analysis, visualization, and alerting options. The metrics monitoring solution provides real-time security and operational information, and allows you to diagnose and troubleshoot all application and infrastructure problems. Machine learning analytics also means the quick discovery and future prediction of threats and anomalies before they can become an issue and affect end-users.

**Link: **<https://www.sumologic.com/>

**Cost:**

  * Free: Up to 500MB/day
  * Professional: Logs & Metrics: $90/month, 1GB/day
  * Enterprise: Logs & Metrics: $150/month, 1GB/day

## 24\. Prometheus

Developed by SoundCloud, Prometheus is an open source system-monitoring and alerting toolkit. It incorporates many aspects of monitoring such as metric generation and collection, results visualization, and alerting capabilities for when anomalies occur. Prometheus excels at recording numeric time series and complements both machine-centric monitoring as well as highly dynamic service-oriented architectures.

**Link: **<https://prometheus.io/>

**Cost:** Free

## 25\. Sysdig

Sysdig open-source is the core technology behind all Sysdig products. The open-source tool is designed to provide detailed troubleshooting of a single host and works as a command-line based interface.

**Link: **<https://www.sysdig.org/>

**Cost:**

  * Open-source: Free
  * Basic: $20/month
  * Pro Cloud: $30/month
  * Pro Software: Varies

## 26\. Sysdig Monitor

Sysdig Monitor (formally called Sysdig Cloud) is Sysdig's commercial solution for the generation and analysis of system-level information and real-time data. Designed as a troubleshooting tool for Linux system exploration, it provides in-depth container visibility making it incredibly useful in Docker environments.

**Link: **<https://sysdig.com/product/how-it-works/>

**Cost:** Flexible pricing for Cloud and Software versions

## 27\. Datadog

Datadog is a SaaS-based data analytics platform for large-scale cloud environments that generates and collects metrics/data events from servers, databases, and applications. The full-stack monitoring service provides support for Docker, Kubernetes, and Mesos.

**Link:**<https://www.datadoghq.com/>

**Cost:**

  * Free up to 5 hosts
  * Pro: $15/host/month
  * Enterprise: $23/host/month

## 28\. New Relic

An industry leader, New Relic is a pure SaaS-based performance management solution which allows developers to diagnose and fix application performance problems in real-time. Its application performance monitoring (APM) capabilities provide instant visibility, and the Linux agent within its infrastructure automatically collects Docker container metrics which are running on instrumented hosts.

**Link: **<https://newrelic.com/>

**Cost:**

  * Self-Hosted Environments: Pro $149/month; Essentials: $75/month
  * Cloud-Based Options: Dependant on Provider and Instance Size, Runtime, and Quantity
![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/cAdvisor-300x152.png?resize=263%2C133)

## 29\. cAdvisor

Google's cAdvisor (Container Advisor) is a monitoring solution which analyzes all performance characteristics and resource usage of containers running in Docker. The tool generates and collects container metrics such as network statistics, resource isolation parameters, and a complete history of resource usage.

**Link: **<https://github.com/google/cadvisor>

**Cost:** Free

## **Logging**

## 30\. Logspout

Logspout is a great tool for helping to manage the logs generated by programs running inside Docker containers. It routes container-app logs to a single location (e.g. to a JSON object or a streamed endpoint available over HTTP). Logspout also has an extensible module system.

**Link: **<https://github.com/gliderlabs/logspout>

**Cost:** Free

![](https://i0.wp.com/caylent.com/wp-content/uploads/2017/11/Fluentd-300x104.png?resize=300%2C104)

## 31\. Fluentd

Fluentd works as an open source data collector-a container for unifying and logging all other containers' logs. With 500+ plugins, Fluentd connects to many data sources and data outputs to collect events; these are tagged to route them where needed. This tag-based routing enables complex routing to be expressed cleanly.

**Link: **<https://www.fluentd.org/>

**Cost:** Free

![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/logstash-300x89.png?resize=300%2C89)

## 32\. Logstash

Part of Elastic Stack, Logstash works well alongside Beats, Elasticsearch, and Kibana. It is an open source, server-side processing pipeline that transports and processes your logs, events, or other data.

**Link: **<https://www.elastic.co/products/logstash>

**Cost:** Free

![](https://i2.wp.com/caylent.com/wp-content/uploads/2017/11/syslog-ng-300x127.png?resize=300%2C127)

## 33\. syslog-ng

Use syslog-ng to collect logs from various sources and process them in near real-time before routing them to different destinations. A well-trusted log management infrastructure, syslog-ng combines high-performance capabilities with rich message parsing and re-writing options.

**Link: **<https://syslog-ng.org/>

**Cost:** Free (Pricing for syslog-ng Premium Edition available on request)

# Security

## 34\. Clair

Clair is an open source project designed to identify and analyze vulnerabilities in Docker and appc application containers. Clair regularly ingests container vulnerability metadata from a customized and configured group of sources in order to identify threats in container images, including those upstream.

**Link: **<https://coreos.com/clair/docs/latest/>

**Cost:** Free

![](https://i0.wp.com/caylent.com/wp-content/uploads/2017/11/Aqua-Security-300x108.png?resize=300%2C108)

## 35\. Aqua Security

Aqua Security works on any platform to secure container-based applications by providing full-stack security. A purpose-built platform, Aqua Security allows tight control of your container environment and process from development phase and beyond. It is a comprehensive tool which provides full visibility and management.

**Link: **<https://www.aquasec.com/>

**Cost:** Pricing is a combination of selected software plan charges plus Azure infrastructure costs for the necessary virtual machines

## 36\. Twistlock

Twistlock Security Suite aims to solve the issue of security in the container based application process. It is an end-to-end security solution which detects vulnerabilities by increasing the layers of monitoring for the way Docker containers work. Twistlock hardens container images and enforces security policies across an application's lifecycle.

**Link: **<https://www.twistlock.com/>

**Cost:** Software pricing is based on chosen subscription and infrastructure options

## 37\. Docker Bench for Security

Docker Bench for Security is a prebuilt packaged container that can be run on any Docker host. It is a group of Bash shell scripts which should be run as a root user. The tests check for common best security practices around deploying Docker containers in production.

**Link: **<https://hub.docker.com/r/docker/docker-bench-security/>

**Cost:** Free

![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/Docker-Notary.png?resize=180%2C162)

## 38\. Docker Notary

Notary is an open-source Docker project that provides security over data collections. Run a Notary service to publish and manage arbitrary content. Digitally sign published collections and allow users to verify the integrity and origin of content.

**Link: **<https://github.com/docker/notary>

**Cost:** Free

## **Storage/Volume Management**

## 39\. Convoy

A Docker volume plugin created by Rancher for managing persistent container volumes. Convoy, an open-source Docker volume driver, can snapshot, backup, and restore Docker volumes anywhere. Create Docker volumes on AWS, supported by all the features and performance of Elastic Block Store. Also, take an existing EBS volume and use it to generate a volume attached to a Docker container.

**Link: **<https://github.com/rancher/convoy>

**Cost:** Free

![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/Portworx-300x118.png?resize=300%2C118)

## 40\. Portworx

Portworx is a decentralized storage solution for persistent, shared and replicated volumes; it automates the deployment and operations of data services at scale.

**Link: **<https://portworx.com/>

**Cost:** Free

## 41\. Blockbridge

The Blockbridge Volume Plugin provides high-performance storage for container applications with advanced security, mobility, backup and restore capabilities. With the 'Managed Docker Plugin' for Docker 1.13+, installation and lifecycle management is taken care of by Docker natively.

**Link: **<http://www.blockbridge.com/>

**Cost:** Free

![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/Flocker.png?resize=178%2C154)

## 42\. Flocker

Easily manage Dockerized applications and container storage with this open source data volume orchestrator. The ephemeral nature of Docker containers means that when a container is deleted, its storage is lost. Flocker allows you to store data persistently by migrating data along with containers as the host changes.

**Link: **<https://clusterhq.com/flocker/>

**Cost:** Free

## **Networking**

![](https://i2.wp.com/caylent.com/wp-content/uploads/2017/11/flannel-300x91.png?resize=300%2C91)

## 43\. flannel

Designed for Kubernetes, flannel is a simple and easy way to configure a secure network fabric by using a Layer 3 IPv4 network between multiple nodes in a cluster. It doesn't control how containers are networked to the host platform, only how the traffic is transported between hosts.

**Link: **<https://coreos.com/flannel/docs/latest/>

**Cost:** Free

![](https://i1.wp.com/caylent.com/wp-content/uploads/2017/11/weaveworks-1-300x124.png?resize=300%2C124)

> _44. Weaveworks_

Weaveworks delivers a productive way for developers to connect, observe and control Docker containers. It creates a flexible virtual network infrastructure that connects containers which are deployed across multiple hosts. Weaveworks extends the efficiency of container orchestrators like Kubernetes and Docker Swarm and simplifies the management of containers in production.

**Link: **<https://www.weave.works/>

**Cost:**

  * Standard: $30 per node/month or $300 annually
  * Enterprise: $150 per node/month or $1500 annually
![](https://i2.wp.com/caylent.com/wp-content/uploads/2017/11/Project-Calico.png?resize=207%2C207)

## 45\. Project Calico

A highly scalable open source project, Calico provides a Layer 3 approach to virtual networking which can support a vast number of virtual machine clusters across countless compute hosts. This tool's simplified network model design supports the configuration of fine-grained connectivity policies for each of your workloads and allows SDNs to be centrally managed.

**Link: **<https://www.projectcalico.org/getting-started/docker/>

**Cost:** Free

## **Service Discovery**

## 46\. Consul

Consul is an easy-to-use, open standards-based approach to service discovery, and runs on FreeBSD, Linux, Mac OS X, Solaris, and Windows. Built to be multi-datacenter aware, Consul offers support for multiple regions without complex configuration. Key features include: service discovery, health checking, and key/value storage, etc.

**Link: **<https://www.consul.io/>

**Cost:** Free

## 47\. Etcd

Created by CoreOS, etcd is a highly-available key-value store designed for shared configuration and service discovery. The tool provides a reliable way to store data over a cluster of machines. It was built especially for clusters running CoreOS, but etcd also works on other operating systems including BSD, Linux, and OS X.

**Link: **<https://coreos.com/etcd/>

**Cost:** Free

## 48\. Proxy

Factorish created proxy as a simple-to-use lightweight ( < 30mb ) container. The tool is based on alpine/gliderlabs with nginx running as a HTTP load balancer.

**Link: **<https://hub.docker.com/r/factorish/proxy/>

**Cost:** Free

## **Builds**

## 49\. Packer

Packer is a Hashicorp tool created to build machine images-including Docker-and integrate with configuration management tools like Ansible, Chef, and Puppet. It is a lightweight tool which runs on every major OS from a single source configuration.

**Link: **<https://www.packer.io/docs/builders/docker.html>

**Cost:** Free

![](https://i2.wp.com/caylent.com/wp-content/uploads/2017/11/Whales.png?resize=247%2C162)

## 50\. Whales

Automatically Dockerize your applications with Whales. The only thing needed is to have Docker installed and running on the host machine. Whales then works by outputting the necessary files to run your applications with Docker.

**Cost:** Free

## 51\. Gradle

The Gradle plugin makes it simple for all your build scripts to talk to a Docker daemon. Each task delegates to the Docker-client, which then connects to Docker's remote API via HTTP. Most configuration parameters are optional.

**Cost:** Free

## **Management**

## 52\. Portainer

Portainer is an open-source lightweight management user interface for Docker environments. Portainer works on top of the Docker API and provides a detailed overview of Docker. Capabilities include the ability to manage containers, images, networks, and volumes.

**Link:**<https://portainer.io/>

**Cost:** Free

And that's the complete list! As always, [Caylent](https://caylent.com/) would love your feedback and suggestions for future articles.

Using Containers? Read our [Kubernetes Comparison eBook](https://dzone.com/go?i=243223&u=https%3A%2F%2Fget.platform9.com%2Fjzlp-kubernetes-comparison-ebook%2F) to learn the positives and negatives of Kubernetes, Mesos, Docker Swarm and EC2 Container Services.
