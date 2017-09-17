# Testing Automation Without Writing Test Scripts

_Captured: 2017-09-05 at 10:58 from [dzone.com](https://dzone.com/articles/testing-automation-without-writing-test-scripts?oid=twitter&utm_content=buffer776ad&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Download the blueprint](https://dzone.com/go?i=228233&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic's 20+ years of business automation experience, and the proven tools and practices the company is already leveraging.

[This article is featured in the new DZone Guide to Automated Testing. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/automated-testing-improving-application-speed-and)

Like many developers charged with creating browser-based testing for our products, we used   
to start by creating test scripts in a CI tool and writing a bunch of code.

Writing test scripts seemed like a step forward over existing approaches because scripting tools provided good support for the latest browsers. As our projects grew, however, we ran into many challenges, including time-intensive, on-prem setup and maintenance to run test   
"automation" tools, like Selenium or Robot, properly at scale. All the code we had to write and the amount of time engineers had to spend on testing kept on growing.

So, we decided there was room for improvement, and made some key discoveries about how the testing process could be improved. In this article, we will discuss the opportunities we found to improve browser-based testing, specifically the ability to speed up testing execution with cloud-  
based providers targeting multiple browsers, and providing better insight into applications under test.

## Our Initial Challenge

We had several, highly visible projects with low tolerance for bugs and performance issues. Unfortunately, as is often thecase, budget and resources for testing were limited. At the time, there were two options: hire manual testers or try to automate. The manual testing route would be too slow and inaccurate for the number of updates we were pushing, so we decided that we had to figure out a way to automate. We were building JavaScript-heavy applications, and traditional automation tools were both out of date and far too expensive for our needs. Selenium ended up being our choice because of its support for many different browsers, ongoing updates, and cloud-based runtime (as opposed to the outdated Win32/desktop tools on the market).

We were excited to expand our usage of test scripts and built a framework around PageObjects that enabled us to get a high degree of modularity and extend the tests quickly. However, the more we dug into writing our own testing scripts, the more critical shortcomings we discovered in this approach. Ultimately, we embarked on a journey to take our own testing automation to the next level. It's this experience and our results that I would like to share in this article.

## Questioning Assumptions

As we got further down the path of script-based testing automation, we realized that we had been making several false assumptions about the whole process. Specifically, we started to question the following:

  1. Was it actually a good thing that we had to spend so much time coding to create and maintain test cases, especially in a rapidly changing application?

  2. In today's JavaScript-heavy applications with changing contexts, multiple div layers, hovers, mouseovers, asynchronous behavior, callbacks, and more, simple selector-based scripting felt very two-dimensional in a three-dimensional world. Was this really the best we could do?

  3. Execution was slow. Why was testing automation stuck in a pre-cloud, pre-elastic-scaling mode of operation?

  4. Why did we have to write multiple classes in order to target the different browsers we cared about, for the exact same test cases?

  5. We were also having to spend a lot of time creating load and performance tests. Given existing frameworks and cloud services, we were creating multiple instances of the same type of test for the same user workflow, simply to test across functional, load, and performance areas. This seemed odd.

Many more questions occurred to us, but these were the big ones that we felt needed to be solved. We looked at every product on the market, every open source project, and we couldn't find anything that was questioning this set of assumptions in the same way that we were.

## Starting Down a New Path

We had an idea. We knew now that the coding-centric paradigm of script-based testing automation was simply too slow and primitive to scale to the needs of our dev team going forward.

The next step was to reimagine how testing automation should be done. We made a few observations:

  1. You should be able to code but you shouldn't have to code in order to create and maintain test cases.

  2. IT is moving to the cloud and this should include testing.

  3. The cloud enables browser-driven workflows. Testing should be managed via a browser and it should be visual.

  4. The cloud means more than just running on remote servers. It's about elastic scalability, and testing should never be a bottleneck.

  5. Machine learning is democratizing, and it's possible for even small teams to take advantage of it in order to build systems that learn.

  6. Browser and testing automation should be "write once, run anywhere."

With these observations in mind, we had the beginnings of a vision for how a new testing automation practice would look. Selenium still ends up being a part of the final solution -- but our system produces the code, not the developer.

## Workflow Capture

Starting with our #1 observation, that you shouldn't have to code, it became clear that this is a revolutionary concept but that it has been tried many times before. One of the core value propositions of legacy Win32 testing automation platforms was that you don't have to code. The downside is that each user needs their own desktop license since this is on-premise software.

On the other hand, you have many projects that aim to create test cases in the browser, visually. They do a decent job for simple tasks, but their limitations become clear quickly when you start dealing with complex applications. We mentioned some of these challenges above in the "Questioning Assumptions" section but, suffice to say, it was impossible to find any visual recorder technology that let us capture sophisticated user workflows and edit those workflows again without having to re-record everything.

There are, it turns out, multiple ways of capturing user workflows in a novel way but we decided to focus on making recording work as a first step. And, as it also turns out, we massively underestimated how challenging this would be. At the time, we thought it was possible to build a recorder in three months that would handle 80-90% of what we needed.

Three years later, we finally had a tool that worked in the way we envisioned. There were far more edge cases to cover than we had originally imagined. Areas requiring extra attention included accurately capturing mouse position after hover elements were selected, complex navigational menus, and automatically creating modules, similar to PageObjects, during the workflow capture process.

## Cross-Browser Targeting

Another area of difficulty is targeting multiple browsers with a single workflow capture. It is easy to imagine how difficult this is, simply because when you're writing test code, you'll usually do this with entirely separate scripts. Our aim was to abstract this away entirely, providing what we call an Action Log for the entire test case and a browser-specific Action Log for each browser targeted by the test.

An additional hurdle was to enable the ad hoc addition of new browsers to an existing test case, even after the test case had already been created. We were able to extend our Action Log abstraction in this case and enable real-time screenshot and video capture along the way.

## Runtime Execution

As we mentioned above, the whole point of the cloud (in our opinion) is not simply about running tasks on remote servers but also to spin up quickly to scale elastically to any sized workload and then spin back down as soon as the task is complete. This single innovation has revolutionized computing and it was high time for it to revolutionize testing as well.

We were able to achieve this in our project by building a custom runtime scheduler on top of both Google Cloud and Amazon Web Services. Both cloud providers have their advantages and disadvantages. Our runtime scheduler allows our team to kick off a test suite execution of any size, guaranteeing completion in 20 minutes, max. This completely changed the game for us because we were tired of waiting for hours at a time for our test suites to complete on traditional, instance-based models.

## Reporting and Results

Another benefit of cloud-based, visual testing orchestration is that you move away from source code and into data. When you stop thinking in terms of Selenium scripts, you start thinking more about the data and insights you can derive from the testing process and how that might improve things overall. Key things that you can start tracking automatically are the number of test cases created by different engineers, how often tests fail (again by engineer), isolating systemic problems faster by categorizing test cases by modules, and more.

## Integrations

The future of cloud applications in general is integration, and the same is true of testing automation as well. The most important integration to get right is with a good continuous integration (CI) tool, such as Jenkins, CircleCI, or any number of options. One of the things we realized, however, was that there is still some bureaucracy in many IT departments in getting even simple integrations such as CI set up, so we also built and included a mini-CI tool inside our new platform. This allows end users and developers to quickly run an entire suite of tests and we included webhook-based APIs as well in order to provide lightweight programmatic access.

Other important integrations include repositories such as Github, alerting tools such as PagerDuty, and chat tools like Slack.

## Machine Learning Opportunities

The final big opportunity we found in our research was, again, tied to this shift away from a source code-centric model to a data-driven approach, which the cloud helps facilitate. There is a ton of data created by the testing automation process and it is a shame that so little of it is properly exploited in the code-driven model.

What we view as the holy grail for testing automation is a platform that can learn on its own from rapidly changing applications and adapt tests to those changes. This is a long road, even given current technology, but this is the big opportunity for the industry.

## Results So Far and Next Steps

In our experience with this new approach, we've had a lot of successes as well as many lessons learned. The biggest benefit we've seen so far has been in a dramatic reduction in time spent on creating and maintaining test cases. Developer teams that we've worked with on this thus far love this aspect: creating a new test case goes from a matter of hours or even days to something they can create in minutes. Updating a test case is something that can done in 5 minutes or less.

Going forward, one of our bigger challenges is in helping quality engineering teams to see the benefits they can derive from a data-driven approach and a move beyond testing scripts as the core technology in the stack of testing automation. Full-stack testing automation is the future as far as we are concerned and our goal is to help as many teams as possible realize this vision.

[This article is featured in the new DZone Guide to Automated Testing.](https://dzone.com/guides/automated-testing-improving-application-speed-and)[Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/automated-testing-improving-application-speed-and)

[Download](https://dzone.com/go?i=228234&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) the 'Practical Blueprint to Continuous Delivery' to learn how Automic Release Automation can help you begin or continue your company's digital transformation.
