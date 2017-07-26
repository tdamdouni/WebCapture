# Why Container-Based Deployment Is Preferred for Microservices

_Captured: 2017-01-27 at 01:31 from [dzone.com](https://dzone.com/articles/why-container-based-deployment-is-preferred-for-mi?edition=264899&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-25)_

Is iPaaS solving the right problems? Not knowing [the fundamental difference between iPaaS and dPaaS](https://dzone.com/go?i=171134&u=http%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-dpaas-e-guide%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%2520-%2520iPaaS%2520vs%2520dPaaS%26utm_source%3DDZONE) could cost you down the road. Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=171134&u=http%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-dpaas-e-guide%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%2520-%2520iPaaS%2520vs%2520dPaaS%26utm_source%3DDZONE)

When it comes to microservices architecture, the deployment of microservices plays a critical role and has the following key requirements.

## **Ability to Deploy and Undeploy Independently of Other Microservices**

Developers never need to coordinate the deployment of changes that are local to their service. These kinds of changes can be deployed as soon as they have been tested. The UI team can, for example, perform A/B testing and rapidly iterate on UI changes. The microservices architecture pattern makes continuous deployment possible.

## **Ability to Scale at Each Microservices Level**

This is important to keep in mind because a given service may get more traffic than other services.

Monolithic applications are difficult when scaling individual portions of the application. If one service is memory-intensive and another is CPU-intensive, then the server must be provisioned with enough memory and CPU to handle the baseline load for each service. This can get expensive if each server needs a high amount of CPU and RAM, and is exacerbated if load balancing is used to scale the application horizontally. Finally, and more subtlety, the engineering team structure will often start to mirror the application architecture over time.

![main.png](https://lh3.googleusercontent.com/W287N5NQTrFbBA9VXRRW5qs7K4kgvHsNoJ2J4hNmX-VgfOvH8fhcxPu5TEFidEWXVBfBf34L6SoCnsQ1DM3xPmLIdAJtR7OcOKBbPYQiONtt1HsvHoTk9j0q03JDYUCqI9XF3bAx)

We can overcome this by using microservices. Any service can be individually scaled based on its resource requirements. Rather than having to run large servers with lots of CPU and RAM, microservices can be deployed on smaller hosts containing only those resources required by that service. For example, you can deploy a CPU-intensive image processing service on EC2 compute-optimized instances and deploy an in-memory database service on EC2 memory-optimized instances.

## **Ability to Build and Deploy Microservices Quickly**

One of the key drawbacks of the monolithic application is that it is difficult to scale. As explained in the above section, it needs to mirror the whole application to scale. With microservices architecture, we can scale specific services since we are deploying services in the isolated environment. Nowadays, dynamically scaling the application is very famous every iSaaS has that capability (i.e., elastic load balancing). With that approach, we need to quickly launch the application in the isolated environment.

Following are the basic deployment patterns that we can commonly see in the industry.

![multipleservice.png](https://lh3.googleusercontent.com/yKqYr24-RPsp3n-Cn9x5njugvac_c3W6ua1yj_qDBnosh-V0c8MVrQEkPhhHTyDLjMeul18b0Kdisk41YBy6MQzGmAmzNgX5Z1CZZ0wYkk3NtoTj8roLHAGK0KuW914Pxmn8IsmN)

_Multiple service instances per host: Deploy multiple service instances on a host._

![multiHost.png](https://lh3.googleusercontent.com/gB7bJMVehS-MQztxI_M2u-ySEWok-E7TsqjnJUzR2CJecG57Ebs9uuNtj8XzgwWTSzUr27Gc7GNnCqsv_-Pkx8a5I_vwDc3IX2I7feU_jPxlnh3H0M9Du__FRG7Z5s6jaupj8mUf)

> _Service instance per host: Deploy a single service instance on each host._

![VM.png](https://lh6.googleusercontent.com/8xWwf0IJH29cnhSQ3adfqrp2R5zeHAFGWTJ4DQtkN03AAGY0jhIYhmw9M3qihllP-X_Y_Vsd1-go4crdTGtE2DKejQg6plC5n3pbb8tN5gvn-zpYDUtuxzOPPGseII1-X1AgHGpi)

_Service instance per VM: A specialization of the service instance per host pattern where the host is a VM._

![container.png](https://lh4.googleusercontent.com/SZOW5qwksvg3Pd47Q4SB-IoNQzfdVyiuYQ06SbrcFL--F-LdQwMBf4_KeCOopcMB7XOVDt46Fc3NH9bpfH8uUvNRRd41rBwa-pzbKakDNBkIF6yRoUl4b4e3TJufLPCc_HPzva8r)

_Service instance per container: A specialization of the service instance per host pattern where the host is a container._

## Container or VM?

As of today, there is a significant trend in the industry to move towards containers from VMs for deploying software applications. The main reasons for this are the flexibility and low cost that containers provide compared to VMs. Google has used container technology for many years with [Borg & Omega](http://static.googleusercontent.com/media/research.google.com/en//pubs/archive/43438.pdf) container cluster management platforms for running Google applications at scale.

More importantly, Google has contributed to container space by implementing cgroups and participating in the libcontainer project. Google may have gained a huge gain in performance, resource utilization and overall efficiency using containers during the past years. Very recently, Microsoft (who did not have an operating system-level virtualization on the Windows platform) took immediate action to implement native support for containers on Windows Server.

![VM_vs_Docker.png](https://lh4.googleusercontent.com/iLhxf_HnA8O8MzUl7vEzFJxPU26HO1j9RmjTfD0y49OoZPvsrKX6UNC2xWhRKPjRQS7oIUd9r6w_Cvfy5e9ygfbkf80bpCGopFjYhPkPxYqAscYrEZe2vZHkGzSjYM0MfFhE3ug9)

I found a nice comparison between the VMS and containers on the internet comparing houses and apartments. Houses (the VMs) are fully self-contained and offer protection from unwanted guests. They also each possess their own infrastructure -- plumbing, heating, electrical, etc. Furthermore, in the vast majority of cases, houses are all going to have at a minimum a bedroom, living area, bathroom, and kitchen. I've yet to ever find a "studio house." Even if I buy the smallest house, I may end up buying more than I need because that's just how houses are built.

Apartments (the containers) also offer protection from unwanted guests, but they are built around shared infrastructure. The apartment building (Docker host) shares plumbing, heating, electrical, etc. Additionally, apartments are offered in all kinds of different sizes, from studios to multi-bedroom penthouses. You're only renting exactly what you need. Finally, just like houses, apartments have a front entrance.

There are design-level differences between these two concepts. Containers share the underlying resources while providing the isolate environment and only provide the resources that are needed to run the application. VMs are different. They first start the OS and then start your application. It's providing a default set of unwanted services that consume the resources.

Before moving into the actual comparison, let's see how we can deploy a microservices instance in any environment. The environment can be single or multi-host in the single VM or it can be the multiple container in the single VM, a single container in the single VM, or a dedicated environment. It is not just starting application on the VM or deploy application in the web container. We should have an automated way to manage it. AWS provides nice VM management capability for any deployment. If we use VM for deployment, we normally build the VM with the required application component. Using this VM, we can spawn any number of different instances.

Similar to AWS VM management, we need some container management platform for the container as well because when we need to scale the specific service, we cannot manually monitor the environment and start a new instance. It should be automated. We can use Kubernetes. It is extending Docker's capabilities by allowing to manage a cluster of Linux containers as a single system, managing and running Docker containers across multiple hosts, offering co-location of containers, service discovery, and replication control.

Both VM and containers are designed to provide an isolated environment. Additionally, in both cases, that environment is represented as a binary artifact that can be moved between hosts. There may be other similarities but those are the major differences that I see.

In a VM-centered world, the unit of abstraction is a monolithic VM that stores not only application code but stateful data. A VM takes everything that used to sit on a physical server and just packs it into a single binary so it can be moved around. However, it is still the same thing. With containers, the abstraction is the application, or more accurately, a service that helps to make up the application.

When we scale up the instances, this is very useful because using VMs means we need to spawn another VM instance. It will take some time to start (i.e., OS boot time and application boot time) but with the Docker-like container deployment, we can start a new container instance within a few milliseconds.

Another important factor is patching the existing services since we cannot develop the code without any issues. We need to patch the code. Patching the code in a microservices environment is a little bit tricky because we may have more than 100 of instances to patch. If we get the VM deployment, we need to make the new VM image by adding new patches and use it for the deployment. It is not an easy task because there can be more than 100 microservices and we need to maintain different types of VM images, but with Docker-like container-based deployment, this is not an issue. We can configure Docker images to get these patched from configured place. We can achieve similar requirements with output script in the VM environment, but Docker has that capability out of the box. Therefore, the total config and software update propagation time would be much faster with the container approach.

A heavier car may need more fuel for reaching higher speeds than a car of the same spec with less weight. Sports car manufacturers always adhere to this concept and use light weight material such as aluminum and carbon fiber for improving fuel efficiency. The same theory may apply to software systems. The heavier the software components, the higher the computation power they need. Traditional virtual machines use a dedicated operating system instance for providing an isolated environment for software applications. This operating system instance needs additional memory, disk, and processing power in addition to the computation power needed by the applications. Linux containers solved this problem by reducing the weight of the isolated unit of execution by sharing the host operating system kernel with hundreds of containers. The following diagram illustrates a sample scenario of how much resources containers would save compared to virtual machines.

![RESOURCE.png](https://lh5.googleusercontent.com/3nXZhem-wH-RK8Fci7mm3WgKwTn60Bz5MR-JoMqtI3XB-cwbzUiQvwM3xc6sDNdFFu3HyWeCMMj1orzNl2ooTmmcjZE3fahdR5GK0lPVGU2_orPlUF0d5ShayCPSj1SLLS5yzizx)

We cannot say that container-based deployment is the best for microservices for every deployment. It is based on different constraints. We need to carefully select one or both as the hybrid way based on our requirements.

Discover the unprecedented possibilities and challenges, created by today's fast paced data climate and [why your current integration solution is not enough](https://dzone.com/go?i=171135&u=http%3A%2F%2Fbit.ly%2F2aydpMZ%25C2%25A0), brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=171135&u=http%3A%2F%2Fbit.ly%2F2aydpMZ%25C2%25A0)
