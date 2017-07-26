# The Ultimate DevOps Tools Ecosystem Tutorial, Part IV: Testing 

_Captured: 2017-01-30 at 22:55 from [dzone.com](https://dzone.com/articles/the-ultimate-devops-tools-ecosystem-tutorial-part-3?edition=266885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-30)_

### This stage requires many different kinds of tests. The data from the tests needs to be managed and analyzed in rich reports to improve the product.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

Welcome to Part IV of our "Ultimate DevOps Tools Ecosystem Tutorial." In this blog post series, we are covering the top DevOps and development process tools. In [Part I](https://dzone.com/articles/the-ultimate-devops-tools-ecosystem-tutorial-part), we introduced the DevOps work cycle. It's divided into five stages: Plan, Develop, Test, Release, and Operate. You can see the complete infographic here:

![devops infographic](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/DevOps-Infographic-v1.4%20690x690.png)

In [Part II,](https://dzone.com/articles/the-ultimate-devops-tools-ecosystem-tutorial-part-1) we covered main tools from the planning stage, and in [Part III](https://dzone.com/articles/the-ultimate-devops-tools-ecosystem-tutorial-part-2), we went over the developing stage. This time, we will go over tools from the testing stage.

Testing examines the product and service and makes sure they work in real time and under different conditions -- even extreme ones, sometimes. This stage requires many different kinds of tests, mainly functional tests, performance or load tests, and service virtualization tests. It's also important to test compatibility and integrations with third-party services. The data from these tests needs to be managed and analyzed in rich reports, for improving the product according to test results.

Here are some of the top tools in the testing stage.

## Load Testing: JMeter

[JMeter](http://jmeter.apache.org/) is the most popular open-source load testing tool. JMeter enables users to create a test scenario that contains the actions and requests they want to test on their website or app. Then, the can modify it according to their business needs with elements like ramp-up time and timers, run it for multiple users, and examine the results.

  * **Pros: **Open-source, easy to use, robust, has a vibrant and involved support and development community, has multiple plugins, and integrates with Continuous Integration tools like Jenkins.

  * **Cons: **Requires downloading, limited scalability, limited reporting, and creating a test scenario can be meticulous. 

![jmeter gui](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/devops41.png)

> _Click here to see a comparison of different open-source load testing tools._

## Load Testing: CA BlazeMeter

CA BlazeMeter has all the abilities JMeter has since it's an [enhanced and upgraded version of JMeter](https://www.blazemeter.com/jmeter-load-testing?utm_source=BM&utm_medium=BM_blog&utm_campaign=ultimate-devops-tools-ecosystem-tutorial-part4).

  * **Pros: **Scalability (JMeter in the cloud), advanced reporting, collaboration options, and multiple plugins and test recording features.

  * **Cons: **Not open-source. 

CA BlazeMeter reports:

![blazemeter gui reports analysis](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/devops42.png)

## Functional Testing: Selenium

Selenium is an open-source functional testing tool that automatically tests browsers and enables the testing of web applications.

  * **Pros: **Open-source, supports a variety of languages, operating systems and browsers, records scripts (through Selenium IDE), and [works with JMeter](https://www.blazemeter.com/blog/jmeter-webdriver-sampler?utm_source=BM&utm_medium=BM_blog&utm_campaign=ultimate-devops-tools-ecosystem-tutorial-part4).

  * **Cons:** Requires high expertise to use, does not support windows based applications, and lacks online support. 

![selenium system](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/devops43.png)

## Functional Testing: Perfecto Mobile

[Perfecto Mobile](https://www.perfectomobile.com/) is a functional testing tool for mobile apps that runs automated app tests on real devices.

  * **Pros:** High optimization and accuracy due to running tests on real devices.

  * **Cons:** Testing speed can be slow.

## Service Virtualization: CA

CA Service Virtualization creates virtual assets that enable developers and teams to work in parallel on their systems without having to write code to duplicate infrastructure or dependencies.

  * **Pros: **Quick setup and integrates with testing and Continuous Integration tools.

  * **Cons: **On-premise and heavy-weight. 

We're more than halfway through the DevOps cycle! Next time, we'll discuss the release stage, so stay with us.

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
