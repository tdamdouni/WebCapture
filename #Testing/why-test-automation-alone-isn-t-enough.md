# Why Test Automation Alone Isn't Enough

_Captured: 2017-11-12 at 11:22 from [dzone.com](https://dzone.com/articles/why-test-automation-alone-isnt-enough?edition=334864&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-10)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

There is no doubt that it is an exciting time to be in testing. Over the past few years, testing has lagged in the adoption of agile practices, but over the last year, we've quickly seen things change. The conversation is no longer about manual vs. automated testing, but how I can do automated testing correctly? "Correctly" being the core word. When most people think about automated testing they think about buying a tool that will auto-run the tests. But that is a very limited perspective that delivers limited results. Why? Because what we're actually talking about is not simply how to automate tests but how to innovate faster and get changes into production faster without impacting the business, especially when dealing with mission-critical enterprise applications.

The first thing I tell clients is that they need to think differently about testing and automation. Testing needs to be prioritized and driven by what drives the business and automation needs to become the first option looked at for all activities across the cycle.

Consider the typical lifecycle of an enterprise application project:

![](https://www.worksoft.com/wp-content/uploads/2017/11/image-1.png)

> _What are the key activities that need to happen along the way?_

  * Document existing business processes
  * Evaluate the impact of change requests
  * Prioritize testing based on business impact
  * Create test cases
  * Get test data
  * Run test cases
  * Update ALM system with results
  * Produce required compliance reports

Which of the above can you automate? ALL OF THE ABOVE!

This is where we need to RETHINK automation. Typically, when we think of automation, we think of a very linear process. First, we write the test requirements, then the documents are created, then somebody goes and creates the automation, then someone runs it. Even within most agile environments, the creation of test automation is still a very linear process. But what if we stop thinking linearly? What if we think about how we can use automation to do more things in parallel and how automation can be used to then create additional automation.

![](https://www.worksoft.com/wp-content/uploads/2017/11/image2.png)

## RETHINK Automation - Automate From the START

End-to-end business process testing almost always starts with the identification and documentation of the potentially impacted business processes. For the sake of simplicity, let's put aside the questions of how you identify and determine what the impacted business processes will be and say you know the processes. Now, instead of manually creating a document with written steps, screenshots, and process flowcharts, you instead use automation to auto-generate the written steps, capture the associated screens, and create the visual flow. Because software was used to capture the business processes, the steps are immediately available to be transferred to the QA team to auto-create test cases.

Automated discovery "watches" the user perform the actual steps within a business process either in a production or pre-production system. All the ambiguity due to poor documentation or missing steps has been removed because the actual end-to-end business process was captured using automation. QA now knows exactly what the steps in the business process are. The automation can be hardened/parametrized within hours of receiving the change requests. Customizations can easily be made because now the tester understands exactly what the business is trying to achieve. Impact analysis can be run to predict any upstream/downstream impacts of the change along with current test coverage levels. Operations can consume the automation to run as part of a standard DevOps environment.

Teams can start to work independently of each other and in parallel. The organization is enabled to start building automation faster and at scale. New test cases are auto-generated each time a change to a process is captured and documents and processes maps are kept up to date. Compliance reports are auto-generated at the completion of each test run, validating that no one must perform a bunch of manual things to restart the process. The process is always in play, always in motion, always churning, and that is the way you want it. Now you have built core infrastructure that keeps your automation coming as fast as your organization is changing.

In my next post, I'll talk about how automation in QA can then be transferred to other parts of the organization to enable robotic process automation.

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**
