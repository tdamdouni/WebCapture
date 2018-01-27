# Bootstrapping Microservices - Getting Your Microservice Architecture Ready

_Captured: 2018-01-18 at 19:30 from [dzone.com](https://dzone.com/articles/bootstrapping-microservices-your-microservice-arch?edition=357091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-18)_

### Check out this open source project to get a start on your microservices architecture, learn about the tools you need to connect your microservices, and more.

The computing world has seen increasing attention on microservices software architecture in order to enhance software scalability and efficiency. Microservices brings many benefits for tech organizations. However, it is also clear that despite the benefits of modularization and containerization, many organizations continue to struggle with microservices.

A microservices-based application comprises numerous tiny independent services that are integrated with each other to offer the desired software functionalities. While these tiny individual services may be simple, there is a significant complexity that arises from their interaction in an effort to orchestrate the desired business operations. While in practice, the idea of microservices works excellently, in reality, the complexity rises considerably.

Despite all this complexity added to this new approach exists, the community has already worked in minimizing most of the challenges found in this architecture, today we have available many frameworks, tools and patterns ready to be easily integrated into your microservice project.

We know already the complexity added to microservices architecture and we also know that the community has already created many things to minimize it. Now you need to know about my open source project, which helps you to start with microservices and addressing many common challenges using the solutions built by the open source community.

## **Bootstrapping a Microservice Project**

The idea of this project is to provide you a bootstrap for your next microservice architecture using Java. we are addressing some of the main challenges that everyone faces when starting with microservices. This project will definitely help you get an understanding of the microservices world and save you a lot of time in setting up your initial microservice architecture.

Basically, if you are interested in microservices and either study or want to implement a microservices approach at your work, this project is for you!

Some challenges to which we are already providing a solution in this project:

  * Log management

  * Service discovery

  * Fault tolerance

  * Synchronous and asynchronous communication

  * API gateway

  * Centralized Configuration

  * Distributed authentication

  * Distributed transactions

  * Distributed Event

  * Applications management

  * Infrastructure management

  * Continuous deployment

In this blog post, I will walk through some concepts and technologies that we have placed in our bootstrap microservice project. I'm not planning to go deep in the concepts and tools, we have a lot of posts about those out there - the intention here is to present an application example containing the patterns, tools, and technologies used to develop microservices.

We are going to work with a To-Do application, which will be composed of six services (Reminder, User, Mailer, OAuth Server, API Gateway, and Web app client) and seven tools (Service discovery server, load balance server, configuration server, log management, application management, Event broker, and Continuous deployment server).

Some patterns, tools, and technologies that you will see in this system:

Spring Boot, Spring Data, Spring Cloud Eureka, Load Balancing with Ribbon, Declarative REST Clients with Feign, Software Circuit Breakers with Hystrix, Monitoring using Hystrix dashboard, Administrating using Spring admin, Log management with Elasticsearch, Logstash and Kibana (ELK), Server load balancing with Nginx, Infrastructure management with Docker-compose, JMX application monitoring, Security with Spring Security OAuth, Oauth2 with JWT, Aspect Oriented Programing, Distributed events with Kafka, Spring Stream, Maven Multimodule project, Event Sourcing, CQRS, REST, Web Sockets, Continuous deployment with Jenkins, and everything developed using Java 8. This first post is going to provide an overview of the whole project, and in the coming posts, I will explain more deeply about what and how we are using the components in each microservice.

![Image title](https://dzone.com/storage/temp/7832616-microservices-arch.jpg)

In the image above, you can see how our system interacts, along with all microservices. The user will access a web application written using Angular 2, it will connect to an OAuth Authorization Server, which will be a central point where users and authorities can be assigned. This server will return a JSON Web Token containing info about the client with its authorities and the grated scope. After the user being authenticated and with the token, the web application will be able to talk to the API gateway, it will take the JWT, verify if it's coming from the Authorization Server, then make calls to the microservices and build the response.

The User service is being used by the OAuth server to get the user's authentication details, and is also being used by the API gateway to get the user's information.

The Remainder Service is where the To-Do functionalities are placed. The Remainder Service has a scheduled job to check for reminders and notify the user by email. The emails are sent by the Mailer Service, which is triggered by the Reminder service by an event using Kafka.

The System Integration Test is a Java application responsible for reaching the Reminder service's endpoints.

I have recorded a few videos presenting the project, and how to test the whole project on your computer and deploy it on AWS. [Check it out](https://medium.com/@alexsandrosouza/bootstrapping-a-microservices-screencast-7212aa3912cc).

## **Connecting Microservices**

In microservices architecture, we have to deal with many microservices running in different IPs and ports; therefore, we need to find a way of managing each address without hard coding, and that is where Netflix Eureka comes to rescue. It is a client-side service discovery that allows services to find and communicate with each other automatically. We are using Spring Cloud Eureka in our system and you will need to have a look at how it works to understand how our REST services are communicating between different microservices. Once Eureka cares about where the services are running, we can add instances and apply load balancing to distribute the incoming application traffic between our microservices.

In our system, we are using Netflix Ribbon as a client-side load balancer that enables us to achieve fault tolerance and increase the reliability and availability through redundancy. We are using Netflix Foreign to write a declarative REST client and integrate Ribbon and Eureka to provide a load balance HTTP client.

Our system has some dependencies and we are trying to isolate our application from dependency failure using Netflix Hystrix Circuit Breaker, which helps stop cascading failures and allows us to fail fast and make a rapid recovery, or add fallbacks. Hystrix maintains a thread-pool for each dependency and rejects requests (instead of queuing requests) if the thread-pool becomes exhausted. It provides circuit-breaker functionality that can stop all requests for a dependency. You can also implement fallback logic when a request fails, is rejected, or times out.

## **Authentication**

Security is very important when we are developing any system and with microservices architecture is not different. The question "How can I maintain security in my microservices?" comes up immediately, and the first answer is OAuth2! And definitely, OAuth2 is a very good solution; it is a well-known authorization technology, it is widely used for Google, Facebook, and GitHub for their APIs.

It's impossible to talk about security and not mention Spring Security, and in our project, we are using it along with OAuth2.

Spring Security and OAuth2 are obvious choices when talking about secure distributed systems, however, we are adding one more element to our security concern: JWT (JSON Web Token). Using only OAuth, we would need to have an OAuth Authorization Server to authenticate the user and generate the token, and also an endpoint for the Resource servers to ask if the token is valid and which permissions it grants, requiring twice as many requests to the Authorization Server than we really need. JWT provides a simple way of transmitting the permissions and user data in the access token, and once all the data is already in the token string, the resource servers don't need to ask for token checks. All the information is serialized into JSON first, encoded with base64, and finally signed with a private RSA key. It assumes that all resource servers will have a public key to check if the token was signed for the proper private key and deserialize the token to get the information.

You can have a look at the OAuth2 Authorization Server (OAuth-server) and the Resource Server (API Gateway) implementations to see what the code looks like. The implementation was done mainly following [this ](http://stytex.de/blog/2016/02/01/spring-cloud-security-with-oauth2/)blog post.

## **REST**

In our system, we have two interaction styles: synchronous and asynchronous. For the async style, we are using distributed events with Kafka, following the model publish/subscribe, and for sync, we have the REST style supporting JSON and XML.

There are four levels of maturity of RESTful services, starting at level 0, as described by Martin Fowler, and our services are on level 2 because I decided not implement the Hypermedia Controls using the HATEOAS design pattern, for simplicity.

Because we are using Spring Cloud, we have some scalability patterns out of the box, which are placed in our HTTP connections and are worth mentioning: Circuit breaker, Bulkheads, Load Balancing, Connection pooling, timeouts, and retry.

## **Distributed Events**

As mentioned above, our communication between the Reminder service and Mailer service is done asynchronously using Kafka to distribute our events across the other microservices. In our project, we are managing the Distributed Events though an event-driven streaming pipeline, made possible by Spring Stream, where the framework hides the boilerplate and infrastructure concerns and we can focus on the core business premise and develop standalone data-centric applications. The next step is orchestrating our stream processing pipeline using Spring Cloud Data Flow and build a high throughput stream processing and event-driven use-case.

## **Event Sourcing and CQRS**

Monolithic applications typically have a single relational database and we can use ACID transactions. As a result, our application can simply begin a transaction, change multiple rows, commit the transaction if everything goes right, and rollback if something goes wrong. Unfortunately, dealing with data access in the microservice architecture is much more complex due to the data being distributed in different databases, and implementing business transactions across multiple services is a big challenge.

In our "To-Do" project, we are using events to deal with a business transaction that spans multiple services, and you can look at the implementation of Event Sourcing with CQRS applied in the Mailer service. You will see how to separate Reads and Writes that enable us to scale each part easily. We are using a relational database as an event store, then distributing the events using Kafka. We will need to make these two actions Atomic, avoid storing the event, and not publish in an eventual JVM crash. I'm not using Kafka as the event store because is simpler to construct the aggregates from a relational database, and we are trying to make things easy here.

## **Log Management**

Having well-planned logging, monitoring, and analytics strategies is the key to this type of project. They should be implemented from the beginning of the project to increase development and testing velocity, as well as provide quick troubleshooting.

Such an important part of the microservice world could not be left out of our project, and here we have addressed it using the ELK solution, where we have set up an agent in every container responsible for sending the logs to a log management server, where it will store all logs from our microservice components and provide an amazing user interface to search and build reports based on the sent data.

## **Application Management**

To manage a system consisting of multiple microservices, you need to collect all relevant information in one centralized place. This applies to the logs and details about the status of all application instances, which are running right now in our microservice cluster.

We are using Spring Boot Admin to help us to manage our Java apps. It is a simple solution created to manage and monitor Spring Boot applications, and gets the data from Actuator endpoints and provides insights about all the registered applications in a single dashboard.

## **Infrastructure Management**

Microservices are well matched to container technologies and often work in conjunction. Containers are often the preferred choice because they are self-contained and rapidly provisioned or cloned. In our project, all component parts are dynamically managed using Docker, which means you don't need to worry about setting up your local environment, the only thing you need is to have Docker installed.

Having separate services, you will have to manage the infrastructure for each service. Infrastructure as Code (IaC) was born as a solution to this challenge. Everything that our application needs will be described in a file (Dockerfile). Along with docker-compose file, we orchestrate multi-containers application and the entire service configuration will be versioned, making the process of building and deploying the whole project easy.

## **Config Management**

In a traditional application, properties files are tied to the codebase or statically packaged, so any changes in the properties file mean rebuilding and redeploying the application, which is a violation of the microservices principle. With microservices, we create a central config server where all configurable parameters of microservices are written, version controlled, and managed in a centralized configuration management. The benefit of a central config server is that if we change a property for a microservice, it can reflect that on the fly without redeploying the microservice.

In our bootstrap application, we are already addressing centralized configuration management with the Spring Config Server. By default, our config server is not using Git, we are placing our properties in the local file structure, but in production environments, you should switch to a Git profile and set up your Git repository address and be able to change your configuration properties easily.

## **Automated Deployment**

Every microservice should have the ability to automatically and reliably deploy any version to any environment. Keeping deployment fully automated and simple makes it easy to confidently deploy small changes often.

In our architecture, we have a continuous integration server using Jenkins, which makes possible to deploy our entire system automatically into the AWS container system with just a few steps. We are using the concept of Pipeline as Code, where we have described in a file (Jenkinsfile) a set of features that allow Jenkins users to define pipelined job processes with code, stored and versioned in a source repository.

Our automated deployment of our services includes pulling the source code, building the Java code, packaging the jar, building a Docker image, deploying the Docker image in a Docker repository, and deploying the container on the AWS container service. To execute all those steps, we need to have an environment with a lot of software and many tools installed. For that, we decided to create a[ separate project](https://github.com/apssouza22/build-deploy) to maintain a Docker image with everything we need to build and deploy our architecture on AWS.

## **Next Steps**

As you can see, we already have a lot of things in this project, but there are still many challenges that are not addressed here yet. However, this is a project in development and we are planning to add more stuff to it, so stay tuned on our [GitHub ](http://github.com/apssouza22/java-microservice)repository to see more fun things.
