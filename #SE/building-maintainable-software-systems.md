# Building Maintainable Software Systems - DZone DevOps

_Captured: 2019-08-07 at 18:46 from [dzone.com](https://dzone.com/articles/building-maintainable-software-systems?edition=513293&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202019-08-07)_

Below are some reflections on factors that can assist in building maintainable software systems. There’s nothing new here, just putting together some thoughts that were of interest to me and may be of interest to others, but if you find it too long to read, then simply scroll to the bottom and look at the “Reading material” section to find the source.

## Design the System

Let’s start with a funny anecdote about the value of design.

_“Weeks of coding can save you hours of planning.”_

This is probably wiser when written the other way around (“Hours of planning can save you weeks of coding”), but it’s certainly funnier this way.

Another is “Avoid the task-board shuffle,” which comes from Vaughn Vernon’s Domain-Driven Design Distilled, where the design process is reduced to simply moving a sticky note from the “To-Do” list to the “In-Progress” list.

He also makes the point that there is no such thing as no design, there is just good design and bad design, and that by simply starting to write code you are most likely wandering into bad design.

So how do you look to engender good design and avoid the trap of bad design?

One way would be to investigate Domain-Driven Design (using the books written by Eric Evans and Vaughn Vernon), as it provides a structured and disciplined approach.

It involves working closely with those who have a deep knowledge of the business and then building a common language with which you can create your system so that it reflects its intentions.

For example, let’s say you are speaking to a business expert in the logistics department. You ask them what a customer is and they say that it’s someone with a first name, last name, and address. So, later during modeling, you may decide on a customer object, which would consist of a first name, last name, and address.

You then speak to someone in the sales department and ask them what a customer is, and they say that it’s someone with a first name, last name, age, email address, phone number, and employment status.

So, what do you do?

Once again, during modeling, you could just modify the customer object and add age, email, phone number, and employment status, but they don’t have any meaning to logistics and the address doesn’t matter to sales.

A better way may be for sales and logistics to reside in two separate systems each with their own view of a customer which reflects the language of the business (clearly other factors would also come into play when identifying the boundaries of a system, just keeping it simple here).

Along the design process, one must give due attention to security. For example, it’s not enough to know that a customer has a last name; it’s also important to narrow down the constraints of the last name. How long can a last name be, and what special characters are allowed? Also, when you have more than one system how should they communicate with one another so that it’s secure and prevents unauthorized access?

At this point you haven’t written any code, what you have done is spoken with the experts to understand what it is you are meant to build and then started to design a system (in this simple example, you realize the need for two systems).

## Architect the System

If we focus now on the sales system, we have a domain within which we have modeled a customer object. A customer isn’t of much use if there isn’t a use case for them, and in talking with the business they want to determine the price of products based on the customer's age and employment status. You’ve just realized that you need to model a product and price object, and that you may need a product and/or pricing use case.

Within our architecture, we don’t want business logic in our use cases (can also be known as application services) because our domain is responsible for that. The use cases are not the home of business logic; rather they are orchestrators of requests which are delegated to the domain.

To keep the code clean and maintainable one can use clean architecture principles. There’s a whole book on that by Robert Martin and the acronym SOLID to go with it, but here I’m going to simplify it as separating what the system does from how it does it, and that the “what” is not dependent on the “how.”

What the system does at its core is the domain and the use cases that surround it. How the system does it, relates to its infrastructure, presentation and configuration.

To externalize the thought process could lead us to the following architecture:

![Image title](/storage/temp/12192030-architecture.png)

The first thing to note here is that the domain doesn’t depend on anything else. You can add use cases, switch infrastructure, presentation and configuration without impacting the domain of your system.

Another thing to note is that the arrows only point in one direction which is inwards, avoiding unwanted circular dependencies and spaghetti code.

To break down the above diagram:

  * Domain contains the business logic using the language of the business
  * Use cases orchestrate the requests coming in and delegates to the domain
  * The presentation takes a request (e.g. URL endpoint or UI button click) and passes it onto the use case
  * Infrastructure implements the interfaces defined in the domain (e.g. repositories). This allows the domain to be decoupled from its implementation according to the dependency inversion principle (not to be confused with dependency injection).
  * Configuration can be used to glue together the system (e.g. dependency injection), so it needs to access everything.

In relation to code organization, there is a good chapter in the _Clean Architecture _book called “The Missing Chapter” by Simon Brown where he goes through the different approaches of packaging by layer, packaging by feature, ports and adapters, and packaging by component. This is important as you don’t want a scenario where you are going to create a new object, but you don’t know where in the code structure it’s meant to go, so you end up creating a new package and putting it there. That’s like buying an armchair and not knowing where to put it, so you end up building an extension to your home.

The aim is to end up with a defined and predictable architecture, where each piece resides in a logical place that’s cleanly separated from the other.

## Justifying Architectural Decisions

A key point in determining which architecture, code organization, language, framework, etc. to use is the ability to justify your decisions.

If you can’t justify the decision(s), then you are taking a chance that it will just work out. A better approach might be to first justify the decision to yourself, so that you can later justify it before others.

A good way is to record those decisions, for example, by using [Architecture Decision Records](http://thinkrelevance.com/blog/2011/11/15/documenting-architecture-decisions). Writing down your decision(s) helps you identify if it really makes sense, but it also benefits those coming after you to understand why the system is in its current state.

## Maintaining Architectural Integrity

Initially, a well-defined architecture would work as expected, but over time different people with various experiences and competencies can inadvertently create connections that were not intended, thus violating the architecture.

There are some options to avoid breaking your architecture:

  * As mentioned previously, Simon Brown in the “The Missing Chapter” promotes using the compiler as much as possible to enforce the architecture, by making the implementation classes of interfaces more restrictive (i.e. everything shouldn’t just be public).
  * If you are using Java, you can use [ArchUnit](https://www.archunit.org/) as part of your unit tests.
  * In the book _Building Evolutionary Architectures_, they use [JDepend](https://ant.apache.org/manual/Tasks/jdepend.html) in unit tests.
  * If you don’t mind XML, then you can use [Checkstyle’s import control](https://checkstyle.sourceforge.io/config_imports.html#ImportControl). This allows you to get feedback directly in your IDE, without needing to run unit tests.

## Testing

The intention here is to be confident that your system works as expected. An approach to take with testing is to create a test pyramid that gives you confidence in your system.

There is a helpful article from Martin Fowler on the subject of [test pyramids](https://martinfowler.com/articles/practical-test-pyramid.html).

So, you might end up with something like this:

![Test pyramid](/storage/temp/12192039-test-pyramid.png)

The staple are unit tests.

The integration tests are testing how your system works when it talks for example with a database or an external service. [Testcontainers](https://www.testcontainers.org/) is a library which can prove helpful here.

The acceptance tests are the scenarios that are discussed with the business which can help in determining how complete a business feature is. This can take the “Given-When-Then” format.

For example, if we go back to the use case of the sales system which stated that the price of some products is dependent on the age and employment status of the customer, then an acceptance test scenario could be:

_Given a customer that is over 18 and under 30 who is employed_

_When displaying the prices of all smartphones_

_Then the price should be discounted by 20%._

Tools like [Cucumber](https://cucumber.io/), [Concordion](https://concordion.org/), [Fitnesse](http://fitnesse.org/), [JBehave](https://jbehave.org/) are worth looking into. Once again, the [testcontainers](https://www.testcontainers.org/) library can also prove helpful.

The contract tests are there to ensure that consumers won’t get a nasty surprise if you change your API, because what use is an API if the consumer can’t use it. Tools like [Pact](https://docs.pact.io/) and [Spring Cloud contract](https://spring.io/projects/spring-cloud-contract) are quite popular.

Performance tests are there to ensure that your system continues to perform as expected, and isn’t taking longer than what is deemed acceptable. Tools like [Gatling](https://gatling.io/) and [JMeter](https://jmeter.apache.org/) are worth looking into.

End-to-end tests test the interaction between all your systems. This can potentially be quite flaky since all your systems need to be in a good state for the test to run. One approach to alleviate this is to start each system within its own Docker container using the [testcontainers](https://www.testcontainers.org/) library.

There is no layer here in the pyramid called security tests, as that is part of each layer. For example, in your unit tests, you should check the constraints of last name not exceeding the max length. If you have session cookies or are returning HTML pages in your application then your integration tests should check that your session cookie has the correct security values, that your response headers and content-security policy is as expected. In your end-to-end tests you should check that systems cannot access secured resources without the right permissions and so on.

## Code Style and Analysis

It’s important for code to follow accepted standards and conventions.

It’s not possible to catch everything in code reviews, so having automated code analysis, can save time and help ensure those standards. For code styles, there are options like [checkstyle](https://checkstyle.sourceforge.io/) and [editorconfig](https://editorconfig.org/).

For code analysis, there are options like [SonarLint](https://www.sonarlint.org/), [SonarQube](https://www.sonarqube.org/), [PMD](https://pmd.github.io/), and [SpotBugs](https://spotbugs.github.io/).

## ContinuouS Integration and Delivery

There’s a good book on this topic called, _Continuous Delivery: Reliable Software Releases Through Build, Test, and Deployment Automation_.

To start with, you need to version control your code using something like [Git](https://git-scm.com/) (or another tool of which there are many). It’s important that you regularly check in your code so that your changes are small and manageable. The same principle applies when working with branches, so that your code doesn’t become outdated resulting in lots of conflicts which you then must manually fix (also known as merge hell). Small changes also benefit pull requests, giving you quicker feedback in code reviews.

Once the code is in version control you need to build it and determine that it meets the standards for going out into production. An approach is to use a build pipeline where every change has the potential to go out to production at the earliest opportunity. Tools like [Jenkins](https://jenkins.io/) are a popular choice, and there are many alternatives in this area.

It is here where you can visualize your test pyramid as stages along your build pipeline.

![Build pipeline](/storage/temp/12192043-pipeline.png)

## Production Visibility

It’s important to know that your system is working as expected in production as things can always go wrong.

At a very basic level, you need to know that your application is up and running. This can usually be achieved by specifying an endpoint which can be called at regular intervals to determine that it’s up.

You also need to know that your code is working as expected by logging successful and unsuccessful events. One approach is to use the [Elasticsearch stack](https://www.elastic.co/what-is/elk-stack) where your application code writes log messages to Elasticsearch from which you can query and create dashboards using a tool like [Kibana](https://www.elastic.co/products/kibana). There are alternative options as well.

You also need to know if the environment within which your application is running is working as expected. Metrics can be used to determine things like CPU and memory usage. For the JVM you should also have metrics for garbage collection. Another valuable metric could be how fast your application performs or how many errors you have within a period. One approach is to use the [TICK stack](https://www.influxdata.com/time-series-platform/) or just parts of it. In frameworks like [Spring Boot](https://spring.io/projects/spring-boot) you can use the actuator endpoints to send metrics to tools like Influxdb or [Prometheus](https://prometheus.io/) from which you can query and create dashboards using a tool like [Grafana](https://grafana.com/) or [Chronograf](https://www.influxdata.com/time-series-platform/chronograf/). Once again there are plenty of alternative options.

Another approach to test the resiliency of your production environment is to use [chaos engineering](https://en.wikipedia.org/wiki/Chaos_engineering) to see if you can withstand unexpected conditions.

## Security

It’s important to think of security along the entire development process.

For web application security the [OWASP top ten](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_2017_Project) is a great reference point.

It’s important that the code checks constraints to prevent invalid input.

It’s also important that communication between systems doesn’t allow unauthorized access to protected resources. One approach here is to look into [OAuth2](https://oauth.net/2/) and/or [OpenId Connect](https://openid.net/connect/).

Your build pipeline should give you feedback if a commit has somehow broken your application's security.

When running in the cloud there is a good article about security called [The Three Rs of Enterprise Security](https://builttoadapt.io/the-three-r-s-of-enterprise-security-rotate-repave-and-repair-f64f6d6ba29d) by Justin Smith.

## Reading Material

  * **Domain Driven Design** by Eric Evans and Vaughn Vernon
  * **Clean Architecture** — book by Robert Martin (aka Uncle Bob)
  * **Building Evolutionary Architectures** — by Neal Ford, Rebecca Parsons and Patrick Kua
  * **[Architecture Decision Records](http://thinkrelevance.com/blog/2011/11/15/documenting-architecture-decisions)**
  * **Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation **— book by Jez Humble, Dave Farley
  * **[The Practical Test Pyramid](https://martinfowler.com/articles/practical-test-pyramid.html)**
  * **[The Twelve-Factor App](https://12factor.net/)**
  * **[OWASP Top Ten](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_2017_Project)**
  * **[The Three Rs of Enterprise Security: Rotate, Repave, and Repair](https://builttoadapt.io/the-three-r-s-of-enterprise-security-rotate-repave-and-repair-f64f6d6ba29d)**
