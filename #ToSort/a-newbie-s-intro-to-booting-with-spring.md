# A Newbie's Intro to Booting With Spring

_Captured: 2017-05-14 at 20:11 from [dzone.com](https://dzone.com/articles/newbies-intro-booting-with-spring?oid=twitter&utm_content=buffer8be52&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

![Image title](https://dzone.com/storage/temp/4352206-a1.png)

![Image title](https://dzone.com/storage/temp/4352207-a2.png)

## 1\. Background

Spring is a fantastic open source framework that addresses the complexity of application development. One of the chief advantages of the Spring framework is its layered architecture, which allows you to be selective about which of its components you use. Spring is a cohesive framework for J2EE application development.

While developing desktop, web, enterprise, cloud, or microservices applications, almost every application type needs a robust infrastructure which takes care of dependencies, auto-configuration, and actuators.

![Image title](https://dzone.com/storage/temp/4352214-a3.png)

So getting started with Spring or any other frameworks is a critical and time consuming task.

Spring provides a convenient way over such application infrastructure issues with a framework called Spring Boot.

Spring Boot provides the best industry practices, helps when you start applications from scratch, and boosts your application development speed.

## 2\. Overview

Spring Boot is developed on top of the Spring Framework; it's a modular framework which helps in building application infrastructure, taking care of CLI (command line interface), bootstrapping, dependencies, framework integrations, testing, tools, auto-configuration, and actuators. It favors convenience over configuration.

![Image title](https://dzone.com/storage/temp/4352224-a4.png)

Spring Boot encapsulates Spring and many other frameworks and tools, like Apache Velocity, Log4j, and Tomcat, and provides starters to take care of these framework and tool integrations. The figure below shows the relationship between Spring Boot and other frameworks:

![Image title](https://dzone.com/storage/temp/4352225-a5.png)

> _Figure 1: Overview of Spring Boot_

The spring-boot-starter-parent root module hooks your application with Spring Boot; and the rest of the starter modules can be included as needed.

Spring Boot supports XML configuration to support legacy applications, and favors Java-based configurations.

## 3\. Getting Started

Spring Boot is the easiest recommended way to setup your Spring application environment. You just need to choose one of the ways to initialize your Spring application.

Spring Boot supports Ant, Maven, and Gradle build systems, including traditional building methodology. Simply dump Spring libraries in the application class path. Maven and Gradle are the recommended ways to build your project.

## 4\. Project Builder

Getting started with any new project from scratch is a complex task where you have to take care of various task, including the project file structure, creating a build file, and adding dependencies to the build.

Spring projects can be built in various ways:

  1. Manual Build

  2. Spring Initializer

  3. Eclipse STS (Spring Tool Suite)

  4. Spring Boot CLI

  5. Maven Build

  6. Gradle Build

In this section we will focus only on Spring Boot CLI, Maven, and Gradle project initializations.

### 4.1 Manual Build

The traditional way to start with Spring is simply to dump all required Spring Framework, Spring Boot, and other external dependencies in your application class path. Spring libraries follow naming conventions, Spring Boot's jar name starts with `spring-boot-*.jar` and the Spring Framework's jar name starts with `spring-*.jar`.

### 4.2 Spring Initializer

The simplest way to get started with Spring is the Spring Initalizer. It is a web interface (SWI) to build your Spring project on the fly. The url <http://start.spring.io/> points to Spring Initalizer.

The SWI simply needs input from you as to what kind of project build you would prefer: Maven or Gradle. Similarly it asks for group, artifact, and dependencies, and based on these inputs generates the project.

### 4.3 Eclipse STS

Eclipse is a widely used IDE with Spring Tool Suite (STS) plugin support. To create any project in Eclipse, simply press the Ctrl+N shortcut, which will show figure 1.2.

![Image title](https://dzone.com/storage/temp/4352553-a7.png)

> _Figure 2: Eclipse New Project._

Click on next and it will nevigate you to the New Spring Starter Project window, go to Spring > Spring Starter Project, it will show figure 3 where you will assign the name of your project and configure your build as per your Maven or Gradle choice.

![Image title](https://dzone.com/storage/temp/4352584-a8.png)

> _Figure 3: New Eclipse New Project_

After clicking next it will navigate you to the Spring Starters config choice window, shown below, where you need to select Starter modules as per your project needs.

![Image title](https://dzone.com/storage/temp/4353601-a9.png)

> _Figure 4: Spring Starters config choice_

At this point, you can click on finish, which will create the project for you based on your configuration, or hiting next will nevigate you to the Create Spring Starters Project screen. Here your project is created in your workspace:

![Image title](https://dzone.com/storage/temp/4353624-a10.png)

> _Figure 5: Create Spring Starters Project_

### 4.4 Spring Boot CLI

Spring Boot provides a command line interface (CLI) for Spring applications, it provides commands which helps to get a quick start on Spring application development. Spring Boot CLI is optional, but it's simple, standard, and a recommended way to setup your application development environments.

#### Install Spring Boot CLI

There are several ways to install Spring Boot CLI, but we will use the simplest recommended way.

  1. Download Spring Boot CLI distribution.

  2. Update the `SPRING_HOME` environment variable with its directory.

  3. Update `PATH` environment variable with its `SPRING_HOME/bin` directory.

  4. Fire command `spring -version`

If everything is fine then you will get the Spring Boot version, otherwise something is missing. It's assumed that Java, Maven, and Gradle are already installed and configured.

It provides a handy way to interact with your Spring application, simply by firing a few commands we can create, build, test, and run Spring applications.

#### 4.4.1. Init

The init command simply initializes your baseline spring boot application development environment.

![Image title](https://dzone.com/storage/temp/4353635-b1.png)

This is the simplest form of init command. It creates the project demo.zip with a maven pom.xml build script, and adds the most basic dependencies in it. Init command has several command line parameters.

**Build:** The build parameter specifies the build type of your project if default build type is Maven. The build command allows Maven and Gradle as build parameter values. If the build parameter is not provided, then Maven is taken as an implicit build parameter.

![Image title](https://dzone.com/storage/temp/4353663-b2.png)

**Dependency:** The `-d` or `-dependencies` parameter is used to specify additional dependencies to the project. The dependencies must be seperated by commas.

![Image title](https://dzone.com/storage/temp/4353668-b3.png)

This example creates Demo.zip with Spring Boot web, JPA, and security dependencies in pom.xml. If you want a different name for your project, then it can be specified in the last part of the init command.

**Packaging:** Applications need to be wrapped in a jar or war file. The packaging is supplied with a `\--packaging` or `-p` parameter:

![Image title](https://dzone.com/storage/temp/4353669-b4.png)

> _Extract: The --extract or -x parameters extract the project into the current directory._

![Image title](https://dzone.com/storage/temp/4353673-b5.png)

**List:** The `\--list` or `-l` parameter can be used with Spring Boot commands to list all available options.

![Image title](https://dzone.com/storage/temp/4353674-b6.png)

#### 4.4.2. Help

This command can be used to get help for any commands.

### 4.5 Maven Build

Spring applications are configured to inherit Maven pom with `spring-boot-starter-parent`, it is an excellent way to start with the Spring platform. Any one of these options can be used to configure your Spring Boot Application.

Applications may have Spring Boot or any other dependencies which can be configured in the <dependencies> section of the application pom. Spring Boot takes care of dependency management of the underlying Spring Framework, Spring Cloud, Spring Integration, and any other dependencies of the Spring platform as per your configuration.

![](https://media.licdn.com/mpr/mpr/AAEAAQAAAAAAAAksAAAAJDJkNzFlODJkLTUwMjEtNDU4MC1hYmJjLWFiZGJmMWMyM2UzMQ.png)

Java does not provide any standard way to wrap the external application jars, configurations, and entities required. `spring-boot-mavenp-plugin` solves this problem by wrapping your application in an executable jar, also known as a fat jar.

![Image title](https://dzone.com/storage/temp/4353807-b7.png)

### 4.6 Gradle Build

In order to build your application in Gradle, you need to insert the lines mentioned in the figure below.

![Image title](https://dzone.com/storage/temp/4353814-b8.png)

**buildscript:** The buildscript element is used to declare a Spring version and the Spring Boot plugin.

**apply plugin:** Similarly, Java, Eclipse, and Spring Boot plugins are applied to this project using the apply pluign.

**Jar:** Used to define the type of build and its verion. With spring-boot-starter-parent, it is an excellent way to start with the Spring platform.

**sourceCompartability and targetCompartability:** These elements are used to define the acceptable version range of Java and JDK compatible with the source code.

**repositories:** Defines the dependant repositories needed for the project build.

**Dependencies:** This element is used to define the application dependencies configured in the application classpath.

## 5\. Run Application

Spring Boot provides a convenient way to run your application. You have to fire `mvn spring-boot:run` from the root directory of your project or from Eclipse. The `spring-boot:run` command is sufficient to start your application, and the deliverables are wrapped in an executable jar as below.

### **Syntax**

![Image title](https://dzone.com/storage/temp/4353840-b9.png)

![Image title](https://dzone.com/storage/temp/4353848-b10.png)

## 6\. Hello Spring Boot

With respect to the Hello world program tradition, we are going to buld a "Hello Spring Boot" program using Spring Boot framework.

1\. Create a new spring boot starter project using any of the above ways mentioned in the Project Build section.

2\. Create BootingWithSpringStarter class in project.

3\. Annotate class BootingWithSpringStarter using the @SpringBootApplication annotation.

![Image title](https://dzone.com/storage/temp/4353853-c1.png)

4\. Create another class. AppLoader implements ApplicationListener<ContextRefreshedEvent> and overrides the public void onApplicationEvent(ContextRefreshedEvent event) method.

5\. Write your "Hello Spring BOOT" print statement into the onApplicationEvent method implementation.

![Image title](https://dzone.com/storage/temp/4353856-c2.png)

Spring boot provides standard mechanism to start you spring platform application like Java. Java by always starts an application execution from its main method. Similarly Spring boot provides convenient way to start execution of Spring boot application. You simply need to write the code in the main method to load Spring boot calling the SpringApplication class run() method, so applications based on the Spring platform can use the same mechanism to bootup with the Spring platform.

Application main class is annotated with Spring Boot @SpringBootApplication annotation, it enables the auto configuration of the Spring framework configuration based on the Spring libraries found in your application classpath.

The BootingWithSpringStarter class starts the execution of your application, the main method hook application bootstrap application by calling `SpringApplication.run(BootingWihtSpringStarter.class, args))` , The BootingWithSpringStarter is the base startup class of application, and the args array is also passed to expose command line arguments if any.

## 7\. Summary

Spring boot simplifies the lives of Spring developers, supporting project builds, auto-configuration, managing dependencies, devtools, and actuators. It helps in building robust application infrastructures and boosts application development speed.

[Download Modern Java EE Design Patterns](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035): Building Scalable Architecture for Sustainable Enterprise Development. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035).

### Like This Article? Read More From DZone
