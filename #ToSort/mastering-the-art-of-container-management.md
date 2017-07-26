# Mastering the Art of Container Management

_Captured: 2017-05-14 at 21:53 from [dzone.com](https://dzone.com/articles/mastering-the-art-of-container-management?edition=298100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-14)_

Learn how our [document data model](https://dzone.com/go?i=214229&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Ddb%26jmp%3Ddzone-ad) can map directly to how you program your app, and native database features like secondary indexes, geospatial and text search give you full access to your data. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=214229&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Ddb%26jmp%3Ddzone-ad).

Managing containers in cloud environments would be a lot simpler if there were just one type of container you and your staff needed to deal with. Any technology as multifaceted as containerization comes with a bucket full of new management challenges. The key is to get ahead of the potential pitfalls before you find yourself hip deep in them.

The simplest container scenario is packaging and distributing an existing application as a Docker container: all of the app's dependencies are wrapped into a Docker image, and a single text file (Dockerfile) is added to explain how to create the image. Then each server can run only that instance of the container, just as the server would run one instance of the app itself.

Monitoring these simple containers is the same as monitoring the server, according to TechTarget's Alastair Cooke in an [April 2017 article](http://searchitoperations.techtarget.com/feature/What-admins-need-to-know-to-master-containerization-technology). The app's use of processes and resources can be viewed on the server. There's no need to confirm that the server has all the required components because they're all encapsulated in the Docker image and controlled by the Docker file, including the proper Java version and Python libraries.

## **How Containers Alter Server Management Tasks**

Placing apps in a Docker container means you no longer have to update and patch Java on the server. Instead, you update the Dockerfile and build a new Docker image. In fact, you may not need to install Java on the server at all. You'll have to scan the Docker files for vulnerabilities and unsupported components in the image. You may also need to set and enforce policies relating to the maximum age of Docker images because dependency versions are set inside the image and can only be updated by creating a new image.

![](https://assets.morpheusdata.com/SpudMedia/1063/attachment/04_10_17_containers1_original.png)

> _By removing a layer of software from the standard virtualization model, containers promise performance increases of 10 percent to 20 percent. Source:_

_[Conetix](https://www.conetix.com.au/blog/cloud-and-container-based-hosting)_

Containers can be started and stopped in a fraction of a second, making them a lot faster than VMs. Microservice-enabled apps will use far more containers, most of which have short lifespans. Each of the app's microservices will have its own Docker image that the microservice can scale up or down by creating or stopping containers. Standard server monitoring tools aren't designed for managing such a fast-changing, dynamic environment.

## **Overcoming Obstacles to Container Portability**

Since your applications rely on data that lives outside the container, you need to make arrangements for storage. The most common form is local storage on a container cluster and the addition of a storage plug-in to each container image. For public cloud storage, AWS and Azure use different storage services.

TechTarget's Kurt Marko explains in an [April 2017 article](http://searchitoperations.techtarget.com/tip/Overcome-app-portability-hurdles-of-containers-in-cloud-computing) that Google Cloud's Kubernetes cluster manager offers more flexibility than Azure or AWS in terms of sharing and persistence after a container restarts. The shortcoming of all three services is that they limit persistent data to only one platform, which complicates application portability.

Another weakness of cloud container storage is inconsistent security policies. Applying and enforcing security and access rules across platforms is never easy. The foundation of container security is the user/group directory and the identity management system that you use to enforce access controls and usage policies.

## **Containers or VMs? The Factors to Consider**

The difference between containers and VMs is where the virtualization occurs. VMs use a hypervisor to partition the server below the OS level, so VMs share only hardware. A container's virtualization occurs at the OS level, so containers share the OS and some middleware. Running apps on VMs is more like running them on bare metal servers. Conversely, apps running on containers have to conform to a single software platform.

![](https://assets.morpheusdata.com/SpudMedia/1065/attachment/04_12_17_containters2_original.png)

> _VMs offer the flexibility of bare metal servers, while containers optimize utilization by requiring fewer resources to be reserved. Source:_

_[Jelastic](http://blog.jelastic.com/2016/12/01/containers-configuration-guide-for-complex-java-applications/)_

On the other hand, containers have less overhead than VMs because there's much less duplication of platform software as you deploy and redeploy your apps and components. Not only can you run more apps per server, containers let you deploy and redeploy faster than you can with VMs.

[TechTarget](http://searchcloudcomputing.techtarget.com/tip/Containers-vs-VMs-Which-should-you-use-for-cloud)'s Tom Nolle highlights a shortcoming of containers in hybrid and public clouds: co-hosting. It is considered best practice when deploying an application in containers to co-host all of the app's components to speed up network connections. However, co-hosting makes it more difficult to manage cloud bursting and failover to public cloud resources, which are two common scenarios for hybrid clouds.

Cloud management platforms show the eroding distinctions between containers and VMs in terms of monitoring in mixed-cloud environments. It will likely take longer to bridge the differences between containers and VMs relating to security and compliance, according to Nolle.

Discover when your data grows or your application performance demands increase, MongoDB Atlas allows you to scale out your deployment with an [automated sharding process](https://dzone.com/go?i=214230&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Ddb%26jmp%3Ddzone-ad) that ensures zero application downtime. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=214230&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Ddb%26jmp%3Ddzone-ad).
