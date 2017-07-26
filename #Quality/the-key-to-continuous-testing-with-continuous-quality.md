# The Key to Continuous Testing with Continuous Quality

_Captured: 2017-03-30 at 01:29 from [dzone.com](https://dzone.com/articles/automated-white-box-testing-the-key-to-continuous)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Continuous Delivery (CD) is the new paradigm for application development. For organizations leveraging software to engage buyers in the digital realm, it has become a necessity to outpace the competition and to continuously improve the customer experience.

![](https://media.licdn.com/mpr/mpr/AAEAAQAAAAAAAAd8AAAAJDg4MDJlZjk1LTg0YTAtNGQ3OS1iYzljLWY4ZDEyOGE1ODg5ZQ.png)

[Image Source: <https://www.tricentis.com/>]

CD is a logical extension of the DevOps movement and has increased the velocity of software development to a point where near-impossible demands are being placed on software testing and quality assurance. Here's why software testing must evolve.

  * Small batch releases have significantly driven up the volume of test operations.

  * Code must be tested much earlier in the cycle, typically ahead of the user interface.

  * Integration testing of distributed code modules has become critical and complicated.

  * It's impossible to produce test data in a timeframe that keeps pace with this process.

  * Engineers are required to write code to test business logic and DB transactions.

The last bullet refers to the need for white box testing, a type of testing that examines the internal source code of the software and enables full coverage of an application's business logic and database interactions prior to source code check-in. Automation of white box testing is essential to balance the need for speed with the need for quality. Unfortunately, most organizations lack the time or resources to fully implement a white box testing regimen.

For example, fully testing an application designed for a database with 100 tables can require 1,000 test operations just to perform the necessary create, read, update, and delete (CRUD) interactions combined with associated constraint and performance tests (in this example, we assume 10 operations per table).

![](https://media.licdn.com/mpr/mpr/AAEAAQAAAAAAAAikAAAAJGI1NzYyZTM3LWM5NTgtNGViNS05YjMyLTA5NGE5OTllNzQ4OQ.png)

[Image Source: <https://www.genrocket.com/>]

With a manual testing process, implementing a test for each table (i.e., writing test scripts and/or code, producing and loading appropriate test data, and performing all test operations) would take 10 hours per test * 100 test operations * 100 tables, totaling 10,000 hours. That translates to 250 work weeks -- much too long to wait and much too expensive to fund with manual testing resources.

As a result, the quality of the code under this kind of scenario suffers and the organization releasing this code into production is exposed to higher business risk. Making this kind of trade-off is not ideal, but it is understandable. How can any organization hope to keep pace with the velocity of Continuous Delivery while, at the same time, maintaining high standards for the level of code coverage and quality?

## ** Continuous Delivery Requires a New Testing Approach**

Continuous Delivery redefines the software development lifecycle in a fundamental way. It affects the application design and release frequency and places new demands on software quality assurance. It calls for a completely new approach to software testing along the dimensions of people, process, and technology.

Here are the main elements of this new approach:

  * **People:** A DevOps culture for eliminating silos and empowering test engineers.

  * **Process: **Continuous Integration and continuous testing with full code coverage.

  * **Technology:** Automated white box testing and real-time, on-demand test data.

While organizations must focus internally on how to best approach the people and process dimensions of software testing, new technology can be brought to bear to accelerate the speed of testing while improving the coverage and quality of code.

![](https://media.licdn.com/mpr/mpr/AAEAAQAAAAAAAAe3AAAAJDA1OTM4NzcyLTVhMmUtNGIxMi1iZTkzLWQwYjNmZWNkNTc2MQ.png)

[Image Source: <https://www.genrocket.com/>]

The combination of white box testing, automatic test code generation, and real-time, model-based test data generation accelerates the testing process while ensuring the highest level of software quality.

If automated white box testing is applied to the scenario described above, the time required to execute the same 1,000 test operations can be accelerated by 90%.

![](https://media.licdn.com/mpr/mpr/AAEAAQAAAAAAAAeWAAAAJDM0ODg5Njg2LTMxODItNGFmZS1hMWY3LTYyNjBjMGY3MTk4Ng.png)

[Image Source: <https://www.genrocket.com/>]

The impact of white box test automation on this test plan is a reduction in total test time from 250 weeks to just 25 weeks. This is a major reduction in time and cost without compromising a commitment to full code coverage.

As illustrated by the software test pyramid in the diagram below, white box testing represents 90% of the test operations required for continuous testing and continuous integration. The remaining 10% of test operations remains a manual process in order to perform end-to-end functional testing and validate the end-user experience.

![](https://media.licdn.com/mpr/mpr/AAEAAQAAAAAAAAigAAAAJGZhMzdiZGVlLWM0ZjMtNDA1My04YjU5LTkwMmRlNDMyYzM4Nw.png)

[Image Source: <https://www.genrocket.com/>]

The automated generation of test code accelerates unit test and integration test operations for each new release.

Model-based, real-time test data with full referential integrity is generated on-demand to simulate a production environment for a database with just a few tables or one that has hundreds or even thousands of tables.

## **The New Rules of Software Testing**

In the age of Continuous Delivery, software testing must conform to a new set of rules:

  * Testing must be continuous and keep pace with software development.

  * Test operations must run automatically and operate at high speed.

  * All of the application code must be fully tested (100% code coverage).

  * All test data must be generated on-demand and not pruned from production data.

  * Data must represent the format needed (realistic, random, patterned, conditioned).

  * Test code and data must automatically update to reflect changes in data models.

  * The user experience must be intuitive allowing a tester to use it in a matter of days.

  * The solution must be low cost allowing any organization to afford and utilize it.

Software testers must evolve to become software test engineers capable of using a new generation of tools allowing them to easily design and execute white box test operations at the unit test, integration test, and functional test levels. Once created, white box test code can be repurposed to adapt to changes in data models and business logic throughout the software testing life cycle. As this lifecycle progresses, a number of reusable assets can be created, stored, revised and re-run to accommodate changes to the application, to incorporate new test procedures and to streamline regression testing as new code releases are developed and integrated into the application.

The new rules of software testing combined with new technology to automate the use of white box testing with real-time test data will transform the way software testing is performed. This will enable continuous testing with continuous quality and serve as an essential component of a continuous delivery software development model.

_[To learn more about GenRocket software testing technology, visit www.genrocket.com_](http://www.genrocket.com/)

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).

### Like This Article? Read More From DZone
