# QA in a Microservices World

_Captured: 2018-06-06 at 21:35 from [dzone.com](https://dzone.com/articles/qa-in-a-microservices-world?edition=376267&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=microservices%202018-05-09)_

Containerized Microservices require new monitoring. See why a new APM approach is needed to even [see containerized applications](https://dzone.com/go?i=279427&u=https%3A%2F%2Fwww.instana.com%2Flibrary%2Febook-application-monitoring-in-containerized-world%2F%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dcontainer_apm_ebook%26utm_content%3Deverything_changed).

Microservices demand a new approach to QA. In contrast to monolithic applications, where every part of an application can be tested at the same time, microservices make QA much more complicated because each microservice may be developed and delivered according to its own schedule.

How can QA teams adapt to meet this challenge? Let's take a look.

## Unit and Integration Testing

The base of any solid strategy around QA in a microservices world is to have every piece of code covered by tests at the lowest levels. These tests are unit tests and integration tests.

By introducing unit tests as part of the activities a developer is responsible for, and having code coverage checks as part of the continuous integration (CI) pipeline that microservices rely on, it becomes routine to expect 80+% of code to have tests that happen during the build process before the code actually interacts with anything else.

Integration testing is the next level that developers are also responsible for. Integration testing is building tests that wrap around the entire object to test that all its inputs and outputs work as expected. With all the inputs and outputs meeting previous standards, the component can be deployed up the stream, without negatively impacting any microservices or other integration points that rely on it.

## System and User Acceptance Testing

At the system and user acceptance testing layers of any environment, there needs to be routine end-to-end testing across all the services and user interfaces involved in day-to-day business transactions.

With a CI pipeline able to require that a component successfully pass all its unit and integration tests before being deployed to the system test and user acceptance testing environments, any tests in these environments can focus on higher value tests like validating entire use cases and storyboards that the microservices and micro-frontends are modeled after.

As with other testing levels, these tests can also be automated using tools like Selenium and JMeter to allow manual testing to focus on automating tests around new functionality, working with anomalies, and tracking down what caused an existing automated test to fail.

## Service Virtualization

On top of more testing, there is currently a move towards more advanced input and output testing. In traditional testing, a developer would create a mock endpoint which simulated the data, expecting just to test the internal code. While this provides some basic validation, it does not test the full request as in a real environment.

To resolve this limitation, there are now products available which can simulate an API endpoint so the entire call tree will be used, just like when a microservice is running in a live environment. A quick Internet search will reveal multiple vendors in this space, from open source-based solutions to high-end, enterprise-class solutions that include features like being able to simulate network reliability and latency issues.

## API Runtime Validation and Monitoring

As the API is moved along the CI/CD pipeline, teams involved should be identifying which use cases will be monitored on a continual basis for performance and availability purposes. While some companies only enable monitoring in customer-facing environments, there is a lot of value in monitoring some or all of the identified use cases through the entire DevOps lifecycle so there will be baselines to compare live environments to. Having no idea what performance is like before going live can lead to some very late nights that can be mitigated with planning and testing. As Benjamin Franklin once said, "An ounce of prevention is worth a pound of cure."

As a side note, if development teams write their microservices by leveraging the [OpenAPI](https://github.com/OAI/OpenAPI-Specification) standard for the interface definition and documentation, the number of tools which can import the API and leverage it immediately in the API Monitoring and Management space increase drastically, and save a lot of work for operational teams.

## Summary

QA is a key piece of the puzzle for ensuring that organizations derive full value from microservices architectures. Effective QA in the microservices age requires not just basic testing like integration tests, but also acceptance testing, service virtualization, and API monitoring coverage.

[Automatically manage containers and microservices](https://dzone.com/go?i=290421&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana) with better control and performance using [Instana APM](https://dzone.com/go?i=290421&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana). Try it for yourself [today](https://dzone.com/go?i=290421&u=https%3A%2F%2Fwww.instana.com%2Ftrial%3Futm_source%3DdZone%26utm_medium%3Dpre_post_article_text_ad%26utm_campaign%3Dinstana_trial%26utm_content%3Dgot_cloud_get_instana).
