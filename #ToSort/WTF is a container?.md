# WTF is a container?

_Captured: 2016-10-18 at 17:46 from [techcrunch.com](https://techcrunch.com/2016/10/16/wtf-is-a-container/)_

[Source](https://techcrunch.com/2016/10/16/wtf-is-a-container/ "Permalink to WTF is a container?  |  TechCrunch")

You can't go to a developer conference today and not hear about software containers: Docker, Kubernetes, Mesos and a bunch of other names with a nautical ring to them. Microsoft, Google, Amazon and everybody else seems to have jumped on this bandwagon in the last year or so, but why is everybody so excited about this stuff?

To understand why containers are such a big deal, let's think about physical containers for a moment. The modern shipping industry only works as well as it does because we have standardized on a small set of shipping container sizes. Before the advent of this standard, shipping anything in bulk was a complicated, laborious process. Imagine what a hassle it would be to move some open pallet with smartphones off a ship and onto a truck, for example. Instead of ships that specialize in bringing smartphones from Asia, we can just put them all into containers and know that those will fit on every container ship.

The promise behind software containers is essentially the same. Instead of shipping around a full operating system and your software (and maybe the software that your software depends on), you simply pack your code and its dependencies into a container that can then run anywhere — and because they are usually pretty small, you can pack lots of containers onto a single computer.

Why is this such a big deal? Before containers became popular, so-called "virtual machines" were the go-to technology to allow a single server to run lots of different applications that were isolated from each other. That's the technology that made the first generation of cloud applications (and even web hosting services) possible. If you had to spin up a new server for every application, the cost would have gone through the roof.

The way virtual machines work, however, is by packaging the operating system and code together. The operating systems on the virtual machines believes that it has a server to its own, but in reality, it's sharing the server with a bunch of other virtual machines — all of which run their own operating systems and don't know of each other. Underneath it all is the host operating system that makes all of these guests believe they are the most important thing in the world. You can see why this is a problem. The guest virtual machines basically run on emulated servers, and that creates a lot of overhead and slows things down (but in return, you could run lots of different operating systems on the same server, too).

In the context of talking about shipping containers (and to take that metaphor to its absurd end), that's akin to having a big container ship with lots of little pools that all feature their own small specialized container ship.

Containers work very differently. Because they only contain the application and the libraries, frameworks, etc. they depend on, you can put lots of them on a single host operating system. The only operating system on the server is that one host operating system and the containers talk directly to it. That keeps the containers small and the overhead extremely low.

Virtual machines use so-called "hypervisors" as the emulation layer between the guest and host operating system. For containers, the rough equivalent is the container engine, with the Docker Engine being the most popular one right now.

Containers became a core feature of Linux a long time ago, but they were still hard to use. Docker launched with the promise of making containers easy to use and developers quickly latched onto that idea.

Containers simply make it easier for developers to know that their software will run, no matter where it is deployed. They also enable what's often called "microservices." Instead of having one large monolithic application, microservices break down applications into multiple small parts that can talk to each other. This means different teams can more easily work on different parts of an application and, as long as they make no major changes to how those applications interact, they can work independently of each other. That makes developing software faster and testing it for possible errors easier.

To manage all of these containers, you need another set of specialized software like Kubernetes (which Google originally developed) that helps you push those containers out to different machines, makes sure that they run and lets you spin up a few more containers with a specific application when demand increases. And if you want containers to know about each other, you also still need some way of setting up a virtual network, too, that can assign IP addresses to every container.

Containers can run all kinds of applications, but because they are so different from virtual machines, a lot of the older software that many big companies are still running doesn't translate to this model. Virtual machines can help you move those old applications into a cloud service like AWS or Microsoft Azure, however, so even though containers have their advantages, virtual machines aren't going away anytime soon.

