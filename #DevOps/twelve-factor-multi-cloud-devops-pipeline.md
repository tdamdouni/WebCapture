# Twelve-Factor Multi-Cloud DevOps Pipeline

_Captured: 2017-11-25 at 19:21 from [dzone.com](https://dzone.com/articles/twelve-factor-multicloud-devops-pipeline?edition=337908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-25)_

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

## 1\. Source Code Management

The continuous delivery pipeline starts when the developer commits the code related to the microservice, configuration files (Ansible playbook, Chef cookbooks, or shell scripts), or infrastructure as a code such as CFT, ARM, GCP, or Terraform.

Based on organization policy, post-merge to the build branch, it will trigger the build.

## **2\. Build Management**

The pipeline defines the entire lifecycle of an application as code. This can be achieved in many ways, including a Jenkins or Spinnaker pipeline. Spinnaker is a cloud agnostic that can target any cloud platform, and is YAML file based.

Entire stages of an application are written in a JenkinsFile and are executed automatically. There can be N number of Jenkins masters and a pool of executors or agents in order to manage it efficiently. CloudBees JOC Enterprise manages shared slaves quite efficiently. Another way to scale Jenkins is by using DCOS and Marathon, which allow multiple Jenkins masters to share a single pool of resources to run builds. The dynamic destruction or creation of Jenkins agents is directly related to the demand.

## **3\. Quality Management**

SonarQube can analyze [20+ different languages](https://docs.sonarqube.org/display/PLUG/Plugin+Library). The outcome of this analysis includes quality measures and issues (instances where coding rules were broken). However, the software that is analyzed will vary depending on the language.

## **4\. Repository Management**

Artifacts built by Jenkins are pushed to the repository manager and can be tagged based on environments.

## **5\. Docker Registry**

The Docker daemon running on the CI server is going to build an image based on the DockerFile as a source code and will push it to the Docker registry. It can be DockerHub, AWS ECR, Google Container Registry, Azure Container Registry, or even a private registry.

## **6\. Deployment Management**

Here, artifacts are going to pass all the stages starting from dev to prod. We have to ensure that it passes each stage gate as per organization standards and is promoted to a higher environment using the proper tag(s).

## **7\. Build Infrastructure in the Cloud**

If it is a single cloud provider, based on the provider, we can use templates; for AWS, we have Cloud Formation Template, for Azure, we can use Azure Resource Manager, and for Google, it will be Google Cloud Platform Template. We have CLI in build tools agent, which will help us trigger it automatically and create the infrastructure for the target environment.

Terraform is cloud-agnostic and allows a single configuration to be used to manage multiple providers. It can even handle cross-cloud dependencies. This simplifies the management and orchestration of the infrastructure, helping operators build large-scale multi-cloud infrastructures.

If you use [Docker](https://www.docker.com/) or [Packer](https://www.packer.io/), you won't require configuration management tools to configure the server because these tools already have that ability; all you need is a server to run the container. To provide multiple servers, Terraform is the ideal orchestration tool.

## **8\. Container Configuration**

It is advisable to have the _same _container for all environments. There are multiple ways of configuring it. I have listed a few of them below:

  * Set the application configuration dynamically via environment variables.

  * Map the config files via Docker Volumes.

  * Bake configuration into the container.

  * If provided as service, then Fetch it from Config Server.

## **9\. Test Automation**

A fast User Acceptance Test [UAT] feedback cycle is critical for continuous delivery to be successful. Automated Test-Driven Development [ATDD] is a necessity to establish a speedy feedback loop. With ecosystems like Docker and cloud infrastructure, automated tests that require compute, storage, and network environments get easier. For ATDD, we can use Mockito, Cucumber, or Selenium Grid.

## **10\. Container Cluster Management**

Using the microservices architecture, you can easily deploy containers and run your application. These containers are light-weight in comparison to Virtual Machines [VM] and more efficiently use the underlying infrastructure. They can be scaled up or down depending on the demand. In addition, they make it easier to add or remove applications between different environments.

Orchestration tools should have the following capabilities:

  * Provisioning

  * Monitoring

  * Rolling Upgrades and Rollback

  * Configuration-as-text

  * Policies for Placement, Scalability, etc.

  * Administration

A few of the orchestration tools we can use are Kubernetes, Docker Swarm, Mesos+Marathon, Mesosphere DCOS, and Amazon EC2 Container Service.

## **11\. Log Management**

There is a plethora of log management tools available in the market, and Docker has introduced plug-ins for them. These can be installed as binaries.

Listed below are the various drivers for log management:

  * Journald -- storing container logs in the system journal
  * Splunk -- HTTP/HTTPS forwarding to Splunk server
  * Syslog Driver -- supporting UDP, TCP, TLS

For a complete log management solution, additional tools need to be involved:

  * Log parser to structure logs, typically part of log shippers
  * Log indexing, visualisation and alerting
  * Elasticsearch and Kibana
  * Graylog OSS / Enterprise
  * Splunk

## **12\. Monitoring Management**

The Agent collects metrics and events from our systems and apps. You can install at least one Agent in the container, and then it can generate the metrics and publish them.

The user can see the number of containers over time and information across instances such as CPU usage, the operating system usage, and container usage.

![Image title](https://dzone.com/storage/temp/7198461-cicd3.png)

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

Topics:

devops ,docker ,cloud ,ci/cd ,jenkins ,terraform ,aws ,google container engine ,azure

Opinions expressed by DZone contributors are their own.
