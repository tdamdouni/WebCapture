# Building a Web UI for MySQL Databases in Plain Java

_Captured: 2017-04-16 at 10:30 from [dzone.com](https://dzone.com/articles/building-a-web-ui-for-mysql-databases-in-plain-jav-2?edition=290923&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-15)_

_Note: This post has been updated to use Vaadin 8._

This guide walks you through the process of connecting to [MySQL](https://www.mysql.com/) databases from Java web applications using JDBC and Spring Framework. The UI part will be built using [Vaadin](https://vaadin.com) Framework that allows you to build modern single-page web apps with only Java.

When connecting to databases from Java applications you have two main options: Using an ORM, such as JPA, or using low level JDBC. ORM frameworks are a better option if you are developing an application from scratch. The approach shown in this guide suits cases in which you have an existing and probably old database which might not really be compatible with an ORM, such as JPA.

## Prerequisites

This guide assumes you have previously installed MySQL Server, your favorite IDE, and Maven. No previous experience with Spring Framework is required to follow this guide.

## Create a Spring-based Project

The easiest way to create a new Spring-based application is by using [Spring Boot](http://projects.spring.io/spring-boot/) and [Spring Initializr](https://start.spring.io/). Spring Boot simplifies the process of developing Spring applications. Spring Initializr is a web-based tool that allows you to create project skeletons for Spring applications.

To create a new application, go to <http://start.spring.io> and add the Vaadin, MySql, and JDBC dependencies as shown in the following figure:

![Image title](https://vaadin.com/documents/226808/13268303/spring-initializr-vaadin-mysql-jdbc.png/fbb94f48-13ef-4523-9e19-1dd3f6db671f?t=1464867376399)

Click the _Generate Project_ button and extract the generated zip file. You should get a Maven project you can [import into your favorite IDE](https://vaadin.com/blog/-/blogs/the-maven-essentials-for-the-impatient-developer).

## Create a MySQL Database

Connect to the MySQL instance and create a new schema:

Create the following table:

Add some test data, such as the following:

## Create a Customer class

Create the following _[Customer_](https://raw.githubusercontent.com/alejandro-du/mysql-jdbc-vaadin/master/src/main/java/com/example/Customer.java) class to encapsulate the data from the _customers_ table:

## Create a Backend Service Class

Start by configuring the database connection in the _[application.properties_](https://raw.githubusercontent.com/alejandro-du/mysql-jdbc-vaadin/master/src/main/resources/application.properties) file inside the _src/main/resources_ directory:

You may need to change the username and password used to connect to your database.

We will encapsulate the logic to query and modify data in a service class. This service class will use Spring Boot's autoconfiguration capabilities and Spring Framework's _JdbcTemplate_ class to connect to the database and to query and update rows in the _customers_ table.

Create the following _[CustomerService_](https://raw.githubusercontent.com/alejandro-du/mysql-jdbc-vaadin/master/src/main/java/com/example/CustomerService.java) class:

Notice how the _CustomerService_ class is annotated with _@Component_. Spring Framework will automatically create an instance of this class. The term for this kind of instance is a bean. We can inject beans in other beans. Spring Boot itself has defined some beans for us that we can inject into the _CustomerService_ bean. One way of injecting beans is by using the _@Autowired_ annotation. We used this annotation to tell Spring to inject a bean of type _JdbcTemplate_. This is one of the beans Spring Boot has predefined for us.

The _JdbcTemplate_ class simplifies the use of JDBC. For example, the update method of the _JdbcTemplate_ class will execute an update (or delete) statement using Prepared Statements which protects against SQL injection.

The _findAll_ method in the _CustomerService_ uses Java 8 lambda expressions to map the values of the SQL query result with _Customer_ instances.

## Implement the UI

Create a Vaadin UI by implementing the _[VaadinUI_](https://raw.githubusercontent.com/alejandro-du/mysql-jdbc-vaadin/master/src/main/java/com/example/VaadinUI.java) class:

This class creates a UI containing a _Grid_ component to show all the customers in the database and a form to edit customers' first and last names. Notice how the _VaadinUI_ class is annotated with _@SpringUI_. This means we can inject the _CustomerService_ bean in this class and use it to read and update customers.

The most interesting part of this class is how data binding is managed. The _Binder_ class allows us to connect the text fields with the corresponding Java properties in the _Customer_ class.

## Running the Application

Spring Initializr created the _Application_ class with a standard _main_ method defining the entry point of the Java application. When you run the application using this method, Spring Boot configures and runs a Jetty server on port 8080 (all this can be [configured](http://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#howto-embedded-servlet-containers)).

Before running the application you have to build it. You can use the command line to build and run the application:

The following is a screenshot of the application:

![Image title](https://vaadin.com/documents/226808/13268303/vaadin-mysql-jdbc-screenshot.png/5e3261a2-f0d5-4077-b348-0104bfee0c68?t=1464867467293)

## Tips for More Advanced Requirements

The following sections give hints on how to implement more advanced requirements.

### Connecting to Multiple Databases

In order to connect to multiple databases, you need to define additional data sources and set the data source in the _JdbcTemplate_ instance. The following is one way of defining an additional data source:

The connection properties can be added into the _application.properties_ file and should be defined using the prefix specified in the _@ConfigurationProperties_ annotation:

The data source can be injected and used in a service class as shown below:

### Using Named Parameters

Use the _NamedParameterJdbcTemplate_ class to use named parameters in queries instead of classic question mark placeholders:

### Invoking Stored Procedures

For simple stored procedures such as the following:

A simple call to the procedure using _JdbcTemplate_ is enough:

However, for more sophisticated store procedures (such as when having multiple OUT parameters) use the _[SimpleJdbcCall_](http://docs.spring.io/spring/docs/current/spring-framework-reference/html/jdbc.html#jdbc-simple-jdbc-call-1) or _[StoreProcedure_](http://docs.spring.io/spring/docs/current/spring-framework-reference/html/jdbc.html#jdbc-StoredProcedure) classes.

### Lazy Loading

One way to implement lazy loading is to use _LIMIT_ and _OFFSET_ clauses in the SQL queries and introduce parameters for them in the service class. For example:

The UI implementation should include components to change the offset accordingly.

It's also possible to make the _Grid_ component to lazy load data. The easiest way to do this is by using the [Viritin add-on](https://vaadin.com/directory#!addon/viritin). For small or trivial applications, the _SqlContainer_ class is an option but requires a small change in the [architecture](https://vaadin.com/docs/-/part/framework/sqlcontainer/sqlcontainer-architecture.html).

[See the complete source code on GitHub](https://github.com/alejandro-du/mysql-jdbc-vaadin).
