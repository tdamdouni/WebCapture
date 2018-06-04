# Easily Automate Your CI/CD Pipeline With Jenkins, Helm, and Kubernetes

_Captured: 2018-03-07 at 15:30 from [dzone.com](https://dzone.com/articles/easily-automate-your-cicd-pipeline-with-jenkins-he?edition=366204&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-03-07)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

Developers don't want to think about infrastructure and why it takes so long to deploy their code to a real testing environment. They just want it up and running!

This 6-step workflow will easily automate your CI/CD pipeline for quick and easy deployments using Jenkins, Helm, and Kubernetes.

Nowadays it's critical to get your releases out fast, which requires having an automated CI/CD pipeline that takes your code from text to binaries to a deployed environment. Implementing an automated pipeline in the past has been challenging, especially when dealing with legacy applications. This is where [Kubernetes](https://kubernetes.io/) comes in. Kubernetes has revolutionized the way we deploy and manage our containerized applications. Using [Helm](https://helm.sh/) together with Kubernetes, you gain simplified application deployment.

This article will show you how to prepare and configure your environment to achieve a complete automated CI/CD pipeline for your containerized applications using [Jenkins](https://jenkins.io/), Helm, and Kubernetes. You will receive tips on how to optimize your pipeline and a working template for customizing your own pipeline.

In order to get familiar with the Kubernetes environment, I have mapped the traditional Jenkins pipeline with the main steps of my solution.

**![Image title](https://dzone.com/storage/temp/8260021-ci-cd-jenkins-helm-k8s.png)**

Note: This workflow is also applicable when implementing other tools or for partial implementations.

## ****Setting Up the Environment****

### ****Configure the Software Components****

Before you create your automated pipeline, you need to set up and configure your software components according to the following configuration:

### Software Components

### Recommended Configuration

**A Kubernetes Cluster**

  * Set up the cluster on your data center or on the cloud.

**A Docker Registry**

  * Find a [solution for hosting a private Docker registry](https://www.jfrog.com/confluence/display/RTF/Docker+Registry).
  * Consider requirements like privacy, security, latency, and availability when choosing a solution.

**A Helm Repository**

  * Find a [solution for hosting a private Helm repository](https://jfrog.com/blog/master-helm-chart-repositories-artifactory/).
  * Consider requirements like privacy, security, latency, and availability when choosing a solution.

**Isolated Environments**

  * Create different namespaces or clusters for **Development** and **Staging**
  * Create a dedicated and isolated cluster for **Production**

**Jenkins Master**

  * Set up the master with a standard Jenkins configuration.
  * If you are not using slaves, the Jenkins master needs to be configured with Docker, Kubectl, and Helm.

**Jenkins Slave(s)**

  * It is recommended to run the Jenkins slave(s) in Kubernetes to be closer to the API server which promotes easier configuration.
  * Use the [Jenkins Kubernetes plugin](https://plugins.jenkins.io/kubernetes) to spin up the slaves in your Kubernetes clusters.

### **Prepare Your Applications**

Follow these guidelines when preparing your applications:

  * Package your applications in a Docker Image according to the [Docker Best Practices](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/).
  * To run the same Docker container in any of these environments: Development, Staging or Production, separate the processes and the configurations as follows: 
    * For Development: Create a default configuration.
    * For Staging and Production: Create a non-default configuration using one or more: 
      * Configuration files that can be mounted into the container during runtime.
      * Environment variables that are passed to the Docker container.

## The 6-Step Automated CI/CD Pipeline in Kubernetes in Action

### General Assumptions and Guidelines

  * These steps are aligned with the best practices when running Jenkins agent(s).
  * Assign a dedicated agent for building the App, and an additional agent for the deployment tasks. This is up to your good judgment.
  * Run the pipeline for every branch. To do so, use the [Jenkins Multibranch pipeline job](https://jenkins.io/doc/book/pipeline/multibranch/).
  1. Get code from Git 
    1. Developer pushes code to Git, which triggers a Jenkins build webhook.
    2. Jenkins pulls the latest code changes.
  2. Run build and unit tests 
    1. Jenkins runs the build.
    2. Application's Docker image is created during the build.- Tests run against a running Docker container.
  3. Publish Docker image and Helm Chart 
    1. Application's Docker image is pushed to the Docker registry.
    2. Helm chart is packed and uploaded to the Helm repository.
  4. Deploy to Development 
    1. Application is deployed to the Kubernetes development cluster or namespace using the published Helm chart.
    2. Tests run against the deployed application in Kubernetes development environment.
  5. Deploy to Staging 
    1. Application is deployed to Kubernetes staging cluster or namespace using the published Helm chart.
    2. Run tests against the deployed application in the Kubernetes staging environment.
  6. [Optional] Deploy to Production 
    1. The application is deployed to the production cluster if the application meets the defined criteria. Please note that you can set up as a manual approval step.
    2. Sanity tests run against the deployed application.
    3. If required, you can perform a rollback.

## **Create Your Own Automated CI/CD Pipeline**

Feel free to build a similar implementation using the following sample framework that I have put together just for this purpose:

Bon voyage for your Kubernetes CI/CD voyage!

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**

Topics:

jenkins ,kubernetes ,helm ,docker ,jenkins pipeline ,ci/cd ,devops

Opinions expressed by DZone contributors are their own.
