# What Is Spring Boot Auto Configuration?

_Captured: 2017-05-24 at 13:32 from [dzone.com](https://dzone.com/articles/what-is-spring-boot-auto-configuration?edition=299096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-23)_

What every Java engineer should know about microservices: [Reactive Microservices Architecture](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone). Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).

Let's start with a question: Why do we need Spring Boot Auto Configuration?

Spring based applications have a lot of configuration.

When we use Spring MVC, we need to configure a component scan, the dispatcher servlet, a view resolver, web JARs (for delivering static content), among other things.
    
    
      <mvc:resources mapping="/webjars/**" location="/webjars/"/>

The following code snippet shows a typical configuration of a dispatcher servlet in a web application.
    
    
            <load-on-startup>1</load-on-startup>

When we use Hibernate/JPA, we would need to configure a datasource, an entity manager factory, a transaction manager, among a host of other things.
    
    
        <bean id="dataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource"
    
    
            <property name="jdbcUrl" value="${db.url}" />
    
    
            <property name="user" value="${db.username}" />
    
    
            <property name="password" value="${db.password}" />
    
    
            <jdbc:script location="classpath:config/data.sql" />
    
    
        <tx:annotation-driven transaction-manager="transactionManager"/>

The above examples are typical with any Spring Framework implementation or integration with other frameworks.

## Spring Boot: Can We Think Differently?

Spring Boot brings in a new thought process around this.

> Can we bring more intelligence into this? When a Spring MVC JAR is added into an application, can we auto configure some beans automatically?

  * How about auto configuring a Data Source if a Hibernate JAR is on the classpath?
  * How about auto configuring a Dispatcher Servlet if a Spring MVC JAR is on the classpath?

There would be provisions to override the default auto configuration.

> Spring Boot looks at a) Frameworks available on the CLASSPATH b) Existing configuration for the application. Based on these, Spring Boot provides basic configuration needed to configure the application with these frameworks. This is called `Auto Configuration`.

To understand Auto Configuration further, let's bootstrap a simple Spring Boot Application using Spring Initializr.

## Creating REST Services Application With Spring Initializr

> Spring Initializr <http://start.spring.io/> is great tool to bootstrap your Spring Boot projects.

![Image](http://www.springboottutorial.com/images/Spring-Initializr-Web.png)

> _As shown in the image above, following steps have to be done._

  * Launch Spring Initializr and choose the following 
    * Choose `com.in28minutes.springboot` as Group
    * Choose `student-services` as Artifact
    * Choose following dependencies 
      * Web
      * Actuator
      * DevTools
  * Click Generate Project.
  * Import the project into Eclipse.
  * If you want to understand all the files that are part of this project, you can go here.

### Spring Boot Auto Configuration in Action

When we run StudentServicesApplication.java as a Java application, you will see a few important things in the log.
    
    
    Mapped "{[/error]}" onto public org.springframework.http.ResponseEntity<java.util.Map<java.lang.String, java.lang.Object>> org.springframework.boot.autoconfigure.web.BasicErrorController.error(javax.servlet.http.HttpServletRequest)

The above log statements are good examples of `Spring Boot Auto Configuration` in action.

As soon as we added in Spring Boot Starter Web as a dependency in our project, Spring Boot Autoconfiguration sees that Spring MVC is on the classpath. It autoconfigures dispatcherServlet, a default error page and webjars.

If you add Spring Boot Data JPA Starter, you will see that Spring Boot Auto Configuration auto configures a datasource and an Entity Manager.

## Where Is Spring Boot Auto Configuration Implemented?

All auto configuration logic is implemented in `spring-boot-autoconfigure.jar`. All auto configuration logic for MVC, data, JMS, and other frameworks is present in a single JAR.

![Image](http://www.springboottutorial.com/images/spring-boot-autoconfigure-jar.png)

> _Spring Boot Auto Configure Jar_

Another important file inside spring-boot-autoconfigure.jar is /META-INF/spring.factories. This file lists all the auto configuration classes that should be enabled under the EnableAutoConfiguration key. A few of the important auto configurations are listed below.
    
    
    org.springframework.boot.autoconfigure.EnableAutoConfiguration=\

We will take a look at DataSourceAutoConfiguration.

Typically, all auto configuration classes look at other classes available in the classpath. If specific classes are available in the classpath, then configuration for that functionality is enabled through auto configuration. Annotations like @ConditionalOnClass, @ConditionalOnMissingBean help in providing these features!

`@ConditionalOnClass({ DataSource.class, EmbeddedDatabaseType.class })` : This configuration is enabled only when these classes are available in the classpath.

`@ConditionalOnMissingBean`: This bean is configured only if there is no other bean configured with the same name.

Embedded Database is configured only if there are no beans of type DataSource.class or XADataSource.class already configured.

## Debugging Auto Configuration

There are two ways you can debug and find more information about auto configuration.

  * Turning on debug logging
  * Using Spring Boot Actuator

You can turn on debug logging by adding a simple property value to application.properties. In the example below, we are turning on Debug level for all logging from org.springframework package (and sub packages).

When you restart the application, you will see an auto configuration report printed in the log. Similar to what you see below, a report is produced including all the auto configuration classes. The report separates the positive matches from negative matches. It will show why a specific bean is auto configured and also why something is not auto configured.

Another way to debug auto configuration is to add Spring Boot Actuator to your project. We will also add in HAL Browser to make things easy.

HAL Browser auto configuration (<http://localhost:8080/actuator/#http://localhost:8080/autoconfig>) will show the details of all the beans that are auto configured and those which are not.

![Image](http://www.springboottutorial.com/images/spring-boot-auto-configuration-actuator-negative-matches.png)

> _Negative Matches Spring Boot Auto Configuration_

![Image](http://www.springboottutorial.com/images/spring-boot-auto-configuration-actuator-positive-matches.png)

> _Positive Matches Spring Boot Auto Configuration_

Microservices for Java, explained. Revitalize your legacy systems (and your career) with [Reactive Microservices Architecture](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone), a free O'Reilly book. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).
