# Mobile Apps and Continuous Delivery

_Captured: 2017-03-14 at 18:33 from [dzone.com](https://dzone.com/articles/mobile-apps-and-continuous-delivery?edition=283881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-14)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

You can build a Continuous Delivery pipeline for any type of app -- whether it's designed to run on a desktop, mobile device, server, or anything else.

However, that doesn't mean that the Continuous Delivery chain that you create for one category of application will be identical to the one you build for a different type of app. The approach you take to Continuous Delivery will vary significantly depending on what type of device and environment you are delivering for.

Nowhere does this become clearer than in the context of mobile app development. When you're delivering software for mobile devices, the design, testing, deployment and feedback parts of your continuous delivery chain will be quite different than those for desktop or server app delivery.

In this post, we'll take a look at the special considerations you should keep in mind when you are doing Continuous Delivery for mobile.

## What Makes Mobile Different

To understand why Continuous Delivery for mobile apps is different, you have to understand what makes mobile itself different.

Consider the following key differentiators for mobile apps.

### They Run on a Wide Range of Hardware and Software Environments

If you're delivering a desktop or server app, you basically have three operating systems (Windows, Linux, and macOS) to contend with, and your hardware (in at least 90 percent of cases) is going to be plain old x86-based. Sure, exact hardware specifications will vary, but these days, hardware nuances are mostly abstracted away by the OS. Display resolutions fall into a predictable range.

With mobile, however, the game is wildly different. There are only two OSes to worry about -- Android and macOS -- but their versioning changes more frequently than it changes on desktops and servers. Plus, there is something like [24,000](https://qz.com/472767/there-are-now-more-than-24000-different-android-devices/) different mobile devices in existence, each with its own hardware specifications (and that's just counting Android devices). CPUs could be based on x86 chips, some form of ARM, or something else. Screen sizes vary widely. New types of mobile hardware are being released all the time.

### They Are Deployed Automatically

On desktops and servers, users or admins often install and manage software. On mobile apps, installation and updates usually happen in a mostly automated way. The extent that manual user interaction takes place on mobile is usually in the form of a one-click choice to install an app. After that, the installation happens automatically, as do all of the updates and management of the app after it is installed.

### They Can Be Native, Web-Based, or Hybrid

Most desktop and server apps run as either native applications (meaning they are executed locally on the host system) or as web apps delivered through a browser. Mobile apps can work in these ways, but there is also a third popular option: hybrid apps, which combine native functionality with HTML.

You _could_ create a hybrid desktop or server app, but that is a much less common practice.

## Planning a Continuous Delivery Chain for Mobile

The special characteristics of mobile apps outlined above mean that several parts of your Continuous Delivery chain need to be designed differently in order to handle mobile.

Specifically, the following parts of the pipeline require extra attention in order to handle mobile software delivery.

### **Testing**

Testing should be a part of any Continuous Delivery chain -- but with mobile, your testing needs become more complex; for one, because you have to test for so many different hardware and software environments, testing needs to be as automated as possible in order to minimize the possibility of delays that could hinder continuous delivery. For another, you should consider breaking your automated testing into two stages. The first stage should occur early in the pipeline and involve testing on simulated mobile devices since those tests run faster. However, in order to guarantee quality, real-device testing should occur before software is deployed.

### **Multiple Code Branches**

In order to support so many different types of mobile devices and apps that can be native, web-based, or a combination of the two, you'll likely need to maintain multiple code branches -- especially early in the pipeline.

### **Agile Development Frameworks**

Any Continuous Delivery pipeline should be designed with agility in mind -- but with mobile development, agility is especially important. That's because a mobile app that is native today may be refactored to run as a web or hybrid app tomorrow. In order to have the flexibility to migrate to a new type of development framework, you need a highly Agile delivery chain.

### **Automated Deployment**

Any Continuous Delivery pipeline should automate the deployment process, too -- but here again, with mobile, the priority of automated deployment is especially high. You can't rely on users, admins, or anyone else to apply updates manually as part of your mobile app delivery.

The items listed above are best practices for any type of Continuous Delivery pipeline. For mobile, they're more than just best practices. They're essential if you want to deliver mobile apps continuously.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
