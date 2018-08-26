# The Basics of BDD in Testing

_Captured: 2018-03-29 at 01:17 from [dzone.com](https://dzone.com/articles/the-basics-of-bdd-in-testing?edition=369206&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-28)_

Planning to extract out a few microservices from your monolith? Read this [free guide](https://dzone.com/go?i=265421&u=https%3A%2F%2Ftry.split.io%2Fmonolith-breakup-stateful-services-ebook%3Futm_campaign%3D2018%252520DZone%252520DevOps%26utm_source%3Ddzone%26utm_medium%3Dpre%252520roll) to learn the best practice before you get started.

Everyone likes to get things done their own way, but in software development, it can be helpful to have some guiding principles for the way your organization handles each part of the software development lifecycle.

Opening the conversation and keeping different teams on the same page means that software is shipped seamlessly. Additionally, as these organizations start shifting left, they have to adapt those processes to fit their current workflows.

Let's look at one method that's becoming increasingly popular and discover how it's helping different teams ship state-of-the-art software.

## What Is BDD?

You might be hearing a lot about [Behavior-Driven Development](https://www.agilealliance.org/glossary/bdd/), or BDD, lately. BDD is an extension of Test-Driven Development (TDD) that emphasizes developing features based on a user story and writing code that provides a solution to real problems.

This means that the client or product manager communicates a vision, and the developer then needs to define those behaviors to meet stated business goals. Then, the tester comes in to see if this new feature meets the "why" behind the code.

For example, if a client said they found in their research that they had a lot of older users handling their application and they need a way to make it more accessible, your move as the developer following a BDD model would be to consider how this behavior changes which features you would add to the application - perhaps larger fonts and easily clickable items.

Of course, a big part of BDD is being able to determine what different behaviors mean for the application and requires keeping an open conversation with key players to correctly identify the right additions or fixes.

BDD places a heavy emphasis on team collaboration and cross-functional workflows. Making sure these user stories and behaviors are communicated from the business side to the technical delivery is an integral part of successful BDD.

## Testing and BDD

Like TDD, BDD advocates that tests should be written first, which is good for having high test coverage. In BDD, you're building up an accumulation of acceptance tests, which means that often teams that follow it use [test automation](http://crossbrowsertesting.com/automated-testing) and [CI/CD](http://crossbrowsertesting.com/continuous-integration) tools.

While the misconception of test automation taking testing jobs arises, the BDD mindset further proves the importance of testers in the SDLC. Not only do testers have to make sure the code works, but they also have to consider the problems that it's solving.

This means testing in BDD is testing the functionality of the features as well as the initial behaviors it's being built for. Instead of just thinking about whether a certain function works, testers must think about it in the context of the scenario it's being used in.

## Cucumber

[Cucumber](https://cucumber.io/) is an open source tool that supports BDD. Not to mention, it reached 5 million downloads in its first 3 years, so it's safe to safe it's a popular choice among testers.

By letting contributors define application behavior in plain English through Cucumber's Gherkin language, it's used to communicate with software stakeholders how the application is supposed to act and respond, what behavior defined that, and why.

While the Gherkin text is based on the code in the application, anyone can read and understand it. The purpose of this is to clarify different steps in the development process to everyone involved with the release of the software.

This adds a layer of detail that communicates the benefit of added functionalities to the client in a way that tells them whether or not it meets the original vision and answers business problems with a clear solution.

By keeping the flow of information open as the application reaches different stages in the SDLC, it's easier for anyone involved to pinpoint where someone might have taken a wrong turn and identify which elements may need to be changed.

## The Big Ideas Behind BDD

This is a very high-level understanding of BDD. To learn more about BDD and Cucumber, listen to [The Big Ideas Behind BDD](https://www.youtube.com/watch?v=hQyXgKENDtg&feature=youtu.be) from SmartBear's recent meetup.

If you've been hearing all about the benefits of BDD from your peers and colleagues but don't know where to start in bringing actionable items back to your organization, you'll want to tune in to this recording.

Cucumber co-owner Seb Rose will be your guide in understanding where you and your team stand in the industry shift left, and how you can take the best parts of the BDD process to improve your workflows.

_This article was first published on the [CrossBrowserTesting](https://crossbrowsertesting.com/blog/development/what-is-bdd-cucumber/) blog._

[Learn how](https://dzone.com/go?i=275425&u=https%3A%2F%2Ftry.split.io%2Fmonolith-breakup-stateful-services-ebook%3Futm_campaign%3D2018%25252520DZone%25252520DevOps%26utm_source%3Ddzone%26utm_medium%3Dpre%25252520roll) to measure the impact of every feature release on performance and customer experience metrics.
