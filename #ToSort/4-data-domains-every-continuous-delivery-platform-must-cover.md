# 4 Data Domains Every Continuous Delivery Platform Must Cover

_Captured: 2017-03-11 at 10:05 from [dzone.com](https://dzone.com/articles/4-data-domains-every-continuous-delivery-platform?oid=twitter&utm_content=buffer07843&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

Transitioning towards Continuous Delivery involves a combination of people, processes, and tooling. While no tool in the world -- even the ones with the shiniest pipeline view -- will bring Continuous Delivery by itself, it is important to ensure your CD platform has the functionality to support true end-to-end Continuous Delivery.

> "The ability to independently manage the four data domains and then bring the what, why, where, and how together at deployment run time is key for a high performance CD platform."

The key to achieving Continuous Delivery is your chosen solution's ability to handle the four equally important key data domains required for effective end-to-end CD pipeline management. These domains cover the what, why, where, and how of every release.

![© 2017 Benny Van de Sompele](https://dzone.com/storage/temp/4581960-screen-shot-2017-03-08-at-105541.png)

> _(C) 2017 Benny Van de Sompele_

## **1\. Release Data Model = The Why**

The "why" is the shiny part for most organizations that encompasses defining, planning, executing, and monitoring your various release cycles, release phases, and release delivery resources. The ability to map and measure what each release cycle is contributing to the Continuous Delivery of changes is crucial.

This data model should be very flexible: able to cope with short agile release cycles of only a few days, as well as major release cycles of a few weeks. You also need to be able to group releases into release trains in order to coordinate bigger releases that have more integrated elements, dependencies, or enterprise-wide components.

To ensure every team member and release stakeholder understands the exact status of any release, the CD platform should visualize the CD pipeline from both a technical and business relevant point of view.

## **2\. Artifact Data Model = The What**

The application artifacts is still a blind spot in many organizations. DevOps and CD best practices dictate that artifacts should be under full lifecycle management and usage should be tracked and traced throughout.

Gaining control of artifacts includes defining, managing, and mapping the various artifact types, which are produced by the various stakeholders. These can be pure code build artifacts (JARs, EARs, SQL files), deployable component artifacts (images, containers), environment artifacts (config files, properties), and test artifacts (generated test data, test scripts, test execution lists). Less obvious types of artifacts must also be part of the same data model such as security (certificates), monitoring, and workload artifacts.

## **3\. Environment Data Model = The Where**

The "where" of environment models are an ongoing struggle in many organizations. This includes defining, managing, and changing the infrastructure used within each environment along the release life cycle and understanding which endpoint or configuration item is used for which role in the architecture of the application.

While most organizations can work well with relatively static physical/virtual/cloud environments, few are ready to work with truly dynamic environments which are provisioned and decommissioned on-the-fly as needed along the CD pipeline. Microservices and containerized components, combined with canary deployments, are further challenging organizations to remain in control of the running environment instances.

## **4\. Process Automation Data Model = The How**

This is the comfort zone for most enterprises. Using process automation tools (open source, deployment automation tools, scripts, and sometimes even CI tools), most organizations have the capability to perform fully-automated zero/one/few-click deployments to at least some environments. With PaaS platforms and cloud-native application architectures, the process automation is becoming more simple and straightforward. What matters most for this data model is the capability to map which automation process is required for the deployment of what type of artifact.

## Agnostic Data Models

A comprehensive CD platform must bring all these four data domains together whenever application content (what) needs to be released (why) onto some infrastructure (where) using automated deployment steps (how). Only when each of these domains can be managed and maintained completely agnostic and evolve independently from each other, will you have a dependable, robust, dynamic CD platform that can evolve over time and delivers the lowest Total Cost of Ownership possible.

It is key that the [CD platform](http://www.ca.com/us/products/ca-release-automation.html) has the out of the box ability to glue the "agnostic" data domains together at run time. Failing to treat those data models agnostic from each other will result in a much higher effort (cost) for managing and maintaining that data over time as people will have to ensure the dependencies between the data models are not broken or impacted when something changes in one of the domains.

## Analyzing Your Continuous Delivery Data Domains

Rather than performing a pure features and functions tools analysis for your CD landscape, do an evaluation to assess where the master for each data model resides. How agnostic are each of the four data domains from each other? How do those four separate parts of the Continuous Delivery data model come together "at run time?"

Do the review and validate what it would take if one of your development teams would introduce a complete new artifact type, asking these questions:

  * Where do you go to define that "master" artifact type?
  * How do you ensure you can map it to a relevant deployment step and attach the right deployment automation process?
  * How do you define which infrastructure roles in your application architecture need to be provisioned with any new artifacts of that type?
  * How will the business stakeholders be informed that their request (which required that new artifact type) has now been delivered into production?

Repeat this analysis from the environment dimension and from the release dimension.

It is a simple analysis, but it provides so much insight on your enablement and readiness for end-to-end Continuous Delivery.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

### Like This Article? Read More From DZone
