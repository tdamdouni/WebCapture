# Points of View to Consider When Switching to Automated Testing

_Captured: 2017-02-10 at 19:29 from [dzone.com](https://dzone.com/articles/approaching-to-needs-for-an-automated-test-platfor?edition=268937&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-10)_

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

The term "automated test platform" refers to the infrastructure, tools, applications, and software that can be used to include automated tests (usually functional tests) in the [Continuous Delivery](https://en.wikipedia.org/wiki/Continuous_delivery) pipeline.

There are different ways to set up an automated test platform, such as with products like [Extensive Testing](http://www.extensivetesting.org/), [ATestingP](http://atestingp.sourceforge.net/), [SmartBear](https://smartbear.com/), etc. On the other hand, you can build your custom platform integrating [test management tools](https://en.wikipedia.org/wiki/Test_management_tools) in your Continuous Integration (CI) process.

The aim of this article is not to compare different products but to provide a simplified explanation based on the checklist that an automated test platform must have -- a list of features you should think about when you are thinking about doing automate testing.

## User Point of View

You must integrate different actors. The tools to be used have to be adaptable for the different kind of users.

  * **QA: **Management of use cases, test cases, test plans, etc.
  * **Developers and testers: **Test case implementation.
  * **DevOps: **Integration with the CD pipeline.
  * **Managers: **Reports, reports... and more reports.

## Tester Point of View

First of all, tests have to be [robust](https://en.wikipedia.org/wiki/Robustness_%28computer_science%29) and [stable](https://en.wikipedia.org/wiki/Stability_Model). Test implementation also must have the following qualities:

  * An **easy learning curve** for new developers.
  * **Ease of development.**
  * **Ease of maintenance.** Be ready for changes. 
  * **Portability. **Tests have to be easy to execute when developing, the same way as they will be executed automatically by the automated platform. 

## Execution Point of View

Here, we are thinking about the ability to execute a test with different configurations and easy integration with deployment tools and Continuous Integration.

  * **Adaptability. **Integrate different testing assets, such as desktop applications, web applications, mobile applications, services, etc. It must be able to support different tools and programming languages (i.e., SikuliX, WebDriver (Selenium), JMeter, SoapUI, etc.) and be adaptable to the needs of each test.
  * **Configuration flexibility. **The environment of the execution should be configurable (parametrizable). Execute the same test with different parameters, different runtime environments, different application properties, etc.
  * **Parallelization. **It must be "fast enough" to be integrated into a CD. Run parallel tests for different versions of the product. For example, if we need to do two releases at once (for example, a patch and an upgrade), the test platform should not be the bottleneck.
  * **Scalability. **Test cases can grow, but the total execution time should be maintained.
  * **Availability.** The platform must have at least the same criticality as the rest of the tools that allow us to obtain a CD.
![Image title](https://dzone.com/storage/temp/4251380-automatedplatform.jpg)

## Reporting Point of View

Finally, we have to think about monitoring the executions and in the generation of reports. Consider the following qualities:

  * **Capable of sending email reports and alerts.**
  * **Traceability. **There should visibility of the executions over the different environments in production (i.e., versioning tests, test plans, etc.). The tests have to follow the same versions that you have in your product.
  * **Diagnostic.** Easily diagnose issues, because the reason for having automated tests is to find issues and to make finding issues easy (you should have logs!).
  * **History. **You should have a historical repository of executions with details.
  * **Customizable reporting. **This includes custom reports, testing coverage between versions, measuring product performance between versions, and comparing different test executions over different software and product versions.

As I said, this is a simplified explanation, but I hope this list is helpful as a checkpoint for automated test platform requirements.

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
