# Creating Microservices on the Pivotal Platform

_Captured: 2017-06-08 at 21:21 from [dzone.com](https://dzone.com/articles/spring-cloud-microservices-at-pivotal-platform?edition=304123&utm_source=weekly%20digest&utm_medium=email&utm_campaign=wd%202017-06-07)_

Build APIs from SQL and NoSQL or Salesforce data sources in seconds.[ Read the Creating REST APIs white paper](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D), brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Imagine you have multiple microservices running on different machines as multiple instances. It seems natural to think about the tools that help you in the process of monitoring and managing all of them. If we add that our microservices like most people are created based on the Spring Cloud framework obviously seems to look at the Pivotal platform. Here is a figure with the platform's architecture downloaded from the main Pivotal site.

![Image title](https://dzone.com/storage/temp/5439056-pvdi-microservices-architecture.png)

Although the Pivotal platform can run applications written in many languages, it has the best support for Spring Cloud Services and Netflix OSS tools, like you see in the figure above. From the possibilities offered by Pivotal, we can take advantage in three ways:

**Pivotal Cloud Foundry** \- this solution can be run on public IaaS or a private cloud like AWS, Google Cloud Platform, Microsoft Azure, VMware vSphere, or OpenStack.

**Pivotal Web Services **\- a hosted cloud-native platform available at the pivotal.io site.

**PCF Dev** \- this instance can be run locally as a single virtual machine. It offers the opportunity to develop apps using an offline environment which basic services installed like Spring Cloud Services (SCS), MySQL, Redis databases and RabbitMQ broker. If you want to run it locally with SCS you need more than 6GB RAM free.

As Spring Cloud Services, Circuit Breaker (Hystrix), Service Registry (Eureka) and standard Spring Configuration Server are available based on the git configuration.

![Image title](https://dzone.com/storage/temp/5439067-scs.png)

That's all I wanted to say about the theory. Let's move on to practice. On the Pivotal website, we have detailed materials on how to set up, create, and deploy a simple microservice based on Spring Cloud solutions. In this article, I will try to present the essence collected from these descriptions based on one of my standard examples from the previous posts. As always, the sample source code is available on GitHub. If you are interested in a detailed description of the sample application, microservices, and Spring Cloud, read my previous articles: [Creating microservice using Spring Cloud, Eureka and Zuul](https://piotrminkowski.wordpress.com/2017/02/05/part-1-creating-microservice-using-spring-cloud-eureka-and-zuul/) and [Creating Microservices: Circuit Breaker, Fallback and Load Balancing with Spring Cloud](https://dzone.com/articles/circuit-breaker-fallback-and-load-balancing-with-n).

If you have a lot of free RAM, you can install PCF Dev on your local workstation. You need to have Virtual Box installed. Then, download and install Cloud Foundry Command Line Interface (CF CLI) and PCF Dev. All this is described [here](https://pivotal.io/platform/pcf-tutorials/getting-started-with-pivotal-cloud-foundry-dev). Finally, you can run the command below and take a small break for coffee. The virtual machine needs to be downloaded and started.

For those who do not have RAM enough (like me), there is the Pivotal Web Services platform. It is available [here](https://login.run.pivotal.io/). Before using it, you have to register on Pivotal's site. The rest of the article is identical for both options.

In comparison to previous examples of Spring Cloud-based microservices, we need to make some changes. There is one additional dependency inside every microservice's `pom.xml`.

We also use the Maven Cloud Foundry plugin `cf-maven-plugin` for application deployment on the Pivotal platform. Here is a sample for `account-service`. We run two instances of that microservice with max memory 512MB. Our application name is piomin-account-service.
    
    
            <target>http://api.run.pivotal.io</target>

Don't forget to add credentials configuration into the Maven `settings.xml` file.
    
    
        <id>cloud-foundry-credentials</id>

Now, when building a sample application, we append `cf:push` command.

Here is a circuit breaker implementation inside `customer-service`.

There is a randomly generated delay on the account's service side, so 25% of circuit breaker calls should be activated.
    
    
      logger.info(String.format("Account.findByCustomer(%s)", customerId));
    
    
      return accounts.stream().filter(it -> it.getCustomerId().intValue() == customerId.intValue())

After successfully deploying the application using the Maven `cf:push` command, we can go to the Pivotal Web Services console available [here](https://console.run.pivotal.io/) . Here are our two deployed services: two instances of piomin-account-service, and one instance of piomin-customer-service.

![Image title](https://dzone.com/storage/temp/5465478-pivotal-1.png)

> _I have also activated Circuit Breaker and Service Registry from the Marketplace._

![Image title](https://dzone.com/storage/temp/5465479-pivotal-2.png)

Every application needs to be bound to a service. To enable it, select service, then expand _Bound Apps_ overlap and select the checkbox next to each service name.

![Image title](https://dzone.com/storage/temp/5465483-pivotal-4.png)

After this step, the application needs to be restarted. It also can be done using the web dashboard inside each service.

![Image title](https://dzone.com/storage/temp/5465484-pivotal-5.png)

Finally, all services are registered in Eureka and we can perform some tests using customer endpoint `https://piomin-customer-service.cfapps.io/customers/{id}` .

![Image title](https://dzone.com/storage/temp/5465485-pivotal-3.png)

With the Pivotal solution, we can easily deploy, scale, and monitor our microservices. Deployment and scaling can be done using Maven plugin or via web dashboard. There are also available some services prepared especially for microservices needs like service registry, circuit breaker and configuration server. Pivotal is the competition for such solutions like Kubernetes which based on Docker containerization (more about this tools [here](https://piotrminkowski.wordpress.com/2017/03/31/microservices-with-kubernetes-and-docker/)). Pivotal is useful if you are creating a microservices based on Spring Boot and Spring Cloud frameworks.

The Integration Zone is brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Use CA Live API Creator to quickly [create complete application backends, with secure APIs and robust application logic](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D), in an easy to use interface.

Topics:

pivotal ,microservices ,spring cloud ,hystrix ,cloud foundry ,integration ,tutorial
