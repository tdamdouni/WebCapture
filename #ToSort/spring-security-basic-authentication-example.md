# Spring Security: Basic Authentication Example

_Captured: 2017-05-24 at 13:32 from [dzone.com](https://dzone.com/articles/spring-security-basic-authentication-example-1?edition=299096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-23)_

In this post, we will discuss Basic Authentication and how to use it using Spring Security.

## Basic Authentication

  * It's the simplest of all techniques and probably the most used as well. You use login/password forms - it's basic authentication only. You input your username and password and submit the form to the server, and the application identifies you as a user - you are then allowed to use the system - otherwise, you get an error.
  * The main problem with this security implementation is that credentials are propagated in a plain way from the client to the server. Credentials are merely encoded with Base64 in transit, but not encrypted or hashed in any way. This way, any sniffer could read the sent packages over the network.
  * HTTPS is, therefore, typically preferred over, or used in conjunction with, Basic Authentication, which makes the conversation with the web server entirely encrypted. The best part is that nobody can even guess from the outside that Basic Auth is taking place.

Let's create a simple Spring Boot application which Basic Authentication enabled. You can read my previous post on how to create [Simple Spring Boot application](https://dzone.com/articles/spring-boot-a-quick-start), if not familiar with it.

## Add Dependencies in Pom.xml

We will add a `spring-boot-starter-security` dependency to the pom.xml

## Configurations for Basic Authentication

We need to register `BasicAuthenticationFilter` and `BasicAuthenticationEntryPoint` as a bean in the Spring context.

## Enabling Basic Authentication and Configuring Properties

Basic Authentication is by default enabled when you add spring-security in your classpath. You need to configure the username and password for basic authentication. Here are some of the security properties. You can see `SecurityProperties` for other properties that you can configure, like realm name, etc.

## XML Based Configuration for Basic Authentication

This is how to enable basic authentication in Spring Boot application using Spring Security. You can get the full working example code for basic authentication on [Github](https://github.com/gauravrmazra/gauravbytes/tree/master/spring-basic-auth-example).
