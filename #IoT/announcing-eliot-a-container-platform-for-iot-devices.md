# Announcing Eliot: A Container Platform for IoT Devices

_Captured: 2018-02-13 at 15:44 from [dzone.com](https://dzone.com/articles/announcing-eliot-a-container-platform-for-iot-devices?edition=361106&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-02-13)_

I'm super excited to tell you about a project that I have been working on in my free time for the past few months. [Eliot](http://www.eliot.run) is [Docker](https://www.docker.com)\- and [Kubernetes](https://kubernetes.io)-inspired platform for managing containers in IoT devices, and it's [available under the MIT open source license](https://github.com/ernoaapa/eliot).

While I was working for a drone company building a drone-based automated inspection service, I was surprised that there's no state-of-the-art solution for managing software in the connected devices that are common nowadays in cloud environments.

Most solutions were clumsy, error-prone "manually-install-and-copy-image" solutions. OTA (over-the-air) solutions were mostly outdated or otherwise unusable for the modern continuous delivery world, not to mention they had poor security. And all IoT platforms were basically just agents to push data to some cloud service for analysis.

Requirements:

  * No internet connection required
  * Good configuration management
  * Easy development and debugging in the device
  * Simple and fast application deployment and updates
  * Good security and software isolation
  * Built for connected devices from ground up

And that's the day Eliot was born. ️

## Open Source From the Heart

In Eliot, everything runs inside containers. It's like [CoreOS](https://coreos.com) or [Kubernetes](https://kubernetes.io) in the sense that there's pretty much only a Linux kernel and a small agent in the OS. Everything else gets deployed to the device in containers. This makes managing and updating software on the device really easy, and the attack surface for hackers is minimal.

![](https://cdn-images-1.medium.com/max/2000/1*R4gGgH46JufSwmJDDorqVg.jpeg)

> _Eliot is built on top of open source components that are already in use by millions of users_

Eliot uses [containerd](https://github.com/containerd/containerd) to run containers. containerd is the container runtime from the core of Docker. It was recently [open sourced by Docker Inc.](https://blog.docker.com/2017/12/cncf-containerd-1-0-ga-announcement/) It's used everywhere Docker is used, and that's almost everywhere

It uses [linuxkit](https://github.com/linuxkit/linuxkit), another open source project from Docker Inc., to build a minimal operating system to run containers. EliotOS is less than 70MB, which is small compared to, for example, Raspbian's 1.5GB!

To make the life of developers and operators as easy as possible, Eliot provides a nice "Kubernetes-like" interface on top of these open source components while keeping the setup small and secure.

You don't need to switch your chosen IoT tool or platform to collect and process data in the cloud -- Eliot just helps you manage device configuration and software more easily. For instance, you can use Eliot to deploy your IoT platform to the device. It probably makes your life even easier because the community can share common building blocks as images in [Docker Hub](https://hub.docker.com).

## Getting Started

Connecting to Eliot-enabled device is super easy. You don't need to figure out what IP address the device has or hard-code static IPs -- just ask Eliot to list devices, and it will take care of it on your behalf.

Eliot discovers devices in the same network automatically with a technique called [Zeroconf](https://en.wikipedia.org/wiki/Zero-configuration_networking). When your PC "magically" find printers from the network or when you start playing the YouTube video in your Chromecast, you actually use the same technology.

> It's the same magic that Apple, Google, Microsoft uses to make your life easier 

## Running Containers

To run a container on your device, you can use the same command that you're used to already when you run containers locally with Docker -- just change the `docker` command to `eli`.

Running containers in a device is usually for one-time ad-hoc testing, and that's why, by default, Eliot deletes the container when you exit from the process. To deploy containers permanently, you need to create a Pod.

## Deploying Containers

The core concept in Eliot is Pods. That might sound familiar if you have used Kubernetes. A Pod is the basic building block of Eliot and is the main model object that you deploy and manage. A Pod groups one or more containers together that are meant to be started, deployed, and deleted together.

You can list all running Pods with `eli get pods`

And get more detailed information with `eli describe pod <name>`, just like in Kubernetes:

## Accessing the Container

I won't list all of Eliot's features here, but I'll show you one more thing. Often, you need to get access to a device and container for debugging or to run some command.

With Eliot, you don't need to start setting up SSH or some other terminal access -- all you need to do is ask Eliot to execute a shell in the container and connect your local terminal session with it.

Now that's cool, right?!

And at the end, we clean up the device by removing all Pods. It's fresh like the beginning of the day!

## Like It While It's Hot!

I would really appreciate if you drop me a ️star on GitHub so I'll get my dopamine boost and keep pushing new features out!

Eliot is in an early phase, but it already implements the most important functionalities to manage containers. Furthermore, getting started with a Raspberry PI 3 is easy with EliotOS.

Check out the documentation at [http://docs.eliot.run](http://docs.eliot.run/installation.html) and the source code at <https://github.com/ernoaapa/eliot>.
