# Announcing the General Availability of Jenkin's Declarative Pipeline

_Captured: 2017-04-03 at 09:11 from [dzone.com](https://dzone.com/articles/announcing-general-availability-of-declarative-pip?oid=twitter&utm_content=buffercdedd&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

I am very excited to announce the addition of [Declarative Pipeline syntax](https://plugins.jenkins.io/pipeline-model-definition) 1.0 to [Jenkins Pipeline](https://plugins.jenkins.io/workflow-aggregator). We think this new syntax will enable everyone involved in DevOps, regardless of expertise, to participate in the Continuous Delivery process. Whether creating, editing, or reviewing a pipeline, having a straightforward structure helps to understand and predict the flow of the pipeline and provides a common foundation across all pipelines.

Pipeline as Code was one of the pillars of the Jenkins 2.0 release and an essential part of implementing continuous delivery. Defining all of the stages of an application's CD pipeline within a Jenkinsfile and treating it as part of the application code automatically provides all of the benefits inherent in SCM:

  * Retain history of all changes to Pipeline.
  * Rollback to a previous pipeline version.
  * Review new changes to the pipeline in code review.
  * Test new pipeline steps in branches.
  * Audit changes to the pipeline.
  * Run the same pipeline on a different Jenkins server.

We recommend people begin using it for all their pipeline definitions in Jenkins and the CloudBees Jenkins Platform. The plugin has been available for use and testing starting with the 0.1 release that was debuted at [Jenkins World](https://www.cloudbees.com/introducing-new-way-define-jenkins-pipelines) in September. It has already been installed over 5,000 times.

If you haven't tried Pipeline or have considered Pipeline in the past, we believe this new syntax is much more approachable with an easy adoption curve so that you can quickly realize all of the benefits of Pipeline as Code. In addition, the predefined structure of Declarative makes it possible to create and edit pipelines with a graphical user interface (GUI). The Blue Ocean team is actively working on a Pipeline Editor that will be included in an upcoming release.

If you have already begun using Pipelines in Jenkins we believe that this new alternative syntax can help expand that usage. The original syntax for defining pipelines in Jenkins is a Groovy DSL that allows most of the features of full imperative programming. This syntax is still fully supported and is now referred to as "Scripted Pipeline Syntax" to distinguish it from "Declarative Pipeline Syntax." Both use the same underlying execution engine in Jenkins and both will generate the same results in Pipeline Stage View or Blue Ocean visualization. All existing pipeline steps, global variables and shared libraries can be used in either. You can now create more cookie-cutter pipelines and extend the power of Pipeline to all users regardless of Groovy expertise.

Other key features of Declarative Pipeline include the following.

## **Syntax Checking **

  * Immediate runtime syntax checking with explicit error messages.
  * API endpoint for linting Jenkinsfiles.
  * CLI command to lint Jenkinsfiles.

## Docker Pipeline Plugin Integration

  * Run all stages in a single container.
  * Run each stage in a different container.

## Easy Configuration

  * Quickly define parameters for your pipeline.
  * Quickly define environment variables and credentials for your pipeline.
  * Quickly define options (such as timeout, retry, and build discarding) for your pipeline.

## Conditional Actions

  * Send notifications or take actions depending upon success or failure.
  * Skip stages based on branches, environment, or other Boolean expressions.![](https://www.cloudbees.com/sites/default/files/declarative-pipeline-refcard-page-1.png)

Be on the lookout for future blog posts here or on Jenkins.io detailing specific examples of scenarios or features in Declarative Pipeline. Andrew Bayer, one of the primary engineers behind Declarative Pipeline, will be presenting at [FOSDEM](https://fosdem.org/2017/schedule/event/declarative_pipeline/) in Brussels, Belgium this weekend. We have also scheduled an online [Jenkins Area Meetup (JAM)](https://www.meetup.com/Jenkins-online-meetup/events/237317346/) later this month to demo the features of Declarative Pipeline and give a sneak peek at the upcoming Blue Ocean Pipeline Editor.

In the meantime, we have updated all [Pipeline documentation](https://jenkins.io/doc/) to incorporate a Getting Started guide, a Guided Tour, and a Syntax Reference page with numerous examples to help you get on your way. We have also created a that can be printed and hung nearby.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).

### Like This Article? Read More From DZone
