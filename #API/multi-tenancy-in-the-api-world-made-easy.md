# Multi-Tenancy in the API World Made Easy

_Captured: 2018-02-09 at 20:20 from [dzone.com](https://dzone.com/articles/multi-tenancy-in-the-api-world-made-easy?edition=355134&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202018-02-08)_

**_Multi-tenancy_** is a fundamental architecture that can be used to share IT resources cost-efficiently and securely in cloud environments in which a single instance of software runs on a server and serves multiple tenants.

It's been years since we first heard about it; it came out again riding the wave of **cloud computing**, so we can assume that multi-tenancy is a consolidated architecture -- and the benefits in terms of maintainability and costs are well-known.

_**APIs**_ are the _backbone_ of a distributed cloud architecture, so building a multi-tenant API is the natural aftermath of this scenario.

In this article, I will show you how to build a simple **multi-tenant RESTful API** using Java in a quick and easy way, dramatically reducing the configuration code required by the most frequently adopted solutions.

## A Multi-Tenant Implementation May Be Cumbersome

The first impression, looking for multi-tenancy implementation strategies, is that there's no specific standard and no well-defined best practices.

One of the most common solutions is relying on [Hibernate](http://hibernate.org/) to implement multi-tenancy behavior at the DataSource level. Hibernate requires two interfaces to be implemented: `CurrentTenantIdentifierResolver` to resolve what the application considers the current tenant identifier and `MultiTenantConnectionProvider` to obtain connections in a tenant-specific manner. This could be tricky and not-so-trivial, possibly leading to more boilerplate code.

And finally, last but not least, this solution is only suitable for a **JPA implementation**, since Hibernate is directly used as tenant resolver and connection router.

Furthermore, the [Spring Framework](https://spring.io/) is often used in conjunction with Hibernate to build a multi-tenant API or application. One of the most useful aspects of the core Spring architecture is the availability of **scopes**: In a multi-tenant scenario, sooner or later, you'll surely miss a tenant scope, which is not available out of the box. Creating a custom scope in Spring is not trivial. It requires a deep knowledge of the Spring architecture and a lot of code to implement and register the new scope.

You can check the **Spring+Hibernate** version of the example shown in the second part of this article here: <https://github.com/fparoni/spring-boot-hibernate-multitenant-jaxrs-api>.

## The Easy Way

Now let's streamline the process in order to highly simplify the multi-tenancy setup and to cut down the required configuration effort, getting rid of all the boilerplate code.

We will use the [Holon platform](https://holon-platform.com/) to achieve this goal, relying on the platform's native multi-tenant support. I'll show you a working example of a simple **RESTful API** using the following Holon platform's components and configuration facilities:

  1. The `**TenantResolver**` interface to provide the current tenant identifier.
  2. A **tenant Spring scope** provided out of the box, automatically configurated and registered when using Spring Boot.

The complete example is available on GitHub: <https://github.com/holon-platform/spring-boot-jaxrs-multitenant-api-example>.

Our RESTful API implements the **CRUD** operations to manage a simple _Product_, providing methods to create, update, delete, and query the product data.

The multi-tenancy architecture of this example is organized per _schema_: each tenant is bound to a **separate database schema** and will access data through a different Java `DataSource`.

![](https://holon-platform.com/contrib/uploads/mt_architecture.jpg)

Each time an API request is performed, we need to know the caller's **tenant identifier** to correctly route the persistence operations to the right database schema.

The three most common ways to provide the tenant identifier are:

  1. Providing the tenant identifier as a **URL part**, for example using a query parameter
  2. Using a custom **HTTP request header**

We will use the second option through a custom **HTTP header** called **'X-TENANT-ID'**.

An example to use JWTs to provide the tenant identifier is available in the [jwt branch](https://github.com/holon-platform/spring-boot-jaxrs-multitenant-api-example/tree/jwt) of the GitHub example repository.

Besides the Holon platform components listed above, our example will use:

  1. **Spring Boot** for application auto-configuration and to create a runnable JAR with an embedded servlet container.
  2. The **H2** in-memory database for data persistence.
  3. **JSON** as data exchange format.

The **Holon Datastore API** will be used to access data in a technology-independent way (using JDBC in this example is only a matter of configuration) and the **Holon _Property_ model** to define the _product_ data model. Check the [Holon reference documentation](https://docs.holon-platform.com/current/reference/holon-core.html#Property) for detailed information.

The result will be a fully working example made of just three Java classes. Now, let's build our example step by step.

### Step 1: Project Configuration

First of all, we will use **Maven** for project configuration and dependency management.

We'll use the **Holon Platform BOM** (Bill of Materials) to easily obtain the dependencies we need.
    
    
       <holon.platform.version>5.0.6</holon.platform.version>
    
    
             <version>${holon.platform.version}</version>

The **Holon JDBC Datastore Spring Boot starter** is used to automatically configure the data access layer:

Likewise, we declare the **Holon JAX-RS Spring Boot starter** dependency to use and auto-configure [Jersey](https://jersey.github.io/) as our JAX-RS implementation.

At last, the H2 database dependency:

To configure our Spring application, we will use an **_application.yml_** configuration file.

We simulate that two tenants are available -- the first bound to a schema named **_tenant1_** and the second associated to a schema named **_tenant2_**. So we need two DataSource instances, one for each schema.

Auto-configuring more than one DataSource with the default Spring Boot DataSource auto-configuration is not possible without writing additional code. For this reason, we'll rely on the **Holon platform DataSource auto-configuration facilities** to define the two tenant DataSources through a _holon.datasource_ configuration property structure like this:

By default, for each auto-configured DataSource, a **Holon JDBC Datastore** is created, too. Each DataSource/Datastore pair will be available as a Spring bean and qualified with the name specified through the _holon.datasource.*_ properties. For example, the DataSource bound to the first tenant can be injected in a Spring component using the `@Qualifier("tenant1")` annotation.

To be up and running at startup, we will use a couple of _.sql_ files to create a sample table named 'product' and one row for each tenant.

## Step 2: Writing the Code

As I said before, we need just three Java classes.

### 1\. Application Definition and Configuration

First of all, we create the `Application` class, which acts as the Spring Boot application entrypoint and as the main Spring configuration class:

We have configured two Spring beans:

  * A `**TenantResolver**` implemetation to provide the current tenant identifier and to enable the Holon platform **tenant scope**. In this example, we want to use a custom HTTP header named "X-TENANT-ID" to obtain the tenant identifier from the caller. We need the current `HttpServletRequest` to obtain the header value, so we declare the TenantResolver as _request-scoped_ and rely on Spring to obtain a reference to the current request.
  * A tenant-scoped `**Datastore**` is correctly retrieved by Spring through the tenant identifier which acts as bean qualifier. The two Datastore instances have already been configured by the Holon Platform Spring Boot autoconfiguration facilities, using the two DataSources declared through the _holon.datasource.*_ configuration properties. The current tenant-related Datastore is retrieved using the bean qualifier which matches with the current tenant id, provided by the `TenantResolver` interface.

### 2\. The Data Model

The `Product` interface represents our data model:

The _Holon platform Property model_ is used to define the product data model. Deepening this topic is out of the scope of this article, so check the [official Holon documentation](https://docs.holon-platform.com/current/reference/holon-core.html#Property) for further details.

### 3\. The API Endpoint

The `ProductEndpoint` class represents the JAX-RS resource that will provide the API CRUD, using JSON as data exchange format. The class is annotated with `@Component` to make it available as a Spring component, and we rely on the **Holon platform Jersey auto-configuration facilities** to automatically register the endpoint in the JAX-RS application:

Note that we injected the Datastore instance to perform data access operations: Thanks to **tenant scope**, with which the Datastore bean is declared, we'll obtain the right Datastore instance according to the current tenant identifier.

## Run the Application

The _spring-boot-maven-plugin_ will create a runnable JAR to have our application up and running using our JRE. We can run an application using this Maven command:

The application is running under Tomcat, listening to port 8080. We can test our endpoint using a [Postman](https://www.getpostman.com/) application and making GET or POST request to the path we've defined before. Let's test the_ /products_ operation using both tenants. Setting the **X-TENANT-ID header** to _tenant1_ will produce the following result:

![](https://holon-platform.com/contrib/uploads/tenant_1.jpg)

Using _tenant2_ as the X-TENANT-ID header value, the result is:

![](https://holon-platform.com/contrib/uploads/tenant_2.jpg)

## Summary

We've seen how to set up a multi-tenant API quickly, highly reducing the configuration effort and boilerplate code that is often required for this kind of task. The multi-tenant architecture that we've used in our simple API implementation can, of course, be leveraged for other, more complex, services or applications. The source code of the application can be found at <https://github.com/holon-platform/spring-boot-jaxrs-multitenant-api-example>.
