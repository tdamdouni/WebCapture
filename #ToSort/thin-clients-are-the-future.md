# Thin Clients Are the Future

_Captured: 2017-05-30 at 13:44 from [dzone.com](https://dzone.com/articles/thin-clients-are-the-future?edition=303091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-28)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

For many years now, the sweet spot of developer productivity and user experience was the fat client architecture. In this architecture, the information is accessed through isolated layers of apps. The first layer executes directly on the user's computer, while the other layers execute on the server.

### **Most Web Apps Are Fat**

Embraced for over a decade, the fat client architecture was a response to a problem that is mostly gone now.

The year 2004 brought Gmail, a hugely successful email service accessed directly in the web browser. The users did not need to install any additional software to use it. The breakthrough was in the ease of use, near-instant performance, and contextual interactivity that was unmatched in regular desktop email software.

Since then, JavaScript frameworks and libraries such as Prototype, jQuery, Dojo, AngularJS, and React have polished out the concept of using a web browser as a rich application runtime environment and executing more and more code directly on the user's computer.

Fast forward to 2017. It is now near to impossible to find a web app that does not rely on JavaScript. Dubbed the "website obesity crisis," the appetite of web developers for running code in your browser has been unstoppable. Most web services require you to download megabytes of data just to render the basic function. Despite our superfast networks and excellent hardware on our desks and in our pockets, most business software feels sluggish and unreliable.

### **Two Apps For the Price of Three**

Fast client architecture means that the end user interacts with an app that runs on his or her computer. That app communicates with another app (or apps) running on a server.

There are different teams building each of these apps. They work at their own pace, have different design processes, and solve different problems. However, huge amounts of time are spent on solving challenges that are only specific to this architecture.

Many features, changes, and security measures need to be implemented on all levels.

To communicate with each other, the apps expose and consume APIs that must be designed, documented, implemented, and tested. That results in tons of unseen code that is only used for binding. The amount of this so-called "glue code" often exceeds the amount of code for the actual features.

Apart from the glue code that binds the apps, there is even more repeated code. The same features are implemented on the client, for instant feedback to the user, and on the server, for storage and consistency. Small discrepancies in their implementations may lead to bug hunts that take weeks.

### **What Makes Us Ready For the Thin Client?**

The software and hardware of today allows developers and software architects to return to the whiteboard.

A server in-memory application platform, such as Starcounter, can execute millions of data transactions per second. It can handle millions of simultaneous user sessions, with real-time data access in a fully consistent manner.

For the first time in the history of computing, we have a ubiquitous way to access information. All devices that have screens are becoming capable of rendering web content through the always connected network.

Recent specs added to the HTML standard, such as Custom Elements, Shadow DOM, and CSS Grid Layout go far beyond rendering text documents. They allow the developer to render a web app from loosely-coupled, standardized components and layouts. What once required complex frameworks and monolith development processes, now becomes just a composition of pieces that are compatible in many ways.

### **How to Benefit From This Improved Architecture**

Using a persistent connection, an in-memory application platform, and modern HTML, you get on the bleeding edge of thin client architecture. Now, what are the benefits?

If you can ensure a persistent network connection, you win the ultimate consistency of your data with a single source of truth. No matter who accesses the information or when it is accessed, it is always up to date.

It is also real time because the client has no other choice than to display the current data. Your apps push updates of shared data to all connected clients with no special effort. However, the perceived performance of your app is affected by the network latency. The physical distance between the client and the server should be within a few thousand kilometers for the interaction to be considered instant by your users.

Now to the greatest part. With no "glue code," the app developers have much less code to design and maintain. This means more focus can go to the work that matters. All the application logic lives on the server, and that is a huge productivity boost.

Even more importantly, it enables a new mindset. Your app executes directly where the data is. It can take insights from the complete dataset. That is impossible in fat clients because they can only operate on the fragments of data obtained upfront.

What the user gets on their screen is an HTML template and live connection to the server using a synchronized view-model. HTML is framework-less and can leverage the interactive Custom Elements created by your team or obtained from the thriving community at WebComponents.org.

Apps that run on the server can also be combined into bigger systems. The output HTML from multiple apps is merged and can be presented in a consistent user experience, in a process that Starcounter calls blending.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
