# The Value of Feature Flags in CI/CD

_Captured: 2018-09-05 at 20:12 from [dzone.com](https://dzone.com/articles/the-value-of-feature-flags-in-cicd?edition=391198&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-09-05)_

Easily enforce open source policies in real time and reduce MTTRs from six weeks to six seconds with the Sonatype Nexus Platform. See for yourself - [Free Vulnerability Scanner.](https://dzone.com/go?i=290455&u=https%3A%2F%2Fwww.sonatype.com%2Fsoftware-bill-of-materials%3Futm_campaign%3Ddzone%252520-%252520AHC%26utm_source%3DDZone%252520-%252520AHC%2525202018%26utm_medium%3DDZone%252520-%252520AHC%2525202018)

Using [feature flags](https://rollout.io/blog/feature-flags-as-a-service/) is a technique that will help you integrate code into a shared repository at least once a day and ship it, even if you haven't finished the feature yet. You'll be able to deploy at any time but defer the decision to release for another day. [Continuous integration](https://www.thoughtworks.com/es/continuous-integration) (CI) and [continuous delivery](https://www.thoughtworks.com/continuous-delivery) (CD) are practices that could help you deliver software more quickly.

With CI, you start by integrating code changes into a shared repository several times a day. Then you continue with CD to deliver working software to the customer's hands -- even if it's not done yet. (More on this later.) You get feedback often, so you're able to improve things sooner. But you also get better at releasing software because it becomes a natural skill.

So how do CI/CD practices help you deliver software more quickly? First, it takes time and a lot of discipline. And second, there are processes, tools, and techniques that influence the success of CI/CD practices. This week we'll take a look at how feature flags will help you to integrate code and ship software more frequently.

## Continuous Integration With Feature Flags

[CI](https://martinfowler.com/articles/continuousIntegration.html) is a practice where developers integrate their code frequently (at least once per day) to a shared repository. An integration system then automatically verifies the integrated code. CI helps developers spot problems early in the process of delivering features to customers. As the developer team grows, it becomes more complicated to integrate everyone's code. Feature flags will let you switch off a portion of code that's causing problems after being integrated.

There are three questions that will help you certify CI. ([Jez Humble](https://twitter.com/jezhumble), who [came up with them](https://martinfowler.com/bliki/ContinuousIntegrationCertification.html), asks them every time he talks about CI at a conference.)

  * Are developers committing at least once a day to a shared mainline (aka master branch in Git)?
  * Do you have a trigger in place to automatically build and test the software after a code commit?
  * Is the team applying fixes within ten minutes if the automated build and tests fail?

Now, these questions imply that you'll be doing simple things, but in practice, it's a different story. That's mostly because it takes a lot of discipline to get it right, and having pressure from upper management doesn't help. Implementing feature flags will make a difference in certifying CI because, with feature flags, you'll be able to answer "yes" to the first and third questions more quickly and easily.

### Integrate Half-Finished Work to the Master Branch

Developers will always be interrupted, either because priorities/requirements change or something goes wrong in production. The first reason could be prevented in some cases by working in short sprints. The second one is more difficult to control, simply because there could be scenarios we didn't consider. But a reliable battery of tests could reduce these types of interruptions.

So let's set a foundational assumption: just acknowledge that you _will_ experience interruptions. The team can respond by following [a pre-established plan.](http://agilemanifesto.org/)

When a developer is working on something that will take more than a day or it's too risky to deploy all the changes at once, then using feature flags makes sense. It won't matter if the developer needs switch tasks-the feature will always be "off" by default if it's incomplete work, so there's no chance of a rollback occurring. Having portions of code that can be enabled/disabled will allow developers to push their code to the master branch more frequently. Clients won't notice there's something new until it's completed and enabled in the environment.

### Keep Your Master Branch Healthy and Free of Broken Code

I just talked about how to integrate code more frequently, but there's always a chance that things could go wrong...and, to be perfectly honest, they will. Having a reliable battery in CI will identify portions of the code that are not doing what's expected. If a developer is in a situation where the code is broken, there are two options. One is to check what's wrong and apply a fix if the solution is simple. And the second is to defer the fix for a later time by disabling the portion of code that's causing the problem.

We're coming from a foundation where developers integrate code frequently, so the scope of what could be causing problems is small. The best option is to fix the problem right away. But that's not always possible. Let's say there's another developer who urgently needs to push their code to production. If the fix is more complicated than expected, that developer won't have time to wait around while you try to fix the problem. In those cases, you can use feature flags to disable the code and keep the master branch healthy, without broken code in it.

## Continous Delivery With Feature Flags

[CD](https://continuousdelivery.com/) is a practice to deliver changes to the customer's hands frequently, steadily, and predictably. The types of changes you deliver with CD can be anything from a simple configuration change to an entirely new feature to a bug fix. The important thing is to treat every change equally, meaning that even if it's an emergency, you'll avoid doing things out of the scope of the CD pipeline. And feature flags will help with this because, even when a change is live, you could always disable it and stop the bleeding.

Remember how I discussed earlier, in the CI section, that you should fix a problem within ten minutes of a failure? Well, with feature flags this is possible not just when integrating the code but also when deploying or releasing a change. There are times where problems are not evident immediately, so you might not want to delete feature flags right away.

There's a short, fantastic talk from [Martin Fowler](https://martinfowler.com/) about CD that I highly [recommend you watch](https://www.youtube.com/watch?v=aoMfbgF2D_4). In it, he lists the benefits of CD, which are that it

  * Reduces the risk of deployments and releases by doing them more frequently.
  * Gets real progress because you deliver changes in small batches.
  * Gets user feedback by making available the new features as soon as it's finished.

CD by itself is a powerful practice, but it gets better when you integrate it with feature flags.

### Improving Your Deployment Strategy

When you integrate [feature flags](https://rollout.io/blog/top-5-use-cases-feature-flags/) into your CD pipeline, the [deployment strategy](https://rollout.io/blog/deployment-strategy/) you choose only gets better. You could apply the same principles of releasing a feature in the same way as [blue/green ](https://rollout.io/blog/blue-green-deployment/)or [canary](https://rollout.io/blog/canary-deployment/) deployments. Initially, a feature could be visible by just a portion of users so that you get the chance to prove that it's working correctly with real users. By using feature flags, you're separating the moment of deployment from release. I'll talk more about this in the next section.

As I said before, things could always go wrong during deployment, even if you have a good strategy in place. No matter how gracefully you do rollbacks, they're going to take time. And depending on which system you have, time could impact a company's revenue. I once worked with a pay-per-click system, and every time the system was down we were losing money.

Feature flags increase confidence when delivering software because you'll always have the ability to turn features off.

### Deferring the Decision to Release a Deployed Feature

An essential aspect of CD is that you'll always be ready to deliver something, even if it's not finished. You could deploy something that's not ready to be used, and release it after a few iterations with the intention of improving it. Remember that the aim of CD is not to accumulate changes. The purpose of CD is to deliver something small on a frequent basis. Knowing the difference between deploy and release time is critical because feature flags help you at the time of release.

Releasing a feature shouldn't be a technical decision. You could be deploying partial or complete features, and the choice of when to release them should belong to someone in marketing or management. You give them the chance to say "Hey, let's see how our users react to this new feature." Feature flags allow you to experiment with more confidence and not worry about having to change infrastructure or code if you want to enable or disable a feature.

## Get Ready to Ship After Every Code Push

And that's it. Feature flags enable you to be ready to ship what you've done during the day to a production environment. That's why you've heard that some companies are doing several deployments a day. It doesn't mean that each deployment is a new feature for the customers. It just means that deployments will become less tedious and stressful because you'll deploy more frequently.

CI/CD aren't practices that you could successfully implement overnight; it takes time and discipline. But I've shown you some ways that feature flags add significant value to any CI/CD pipelines. Having the option to rapidly roll out or roll back any change will help you focus on what's important: providing value to your customers.

Automate open source governance at scale across the entire software supply chain with the Nexus Platform. [Learn more.](https://dzone.com/go?i=290456&u=https%3A%2F%2Fwww.sonatype.com%2Fwp-enforce-open-source-policies-with-confidence)
