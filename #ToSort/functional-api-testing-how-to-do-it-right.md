# Functional API Testing — How to Do it Right

_Captured: 2018-03-23 at 19:17 from [dzone.com](https://dzone.com/articles/functional-api-testing-how-to-do-it-right?edition=367215&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-23)_

Maintain Application Performance with real-time monitoring and instrumentation for any application. [Learn More!](https://dzone.com/go?i=281422&u=https%3A%2F%2Fwww.nastel.com%2Fapplication-performance-monitoring%2F%3Futm_source%3DDZone%26utm_medium%3DPrePostRoll%26utm_campaign%3DDZone2018%2520for%2520all%2520pre%2Fpost-roll%2520text%2520ads%3A)

API, or application program interface, is a system of communication methods that gives developers and non-developers access to programs, procedures, functions and services. The most common protocol used in API is HTTP, together with [REST architecture](https://www.blazemeter.com/blog/rest-api-testing-how-to-do-it-right?utm_source=blog&utm_medium=BM_blog&utm_campaign=functional-api-testing-how-to-do-it-right). Developers who program using REST make their code easy to understand. They and others know which language they will be using, how the functions work, which parameters can be used, etc.

Popular frameworks for developing APIs include Swagger, WADL and RAML. Ideally when programming, developers form a "API Contract", which describes how the services developed in the APIs should be consumed.

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/shutterstock_563463502%20\(1\).jpg)

Prior to this standardization, programming was like the Wild West. Developers gave access to their code in the way they saw fit, and it was hard to develop public services and make them available because there were many ways to code. [SOAP](https://www.blazemeter.com/blog/testing-soaprest-web-services-using-jmeter?utm_source=blog&utm_medium=BM_blog&utm_campaign=functional-api-testing-how-to-do-it-right) was the first attempt at standardization, but now REST is the dominant player.

[API testing](https://www.blazemeter.com/api-testing?utm_source=blog&utm_medium=BM_blog&utm_campaign=functional-api-testing-how-to-do-it-right) creates a more reliable code. But historically, testing would take place at the GUI level. When a developer would finish their work, they would hand it off to the QA engineer. The engineers had limited time so they would test the code at the highest level, the GUI. This would cover both the frontend and the backend development.

This worked for manual testing and for the beginning of automation testing, but isn't right for the age of agile and continuous testing. GUI testing is too brittle and GUI automated scripts break easily. In addition, teams can't wait for the entire system to be updated and the GUI to be ready before testing occurs.

In the age of agile, testing must take place at a lower level, i.e at the API level. Developers can even do it themselves. API tests, because of "API contracts", can even be created before development is complete. This means developers can validate their code based on pre-written tests (aka Test Driven Development).

But despite the known importance of API testing, it doesn't always get done. [Agile Developers](https://www.blazemeter.com/blog/continuous-integration-101-how-run-jmeter-jenkins?utm_source=blog&utm_medium=BM_blog&utm_campaign=functional-api-testing-how-to-do-it-right) just don't have time. On average developers only code one day a week, the rest of their time is taken up with testing, documentation, validation, and meetings. So they try to have hardening sprints (that isn't really agile, is it?) where manual testing takes place, but it just takes too long. It's very difficult to be able to get functional API testing done in the two weeks you also need to develop, test, validate and get the documentation complete.

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/shutterstock_525708298%20\(1\).jpg)

Automating API testing makes developing faster and clears up developers' time to do other things, like write code. Automating also enables covering the full scope of tests more easily: positive, negative, edge case, SQL injection, etc. This ensures nothing is left to chance and all parameters and permutations are tested. Agile development groups that attempt to test their APIs might test one or two positive test flows, or one positive and one negative, and call that a success. But this is not thorough API testing and opens the door for unnecessary release risk because many variants are missed and full validation isn't achieved.

For example, let's say an API takes an author's name and a book release date. A positive flow will test the name and date and see if they work. Once the response is properly received the API works. Supposedly.

But what about the negative and edge cases? Fro example, inserting a proper date but no book, or changing the date format, or a correct date format for a year that doesn't exist, or a long name, or inserting a SQL code that grants data to the DB, etc. These are just a few examples out of many variants that need to be tested, even though they are not covered in the contract.

Developers and testers need an easy way to create tests that cover all of these aspects. We recommend you look for a solution that can take your [Swagger ](http://swagger.com/)or other framework files, test them comprehensively according to your API contract, and run them as part of your Continuous Integration process. This ensures you can focus on developing strong and durable code.

To start your [API Functional tests](https://www.blazemeter.com/api-functional-testing) you can [request a BlazeMeter demo](http://info.blazemeter.com/live-request-a-demo?utm_source=blog&utm_medium=BM_blog&utm_campaign=functional-api-testing-how-to-do-it-right) or simply put your URL in the box below to start testing.

Collect, analyze, and visualize performance data from mobile to mainframe with AutoPilot APM. [Get a Demo!](https://dzone.com/go?i=281423&u=https%3A%2F%2Fwww.nastel.com%2Fapplication-performance-monitoring%2F%3Futm_source%3DDZone%26utm_medium%3DPrePostRoll%26utm_campaign%3DDZone2018%2520for%2520all%2520pre%2Fpost-roll%2520text%2520ads%3A)

Topics:

continuous integration ,devops ,functional api testing ,api testing ,swagger ,soap ,developers ,rest architecture ,agility ,load api testing
