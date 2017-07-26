# Development Environments for Microservices

_Captured: 2017-05-03 at 23:42 from [dzone.com](https://dzone.com/articles/development-environments-for-microservices?edition=294992&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-03)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

How do you set up a productive development environment for microservices? While the tooling and infrastructure for building traditional web applications have been highly optimized over time, the same cannot be said for microservices.

In particular, setting up a [productive development environment for microservices](https://www.datawire.io/guide/deployment/) can be considerably more complex than a traditional web application:

  * Your service likely relies on resources like a database or a queue.In production, these will often be provided by your cloud provider, e.g., AWS RDS for databases or Google Pub/Sub for publish/subscribe messaging.
  * Your service might rely on other services that either you or your coworkers maintain. For example, your service might rely on an authentication service.

These external dependencies add complexity to creating and maintaining a development environment. How do you set up your service so you can code and test it productively when your service depends on other resources and services?

This article discusses the various approaches to setting up a development environment, and the tradeoffs.

![Image title](https://dzone.com/storage/temp/5044826-dev-env-msv.png)

## Option #1: Spin Up the Full System Locally

Using tools like [Minikube](https://github.com/kubernetes/minikube) or [Docker Compose](https://docs.docker.com/compose/), you can spin up multiple services locally.  
For resources like databases you use Docker images that match them:

  * For a database like PostgreSQL, you can use the `postgres` Docker image as a replacement for AWS RDS.It won't quite match, but much of the time it will be close enough.
  * For other cloud resources you can often spin up emulators; Google [provides an emulator](https://cloud.google.com/pubsub/docs/emulator) for Google Pub/Sub that you can run locally.
![Image title](https://dzone.com/storage/temp/5044831-dev-env-1.png)

If you're unable to use containers, Daniel Bryant [outlines a number of other approaches](https://opencredo.com/working-locally-with-microservices/) for developing microservices locally with various tradeoffs.

**Pros:**

  * Fast, local development.

**Cons:**

  * Some resources can be hard to emulate locally (e.g., Amazon Kinesis).
  * You need a way to set up and run all your services locally and keep this setup in sync with how you run services in production.
  * Not completely realistic. Depending on the option chosen, there can be major or minor differences from production, e.g., the `postgres` Docker image doesn't quite match the AWS RDS PostgreSQL configuration, mocks/stubs are not a substitute for running a full-blown service.
  * You potentially need to spin up the whole system locally, which will become difficult once you have a large enough number of services and resources.

## Option #2: Spin Up the Full System in the Cloud

You spin up a realistic cluster in the cloud, a staging/testing environment. It might not have as many nodes as the production system since load will be much lower, but it is quite close. Your code also runs in this cluster.

![Image title](https://dzone.com/storage/temp/5044832-dev-env-2.png)

**Pros:**

  * Very realistic.

**Cons:**

  * Development is slower since you need to push code to cloud after every change in order to try it out.
  * Using tools like debuggers is more difficult since the code all runs remotely.
  * Getting log data for development is considerably more complex.
  * Need to pay for additional cloud resources, and [spinning up new clusters and resources is slow](https://www.datawire.io/guide/infrastructure/setting-kubernetes-aws/) (even if you use an [automated tool](http://loom.run)).
  * As a result, you may end up using a shared staging environment rather than one per-developer, which reduces isolation.

## Option #3: Spin Up All Business Logic Locally, Route Cloud Services to Laptop

As with option #1, all services run locally. However, cloud resources (AWS RDS, etc.) are made available locally on your development machine via some sort of tunneling or proxying, e.g., a VPN.

![Image title](https://dzone.com/storage/temp/5044845-dev-env-3.png)

**Pros:**

  * Fast, local development.
  * Very realistic.

**Cons:**

  * You need a way to set up and run all your services locally and keep this setup in sync with how you run services in production.
  * Need to pay for additional cloud resources, and spinning up new cloud resources is slow.
  * As a result, you may end up using a shared staging environment rather than one per-developer, which reduces developer isolation.
  * You potentially need to spin up the whole system locally, which will become difficult once you have a large enough number of services.

## Option #4: Make Local Code for Single Service Available in Remote Cluster

You spin up a realistic cluster in the cloud, a staging/testing environment, but your service runs locally and is proxied/VPNed into the remote cluster.

![Image title](https://dzone.com/storage/temp/5044843-dev-env-4.png)

**Pros:**

  * Fast, local development.
  * Very realistic.
  * Simple local setup.

**Cons:**

  * Need to pay for additional cloud resources, and spinning up new cloud resources is slow.
  * As a result, you may end up using a shared staging environment rather than one per-developer, which reduces developer isolation. This is mitigated by the fact that your changes (and that of others) are local to your environment.
  * Configuring a proxy or VPN that works with your cluster can be complex (although automated tools like [Telepresence](http://www.telepresence.io/) make this easier).

When deciding on the most effective method for setting up a productive development environment for microservices at your organization, you can consider these four options in terms of four main tradeoffs:

  * How closely does the environment mirror production? 

  * How fast is the feedback cycle for developers? 

  * What are the setup and maintenance costs for developers? 

  * How scalable is the environment as your application gets more complex? 

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
