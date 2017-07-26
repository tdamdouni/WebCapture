# Microservices Are Here to Stay

_Captured: 2017-01-27 at 19:44 from [dzone.com](https://dzone.com/articles/microservices-are-here-to-stay?edition=265886&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-27)_

Is iPaaS solving the right problems? Not knowing [the fundamental difference between iPaaS and dPaaS](https://dzone.com/go?i=171134&u=http%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-dpaas-e-guide%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%2520-%2520iPaaS%2520vs%2520dPaaS%26utm_source%3DDZONE) could cost you down the road. Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=171134&u=http%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-dpaas-e-guide%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%2520-%2520iPaaS%2520vs%2520dPaaS%26utm_source%3DDZONE)

A few years back, most software systems had a monolithic architecture and slow release cycle. In recent years, there has been a clear move towards microservices architecture, which is optimized for scalability, elasticity, failure, and speed of change. This trend has been further enforced by the adoption of cloud and containers, which also enables practices such as DevOps.

![Image title](https://2.bp.blogspot.com/-qa-vkTkvqpw/WEwMVyMUAvI/AAAAAAAAG84/ynMR2-Ch26A9U4hkxCDHgQU2t3m1sb8PgCK4B/s400/Screen%2BShot%2B2016-12-10%2Bat%2B14.07.58.png)

> _Trends in the IT industry._

All of these changes have resulted in a growing number of services to develop and an even bigger number of deployments to do. It soon became clear that the explosion in the number of deployments could not be controlled using pre-microservices tools and techniques. New ways have been born. In this article, we will see how cloud-native platforms such as [Kubernetes](http://kubernetes.io/) allow deployment of Microservices in high scale with minimal human intervention.

## Cloud-Native Deployment Traits

### Self-Service Environments

Local, dev, test, int, perf, stage, and prod are all environments, but what is an environment, really? Usually, it is a VM or a group of VMs that represent an environment.

Local is the developer laptop where the user has full freedom to experiment with and break stuff. It still has to be similar to other environments to avoid the "it works on my machine" syndrome.

Dev is the very first environment where changes from all developers are integrated into one working application. It runs a SNAPSHOT version of the services, has mocked external dependencies, and most of the time, it is broken from constant change.

Once a service has been released, it is moved to a more stable environment such as Test. This environment may be slightly more powerful (maybe have more than one VM), may have more external services available rather than mocks, and it has also testers accessing it.

While the environments get closer to production environment such as Int/Stage/Perf, they get bigger, with more VMs and more external dependencies available. At some point, we probably need an environment that has resources quantifiable with the production environment so we can do performance tests that mean something in relation to the production environment.

The main difficulty with this model is that the concept of environment is mapped to a physical or virtual VMs and as such it is slow to alter. You cannot easily change the resource profile of an existing environment, create new environments, or give an environment per developer on the fly.

![Image title](https://4.bp.blogspot.com/-_n8MjbUZKu4/WHGOSEE0eiI/AAAAAAAAHRE/ccxY-XpUQzwVhR4DRnh80HUb-u4LEnrOQCLcB/s400/Screen%2BShot%2B2017-01-08%2Bat%2B00.56.17.png)

> _Environments managed by Kubernetes._

In the cloud-native world, an environment is just an isolated, controlled, and named resource collection. For example, given a pool of eight VMs, you can chunk and use that resource pool for different environment instances depending on the needs of the various teams. And those chunks don't map to VMs, which means it may be that multiple environments are collocated and share few of the VMs. Creating, editing, destroying an environment is achieved with one command, instantly, without a request for VMs and waiting for days or even weeks. This allows teams to change their environment profiles based on their changing needs in a self-service manner more easily and quickly.

### Dynamically Placed Applications

We can see how a self-service platform for managing environments can ease the onboarding of new developers, services, projects, and even enable custom release strategies which may require temporary environments on the fly. Once an environment is ready, the next task is choosing a strategy for placing our Microservices on the environments.

One of my favorite microservices-related books is _Building Microservices _by [Sam Newman](https://twitter.com/samnewman)_._ In the book, Sam approaches microservices from all possible angles and one of those is deployments. In the chapter about deployment, the author describes few strategies for mapping services to hosts and their pros and cons.

![Image title](https://3.bp.blogspot.com/-os0Ft1Z0j44/WHAOTLXdDSI/AAAAAAAAHPQ/QFxBYff_gs4fGz2hUeUtwZvIU4G0W54AQCLcB/s400/k8s%2Bdeployments%2Bold%2B-%2BPage%2B1%25282%2529.png)

> _Service to host mapping strategies._

As you can see, the concept of VM/host disappears with environments spanning multiple hosts, and services being placed on hosts dynamically. We don't care and we don't want to know the actual hosts where our environments are carved and where the microservices are placed (except when predictable performance is critical and shared host resources and platform resources should be avoided).

I have also described this approach in painful details for Apache Camel based applications in my _[Camel Design Patterns_](https://leanpub.com/camel-design-patterns/) book. Basically, it comes down to choosing a way to package your services and grouping them on the available hosts considering all kind of service and host dependencies. Luckily for us, the industry has moved forward quickly and containers has been accepted as the standard for packaging Microservices. Unless you are Netflix and have over 100K Amazon EC2 instances, you shouldn't look for quick ways for burning EC2 images for each service, and instead just use containers. Even [Netflix has moved on](http://techblog.netflix.com/2016/11/netflix-at-aws-reinvent-2016.html) and they are experimenting with containers and even developing open-source container [scheduling](http://www.slideshare.net/aspyker/netflix-container-scheduling-and-execution-qcon-new-york-2016) software.

So, no more one VM per service and no more service to host mapping strategies. Instead, based on your service requirements and dependencies and the available host resources, your cloud-native platform should find a host for every service in a predictable manner defined by policies. That requires an understanding of each service and describing its requirements such as storage, CPU, memory, etc., but later the benefits are huge. Rather than manually orchestrating and assigning each service to a host in advance, the Kubernetes [scheduler](http://kubernetes.io/docs/user-guide/node-selection/) performs a choreography of services and places them on the hosts dynamically when requested.

### Declarative Service Deployments

We can provision environments in a self-service manner and have services placed on the environments with a minimal effort. However, when we have multiple instances of a service, how do we deploy the new instances? Do we first have to stop an instance, then upgrade, and when things go wrong we rollback? Cloud-native platforms (and Kubernetes specifically) have thought about this too. Using the concept of [Deployment](http://kubernetes.io/docs/user-guide/deployments/) Kubernetes allows describing how the service upgrades should be performed.

![Image title](https://3.bp.blogspot.com/-s1P5hN5MkWU/WHAEilN-rZI/AAAAAAAAHO0/uP5QArP06AodEZp7cIZw5jonvGTV5VdkwCLcB/s320/Screen%2BShot%2B2017-01-06%2Bat%2B20.55.24.png)

> _Rolling and fixed deployment._

The rolling update strategy of the deployment updates one pod at a time rather than taking down the entire service at the same time and ensures zero downtime. This fixed (or "recreate," as it is named) strategy, on the other hand, brings downs all service instances and then gradually starts new versions.

In both cases, the deployment will declaratively update the deployed application progressively behind the scene.

## Additional Benefits

Having a platform that is capable of managing the full lifecycle of services offers also additional deployment related benefits.

### Blue-Green and Canary Releases

A [blue-green](https://martinfowler.com/bliki/BlueGreenDeployment.html) release is a way for achieving rapid rollback in case anything goes wrong with the new release.

A [canary](https://martinfowler.com/bliki/CanaryRelease.html) release is a technique for reducing the risk of introducing a new software version in production by introducing change only to a small subset of users before rolling it out to everybody.

![Image title](https://1.bp.blogspot.com/-fBUWjxh8GtQ/WHAEu4a8HTI/AAAAAAAAHO4/xJrH6-RJC4AuZabNuUpfVN4Ayh6cMqAvgCLcB/s320/Screen%2BShot%2B2017-01-06%2Bat%2B20.57.05.png)

> _Blue-green and canary releases._

Both of these techniques can be easily achieved using Kubernetes with minimal human intervention.

### Self-Healing

The cloud-native platform is able not only detect failure but also act and heal it. Kubernetes will regularly perform [health checks](http://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/) for your application and if it detects something wrong, it will restart your service and even go further and move it to a different healthier host if required.

### Auto Scaling

In addition to self-healing, the platform is also capable of [autoscaling](http://blog.kubernetes.io/2016/07/autoscaling-in-kubernetes.html) of services and even the infrastructure. That is a very powerful feature giving the platform some [Antifragile characteristics](http://www.ofbizian.com/2016/07/from-fragile-to-antifragile-software.html).

### DevOps and Antifragile

If we look at all the benefits provided by Kubernetes, I think it is fair to say that it offers primitives and abstractions that are better suited for managing Microservices at scale. With such a tool, it becomes easier for teams and organisations to use practises such as DevOps and focus on improving the business processes towards Antifragility.

## Closing Thoughts

We have seen many of the benefits of cloud-native platforms in regards to Microservices deployments but have not discussed any of its cons in this article on purpose. As you may expect, there is a steep learning curve for Kubernetes, and also a need for a change in the patterns, principles, practices and processes when developing such applications. Basically, that is the move to cloud-native applications.

This may sound too strong, but if you are doing microservices -- and that is microservices at scale -- using a cloud-native platform (such as Kubernetes) is a must.

![Image title](https://3.bp.blogspot.com/-99I7KEYz1Ck/WHCuiHRrT3I/AAAAAAAAHP0/5j9x17D85DEG6s4inA3fGcnnW79RRCzVACLcB/s400/Screen%2BShot%2B2017-01-07%2Bat%2B08.31.30.png)

> _Picture from Wikipedia. Wisdom from W.E. Deming._

If you are using pre-microservices tools, techniques, and practices for developing microservices, it will hit you back, and microservices may not work for you.

Discover the unprecedented possibilities and challenges, created by today's fast paced data climate and [why your current integration solution is not enough](https://dzone.com/go?i=171135&u=http%3A%2F%2Fbit.ly%2F2aydpMZ%25C2%25A0), brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=171135&u=http%3A%2F%2Fbit.ly%2F2aydpMZ%25C2%25A0)
