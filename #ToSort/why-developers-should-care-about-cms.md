# Why Developers Should Care About CMS

_Captured: 2017-07-13 at 11:05 from [dzone.com](https://dzone.com/articles/why-developers-should-care-about-cms?edition=308191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-12)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

As developers, we've got a strong handle on how to manage and deploy our code assets. Yet every one of us, at some point in our application build has said, "What about this text? What about these images? Where do these belong?" That's pretty universal. Nearly every single application today has content in it. Be it a web app or a native app; it's full of strings, images, icons, media, and other classes of content.

This content doesn't really belong in our code base -- because it's not code. These non-code assets make us as developers pretty uneasy. We know that at some point a business user is going to ask us to make a change to one of those strings and we're going to spend hours of build and deploy cycles to handle a 30-second code change. We know that at some point we're going to need to translate that content. We know at some point we're going to replace this UI with another one. We know all these things -- and we know leaving that content, even if it's abstracted into a string table or a resource bundle, is going to come back to haunt us; no matter the abstraction: it's part of the build, developers need to update it. Developers and systems folks need to deploy it.

Smart developers separate code from content. They make sure that the content in the application is completely independent of the build and deploy cycle of the application itself. Where appropriate they make sure non-technical business users and have access to the externalized content and can update it and publish changes at any time.

Consider the following scenario. Your application is for an insurance company. Along comes major regulation change. Now your (and every other application) needs to change its language accordingly. If the content was separate from the application the response time and cost to make changes is minimal. It's business as usual. If the content is not separate you are looking at months of builds, testing, and deployment that costs time, opportunity, and a tremendous amount of money.

What we're really talking about is application architecture. Making the right decisions has significant impacts on our development teams and process and, as we've illustrated, our organization's responsiveness and bottom lines.

## Solving the Content Problem Through Application Architecture

This problem is very similar to another problem: websites. Way back in the 1990s, people built and maintained entire websites in HTML by hand. You had to be a programmer who understood the markup and how to update it and ultimately deploy it to a server once complete. This model didn't work. Once businesses started using the web to communicate to the masses marketing departments started getting involved. Marketers wanted constant updates. Developers wanted to write code, not update copy. They needed a solution. The Web Content Management System (WCM for short) was born. WCM offered a new architectural solution to manage websites. WCM allowed the developers to put the code into templates that contained placeholders for the content and gave authors a user interface to manage and edit the content at any time. The content is managed separately from the code (the templates) and the two are brought together to create the final product. Everyone wins.

We need the same capabilities that WCM provides but for our applications.

## Why Not Use a Traditional CMS?

Simple. Traditional CMS platforms have the wrong underlying design. Most CMS platforms were built or are based on the same design as CMSs that were built 20 years ago.

  * **They were built to manage pages: **Most CMSs do not have a generic concept of what content is. These systems were built to manage pages. You might be able to contort the system to get what you want from it but it will be a hack. You need a CMS that is agnostic to the kind or type of content you need to manage.
  * **They rely on the wrong type of data tier:** RDBMS/SQL databases were the primary backends for data regardless of the problem and open-source options like MySQL were readily available. You need a CMS that leverages a data tier that is more distributed and flexible.
  * **They are built on the wrong technology:** Many CMS platforms are built in PHP. That's fine for certain use cases. But frankly, Java has a larger community, more library support and a lot of powerful platforms like Solr, Elastic Search, Hadoop (and many others) that plug into a Java CMS perfectly. Why run multiple tech stacks to accomplish a single goal?
  * **They aren't secure**: Most CMS platforms couple authoring and delivery together in a single database. That means work in progress (like pending policy updates) is available in the delivery runtime to anyone who finds a way into the database. That can spell disaster in the event of a hack. Large companies and governments have suffered expensive and dangerous leaks due to this kind of coupled, insecure architecture.
  * **They don't support multi-tenancy:** Most of the CMS platforms out there are not multi-tenant. If you're going to back apps with a CMS you need a CMS that will let you properly segregate and secure content between apps. No one wants to do a CMS install PER app.
  * **They don't scale**: RDBMS is hard to scale. You either cluster or replicate. Both have serious issues when it comes to really large, global, and auto-scale type deployments. Supporting an app with your CMS will demand scale. Design for scale from the start.
  * **They don't fit into your development tools and process:** When most CMS platforms were designed, the content authors were the only audience that mattered. Today it's different. Developer tasks like managing templates, CSS, JavaScript, content models, and other artifacts need to be just as easy -- and it needs to fit in with your existing workflow. That means Git source code management, Continous Integration (CI), Integration with your IDE, the ability to fork and support multiple teams simultaneously.

## If Not Traditional CMS, Then What? A Modern CMS, That's What!

To get different results you need a different design. You need a modern CMS:

  1. **Built with the right technologies** like Java, Spring, Groovy, Solr, and Git. These are the technologies that will be easy to hire for, will fit into and integrate with any enterprise, and will have the out of the box capabilities and horsepower to back any scale deployment.
  2. **Decoupled architecture** that cleanly separates authoring and content delivery responsibilities on to separate, independent, highly securable, highly scalable infrastructures by a publishing process. Decoupled Architectures don't have work in progress outside the firewall. They are much easier to scale.
  3. **Built on scalable document-oriented data tiers** like XML+disk/Git and Casandra and others. Disk-based tech is much better for streaming rich content and supporting global distribution better because they don't need to be clustered. At a minimum, you want something that's document oriented and that distributes globally better than a than a SQL backend RDBMS.
  4. **Content type agnostic:** From strings to web pages, to videos and virtual reality experiences. The CMS needs to accept any kind of content. That comes down to how content is modeled and how it's stored. Does the CMS store content in a SQL database or a JCR repo? Red flag. Can't provide Headless Content/APIs AND rendered content? Another Red Flag.
  5. **Is Multi-Tenant**. You need to be able to support many customers/apps on a single install. Either you support it or you don't and today it's a must!
  6. **Supports authors AS WELL AS developers and DevOps**. Developers don't want to work in some clunky CMS. They want to work locally in an IDE, then be able to work with their team and ultimately go through the entire workflow out to production. A modern CMS gives them this.
  7. **Open-Source. **Open is better than closed. The debate is over. Is it a must? No. But you'll get more for your money and you'll get a lot more innovation at a faster rate if you leverage open-source.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
