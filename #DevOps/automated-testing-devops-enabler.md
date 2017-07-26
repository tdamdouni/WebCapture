# Automated Testing: DevOps Enabler 

_Captured: 2017-03-14 at 10:53 from [dzone.com](https://dzone.com/articles/automated-testing-devops-enabler?oid=twitter&utm_content=bufferee73f&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

"Automate everything you can." This DevOps principle propels automated testing into a primary enabling position for any organization that embarks on a DevOps journey. It's no longer an option, no longer something we _should_ do. Either we automate testing or the bright promise of DevOps will remain out of reach.

In this article, we will examine the multiple ways that automated testing is the lynchpin that enables the flow of software through the DevOps pipeline. We will see how it changes -- but does not eliminate -- manual testing. (After all, "everything you can" is not everything.)

## What DevOps Is and Is Not

This article builds on the foundation we laid in the prior one, [What DevOps Is and Is Not](http://techtowntraining.com/blog/2017/what-devops-is-and-is-not/). If you have not yet read that article, I recommend that you do so now.

OK. With that under our belts, let's talk about automated testing.

## Automate Everything You Can

It should be clear that when we say "automate everything you can," automated testing is included. Most development shops recognize that test automation would be valuable for them, but many haven't found a way to get past the cost of the investment.

With DevOps, test automation is no longer optional. The value we get from automating most of our testing is necessary to achieving the promises of DevOps: innovation and speed combined with Operational Stability.

Let's look at Gene Kim's three ways to see why automated testing is necessary to each. (If you are not familiar with Gene Kim's three ways, then you really _do_ need to read the prior article referenced above.)

## The First Way: Flow

When we think about the left-to-right Flow described by the First Way, we think mainly about the flow of software from Dev to Ops.

In their book _Continuous Delivery_, Jez Humble and David Farley visualized this flow as a Deployment Pipeline.

![Image title](https://dzone.com/storage/temp/4588450-screen-shot-2017-03-09-at-13757-pm.png)

This pipeline is a value stream of activities that kicks off every time any developer commits (checks in) a change. (Note that the pipeline graphic from the _Continuous Delivery_ book pictured above is prototypical, and each organization's pipeline would likely be different from what is pictured.)

In keeping with the objectives of the first way, release candidates should flow through the pipeline quickly:

  * Humble and Farley specify that the commit stage where all of the basic checking takes place should ideally complete in about five minutes, and under no circumstances should it take more than 10 minutes. Clearly, to achieve that goal, the unit testing that is part of that stage must be fully automated.
  * In the next two stages, they explicitly specify automated testing and say that each of them should take no more than an hour or so.
  * Next, they show a manual testing stage. (Not all organizations have a manual testing stage in their deployment pipelines.) With all of the automated testing that has preceded this stage, it is clear that manual testing would not represent an extended period of time

There are two prominent features of the deployment pipeline:

  * Automation is necessary in order to move release candidates through the pipeline in a reasonable amount of time. Achieving flow (the objective of the first way) requires automation of as much of the pipeline as we can.
  * Testing is a prominent part of every stage of the pipeline right up to release -- test followed by test followed by test!

Although other parts of the deployment pipeline must also be automated, automated testing is what makes it work. If testing is manual, flow cannot be achieved.

## The Second Way: Feedback

The _Continuous Delivery_ book shows another view of the deployment pipeline in the form of the Sequence Diagram below.

![Image title](https://dzone.com/storage/temp/4588453-screen-shot-2017-03-09-at-13948-pm.png)

This view makes it clear that a release candidate progresses through the pipeline only if it passes all tests and other checks. Any fail ends the journey of that release candidate. The development team must make any changes needed to fix the problem and check them in, creating a new release candidate and starting the pipeline over again.

This sequence diagram also clarifies that each stage of the pipeline provides feedback to the development team, pass or fail. And that feedback comes quickly. The developer sees the results of the automated build and unit test within five to ten minutes (enough time to get a cup of coffee, but not enough time to have begun working on something else). The feedback from the other test phases comes within an hour or two.

This sort of fast feedback on the quality and correctness of the developers' work can only be achieved with automated tests.

## The Third Way: Continual Learning

Automated testing doesn't just enable flow and feedback; it also provides a key input for continual learning and continual improvement. That is because the third way represents a completely new attitude toward failures of all kinds, including the defects that are (or should have been) found in tests.

Every defect that our testing uncovers will trigger more than just a fix. It will also be an opportunity for the development team to learn. "What mistake was made that resulted in that defect?" and "How could we improve our engineering or coding practices to prevent that sort of mistake in the future?" As we embrace the third way, our development team will be making fewer and fewer mistakes, meaning there will be fewer defects to find and more release candidates that pass the tests.

It is not just the developers who benefit. Any defect that escapes testing gives us the opportunity to improve our testing. When a defect is found in Automated Acceptance testing, we ask, "How did it escape detection in Unit Testing? How can we improve our Unit Tests to catch that sort of defect in the future?" When it is found in manual testing, we ask how it escaped detection in the automated testing and how we can improve automated testing. Of course, when a defect makes it to the actual users, we don't just fix it. We also look carefully at all of the testing in our deployment pipeline and make changes to be sure that sort of defect is never missed again.

We can do this sort of introspection and learning because as we automate everything we can, we free ourselves from manual drudgery, and the time we save can be reinvested in process improvement. As most of us well know, when testing is manual, there is little time to think about getting better!

## Automated vs. Manual Testing in DevOps

Some kinds of testing must be manual because a person needs to evaluate the results. Demonstrations, user acceptance, and usability are some examples. The majority of software testing can be automated -- checking technical goodness, verifying requirements have been met (both functional and most non-functional), looking for security holes, and much more.

Any testing we can automate, we should automate. As we do, we will experience more and more DevOps benefits.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).

### Like This Article? Read More From DZone
