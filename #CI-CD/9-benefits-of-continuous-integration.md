# 9 Benefits of Continuous Integration

_Captured: 2017-02-02 at 04:02 from [dzone.com](https://dzone.com/articles/9-bene-ts-of-continuous-integration?utm_content=buffer5c2b6&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

_[This article is featured in the new DZone Guide to DevOps: Continuous Delivery and Automation, Volume IV. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/devops-continuous-delivery-and-automation)_

Across almost every industry, the best companies are increasingly becoming those who make great software. As a result, software development teams are transforming their software operations to optimize for efficiency, quality, and reliability. Continuous Integration, Continuous Deployment, and Continuous Delivery are increasingly popular topics among modern development teams. Together they enable a team to safely build, test, and deploy their code. These modern development practices help teams release quality code faster and continuously.

## Continuous Integration, Delivery, and Deployment Defined

Continuous Integration is a software development practice in which you build and test software every time a developer pushes code to the application.

For example, let's say developers push code to improve their software projects every day, multiple times per day. For every commit, they use a CI tool to test and build their software. The CI tool will run unit tests to make sure their changes didn't break any other parts of the software. Every push automatically triggers multiple tests. Then if one fails it's much easier to identify where the error is and start working to x it. But for this team, they do not deploy to production, so this is considered Continuous Integration only.

Continuous Delivery is a software engineering approach in which continuous integration, automated testing, and automated deployment capabilities allow software to be developed and deployed rapidly, reliably, and repeatedly with minimal human intervention. Still, the deployment to production is de ned strategically and triggered manually.

[Mozilla](https://quality.mozilla.org/2014/10/continuous-delivery-a-generic-plan/) is a good example of an organization using Continuous Delivery. Mozilla says that for many of their web projects "once a code change lands on a master branch it is shepherded to production with little-to-no human intervention."

Continuous Deployment is a software development practice in which every code change goes through the entire pipeline and is put into production automatically, resulting in many production deployments every day. It does everything that Continuous Delivery does, but the process is fully automated; there's no human intervention at all.

Hubspot, Etsy, and Wealthfront all use continuous deployment to deploy multiple times a day. In 2013, Hubspot reported that they deploy [200-300 times per day](http://product.hubspot.com/blog/how-we-deploy-300-times-a-day). People often assume that continuous deployment only works for web-based software companies, so I'd like to offer another example in a completely different industry: Tesla. Tesla Model S is using continuous deployment to [ship updates to the firmware](http://www.forbes.com/sites/steveblank/2014/01/03/tesla-and-adobe-why-continuous-deployment-may-mean-continuous-customer-disappointment/#44839739364f) on a regular basis. These changes don't simply change the dashboard UI or offer new ways to change console settings in your car, they improve key elements of the car, like acceleration and suspension. Tesla proves that continuous delivery can work for any team committed to the practice.

## 9 Benefits of Continuous Integration

The benefits of Continuous Integration, Delivery, and Deployment are clear. However, the process to building the pipeline to do Continuous Delivery or Deployment isn't always easy. But that doesn't mean you shouldn't do it. We believe that modern development teams are working their way up to Continuous Deployment. That's why we suggest getting started with automated testing through Continuous Integration today. With automated tests on each new commit, Continuous Integration is a great way to increase code quality. Here are our top nine reasons why we think every development team should be doing Continuous Integration.

## 1\. Manual Tests Are Only a Snapshot

How many times have you heard a team member say "it worked locally." In their defense, it likely did work locally. However, when they tested it locally they were testing on a snapshot of your code base and by the time they pushed, things changed. Continuous Integration tests your code against the current state of your code base and always in the same (production-like) environment, so you can spot any integration challenges right away.

## 2\. Increase Your Code Coverage

Think your tests cover most of your code? Well, think again. A CI server can check your code for test coverage. Now, every time you commit something new without any tests, you will feel the shame that comes with having your coverage percentage go down because of your changes. Seeing code coverage increase over time is a motivator for the team to write tests.3. Increase Visibility Across the Team

Continuous Integration inspires transparency and accountability across your team. The results of your tests should be displayed on your build pipeline. If a build passes, that increases the confidence of the team. If it fails, you can easily ask team members to help you determine what may have gone wrong. Just like code review, testing should be a transparent process amongst team members.

## 4\. Deploy Your Code to Production

A CI system can automatically deploy your code to staging or even production if all the tests within a specific branch are green. This is what is formally known as Continuous Deployment. Changes before being merged can be made visible in a dynamic staging environment, and once they are merged these can be deployed directly to a central staging, pre-production, or production environment.

## 5\. Build Stuff Now

All your tests are green and the coverage is good, but you don't handle code that needs to be deployed? No worries! CI servers can also trigger build and compilation processes that will take care of your needs in no time. No more having to sit in front of your terminal waiting for the build to finish, only to have it fail at the last second. You can run any long-running processes as a part of your CI builds and the CI system will notify you if anything goes wrong, even restarting or triggering certain processes if needed.

## 6\. Build Stuff Faster

With parallel build support, you can split your tests and build processes over different machines (VMs/containers), so the total build time will be much shorter than if you ran it locally. This also means you'll consume fewer local resources, so you can continue working on something else while the builds run.

## 7\. Never Ship Broken Code

Using continuous integration means that all code is tested and only merged when all tests pass. Therefore, it's much less likely that your master builds are broken and broken code is shipped to production. In the unlikely event that your master build is broken, let your CI system trigger a warning to all developers: some companies install a little warning light in the office that lights up if this happens!

## 8\. Decrease Code Review Time

You can have your CI and Version Control System communicate with each other and tell you when a merge request is good to merge: the tests have passed and it meets all requirements. In addition, even the difference in code coverage can be reported right in the merge request. This can dramatically reduce the time it takes to review a merge request.

## 9\. Build Repeatable Processes

Today's pace of innovation requires development teams to deliver high-quality software faster than their competition. Modern development teams are building ef cient software delivery engines by creating repeatable processes that standardize development best practices. With automated testing, your code is tested in the same way for every change, so you can trust that every change is tested before it goes to production.

## More DevOps Goodness

_[For more insights on implementing unambiguous code requirements, Continuous Delivery anti-patterns, best practices for microservices and containers, and more, get your free copy of the new DZone Guide to DevOps!](https://dzone.com/guides/devops-continuous-delivery-and-automation)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

### Like This Article? Read More From DZone

Topics:

devops ,continuous integration ,continuous delivery ,continuous deployment ,devops adoption ,autoatmion

Opinions expressed by DZone contributors are their own.
