# Implementing a Bounded Context

_Captured: 2018-02-23 at 22:42 from [dzone.com](https://dzone.com/articles/implementing-a-bounded-context?edition=364094&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-23)_

Containerized Microservices require new monitoring. See why a new APM approach is needed to even [see containerized applications](https://dzone.com/go?i=279427&u=https%3A%2F%2Fwww.instana.com%2Flibrary%2Febook-application-monitoring-in-containerized-world%2F%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dcontainer_apm_ebook%26utm_content%3Deverything_changed).

Arguably one of the most difficult microservices patterns to apply and implement is the bounded context.

The bounded context concept originated in Domain-Driven Design (DDD) circles. It promotes an object-model-first approach to a service, defining a data model that a service is responsible for and is "bound to." In other words, the service owns this data and is responsible for its integrity and mutability. This supports the important Microservices features of independence and decoupling.

It makes sense on paper. Plus, implementing a bounded context for a greenfield implementation is not often difficult, as often a legacy underlying data source might not exist.

But to understand the bounded context pattern and the difficulties that can be found during implementation of this pattern, consider a legacy or traditional application. Often, a legacy application is backed by a single database, and this database is probably supporting multiple applications, or even another system of record applications. A common example is depicted below:

![](https://i1.wp.com/keyholesoftware.com/wp-content/uploads/Bounded-Context-1.png?resize=462%2C219&ssl=1)

In a microservices style of development, an application is made up of independent runtime component services that implement some feature of an application. This is contrasted by one monolithic runtime component.

In order to keep these services independent (i.e. with the ability to be changed and moved in and out of a runtime environment without side effects to other services), the data source backing these services also needs to be independent. This is where the bounded context pattern comes into play.

A microservices application might look like the diagram below:

![](https://i0.wp.com/keyholesoftware.com/wp-content/uploads/Bounded-Context-2.png?resize=465%2C263&ssl=1)

Introducing a database per service typically results in a DBA freak-out. This is understandable, as DBAs are usually attempting to create a single source of truth enterprise data structure, and all of a sudden they think they are going to be saddled with having to support an explosion of database instances. If these enterprise databases were to be NoSQL-based, it might not be so bad; but most of them are relational-based which provides robust data integrity, transactional support, and many ways to slice, dice, and represent data. So, a stressed DBA response is understandable.

The goal of this post is to provide you with some information on how to implement a bounded context in such a way that will ease DBA anxiety.

## You Don't Have to Take DB-Per-Service Literally

Say that you need to enforce a bounded context for your service implementations. Let's also say you have an existing relational enterprise database and a traditional Conway's Law organization with a DBA team. In this scenario, here are some options that can work in lieu of creating a database for each instance.

![](https://i0.wp.com/keyholesoftware.com/wp-content/uploads/Conways-Law.png?resize=398%2C248&ssl=1)

The goal is to require applications to access a persistent data store via a service implementation provided API.

### Table-Based Security

Security access rights are applied on a table basis. Tables in a service's bounded context are granted read/write/delete privileges; otherwise, they cannot access tables in other services. A service user account can be created for each service and privileges applied.

### Schema-Based Security

Each service can have a database schema created and authorized service account roles assigned.

### Pseudo Honor System Security

Using code reviews and or apply some meta-data like JPA annotations to your code for a build system to glean and compare against some kind of manifest that defines tables owned by services and report violations.

### Eventual Consistency and Transactions

Since a Microservice platform is a distributed computing environment, eventual consistency is a behavior that comes along with it. ACID-based transaction in a distributed micros services environment can be difficult. Because, application data source will be spread across services, your application data may have to tolerate being eventually consistent. Trading off ACID for tolerable latency. Many applications are typical: search something, add something, remove something, or maybe a calculation or two. These type of applications can exist in an eventual consistent environment. However, if real-time access or ACID-compliant transactions are required, then service API boundaries might need to honor these transaction boundaries.

### Handling Foreign Keys

Referential integrity is a feature provided by relational databases and should be applied to tables and relationship constraints within the bounded context.

However, consider the following project service object model responsible for managing (i.e CRUD) projects and resources for projects.

![](https://i2.wp.com/keyholesoftware.com/wp-content/uploads/Bounded-Context-3.png?resize=703%2C240&ssl=1)

Notice the Employee Object is marked as not in context. This is because Employee Objects are a part of the Employee Service and its bounded context, so should be introduced to the Project Service. Assuming the object models are mapped to a relational data source, instead of the Project Service having to map an Employee type, it only has to map the employee id attribute. The diagram shows this concept below:

![](https://i1.wp.com/keyholesoftware.com/wp-content/uploads/Bounded-Context-4.png?resize=611%2C237&ssl=1)

The underlying mapped table for the ProjectResource model will have only the employeeId for an employee, and will not materialize an Employee object from the database. In order to obtain or mutate an Employee, you will utilize the employee service API calls.

A bounded context is conceptually enforced in this example by preventing the project service from mapping to the employee data elements. This can be physically enforced by physical database boundaries or the previously mentioned database security mechanisms. However, there are some more mechanisms that have to be introduced to support this isolation. Specifically, when an employee is deleted through the employee service, how are other services made aware of this deletion? Having the Employee Service call out synchronously to other services interested in employee's would be coupling. Asynchronous messaging provides a way to communicate in a decoupled fashion.

Using a durable, resilient messaging system such as ZooKeeper/Kafka (or something equivalent) provides a way to accomplish this. Kafka has a persistent logging mechanism and will replay event messaging history to consumers if they are not available when a message event is raised by a publisher. This supports the independence of a Microservice platform with services moving in and out on an ad-hoc basis.

A generalized messaging and convention can be established in your service implementations. When any service performs a create, read, update, or delete operation (CRUD), then they can raise an event that reflects the primary key, operation, user, and maybe a date/time of the event.

Here's a partial example implementation that performs CRUD on an Employee service and raises an event for consumers:
    
    
      KafkaHelper.produceTopic("employee.delete", employee.getId(), CurrentUser.getId(), Calendar.getInstance());

Consumer services, such as the Project Service, need to know when an employee is deleted, so it can update a its Project's Resources, in other words, the employee assigned to a project no longer exists. The project service can listen for this Kakfa event topic published from the employee service and react accordingly.

Here's an example Kafka Topic handler consumer that provides a code block to delete a project resource when an Employee is deleted. This code will be executed after application startup.

Here's a code block Interface that KafkaConsumer helper uses:
    
    
     public void execute(MessageAndMetadata & lt; byte[], byte[] & gt; mmd);

This method initializes consumers to listen for published topics and associate an executable code block to execute when raised:
    
    
       public void execute(MessageAndMetadata & lt; byte[], byte[] & gt; mmd) {
    
    
        String msg = new String(mmd.message());
    
    
        String id = msg.split(":")[1];

This mechanism allows services to listen for and react to database events such as updating, or adding to events, without services having to directly call services interested in these operations.

An example would be an Audit Service, that can capture and record database operations for audit reports and inquiry, as the diagram shows below.

![](https://i1.wp.com/keyholesoftware.com/wp-content/uploads/Bounded-Context-5.png?resize=813%2C375&ssl=1)

## Conclusion

In a traditional monolithic application, the entire application object model is governed and mapped to a single database. Audit information, foreign key constraints, and cascading CRUD operations are handled by a single database.

However, in a Microservices environment with a bounded context, each Service may or may not be backed by the same, single database. In this scenario, a generalized asynchronous messaging mechanism can provide support for a distributed environment.

## Reference

Martin Fowler on Bounded Context - <http://martinfowler.com/bliki/BoundedContext.html>

Got Cloud? Containers? Microservices? Get better control and performance. [Start your trial ](https://dzone.com/go?i=279428&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana)of Instana APM today.
