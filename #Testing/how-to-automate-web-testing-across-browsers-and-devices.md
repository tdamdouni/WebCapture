# How to Automate Web Testing Across Browsers and Devices

_Captured: 2018-09-07 at 16:13 from [dzone.com](https://dzone.com/articles/how-to-automate-web-testing-across-browsers-and-de?edition=391208&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-09-07)_

Discover how you can [reduce your Kubernetes installation from 22 steps to 1](https://dzone.com/go?i=302533&u=https%3A%2F%2Finfo.mesosphere.com%2Fkubernetes-cheat-sheet-registration-page.html%3Futm_source%3Ddzone%26utm_medium%3Dsyndication%26utm_campaign%3Dsite-ad).

Websites and web applications are crucial to how businesses acquire customers, and a growing number of traditional front- and back-office applications are migrated from desktops to web-based interfaces. As web technologies come with their own challenges, being able to test them is highly critical.

IT landscapes across organizations are becoming increasingly simplified as more applications and services are migrated into a single technology (web-based), but it also comes with some risks:

To deliver a great end-user experience, web applications and websites must work across multiple browsers, browser versions, operating systems, and devices, including mobile. With all the possible combinations, the number of usage scenarios to be tested explodes! One provider of hosted environments for automated web testing, [Sauce Labs](https://saucelabs.com/platforms), has identified more than 2,000 devices and more than 800 browser-OS combinations -- and those are just the most commonly used.

## What to Host -- and What Not to Host -- On Your Own

From a testing perspective, a major challenge presents itself: Is it necessary for your organization to host all the possible combinations of browsers, operating systems, and devices in your own infrastructure to support automated web testing? This would come with additional costs and a massive administrative burden negatively impacting the business case for test automation.

Fortunately, there are several options available for offloading or outsourcing the hosting of test environments.

Whether you need to test your application in a specific version of a browser, do cross-browser testing of a website, or run automated tests on mobile devices, you can utilize one of several cloud-based providers of web automation environments. Examples of providers include:

  * BrowserStack
  * Sauce Labs
  * CrossBrowserTesting

The main differences between these vendors are their pricing model and to what extent they rely on real devices versus emulators.

## Setting Up Hosted Environments for Web Automation

What follows is a walk-through of how to use hosted environments for web automation. Besides access to a provider of hosted environments such as setup only requires a few things: A suite of automated test cases ready to be executed and a service running the test cases. In the following, the test runner service is called the Controller.

Here's how the setup works:

  1. The Controller will contact the environment provider with instructions for how to set up the requested test environment.
  2. Once the environment is set up, the Controller will begin pushing automation commands into the specified browser running in the environment.
  3. The browser is instructed to navigate to the website or web application under test and then it will execute operations as commanded.
  4. The results generated from the automated tests are then collected by the Controller for further inspection or verification.

With this setup, a test team does not have to worry about preparing and maintaining the machines and devices on which the test cases are executed. For example, it is not necessary to purchase, maintain, and charging a bunch of different mobile devices.

![](https://www.leapwork.com/hs-fs/hubfs/Executing%20web%20automation%20with%20hosted%20environments@2x.png?t=1535564083819&width=1034&name=Executing%20web%20automation%20with%20hosted%20environments@2x.png)

> _Figure 1: Executing web automation with hosted environments._

### Selenium-Based Automation

All automation taking place in the hosted environments as described above is based on the open-source framework for automated web testing, Selenium. This means that any test case created with Selenium can be executed in the hosted environments.

Selenium-based test cases can be created either by hand-coding them, or, much more efficiently and scalable, by generating them with an automation tool that uses the Selenium framework as its web automation engine "under the hood." This is the case with the LEAPWORK Automation Platform.

Once an automated test case is running, the Controller feeds Selenium-based commands to the hosted environment in which a browser will perform a test of a website or web application. This is illustrated in Figure 1.

### Specifying the Hosted Environment

Before running an automated test case, the Controller needs to instruct the environment provider to set up the required environment. As mentioned earlier, the combinations of variables for defining the environment are practically endless. Consider the following equation:

Test environment _n_ = Device _a_ × OS _b_ × OS version _c _× Browser _x_ × Browser version _y_ × Screen resolution _z _× ...

The Controller will convey to the provider all information about the variables that define the environment.

## Accessing a Protected System Under Test

If the system under test, e.g. a website, is accessible in the cloud or somewhere else outside a company's firewall, then it usually requires little or no additional configuration for a browser in the hosted environment to access the website.

![](https://www.leapwork.com/hs-fs/hubfs/Direct%20vs%20proxy%20access@2x.png?t=1535564083819&width=866&name=Direct%20vs%20proxy%20access@2x.png)

> _Figure 2: Direct vs. Proxy-Based Access in Web Automation._

However, if you need to test an internal website placed behind a corporate firewall and if Security does not allow opening ports in the firewall, then browsers in hosted environments won't be able to directly access the website under test. In this case, you need to do a bit more configuration of your setup. The additional work required is minimal, so this shouldn't discourage you.

The solution, which is offered by most providers of hosted environments, is for the Controller to serve as a proxy between the internal website and the browser performing the automation commands. In practice, this means that the Controller will open a connection to the hosted environment, and then all traffic from the browser in the hosted environment is sent through the Controller to the internal website and back again. The "Direct Access" and "Proxy-Based Access" setups are illustrated in Figure 2.

## Summary

  * Hosting all the possible combinations of browsers, operating systems, and devices in your own infrastructure to support automated web testing would be very costly and time-consuming.
  * You can utilize cloud-based providers of web automation environments to offload or outsource the burden of hosting.
  * Such a setup involves three elements: A test runner service, the environment provider, and then the website or application being automated.
  * If the system under test is located in the cloud or somewhere else outside a company's firewall, then it is directly accessible for the environment provider. If not, then the system under test can be accessed by using the test runner service as a proxy.

[Download the Kubernetes cheatsheet](https://dzone.com/go?i=302534&u=https%3A%2F%2Finfo.mesosphere.com%2Fkubernetes-cheat-sheet-registration-page.html%3Futm_source%3Ddzone%26utm_medium%3Dsyndication%26utm_campaign%3Dsite-ad) to learn more about easy it is to run Kubernetes on any infrastructure with [Mesosphere DC/OS](https://dzone.com/go?i=302534&u=https%3A%2F%2Finfo.mesosphere.com%2Fkubernetes-cheat-sheet-registration-page.html%3Futm_source%3Ddzone%26utm_medium%3Dsyndication%26utm_campaign%3Dsite-ad)
