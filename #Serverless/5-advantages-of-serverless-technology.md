# 5 Advantages of Serverless Technology

_Captured: 2017-11-14 at 15:01 from [dzone.com](https://dzone.com/articles/five-advantages-of-serverless-technology?edition=334911&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202017-11-14)_

Are you joining the containers revolution? Start leveraging container management using Platform9's [ultimate guide to Kubernetes deployment](https://dzone.com/go?i=243221&u=https%3A%2F%2Fget.platform9.com%2Fjzlp-kubernetes-deployment-models-the-ultimate-guide%2F).

![Image title](https://dzone.com/storage/temp/6929833-1-oevrebgq5pv-ew1t3durhw.png)

When Instagram launched in 2010, it was woefully underprepared to become the next rags-to-riches social media company.

In just six hours, skyrocketing traffic overwhelmed the single Los Angeles-based machine running Instagram's back-end. Likening it to open-heart surgery, co-founders Mike Krieger and Kevin Systrom were forced to perform an emergency migration from the local server to Amazon's EC2 cloud service. Instagram's quick switch to the cloud likely saved it from death-by-desertion after its homebrew server failed to keep pace.

Fast-forward six years, and this idea of outsourcing computing power has taken huge leaps forward. Rather than simply moving existing servers into the cloud to help with scaling and operations -- we'll call this "Cloud 1.0" -- a new way to develop software is emerging that takes advantage of elastic computing power to simplify software development.

This trend has further decreased time-to-market and delivered the scaling necessary for Uber, Pokemon GO, Airbnb, "Clash of Clans," and numerous others apps characterized by large user bases and real-time data.

This new movement in software design has earned the sexy moniker of "serverless" or "serverless computing." It's certainly catchy, but the term doesn't begin to illustrate the many facets of this new architecture.

With more than 4 million apps vying for attention on Apple's App Store and Google's Play Store, developers are turning to serverless for a competitive advantage. App development costs can easily top [six figures](http://savvyapps.com/blog/how-much-does-app-cost-massive-review-pricing-budget-considerations), but 90 percent of paid apps earn less than $1,250 per day. By reducing costs and internal complexity, serverless computing has helped app creators cope with the saturated market and deliver compelling experiences.

## The Secret to Serverless

For software developers, serverless architecture means breaking apart their server-side application into functions that each perform a distinct task. Writing software as a collection of functions is something every CompSci 101 student learns in the first week of class, but serverless architecture takes this to the extreme. The entire application is split into separate, loosely coupled components that can be operated at any scale.

A serverless vendor takes each of these functions and runs them in parallel "containers" that can be monitored and scaled separately. This new architecture delivers some key benefits and solves some surprisingly challenging scaling problems that are inherent to other software architectures.

A great example of a serverless architecture working well is the real-time filtering of chat comments. The business requirements of many chat applications often mean each message must be filtered, parsed, or otherwise policed before delivery to recipients.

With the traditional approach, each message is first sent to the app maker's server, parsed, and republished to the chat room. That might work fine for small numbers of simultaneous users, but what about 1 million? A simple chat filtering issue suddenly becomes a distributed computing nightmare.

A serverless approach to the same problem is painless. The developer writes a function that filters the chat message. The serverless provider wraps the function into a container that can be monitored, cloned, and distributed on any number of servers. The app developer routes all chat messages to the provider, who simply runs more containers as necessary to ensure the logic will work at any scale.

## The Serverless Advantage

Whether you're building a chat app or the next Pokemon GO, there are plenty of reasons to go serverless:

### **Decreased Time to Market**

Serverless approaches allow developers to create new apps in hours and days instead of weeks and months. Examples abound in new apps that rely on third-party APIs for services like: authentication (OAuth), social (Twitter), maps (Mapbox), artificial intelligence (IBM's Watson), and more.

### **Enhanced Scalability**

Everyone wants his app to be the next Facebook, but if that happens, can it handle the load? Provisioning infrastructure _just in case_ is a big risk -- but so is being unprepared when success strikes. Serverless architecture means you don't need to make that choice. One online training program scaled to [40,000 users in six months](https://read.acloud.guru/why-serverless-with-aws-is-a-game-changer-3cb37e25f638#.eg8de096p) without a single server.

### **Lower Cost**

In terms of both computing power and human resources, serverless saves. Why pay to reinvent the wheel for authorization, presence detection, and image processing? Or to manage infrastructure? And if there's no need for always-on servers, operational costs plummet. The days of spending hundreds of thousands of dollars for servers are gone.

### **More Time for User Experience**

Users don't care about infrastructure; they care about features and their experience. Serverless architecture allows teams to focus resources on the elements that keep users happy. [The Climate Corporation](https://www.climate.com/), for example, uses serverless infrastructure to give growers a rich interface to a real-time view of farm equipment operations, informing their decisions and enhancing operations.

### **Improved Latency and Geolocation**

An app's ability to scale depends on three things: its number of users, those users' locations, and network latency. Today's apps have global audiences, which can create latencies that diminish experiences. With serverless, providers have points of presence near every user, and apps perform equally well for everyone. For example, [Gett](http://gett.com/about.html) provides on-demand delivery services worldwide, so it chose serverless for its low-latency, real-time messaging to connect passengers and users, as well as streaming geolocation updates.

From photo-sharing apps to farm data dashboards to connected jet engines, serverless can accommodate the wide-ranging needs of app developers.

As data loads continue to grow, expect to see serverless become a standard approach to offloading [functions to execute closer to end users and devices](https://www.pubnub.com/blog/moving-the-cloud-to-the-edge-computing/?utm_source=Syndication&utm_medium=Medium&utm_campaign=SYN-CY17-Q2-Medium-June-26). By reducing costs, latency, time to market, and complexity, the serverless model is poised to become a staple of the app space.

Using Containers? Read our [Kubernetes Comparison eBook](https://dzone.com/go?i=243223&u=https%3A%2F%2Fget.platform9.com%2Fjzlp-kubernetes-comparison-ebook%2F) to learn the positives and negatives of Kubernetes, Mesos, Docker Swarm and EC2 Container Services.
