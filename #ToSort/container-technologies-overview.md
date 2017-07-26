# Container Technologies Overview

_Captured: 2017-06-09 at 22:49 from [dzone.com](https://dzone.com/articles/container-technologies-overview?edition=304154&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-09)_

What if you could learn how to use [MongoDB](https://dzone.com/go?i=219242&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad) directly from the experts, on your schedule, for free? We've put together the ultimate guide for learning [MongoDB](https://dzone.com/go?i=219242&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad). [Sign up](https://dzone.com/go?i=219242&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad) and you'll receive instructions for how to get started!

Containers are lightweight OS-level virtualizations that allow us to run an application and its dependencies in a resource-isolated process. All the necessary components that are required to run an application are packaged as a single image and can be re-used. While an image is executed, it runs in an isolated environment and does not share memory, CPU, or the disk of the host OS. This guarantees that processes inside the container cannot watch any processes outside the container.

![OS Virtualization](https://dzone.com/storage/temp/5512186-os-virtualization-3dc0f783ebbd0da25183f5af863e1c2b.jpg)

> _OS Virtualization_

## **Difference Between Virtual Machines and Containers**

Virtual machines generally include entire operating system along with the application. They also need a hypervisor running along with them to control the VM.

As they include the operating system, therefore their size is of several gigabytes. One of the downsides of using VMs is that they take up several minutes to boot up the OS, and they initialize the application they are hosting. At the same time, the containers are lightweight and are, mostly, in the megabytes size range. Comparing their performance to VMs, containers perform much better and can start almost instantly.

![VM vs Containers](https://dzone.com/storage/temp/5512194-windows-server-virtual-machines-vs-containers.png)

> _VM vs Containers_

## **What Problems Do Containers Solve?**

Many problems come to light when the application computing environment changes. This could be when a developer pushes code from the dev environment to a test environment, and then further on. For example: A developer wrote the application code in Windows, but the upper environment(s) (test, stage, or prod) are Linux-based. In such a case, there is the chance that some functionality will stop working when the OS changes. So, basically, when the supporting software environment is not identical, then the chances of intermittent failure are higher.

As Solomon Hykes, the creator of Docker, says "You're going to test using Python 2.7, and then it's going to run on Python 3 in production and something weird will happen. Or you'll rely on the behavior of a certain version of an SSL library and another one will be installed. You'll run your tests on Debian and production is on RedHat and all sorts of weird things happen."

The change may not be just of the computing environment, but can also be of the network. Hykes also added that "the network topology might be different, or the security policies and storage might be different, but the software has to run on it."

## **Advantages of Containers**

  1. **Agile environment**: The biggest advantage in favor of container technologies is that they can be created much faster than VM instances. Their lightweight footprint enables less overhead in terms of performance and size.

  2. **Enhanced productivity**: Containers increase developer productivity by removing cross-service dependencies and conflicts. Each container can be seen as a different microservice and thus can be independently upgraded without any concerns regarding their sync.

  3. **Version control**: Each image of a container can be version controlled, thus enabling tracking of different versions of the container, watch out for differences between versions, etc.

  4. **Computing environment portability**: Containers encapsulate all the relevant details like application dependencies and operating systems, which are essential to run the application. This helps ease the portability of the container image from one environment to another. For example, the same image can be used to run in Windows/Linux or dev/test/stage environments.

  5. **Standardization**: Most containers are based on open standards and can run on all major Linux distributions, Microsoft, etc.

  6. **Secure**: Containers isolate the processes of one container with another one and the underlying infrastructure as well. Thus any upgrade or changes in one container do not affect another container.

## **Disadvantages of Containers**

  1. **Increased complexity**: With _n_ number of containers running an application, there is an increase in the complexity factor as well. Management of so many containers can be a challenging task in a production environment. Tools like Kubernetes and Mesos can be utilized to manage _n_ number of containers.

  2. **Native Linux support**: Most container technologies, such as Docker, are based on Linux containers (LXC). Therefore, running these containers on a Microsoft environment is a bit clumsy and their daily use can bring up complications, compared to running these instances on Linux natively.

  3. **Immature**: Container technology is relatively new in the market and thus the time to market is slow. The number of resources available is limited among developers, and if one is stuck with some problem, it may take some time to figure out the solution.

## **Container Classifications**

**OS containers**: As per Wikipedia, "Operating-system-level virtualization is a computer virtualization method in which the kernel of an operating system allows the existence of multiple isolated user-space instances, instead of just one. Such instances, which are sometimes called containers, virtualization engines (VEs) or jails (FreeBSD jail or chroot jail), may look like real computers from the point of view of programs running in them."

As stated, they share the kernel of the host operating system but provide user space isolation. Different applications can be installed, configured, and can run just like we run applications on a host OS. Similarly, the resources assigned to a container are visible to that container only. Any other guest OS image will not be able to access resources of another guest OS.

They are useful when there is a need to configure a fleet of OSs having identical configurations. Thus, it helps in creating templates, which can be used to create a similar flavor to another OS.

To create OS containers, we can leverage container technologies like LXC, OpenVZ, Linux VServer, BSD Jails, and Solaris zones.

![OS vs App Containers](https://dzone.com/storage/temp/5512204-os-vs-app-containers-a3f09c304838c7687273371874f61.jpg)

> _OS vs App Containers_

**Application containers**: As per Wikipedia, "Application virtualization is software technology that encapsulates computer programs from the underlying operating system on which it is executed. A fully virtualized application is not installed in the traditional sense, although it is still executed as if it were. The application behaves at runtime like it is directly interfacing with the original operating system and all the resources managed by it, but can be isolated or sandboxed to varying degrees.

In this context, the term "virtualization" refers to the artifact being encapsulated (the application), which is quite different from its meaning in hardware virtualization, where it refers to the artifact being abstracted (physical hardware).

Application containers are designed to package and run services as a single process, whereas in OS containers, multiple services and processes can run.

Container technologies like Docker and Rocket are examples of application containers.

What if you could learn how to use [MongoDB](https://dzone.com/go?i=219243&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad) directly from the experts, on your schedule, for free? We've put together the ultimate guide for learning [MongoDB](https://dzone.com/go?i=219243&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad). [Sign up](https://dzone.com/go?i=219243&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad) and you'll receive instructions for how to get started!
