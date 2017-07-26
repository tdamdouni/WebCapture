# Preparing for infrastructures of the future

_Captured: 2016-05-25 at 22:28 from [techcrunch.com](http://techcrunch.com/2016/05/25/learnings-from-google-about-the-future-of-infrastructure/?ncid=rss)_

![](https://tctechcrunch2011.files.wordpress.com/2016/05/432644816_43394f7ad3_o.jpg?w=738)

There are many abstract notions about what the future of infrastructure will look like, but the truth is that the future is staring companies in the face. The adoption of hybrid cloud models, containers and microservices architectures are only the beginning stages of preparing for infrastructures of the future.

The largest enterprises have already experienced the volume of data that all companies will soon be ingesting. And they have evolved to meet the demands of these changing needs. As more organizations begin to realize the power of big data, they can learn valuable lessons from the evolution of global giants like Google, Facebook and Apple.

Google started with the premise that computer science, at scale, makes the intractable tractable. Underlying Google's scale-supporting infrastructure are warehouse-sized data centers with exabytes of storage and terabit networks.

In recent years, a shift has occurred rendering this infrastructure critical not only for consumer web applications, but also for enterprise class problems, like big data processing, agility needs, 24/7 availability, faster delivery, customer engagement through social mechanisms, real-time communications and so on. And we are on the cusp of new technologies that will require even more infrastructure resources, like IoT and virtual reality.

## Understanding the problem of scale

Companies approach scaled-out systems from several perspectives. Opportunity is often the primary one; harnessing your data gives a company commercial advantage. Cost is another. If your system is designed only to scale up, then you are locked into a certain price point driven by hardware resources being used. Elasticity is a third, for cases when workloads are irregular, prone to peaks or for the cases where you see hockey-stick growth.

While it is sometimes easiest to think my needs are all of the above, it is important to prioritize and stay focused. For example, at Google's scale, elasticity was the most critical criterion. When Google launched "autocomplete," the feature that guesses an individual's search as it's typed, the queries on the backend increased tenfold. Without elasticity already built in, this type of project could have taken years rather than months to deploy into production.

## Addressing the problem with modern tools

Google has famously said everything inside the company runs on containers. In that sense, anyone in the process of "googling" something is involved in a container project. Containers by nature have lower runtime requirements for applications, which reduces their size and allows them to be deployed quickly, making them a better fit for the new stack.

Google uses an internal cluster operating system, Borg (a reference to the decidedly unfriendly species in Star Trek: The Next Generation), that was built to manage both long-running services and batch jobs, which had previously been handled by two separate systems: Babysitter and the Global Work Queue. These predecessors, which were from the early days of Google, strongly influenced Borg and predated Linux control groups.

Borg shares machines between these two types of applications -- filling the troughs of long-running services such as YouTube uploads with batch jobs such as logs processing -- as a way of increasing resource utilization and thereby reducing costs. Such sharing was possible because container support in the Linux kernel became available, enabling better isolation between latency-sensitive user-facing services and CPU-hungry batch processes.

As more and more applications were developed to run on top of Borg, Google's application and infrastructure teams developed tools and services for it. These systems provided mechanisms for configuring and updating jobs; predicting resource requirements; dynamically pushing configuration files to running jobs; service discovery and load balancing; auto-scaling; machine-lifecycle management; quota management and much more.

Similarly, today's developers build management APIs around containers rather than machines, shifting the data centers' focus from machine to application. This frees application developers and ops teams from worrying about specific details of machines and operating systems. It ties telemetry collected by the management system to applications rather than machines, which dramatically improves application monitoring and introspection, especially when scale-up, machine failures or maintenance issues cause application instances to move.

## The future

The future is near. Sensor-generated data, such IoT data, will soon swamp other kinds of data. The need to process this collected data in real-time -- not only for self-driving cars but for all kinds of retail, industrial, gamification or consumer homes -- will spur a need for new degrees of agility. The runtime environment will be more hybrid: AWS, Google Cloud, Azure will be more balanced in terms of market share and will be joined by other large private clouds, such as industrial automation clouds and consumer-home clouds.

Featured Image: [David Merrett](https://www.flickr.com/photos/davehamster/432644816/)/[Flickr](https://www.flickr.com/) UNDER A [CC BY 2.0](http://creativecommons.org/licenses/by/2.0/) LICENSE
