# Content Management Meets DevOps (Part 1 of 2) How a Git-Based CMS Improves Content Authoring and Publishing

_Captured: 2018-03-10 at 19:39 from [dzone.com](https://dzone.com/articles/content-management-meets-devops-part-1-of-2-how-a)_

Traditional CMS platforms based on SQL and JCR repositories have begun to show major signs of weakness in keeping up with today's demands for a high rate of innovation and rapid scalable deployment on modern elastic architectures. This is nowhere more evident than the move towards headless CMS. Many CMS platforms today push headless, or what some call Content as a Service (CaaS), as the one-stop-shop solution to the struggles most CMS platforms have in providing support for scalability, multi-channel, and development integration. It's not. Headless capability is important but it has its own limitations.

Open source Git-based dynamic CMS tackles these all of these challenges head-on with a set of technologies that incorporate lightweight development, integration with developer tools and processes, and elastic scalability for content delivery that provides the ability to serve any front-end technology via an API or markup with fully dynamic content.

In this two-part series, we'll explain the basic mechanics that support content authoring, publishing, and the developer workflow and demonstrate how these mechanics combined with a git-based CMS architecture and developer stack set a new standard for what a CMS can provide in today's competitive digital marketplace.

In this section, we'll explore the mechanics of how (non-technical) content authors work with the CMS and how their changes, once reviewed and approved, are deployed from their authoring tools to a live content delivery system.

A git-based CMS is decoupled, composed of several microservices where content authoring and content delivery services are separated into their own distinct subsystems. This model has many advantages related to security, scalability, and delivery flexibility. In a decoupled architecture, content is published from authoring to delivery as shown in the diagram below. The delivery system may be any number of independent digital channels - enterprise website, mobile app, social, augmented reality, digital kiosk or signage, e-commerce front-end, microsite, etc.

Our Git-based CMS, Crater, supports authoring via Crafter Studio that sits on top of a headless Git-based repository and publishing system. Content authors don't need to know anything about Git. They simply work with Crafter Studio, a web-based application. Crafter Studio provides beautiful content entry forms, in-context editing with multi-channel preview, drag-and-drop layout, component placement, image cropping, and more. While content authors are performing their work, Crafter is managing all of the Git mechanics, managing locking, creating a time-machine like, Git-based version history and audit trail for them behind the scenes, all accessible to them via the Studio UI.

![](https://blog.craftercms.org/wp-content/uploads/2018/02/craftercms-CMS-Meets-DevOps-decoupled-tech.png)

> _Figure 1: Crafter CMS microservices applied to decoupled architecture_

Crafter's publish mechanism deploys content from the Authoring system to the Delivery system. Content logically flows from the authoring environment to the delivery environment. The mechanism for this, given the underlying Git repo, is a "pull" type interaction. Meaning the actual network conversation is initiated from the delivery infrastructure to the authoring infrastructure, as shown in Figure 2.

Each delivery node has a Deployer agent that coordinates deployment activities on the node for each site that is being delivered on that node.

  * Delivery nodes can initiate deployment pulls either on a scheduled interval (a "duty cycle"), on-demand via an API call, or both.
  * The Deployer performs a number of activities beyond receiving and updating content on the delivery node. A list of post-commit processors is run. These can be used to execute updates on search indexes, clear caches, and perform other such operations.
  * The Delivery node maintains a clone of the Authoring Git-based repository. 
  * The Crafter Deployer takes care of managing the synchronization of the delivery node's clone authoring repository from the authoring environment.
  * Git-mechanics ensure content sync is 100% accurate.
![](https://blog.craftercms.org/wp-content/uploads/2018/02/craftercms-CMS-Meets-DevOps-Git-Publish-1024x524.png)

> _Figure 2: Crafter's Dynamic CMS Publishing via Git_

Technically speaking, Authoring does not require knowledge of the Delivery nodes. This makes the architecture more elastic, globally scalable and even enables Crafter to support disconnected and intermittent content delivery.

  * Elastically add new nodes or revive dormant nodes and they will sync to the latest without any additional wiring.
  * Creat region-based depots to avoid transferring data more than once over long distances for global deployments.
  * Airplanes, cruise ships, drilling/mining locations, and other remote disconnected deployments can operate with their latest pull of content, and sync up with Authoring when connectivity is available.![](https://blog.craftercms.org/wp-content/uploads/2018/02/craftercms-CMS-Meets-DevOps-Elastic-Delivery-1024x614.png)

**Figure 3: Elastic Delivery**

In Crafter CMS, only approved content is published to the delivery environment. Crafter manages this by using 2 repositories for each project. One called a "Sandbox" which contains work-in-progress and the other called "Published" which represents approved, published work and complete content history.

  * Authors use the Crafter Studio UI to review and approve content via workflow.
  * Crafter Studio takes care of moving approved work between Sandbox and Published repositories.
  * Delivery nodes monitor the published repository for updates.
![](https://blog.craftercms.org/wp-content/uploads/2018/02/craftercms-CMS-Meets-DevOps-Sandbox-Published-1024x626.png)

> _Figure 4: Authors work in Sandbox. Delivery nodes pull from Published._

Crafter's Git-based publishing model provides your authoring team with a highly reliable, highly accurate publishing mechanism that is elastically scalable, globally distributable, and supports multi-channel. Crafter CMS's architecture enables your team to reliably deliver your dynamic content on any channel, wherever and whenever it is needed.

Further, as we'll see in in Part 2, this architecture enables content authors to work side-by-side with DevOps, while they continually introduce new features and functionality without any disruption to the authors.

The underlying Git repositories and related workflow for Authoring require no setup at all. When you create a project in Crafter Studio it automatically creates the local "Sandbox" and "Published" repositories. When you add a new "Delivery" node a simple command line script is run on that node that configures the node's deployer to replicate and process content from the "Published" repository from authoring.

  * Instructions for creating a site via Crafter Studio can be found [here](http://docs.craftercms.org/en/3.0/getting-started/your-first-website.html).
  * Instructions for initializing a delivery node can be found [here](http://docs.craftercms.org/en/3.0/system-administrators/setup-site-for-delivery.html).

Content authors are non-technical users who need powerful but easy-to-use tools to help create, maintain and manage their digital experiences. Crafter Studio provides these users with a web-based application that makes it easy for content authors to achieve their goals. Under the hood, Crafter Studio leverages a powerful Git-based repository and deployment engine that provides authors with next-generation versioning and auditing mechanics as well as robust, elastic and distributed deployment.

Today's digital marketplace is constantly evolving. Companies are always iterating on existing functionality with improvements and deeper integration or introducing new functionality and channels for their audiences. For today's most innovative and competitive organizations, ongoing development and the move to DevOps is a fact of life. The companies that have the greatest success are those that have the right technology and processes through which they are able to achieve a high, sustainable continuous rate of constant, iterative development, integration and delivery, i.e., Continuous Integration and Delivery (CI/CD).

In the send half of this blog series, we will take a deep dive into how Crafter CMS seamlessly integrates with your CI/CD processes to enable your entire team of developers and content authors to innovate collaboratively without interfering with each other's workstream.
