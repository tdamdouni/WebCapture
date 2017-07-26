# Web CMS Architectures: Coupled, Decoupled, or Headless?

_Captured: 2017-03-22 at 00:18 from [dzone.com](https://dzone.com/articles/web-cms-architectures-coupled-decoupled-or-headles?edition=286887&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-21)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

Generally speaking, there are two main types of Web/Experience Content Management System (CMS) architectures: **coupled** and **decoupled**. Historically the term "coupled" has referred to the relationship between the authoring tools and content delivery of your live site. With the introduction of **headless** CMS platforms, the landscape has become a bit more complicated. Are headless CMS's the new decoupled CMS? Let's explore.

## Headless CMS 

Headless CMS technology provides content to the presentation tier (or content consumer) as a service, typically via a RESTful interface in JSON or XML format. This is known as Content as a Service (CaaS.)

![](http://blog.craftercms.org/wp-content/uploads/2017/03/headless-cms.jpg)

The main advantage of a headless CMS (CaaS) architecture is that content is written and published once but can be requested and presented uniquely by any number of different channels/content consumers.

## Coupled vs Decoupled

The classic example of a coupled CMS architecture is a blog engine. In a coupled system, the underlying store for your content serves both authoring and delivery. Your authoring capabilities are part of the live delivery system but are available only to those who have permissions. In a coupled system, the process of making content live is typically a matter of setting a flag in the database.

![](http://blog.craftercms.org/wp-content/uploads/2017/03/coupled-cms-1.jpg)

A decoupled system, by contrast, is one that puts authoring and delivery in separate applications, and potentially, on separate infrastructure. In a decoupled system, the process of making content live is done through a publishing mechanism where content is pushed from the authoring platform (and underlying content repository) to a content delivery infrastructure.

![](http://blog.craftercms.org/wp-content/uploads/2017/03/decoupled-cms.jpg)

So which approach is the right architecture? The reality is, there is no single right or wrong answer. The answer depends on context: alignment with your requirements, your business process, and your business goals. The topic of coupled vs. decoupled is not a new one. It's a debate that has been going on for a long time and will continue to go on so long as there continues to be Web CMS platforms, "fanboys," and a perception that one size fits all. The more appropriate way to approach the question is to analyze the strengths and weaknesses of each approach and then to consider these in the context your own specific use cases. We'll see that in different scenarios we come to different conclusions on which architecture to use.

### Coupled Architecture

Let's take a look at the strengths and weaknesses of a coupled CMS architecture.

#### Strengths

  * Easy to setup and deploy a single instance.
  * Authoring and delivery are on the same infrastructure which can make it easier to build cohesive authoring tools.
  * Relatively easy administration of production system for single sites.

#### Weaknesses

  * SLAs (Service Level Agreements) are coupled -- meaning that authoring has to be just as available as the live site.
  * Coupled infrastructures are generally more complex to scale, as they typically depend heavily on database scalability.
  * Content is typically captured in a database schema meant for delivery on the site. This can make integration and migration difficult.
  * Software complexity is higher because the code base contains both authoring and delivery concerns. All but the most trivial CMS projects involve some development and thus become a development issue.
  * Pushing content in and out of the CMS to and from third parties takes place in the same system that runs your live site. Integration is not native to the architecture and it may impact the system's performance.

### Decoupled Architecture

Let's take a look at the strengths and weaknesses of a decoupled CMS architecture.

#### Strengths

  * Easier to scale for high traffic websites, and to handle multi-site management.
  * SLAs are decoupled. Authoring can be down for upgrades without impacting delivery. The reverse is also true.
  * Scale only the components that you need. If you are not adding more authors then there is no need to scale out authoring. This affects the complexity of the solution and also license costs where they are involved.
  * Code complexity is isolated within each of the two components (authoring and delivery). Each piece can be as simple or complex as is needed without impacting the other.
  * Integration is a built-in concept, as content is natively published to a remote delivery system, it is generally straightforward to push to other systems as well. Also note, integration takes place on the authoring tier safely away from the live site protecting stability and performance.
  * Content migration and sharing with other systems is generally much more innate to the architecture.
  * Multi-channel support by nature, as publishing to mobile apps, social channels, and other digital channels is a natural extension of the native publishing capability.
  * Content sharing and syndication are more naturally supported.
  * When complexity is isolated and scaling is simple, it's easier to develop and deploy rich features to your users.
  * Integrating with DevOps is much easier. When you need to integrate your development tools, process/automation, and source code repository you are inherently entering into a discussion about security and systems administration -- all of which are significantly more approachable if authoring and delivery systems are separated.

#### Weaknesses

  * Setup has more components and can be more complex.
  * Publishing introduces additional points of failure.
  * Sub-division of components can go too far driving up complexity and driving down the cohesion of the user experience.

## Is a Headless CMS a Decoupled CMS?

While a headless CMS architectures do "decouple" content and presentation, they do not dictate anything about the publishing capabilities of the CMS. And while decoupling content and presentation is certainly one of the most important things you can do architecturally, as we can see above, it's not the only major architecture decision you need to consider. Therefore, it is important to maintain the traditional use of the word decoupled CMS as it relates to separation of authoring and delivery capabilities.

**A headless CMS can either be coupled or decoupled.**

**Further, any CMS worth its salt today, (decoupled or not) must support headless/CaaS based content delivery.**

## Making a Choice Between Coupled and Decoupled CMS

It's clear that each approach has its own strengths and weaknesses. A coupled approach may work really well in one scenario while a decoupled approach may be much more appropriate in another.

Our analysis reveals that a coupled architecture can work well for web apps, mobile apps, and other content-backed digital experiences that need to be set up and put online in short order and that do not need to be able to scale quickly or to publish content beyond the website itself. On the other hand, we see that a decoupled architecture is ideal for websites/content back-ends that require high levels of availability and performance, need a lot of tailored functionality, must be integrated with third party business systems, and must publish to one or more digital channels beyond the website itself.

## Crafter CMS

Crafter CMS is a decoupled CMS that separates authoring and publishing capabilities into their own subsystems in order to achieve the many benefits discussed above. Crafter CMS makes it easy for authors to create, manage, and deliver content in **any format** from RESTful APIs/JSON to HTML5, and even virtual and augmented reality via AFRAME. So for modern digital experiences that must be delivered across many channels, Crafter CMS provides a decoupled architecture combined with Content as a Service capabilities.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
