# Think Beyond Containers

_Captured: 2018-08-22 at 09:41 from [dzone.com](https://dzone.com/articles/think-beyond-containers?edition=385399&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-08-21)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

![](https://www.magalix.com/hubfs/MagalixCorporation_April2018/Images/BlogImages/4a2b9b_137d6b149d324f61aa186bc10fd2ee2d_mv2_d_5000_3333_s_4_2.jpeg?t=1533319566246)

On the first day at my previous job, my manager asked whether we were getting a good return on investment (ROI) from our cloud infrastructure. After just two days on the job, I could clearly see that we weren't. Our VM's CPUs were running at five percent on average, and memory was running below 40 percent.

We spent the next six months working to build[ a more efficient cloud infrastructure](https://goo.gl/tphp8v) -- and by the end of the project, we'd achieved a 25 percent savings. But after just five weeks, the numbers had slid back to their original levels. After a lot of trial and error, we realized we needed a completely different way of building and running our software. We needed containers.

Like many other companies, we rushed into the container-based infrastructure -- and in the beginning, everything seemed much easier and smoother. But our challenges were just beginning. Here are the issues we faced:

**Containers introduced additional overhead. **Instead of working with application and infrastructure metrics alone, we found ourselves constantly monitoring the state of our orchestration system, as well as our containers -- and we began to encounter issues identifying the root cause of issues we faced. For example, one of our containerized web servers would randomly stop working. Customers were complaining -- yet our containers were reporting that they were happy and the metrics of the underlying VMs reported that everything was great. We finally realized that our containers didn't have enough network buffer space, which meant they had almost completely stopped sending data to end users! As a result, we introduced a range of new metrics focusing on the health of our containers as well as their interactions.

**Implementing containers didn't solve our underutilization problem**. We'd assumed that our infrastructure would take responsibility for our capacity issues as long as we set the right rules. But the truth is, there's a strong correlation between user behavior (which is notoriously hard to predict), scalability of containers, and the demands of the underlying VMs. As a result, we (the infrastructure team) often found ourselves running in full-on panic mode. Our containerized applications assumed infinite capacity and full automated scalability and when traffic spiked, our infrastructure collapsed, forcing us to over-provision again. In the end, we realized that we needed a smarter, more proactive way of scaling our infrastructure. That's why we founded Magalix!

**Separation between containers got blurred, straining out infrastructure space.** When we first started out, we thought out containers would keep our developers and infrastructure folks in complete harmony. But in truth, we had a lot of ambiguities in terms of the responsibilities of devs and infra engineers. For example, who controlled the exposure of an endpoint to the Internet? Who controlled the interconnections between microservices? Who controlled which packages should be included in a container? We didn't have clear answers to any of these questions -- which led to a lot of unproductive debates between our teams. As we discovered later on, this is actually a common problem when container orchestration is left fuzzy.

We've seen a lot of teams suffer through these same pain points -- both in our own individual careers, and throughout our journey at Magalix. Since we've experienced these frustrations firsthand, we've worked to keep our applications, containers, and infrastructure easy to manage by using artificial intelligence that understands the connections between these layers and adjusts capacity accordingly.

We recommend the following tactics to help you avoid the challenges we've just described:

**Focus on how containers will maximize your ROI and help your team move faster.** Yes, containers solve the pain points around inconsistent environments -- but they can bring even more opportunities if you focus on using them to help your applications and infrastructure adapt to your business's needs.

**Make sure that you can do all the necessary heavy lifting before you implement containers.** It takes time -- and a lot of effort -- to get your container layer working in harmony with your development needs, as well as the goals of your business. A debate is part of the process. Start by laying out clear guidelines around specific points of control, and defining who has responsibility for each of them.

**Decide on your key performance indicators (KPIs) -- then work backwards from there.** Once you know what your service needs to deliver, work from there to figure out your ideal capacity. For example, if you want to use average latency per feature as a KPI, you'll need make sure you track daily usage, and analyze that data to determine how your infrastructure will keep up with anticipated usage patterns.

**Eliminate any noise introduced by containers.** For all the convenience they provide, there's no getting around the fact that containers add another layer to your infrastructure. That means you're going to see an explosion in metrics on the number of containers, the state of each container, interconnections between containers, and so on. Learn to separate KPIs from noise so you can take useful action.

Like what you read? Gain additional insights from Mohamed Ahmed at the Magalix blog: [magalix.com/blog](https://magalix.com/blog)

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Topics:

containers and containerization ,containers as a service ,docker build ,infrastructure design ,cloud ,monitoring
