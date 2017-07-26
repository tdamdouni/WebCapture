# Serverless Computing With Spring Cloud and Asynchronous Microservices

_Captured: 2017-05-25 at 10:18 from [dzone.com](https://dzone.com/articles/serverless-computing-with-spring-cloud-and-asynchronous-microservices-us?edition=300092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-24)_

In this article, my endeavor is to walk you through an example of running asynchronous microservices using Spring Cloud without dedicated servers (serverless) for each task (read microservices).

The complete code is available on my [GitHub repository](https://github.com/x14gauravg/serverless-springcloud). Let me begin by clarifying a few terms, then build on those terms to present the example.

## **What Is Serverless Computing?**

Serverless does not mean that your services would run without a server. You definitely need a compute layer for your services to run. Serverless simply means that you can run your code without provisioning or managing servers. AWS Lambda is one such example of a serverless compute service. AWS Lambda will execute your code only when needed, scale automatically, and you do not dedicate compute power when your code is not running, which means less cost.

### **Serverless Framework (Key Pieces)**

There are, broadly, three pieces to any serverless program:

![Image title](https://dzone.com/storage/temp/5365892-fig1.png)

  * **Event/Trigger**: An event could be a file upload, a database update, an HTTP request, or anything else that you can think of upon which you would want your function/service to act. For example, you could want to create multiple formats of a video file once the user uploads the file in a directory
  * **Task/Function**: After the event has happened, some work needs to happen. The task is where your write the program logic to do that work.
  * **Task Launch Platform**: The backbone. Once the event is generated, the platform captures the event and launches a task associated with that event. AWS Lambda is an example of one such platform, which manages such plumbing for you. Similarly, Spring Cloud has also come up with structures in their classic Spring annotation formats to run such programs.

In the example below, I will walk you through how to build serverless, asynchronous tasks using Spring Cloud.

## **The Example**

In our example, a user POSTs a web request to run either a blue task or red task. These basic tasks print out arguments, which the user sends out as part of POST request body.

The example is drawn in the figure below. The picture also maps various components to the serverless framework that I described above.

![Image title](https://dzone.com/storage/temp/5365906-fig2.png)

> _Let us look at individual pieces and associated Spring Cloud plumbing code._

### 1\. Event Trigger via HTTP POST Request

The user sends an HTTP POST request with some dummy text in the request body. We could have used any other event trigger as well, such as a file upload, database update etc. I chose an HTTP trigger for ease of demonstration. The URL looks like this: http://localhost:8080/tasks/{color}. The color path variable could be either "red" or "blue" to signify whether to run redtask or bluetask.

### 2\. RestController

The user request is trapped by a standard Spring RestController. We annotate our class with the standard @RestController to enable the behavior:

### 3\. Task Processor

This bean has the sole purpose of putting task launch requests into the queue. We use a standard @Component annotation on top of the class. In order to bind the class to the queue, I have used the @EnableBinding annotation. Along with this, you would also need to specify the RabbitMQ properties. The queue name is where the messages get published:

![Image title](https://dzone.com/storage/temp/5365982-fig3.png)

### 4\. Task Launch Request

Tasks are stored in a Maven repository. Furthermore, the Task Launch requires the Maven URL as an input. The maven URL format reads as maven://[groupid]:[artifactid]:jar:[version]. Groupid, artifactid, and version in the URL are the values that we specify in the pom.xml of our Task.

The other argument to the Task Launch request is the input that we want to give to the task. The code below is abbreviated:

### 5\. Task Launcher

Task Launcher consumes the messages published on the queue. The launcher then uses the Maven repository and Maven URL available in the message to launch the request. The @EnableTaskLauncher annotation makes a Boot app our Task Launcher. In addition, we have to specify RabbitMQ properties in the application.properties file similar to what I described above.

### 6\. Spring Cloud Task

A Spring Cloud Task is a short-lived, asynchronous microservice where the real action happens. In our example, these are the blue/red tasks. These tasks are Spring Boot apps. Being a Spring Boot app, it also has access to various beans in the Spring container, and it could also subscribe to various lifecycle events.

Spring provides the @EnableTask annotation for classifying Boot apps as a Cloud Task. The business logic would be written in Runner, and you could use multiple runners. The task would complete once all runners are completed.

After we are done with task logic, just run `maven -install` to put the task in the repository.

### 7\. Execution History

Each task execution generates task execution history. This history is saved in a database, which is configured in application.properties for the task. Multiple tables are generated by Spring Cloud Task. The key tables to look at are task_execution and task_execution_params. These tables carry the task status and params submitted for task execution.

This concludes the walkthrough of the example.

In a typical setup, both red and blue tasks would have been deployed as services in dedicated containers. However, Spring Cloud enables us to run these tasks without dedicated servers. Services such as AWS Lambda hide the nuts and bolts of such a platform. Hopefully, this example has given you insights on serverless mechanics and how to build such a platform using Spring Cloud.

Happy Coding!
