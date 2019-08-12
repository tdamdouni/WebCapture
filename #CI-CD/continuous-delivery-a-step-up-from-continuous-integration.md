# Continuous Delivery: A Step Up From Continuous Integration

_Captured: 2018-09-05 at 22:24 from [dzone.com](https://dzone.com/articles/continuous-delivery-a-step-up-from-continuous-inte?edition=393195&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-09-05)_

Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=299509&u=http%3A%2F%2Ftechtowntraining.com%2Fresources%2Ftools-resources%2Fdevops-transformation-roadmap%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_content%3Dguide). Brought to you in partnership with [Techtown](https://dzone.com/go?i=299509&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dfooter).

In this series of posts, we will take a look at how to extend and build on your existing Continuous Integration (CI) infrastructure and processes towards a Continuous Delivery (CD) model. In this article, we will go through the basics of CD, it's relation to CI, and its importance in the software delivery model. Additionally, the purpose of this post is to point out the key elements and differences between continuous integration and continuous delivery. For those of you unfamiliar with Continuous Integration, I recommend reading the series of posts:

[Part 1](http://techtowntraining.com/resources/blog/continuous-integration-part-1-fundamentals) \- The basic concepts of CI and its relevance in an Agile and DevOps team culture.  
[Part 2](http://techtowntraining.com/resources/blog/continuous-integration-part-2-ci-server-toolkit) \- What is CI Server and how it can seamlessly bring together various industry standard  
practices of implementing a CI process.  
[Part 3](http://techtowntraining.com/resources/blog/continuous-integration-part-3-best-practices) \- The good and bad practices that make up a CI Process and Workflow.

## Introduction

As per [Martin Fowler](https://martinfowler.com/bliki/ContinuousDelivery.html), an authority on Continuous Delivery, you're doing continuous delivery when:

  * Your software is deployable throughout its lifecycle
  * Your team prioritizes keeping the software deployable over working on new features
  * Anybody can get fast, automated feedback on the production readiness of their systems anytime somebody makes a change to them
  * You can perform push-button deployments of any version of the software to any environment on demand

He also clarifies that Continuous Delivery is different to Continuous Deployment, often mistaken to be the one and the same.

> "Continuous Deployment means that every change goes through the pipeline and automatically gets put into production, resulting in many production deployments every day. Continuous Delivery just means that you are able to do frequent deployments but may choose not to do it, usually due to businesses preferring a slower rate of deployment."

## Why Continuous Delivery? Why Not Stop at Continuous Integration?

In the previous posts linked above, we have seen why CI has become a mandatory investment for any software development company, by virtue of providing measurable benefits to both developers and customers. These measurable variables include software quality, faster time-to-market, quicker feedback cycles on defects, lower costs of development and decreased occurrences of integration issues throughout the whole software development process.

But is that enough to inspire confidence?

Yes, the tests pass and the CI server dashboard is all Green.

Yes, an embarrassing bug has been caught before it has reached the customer.

Could we say with confidence that the software is not going to fail in the production environment? No. That's because the boundaries of CI is within the development organization.

There is a border between developers and operators, and that perimeter has not been breached.

Developers washed their hands of code they pushed to production, safe in the knowledge that the ball is now in someone else's court.

With hardly any communication between the development organization and the operations organizations in most companies, a "handoff" needs to occur. Assumptions that were made by the developers in terms of the customer's operating environment are usually found to be incorrect here, or at best, a well-intended assumption of the customer's world by the development organization.

Imagine the plight of the operations team in the majority of the companies. They have received delivery of software from a team of developers who knew next to nothing about the customer's  
installation environment. What "worked" in the developer's machine is not guaranteed to work in the customer's complex production environment.

That's where CD comes in.

Continuous delivery is a software engineering approach in which teams produce software in short cycles, ensuring that the software can be reliably released at any time. It aims at building, testing, and releasing software with greater speed and frequency.

Part of that is testing every change you've made (i.e. continuous integration ). In addition, you've also made the effort to package up the actual artifacts that are going to be deployed - perhaps you've already deployed those artifacts to a staging environment.

So continuous delivery actually requires continuous integration. It relies on the same underlying principles.

The differences are very well captured in the illustration below.

![](http://techtowntraining.com/sites/default/files/inline-images/CD%20-%20A%20Step%20up%20from%20CI.jpg)

> _(image credits to collab.net - http://www.collab.net/solutions/devops)_

## The Transition of Continuous Integration into Continuous Delivery

Often, CI is already established and running, for instance as part of introducing Agile development methodologies.

Continuous Integration usually refers to integrating, building, and testing code within the development environment. Continuous Delivery builds on this, dealing with the final stages required for production deployment.

Most organizations start with Continuous Integration (CI), which is about developers merging code changes to a repository multiple times a day. Each merge triggers an automated build and  
testing sequence for the project. Automated tests then verify the code, any broken tests are to be immediately fixed by the developers. CI acts as a safety net that lets developers prevent many issues before they reach the end users.

CD is built on the foundations laid by continuous integration by deploying all code changes to a testing environment and/or a production environment after the build stage. When continuous delivery is implemented properly, developers will always have a deployment-ready build artifact that has passed through a standardized test process.

## Continuous Delivery Pipeline

Continuous delivery is enabled through the deployment pipeline. The purpose of the deployment pipeline has three components: visibility, feedback, and continually deploy.

  * Visibility - All aspects of the delivery system including building, deploying, testing, and releasing are visible to every member of the team to promote collaboration.
  * Feedback - Team members learn of problems as soon as possible when they occur so that they are able to fix them as quickly as possible. There is also the User Feedback. The earlier and more frequently you get working software in front of real users, the quicker you get feedback to find out how valuable it really is
  * Continually deploy - Through a fully automated process, you can deploy and release any version of the software to any environment. Since you are deploying smaller changes, there's less to go wrong and it's easier to fix should a problem appear.

At a product level, moving to a CD model is not an overnight job. Major changes have to be made to the code which not only involves significant investment into tooling but also on the core aspects of the existing system itself. Some of them are:

## Automated Tests

If you have CI successfully implemented, your development team will be able to merge code to the master branch up to a few times a day. The automated tests should be able to detect bugs  
every time they merged code into their master branch. Without automating builds and tests, it's simply not possible to find and fix issues at the rate that's needed for Continuous Delivery.

## Product Architecture

CD isn't just a process improvement problem-it's a highly technical initiative. The design of your CD pipeline should closely reflect the architecture of the product.

For instance, it is of utmost importance to know the strengths and limitations of the product, whether there is a cause of concern if delivered frequently?  
Are there roll-back mechanisms that allow for easy revert of the most recent deployment if things go wrong?

How will environment-specific configurations and deployments be handled?

Is the codebase monolithic? In what way should the application be split into smaller parts, how are these smaller parts deployed and interact with each in runtime etc.

Can the deployment be fully automated? Are there parts of the system that needs manual intervention or manual setup?

With the right investment towards the product architecture, the goal of delivering value to the customer frequency and in small batches increases significantly.

## Summary

In summary, here is a recap of the most important terminologies.

Continuous Integration is a DevOps software development practice that is designed to improve code quality and enable rapid delivery and deployment of code. Code changes are automatically  
built, tested, and prepared for a release to production.

Continuous delivery is an extension of the concept of Continuous Integration. Without CI, you can not have CD. CI deals with the build and tests part of the development cycle for each version,  
CD focuses on what happens with a committed change after that point. With continuous delivery, any commit that passes the automated tests can be considered a valid candidate for release and deployment into the production environment.

In theory, with continuous delivery, you can decide to release daily, weekly, fortnightly, or whatever suits your business requirements. You can release more often, thus accelerating the  
feedback loop with your customers. The complexity of deploying software has been taken away. Your team doesn't have to spend days preparing for a release anymore.

In the next post, we'll go through the preparatory stages of your journey towards Continuous Delivery.

Take Agile to the next level with DevOps. Learn practical tools and techniques in the three-day [DevOps Implementation Boot Camp](https://dzone.com/go?i=299510&u=http%3A%2F%2Ftechtowntraining.com%2Fcourses%2Fdevops-implementation-boot-camp-icp-fdo%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_content%3Dcourse). Brought to you in partnership with [Techtown](https://dzone.com/go?i=299510&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dheader).
