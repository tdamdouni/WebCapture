# How to Be a Master in Software Development

_Captured: 2018-02-23 at 22:41 from [dzone.com](https://dzone.com/articles/how-to-be-a-master-in-software-development?edition=364094&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-23)_

**The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=275424&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dfooter). Learn how DevOps and SAFe® can be used either separately or in unison as a way to make your organization more efficient, more effective, and more successful in our [SAFe® vs DevOps eBook](https://dzone.com/go?i=275424&u=http%3A%2F%2Fpages.aspeinc.com%2FSAFe-vs-DevOps.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Dsafe_vs_devops%26utm_content%3Debook).**

A software developer's job description goes well beyond mere computer programming. Many roles require that developers embrace taking part in the full lifecycle of software development and strive to improve the overall product by researching alternative ways and technologies to achieve the overall goal.

Being a master in software development is about knowing the full software development processes and having considerable expertise in the key parts of the process.

It requires an understanding of the nuances of design patterns and algorithms while following the best practices of software development, and an ability to be creative and think outside the box to offer logical solutions for programming problems.

Recently I wrote an article about the [expert-specialist in the software development industry](https://dzone.com/articles/expert-generalist-software-engineer) and the characteristics of this type of professional, which is important in order to become a master in developing software.

Achieving mastery in the IT industry requires skills in server-side development, client-side development, DevOps, cloud computing, web design, distributed system, database, programming principles, code management, infrastructure management, scalability, security and much more.

While you won't reasonably be able to master all of the above, you should try to understand most of them on a superficial level and deep-dive into several of these points.

Below is a list of essential points that experienced developers often lack but which a master engineer should be familiar with when applying for a lead position.

### **Programming Principles**

Coding principles help to ensure good coding practice and concrete product development. Some of the most important Coding Principles to know are:

DRY (Don't Repeat Yourself), SOLID, Object Catallistic, TDD, and Defensive Programming.

### **Design Patterns**

Design patterning is a general, reusable solution to a commonly occurring problem. It is important to know some common DPs, and most importantly, to be able to identify the right pattern to a given problem. Some design patterns are a must have for a good developer, such as MVC, Singleton, DAO, Facade, Proxy, Adapter, Strategy and Abstract Factory.

## **Server-side Development**

In complex systems, there are all kinds of logic that happen in the background and as a back-end developer, we face many challenges in processing business logic in an application. Any developer can write code, but the only experienced developer can write quality code with performance, scalability and reliability. The process of developing good software involves a lot of science and it is very important to know how to deal with:

#### **Caching**

you must know various mechanisms of caching data (file, database, memory, reverse proxy, HTTP...)

#### **Memory Management**

Java has automatic memory management with a nice Garbage Collector that cleans up unused objects and frees up some memory. However, a master Java programmer needs to have a good understanding of how memory actually works, as this gives the advantage of writing high-performance and optimized applications. It is essential to know about:

Stack, Heap, Strong Reference, Weak Reference, Soft Reference, Escape reference, how Strings are referenced, Garbage Collection Process, Metaspace and Garbage collector types.

#### **Exception Handling**

This is a very important and large topic, and I will write a dedicated post about it soon, but for now, some good practices when handling exceptions are:

  * Make your software reliable following the 'fail first' principle;

  * Do not catch exceptions you can not recover from;

  * Do not log your exception and then rethrow it;

  * Choose the right layer to handle the exceptions (e.g your DAO does not know the right decision for a database failure, but your service might know it);

  * Prefer unchecked exception if you cannot recover from it.

#### **IO Operation**

Being aware of the cost of IO operation and the possible unpredictable results.

#### **Asynchronous Programming**

Asynchronous programming in Java is achieved using Threads. It is a fundamental part of the Java platform. Using concurrency effectively is essential for building high-performance applications.

Words such as thread pools, data race, deadlocks, countdown latches, producer-consumer, atomicity, immutable objects, Futures, and Semaphore should not be something new for a master Java developer.

#### **Batch Processing**

Writing a batch job is very common and usually does important tasks. There are some basic rules to be aware of:

  * Every task should be divided by input, processor and output;

  * Always poll data input in batches;

  * Processor should be thread-safe;

  * Output should be atomic;

  * Store job results;

  * Consider using EIP patterns.

### **Distributed Computing**

In the modern world, distributed computing refers to the use of distributed systems to solve computational problems, however, distributed systems are different from conventional non-distributed systems and they add a lot of complexity to systems. Having experience in working in a distributed system will make a difference when a system starts growing and consuming more resources. Microservice software architecture is a good example of distributed computing and all the benefits and trade-offs of a distributed architecture. I am responsible for an open source project which provides a bootstrap to help people start a professional microservice architecture in a few minutes. I have written about the whole architecture [here ](https://dzone.com/articles/bootstrapping-microservices-your-microservice-arch)and also I recorded some videos showing how to use it [here](https://www.youtube.com/user/apssouza1988/channel).

Definitely, microservices is something that is a required skill nowadays and it will require a lot of experience with distributed systems. It is important to have a good understanding of fault tolerance, availability vs. consistency, distributed transactions, distributed events, synchronous and asynchronous communication, distributed authentication, decentralized applications, applications of consensus, and more.

### **Database**

Understand exactly what happens when data is sought from the database and all costs involved, connection handshake, data transmission, etc. It's also very important to have a clear understanding of atomic transactions and how to make sure your data is consistent.

Database is for managing data and this by itself is a tough task; don't even think about adding business logic into your database. In large systems, database have already many challenges with security, scalability, capacity, and availability. Database management is a desired skill from a master software developer and at some point in time, you will be challenged to think about encryption, replication, sharding, Big Data and more. Knowing how a database works and how to optimize it along with the cost of each operation (e.g. reading is more memory intensive, writing more CPU) will help design efficiently the data management of your system.

### **DevOps**

A master developer needs to be able to promote the DevOps cultural philosophies and practices and advocate automation and monitoring at all steps in order to increase the organization's ability to deliver applications and services at high quality and velocity. Deploying code or provisioning infrastructure must be automated, flexible, and monitored. A great developer should know well the development cycle from integration, testing, releasing to deployment and infrastructure management. In order to achieve it, you will need to know about cloud computing, Linux, networking, containers, artifacts management, and more.

### **Code Management**

Given the importance of code, it is only natural that only master developer is able to care of the code lifecycle and promoting engineering best practice. For that, he will need to know well a source code management system and have clear understanding of branching strategy, versioning, distributed revision control system, code quality guarantee tools, code communication, dependency management, configuration management, and much more.

### **Security**

Web security is very hard to achieve and depends on a lot of external parameters; however, we need to follow the best practices and general guidelines for building secure web applications. A master engineer needs to have a good understanding of information security, not only how to avoid building insecure and vulnerable systems, but also how to protect customers privacy.I have written about privacy by design [here](https://dzone.com/articles/gdprdesigning-privacy-and-data-protection).

A great developer needs to be able to create a guideline to handle beyond the top 10 web application security risks. In the web application, we have many more security threats that need engineering action, including:

  * Uploaded file check; 

  * Brute force protection; 

  * Session expiration handler; 

  * Session origin validation; 

  * Secure communication over the internet;

  * Secure Cookie access; 

  * Credentials handling.

### **Front-end Development**

A front-end development is a very important part of a software and you will not be a master software engineer if you don't know how programming and user-experience meet. So far I have avoided naming technologies, but in the front-end world, Javascript and CSS are a must-have for a software engineer. It's not easy to achieve mastery in both but is very important to understand how they work and how both, along with HTML connect, enable us to provide a great user-experience.

To lead a front-end team, you will need to know more than how to build a beautiful layout, front-end development goes beyond, and you will need to know

  * What is possible to build using browsers as engine; 

  * How to develop responsive websites; how to improve website performance; 

  * How to develop a single page application; 

  * How to build a modern and efficient development environment;

  * Be familiar with the new HTML5 APIs.

Web development is huge area and in order to master in this matter, the developer will need to be self-motivated, proactive in learning new technologies and wear many hats during your career. Keep challenging yourself and you will get better at problem-solving, which is the essence of programming. Knowledge is important, critical in some cases, but in a field that changes so quickly, how you go about get that knowledge is more important than what you know at any given time.

**Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F). **

Opinions expressed by DZone contributors are their own.
