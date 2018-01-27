# Five Reasons Why You Should Use a Git-Based CMS (Part 4 of 5)

_Captured: 2017-12-07 at 13:39 from [dzone.com](https://dzone.com/articles/five-reasons-why-you-should-use-a-git-based-cms-pa-3?edition=342109&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202017-12-07)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

In our previous posts, we looked at Git-based, specifically in terms of [versioning (part 1)](https://dzone.com/articles/five-reasons-why-you-should-use-a-git-based-cms-pa), [distributed repository (part 2)](https://dzone.com/articles/five-reasons-why-you-should-use-a-git-based-cms-pa-1) and [deployment mechanics along with its decoupled architecture (part 3)](https://dzone.com/articles/five-reasons-why-you-should-use-a-git-based-cms-pa-2). In this post, we'll take a deeper dive into a feature of Git-based CMS that provides unparalleled support and speed for innovation: **branching.**

Imagine a single train track that stretches from Washington D.C. to New York. How many trains can run simultaneously on this track? How fast can the trains go? How much control over the order of arrival do you have?

  * You can run as many trains as you have room for on the track.
  * Any one train can only go as fast as the train in front of it.
  * The trains always arrive in the order in which they departed.
  * If a train breaks down or gets put on hold, it's nearly impossible to reorder.

With only one track, the railroad's ability to deliver success is throttled by the amount of volume they can handle and even when capacity is not an issue, they are completely dependent on good luck with respect to order and unplanned changes and breakdowns. With railroads, the solution to this problem is implemented with switches and sidings. Sidings are branches in that single track that allow a train to pull off the main line giving the controller the ability to regulate the order, speed, and quantity of trains on the main line.

The same problems of bandwidth, throughput, and order you see in the railroad example exist with projects that need to go through your traditional CMS. Traditional CMS platforms have no ability to branch the content and code base. They are just like that single track from DC to New York. This means you have very little control over the order, speed, and capacity of your development. Your CMS needs branching. Let's explore this further.

Nearly every CMS still sits on an architecture and repository that was devised 20 years ago. Back then innovation was important but the world moved a lot slower. A single pipeline of features got the job done and the CMS was less of a bottleneck. Today, in contrast, digital channels are at the core of many organizations' strategy for serving the customer better and beating the competition. The organization who moves the fastest often wins. Agility is key.

Meanwhile, infrastructure costs have gone down while development costs continue to rise. Balancing costs with volume and speed of innovation is a major challenge of our day. Today it's all about great DevOps. To make DevOps really work with CMS you need to be able to branch.

The traditional software development process has included branching for eons. Developers and DevOps have long since figured out that they need to be able to work in teams, isolate work, and control the order in which work is merged into the critical path for go-live. The CMS track runs right alongside the traditional development track, and, at some point, it merges and the last few steps require the CMS. It's only now that the demand for the speed of innovation has increased that the connective tissues between development and the CMS have been put under so much stress that they are completely failing. The fact is that today, we need that same agility all the way through the CMS and right up to the very last step of production deployment.

Even if the majority of your development is outside the CMS you still need to integrate. Consider the following example:

![](https://blog.craftercms.org/wp-content/uploads/2017/11/traditional-cms-devops-1-1024x741.jpg)

Because the website needs to integrate with, and ultimately deliver the functionality of the microservice, we need to perform development. We also need to support daily content edits and continuous publishing. With traditional CMS we have no option but to use multiple CMS environments to support this scenario. Does this approach give us multiple tracks and control over my releases? Yes, technically it does. But practically speaking? No. Not at all.

[As we learned before, moving content](https://blog.craftercms.org/2017/11/06/five-reasons-why-you-should-use-a-git-based-cms-part-2-of-5/) and code between CMS environments with traditional CMS architecture is extremely difficult. The process of spinning up environments and loading code and content into them is so difficult and time consuming for any DevOps team that most won't even consider it unless absolutely forced to. Even then the size of the team may not support the need. The rate of innovation crawls to a near stop.

To address this problem, we built Crafter CMS v3 on top of a Git-based repository. As a result, the Git-based CMS platform is built on a repository store that not only branches but also is fully distributed. Not only are you able to easily control the order and rate of work, but it's a snap to move work from one environment to another.

![](https://blog.craftercms.org/wp-content/uploads/2017/11/crafter-cms-devops-1024x745.jpg)

Moreover, branching not only supports DevOps and but it makes development easier. Developers and authors can experiment, work on major features and other site enhancements in the safety of branch-based sandboxes that keep them from stepping on each other's toes.

If you want to quickly innovate with your website, mobile app, and other content-rich digital experience apps, you will need multiple teams working on different features at the same time. You need control of who is working on what and the order in which projects will be delivered. Having the capability to manage these concerns with agility is the key to innovating quickly. Traditional CMS platforms don't support the basic feature set that enables this. Moving most of the development outside the CMS only gets you so far. You need a CMS that supports your DevOps process with features like branching and distributed repository if you truly want to be able to move fast.

Stay tuned for our next blog entry to learn another major reason why you should use a Git-based CMS!

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
