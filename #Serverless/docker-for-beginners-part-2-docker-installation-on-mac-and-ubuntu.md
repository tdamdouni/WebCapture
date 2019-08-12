# Docker for Beginners Part 2: Docker Installation on Mac and Ubuntu

_Captured: 2018-02-20 at 15:04 from [dzone.com](https://dzone.com/articles/docker-for-beginners-part-2-docker-installation-on?edition=362118&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-02-20)_

This is the **Part 2** from the Docker series, [Docker for Beginners in 8 Parts](https://blog.hackingcode.io/docker-for-beginners-tutorial-in-8-parts). In this post we're going to see the an overview about the **Docker installation**.

  * [Part 1](https://blog.hackingcode.io/docker-for-beginners-tutorial-containers-versus-virtual-machine) \- Differences between Containers and Virtual Machines
  * [Part 3](https://blog.hackingcode.io/docker-for-beginners-tutorial-docker-images-and-containers) \- Docker Images and Containers

Docker is the new hype is not just hype anymore and you're probably already working with it, even without knowing it!

Docker brings to us the ability to create applications **without worrying about its environment**. Your **production** environment could be the same as the **development** environment. Yes, I know, I know, seems suspicious.

With Docker, we can create, for example, 3 **isolated environments** that can be executed in a **single machine** at the same time, simulating your production, development and stage environment. You'll see that this is pretty easy.

![](https://i0.wp.com/blog.hackingcode.io/wp-content/uploads/2018/01/docker-for-beginners-tutorial-works-on-my-machine.jpg?w=1080&quality=100&ssl=1)

_It's time to avoid that with Docker._

**We're not** going to see a detailed way to install Docker because this is really well covered by the official [Docker documentation](https://docs.docker.com/)! Let's just see a fast overview of how to do it, straight to the point!

### Installing Docker on Mac

Just install the **Docker for Mac**

Make the [download](https://store.docker.com/editions/community/docker-ce-desktop-mac) in the Docker site and have fun with your **.dmg** and the drag and drop style.

![](https://i1.wp.com/blog.hackingcode.io/wp-content/uploads/2018/01/docker-for-beginners-mac-installation.png?w=1080&quality=100&ssl=1)

> _A few words about Docker for Mac:_

  * By default Mac does not have Docker without a Virtual Machine
  * A Virtual Machine with a **minimal Linux distro** will be installed
  * You can use the Stable or Edge version
  * You can configure Proxies and VPNs if you want

We're going to see a detailed post later about how Docker works in Mac.

### Installing Docker on Ubuntu

![](https://i1.wp.com/blog.hackingcode.io/wp-content/uploads/2018/01/docker-for-ubuntu-installation-tutorial.png?w=1080&quality=100&ssl=1)

To do that, we need to follow the steps below. Remember that the official site is really better than me and has a complete guide. Here we're going to see the installation from scratch but, again, straight to the point!

**1\. Let's update the apt package index!**

In this step we're just updating the **apt** package index to get new versions of packages, if there are any:

**2 - Install packages to allow apt to use a repository over HTTPS.**

This step is required because the **apt-transport-https** package enables us to use **https://** to install a package. In our case, this is necessary to install Docker from the address with [https](https://download.docker.com/linux/ubuntu).

**3 - Add Docker's official GPG key.**

**4 - Finding the last 8 characters of the fingerprint.**

In this step we'll just test if we already have the key associated with the [fingerprint](https://en.wikipedia.org/wiki/Fingerprint_\(computing\)). If everything is okay, you will see an output like this:

**5 - Use the following command to set up the stable repository.**

You can use the **stable**, **edge** or **test** repositories but we **always** need to install the **stable**, even if you're planning to use just the edge repository:

**6 - Let's update the apt package index again:**

**7 - Now we just need to install the Docker Community Edition**

Docker has an Enterprise Version and the steps to install it differs from this.

That's it! Simple and fast!

Let's move on and see the next post: [Part 3 - Docker Images and Containers](https://blog.hackingcode.io/docker-for-beginners-tutorial-docker-images-and-containers)

[Follow us](https://twitter.com/hacking_code) to keep up to date!
