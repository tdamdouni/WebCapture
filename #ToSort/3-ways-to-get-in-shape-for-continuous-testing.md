# 3 Ways to Get in Shape for Continuous Testing

_Captured: 2017-05-05 at 16:21 from [dzone.com](https://dzone.com/articles/3-ways-to-get-in-shape-for-continuous-testing?oid=twitter&utm_content=buffer014ff&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

![Image title](https://dzone.com/storage/temp/5078233-3waysto.jpg)

No pain, no gain! Achieving Continuous Testing shouldn't take a "[Hans and Franz](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0ahUKEwjL3-yg2oHTAhVLs1QKHTYQBRgQtwIIJDAB&url=http%3A%2F%2Fwww.nbc.com%2Fsaturday-night-live%2Fvideo%2Fpumping-up-with-hans-and-franz%2Fn10121&usg=AFQjCNH8W234jsLK37YcC9tADp_fNIAYlQ&sig2=Ycs3VfLdA7_4nrYXDB_3-g)" attitude. It should be painless, more like a natural progression from implementing certain practices over time.

Testing continuously throughout the SDLC (Software Development Life Cycle) means [you're not thinking about testing as a phase or as an event](http://softwaretesting.cioreview.com/cxoinsight/to-shift-left-or-to-shift-right-continuous-testing-is-everyone-s-responsibility-nid-23923-cid-112.html). It means every asset created as part of the SDLC, regardless of whom it was created by, must be tested.

If a developer creates a method, that has to be tested at the unit level, and then at the integration level, as that method interacts with other components. And that's [where manual testing becomes a bottleneck](https://dzone.com/articles/continuous-delivery-youre-doing-it-wrong). In a fast-paced, agile development environment, if those simple tests are not automated nor triggered by a CI (Continuous Integration) agent for unattended execution, that means code development is being slowed down.

Similarly, if a tester is creating a functional test case to test a story from the backlog, and that test case is manual, it means someone has to manually execute it within the sprint. Again, a manual testing approach means the testing team will continue to be seen as slow. Developers need immediate feedback - "in-sprint" - not just at the unit level, but also at the story level. That can only be accomplished if functional tests are created in an automated fashion from the beginning, not after the sprint is completed, as it is traditionally done.

So how do you get in shape for taking up the Continuous Testing challenge?

## **1\. Be Smarter With Requirements**

Is your team still capturing requirements in a textual form? If yes, then the team is working too hard. Instead, [requirements should be captured in a visual form](https://dzone.com/articles/better-code-for-better-requirements), such as a flowchart. With the expected behavior of the application (including business rules) modeled in a diagram format, it becomes easy to identify all the possible paths and permutations in a mathematical way. Each of these paths and permutations represents a test case. That means test coverage can be accurately calculated and optimally defined, based on risk.

So, what does that mean? It means that as you're visually modeling the requirement you are finding many [missing requirements conditions you hadn't considered](https://www.linkedin.com/pulse/death-star-ambiguous-requirements-issue-alex-martins?trk=mp-author-card), identifying gaps and clarifying ambiguities, all of which will cause defects to be entered in the application code. This is a required warm-up exercise to start down the Continuous Testing journey so you [truly shift all the way to the left](https://www.linkedin.com/pulse/death-star-ambiguous-requirements-issue-alex-martins?trk=mp-author-card). Otherwise, you'll get stuck on making improvements only in the Development discipline, not the entire SDLC.

## **2\. Practice TDD - Test-Driven Development**

With requirements having the form of a diagram, technology is able to tell developers what tests they should be coding for. This optimization essentially removes the burden from developers to have to read requirements or user stories in a textual format, interpret them and then think about tests so they can start coding for those tests to pass.

By automatically modeling these business processes, hours of time and effort can be saved on the already overloaded list of tasks a developer has to complete on a daily basis. This also puts a focus on writing only the application code that is necessary to fulfill that particular requirement, as opposed to writing unnecessary code for that sprint to be completed.

Lastly, with the requirement being the diagram, it becomes easier for the developer to visualize the interfaces that are required for her code to work. For example, if the user story in scope needs to make a call to a third-party API and it is not available, the developer can [virtualize that API](http://servicevirtualization.com/tired-depending-others-api-testing-service-virtualization-rescue/) so she can write her code to realize the user story assigned to her, without having to wait for that third-party API to be available. Once it becomes available, the developer's code will be ready and only a quick integration test will be required, which would've been automated already when the virtual API was defined.

## **3\. Test Automation**

Traditionally, "Test Automation" has been a term used to describe Functional Test Automation performed by the Testing or QA team members. This Functional Test Automation actually meant automating the execution of the test. The actual creation of the automated script, in whatever scripting language, was still a manual task (i.e. someone had to manually write the code to automate a test).

In today's world, however, Test Automation refers to any automation performed on any testing-related tasks, regardless of by whom. That includes unit tests developers create, API tests, end-to-end tests, security tests, performance tests and the list goes on. The caveat is that Test Automation now must include the generation of the automated script, not just its execution.

This understanding is essential. Think for a moment of what this means. By automatically generating the automated script code and automatically triggering its execution, fully unattended and hands-off, you are truly enabling a [continuous testing state](https://www.linkedin.com/pulse/continuous-testing-same-test-automation-alex-martins-1).

If you have to manually intervene in the automated execution, you don't have, by definition, a continuous test execution. You're semi-automated at best, since you have to stop, do something, watch the outcome, and enable the execution to continue. That is not good enough in a fully automated [Continuous Delivery](https://dzone.com/articles/continuous-delivery-youre-doing-it-wrong) pipeline, where your organization is delivering code to your end users much more frequently and with better quality.

## **No Need to Sweat**

Sounds like too much for you? It really is simpler than you'd think because you're not improving the three areas at once, you're doing that over time as you're educating your team and organization, getting buy-in from all stakeholders and gaining their trust by showing small positive results iteration after iteration. And [if others have done it, so can you](https://www.ca.com/content/dam/ca/us/files/supportingpieces/third-annual-devops-virtual-summit-agenda-for-ca.com.pdf)!

So, don't sweat it, jump on that Continuous Testing treadmill, start slowly and keep on cranking up the speed with the little wins that will happen week after week. In a couple of iterations, you'll be running without breaking a sweat, and be in shape to support your organization's [DevOps initiative](https://www.linkedin.com/pulse/secret-getting-your-organization-embrace-devops-why-alex-martins?trk=mp-author-card) and the goal to transform to a [continuous and modern software factory](https://devops.com/cd-101-podcast-build-modern-software-factory-agile-development-continuous-delivery/).

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
