# Monitoring Your Java Services With Dropwizard Health Checks

_Captured: 2017-05-23 at 03:47 from [dzone.com](https://dzone.com/articles/monitoring-your-java-services-with-dropwizard-health-checks?edition=299094&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-22)_

Troubleshooting applications can be tedious and time-consuming. It generally involves checking application logs, networking, firewalls, databases, database logs, third-party services, internal service logs... you get the idea. When service is interrupted every second can count. Let your application help you track down issues faster. Your application already has configurations set up for connecting to each external service you need. Why not spend a few extra minutes and make your life a little easier.

## What Is a Health Check?

Health checks are generally very simple binary checks. A check can be as simple as a ping command. This covers two troubleshooting use cases. Can we connect to the service and is that service operational? A failing check won't tell you what is wrong, but it can quickly point you in the right direction. Health checks can also be used for preventing and automatically resolving some issues. If you have auto scaling or load balancers that monitor an application's health, they can quickly add/remove servers when there are issues. As with all fully automated systems, this could backfire and accidentally remove all the servers when minor hiccups occur. This is one reason health checks are recommended to be used for simple up/down checks and not for variable/metric-related checks.

## Dropwizard Health Checks

Once again, Dropwizard Metrics comes through with a great addition to its [JVM metrics](https://www.stubbornjava.com/posts/monitoring-your-jvm-with-dropwizard-metrics). Simply create a class that extends `HealthCheck` and overrides the `check()` method and register it to the `HealthCheckRegistry`. You can now easily call all health checks and see if the application is having any issues. Here is a sample health check that assumes we have an external service as a dependency. All it does is request a URL and expect a 20x response code. `HealthCheck` also exposes a way to add a little context to health checks for some additional debugging info.
    
    
            Response response = client.newCall(request).execute();
    
    
            return Result.unhealthy("code: %s - body: %s", response.code(), response.body().string());

What should you add health checks for? As much as you can or that makes sense. (Databases, third party services, internal services, caches, and maybe even critical files). Some third parties already implement health checks for you. [HikariCP connection pooling](https://dzone.com/articles/database-connection-pooling-in-java-with-hikaricp) provides an out of the box SQL database health check.

## HealthCheckRegistry

Simple static singleton `HealthCheckRegistry`. Feel free to use DI if your heart desires.

## HttpHandler for the HealthCheckRegistry

Since we are making a web service let's expose our health checks via HTTP as JSON. Notice how we also change the status code if any of the checks are unhealthy.
    
    
        SortedMap<String, Result> results = HealthChecks.getHealthCheckRegistry().runHealthChecks();
    
    
        boolean unhealthy = results.values().stream().anyMatch(result -> !result.isHealthy());

## Example Routes

Adding a few quick example routes.

## Wiring Up the Health Checks

Let's reuse our connection pools from our previous post [HikariCP connection pooling](https://www.stubbornjava.com/posts/database-connection-pooling-in-java-with-hikaricp) which will automatically add themselves as health checks. We will also add two of our custom `HealthCheck`s (Let's pretend they are actually hitting an external service and not itself). One will be set to always fail just as an example.

## See it in Action

Once again notice the status code is 500, since one of the checks was unhealthy.
