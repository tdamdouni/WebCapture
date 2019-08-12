# Docker For Beginners

_Captured: 2018-02-25 at 18:58 from [dzone.com](https://dzone.com/articles/docker-for-beginners?edition=364096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-25)_

## What is a Container ?

A container is just a way to achieve process isolation. Unlike virtual machines, they don't achieve isolation by simulating hardware, but by using existing Linux kernel features.

In a typical Unix/Linux OS all processes share the same user space, but with the introduction of new features in Linux 2.6+, you can create a process that has its own particular set of isolated contexts like file tree, threads, etc. These features in combination with other kernel technologies are the magic behind containers.

In this article I will introduce basic Docker commands and concepts. After you finish reading, you will be able to adopt some Docker capabilities to accelerate and simplify your day-to-day workflow.

## Installing Docker

Installation of Docker is a simple task in OS X/Windows using the installation wizard. You can find the installer for your OS on the Docker community page. On Linux, Docker is usually available in the distribution package manager.

Installing Docker in [Fedora](https://getfedora.org/es/workstation/):

To start the process:

To make the Docker process start and boot time:

The steps should be similar in others Linux distributions that use Systemd.

## Getting Started

Once you finished the installation we should try a small **Hello World!** for containers:
    
    
    sudo docker run --name hello -it busybox echo "Hello World!" # Hello World!

Using **sudo** is only necessary if you are running some Linux distributions, but keep in mind that Docker require admin rights to create the containment. In OSX and Windows at the moment of writing this article use some Linux-based virtual machine behind the scenes, so Docker commands can be run without privileged users in those systems.

### How It Works

The `run` option creates and run a container, one of the properties is that Docker binds the life of the container to the running process (in this case the Linux command echo), which means that when process finish the container will be terminated.

  * **Name:** We set the name of the container, if you don't choose anything Docker will choose one at random.
  * **It: **This mean interactive, it will connect our terminal to the output of the container virtual TTY, allowing interact with the running process.
  * **Busybox:** This the base image to create the container, think of it as zip file with the files and folders necessary to run the desired application. There is a whole community base images available in [Docker Hub](https://hub.docker.com/), I use [busybox](https://hub.docker.com/r/library/busybox/tags/) because is very light just 715 KB compressed.
  * **Echo: ** As we mentioned earlier, `echo`is the command we try to execute that is included inside the [busybox](https://hub.docker.com/r/library/busybox/tags/) image.

If you want check the commands available in [busybox](https://hub.docker.com/r/library/busybox/tags/) just do this:

When you execute the Docker command for the first time the image is downloaded and is cached to speed up things. You can check local images by using this command:

In some cases we don't want to interact directly with some applications like servers, in this case we want to spawn the process and get back our terminal to continue doing some work, Docker provide us a way to execute the process in daemon mode using the **-d** parameter like this:

This process will run for 15 seconds in the background and then exit.

#### Listing Background Running Containers

Once the container is running in the background, you can check its status with **ps**:

To stop a container is simple:

This command will stop the running container, but the Docker service will keep the container you created including its associated command cached in disk. If you want to replay the exact command again you just need to execute:

If you want to change the configuration and reuse the container name then you need to stop and delete the container, let say we want to change our _snooze_ container, to sleep for 10 seconds instead of 15:

The **v** parameter will allow us to mount/map a folder from the **_host_** (our computer) to a folder inside the container.

Let's create a file:

Now we want to open the file using an isolated text editor available in busybox:

Nothing happens, this is because the vi process we are calling is isolated and is unable to access the file outside the contained area. To solve this, we need to mount the folder so our editor is able to find the file.

This will mount the actual folder `$(pwd`, to the folder `/app` inside the container. If the folder doesn't exist _inside_ it will be created, then, we use **vi** and pass the location of file of the mounted folder `vi app/hello`.

Some observations:

  * The **v** will overwrite any previous folder inside the container. If it exists it will be replaced with the provided folder.
  * This command literally mount the folder, so every change made by the container to this folder will be persisted once the container has been killed, this can be a good idea if you want a DB to persist its data beyond container lifecycle.
  * The container will have access to your system resource (the shared folder) so be careful.

### Networking

Option **p** allow us to expose an isolated port and pass it through a specific **Host** port.

To illustrate how networking works with containers, first let's start by writing a simple Javascript script to startup a server. We are going to do this in our local machine, so let's write some code.

We will call this file **index.js** it basically create a server that waits for connection in port **8080.** When somebody connects it will send a `Hello World!`

Next step is to run our script inside a container. We can do this by writing the following command:
    
    
    sudo docker run -it -v "$(pwd)":/app:z --name myserver mhart/alpine-node node app/index.js

The new stuff here is the base image **mhart/alpine-node** it will pull a Node.JS container, then will just mount using **-v** the folder as we did before and then execute the isolated _node app/index.js_ process.

Let see if our server is working:

This command tests that our server is working from within the container and we should get back `Hello World%` **. **Now let's try to connect from our **Host**, open a new terminal, and write:
    
    
    #curl: (7) Failed to connect to localhost port 8080: Connection refused

We are unable to connect because the container network is isolated; we need to pull the port forward:
    
    
    sudo docker run -it -v "$(pwd)":/app:z -p 8080:8080 --name myserver \
    
    
     mhart/alpine-node node app/index.js

Now try to open [http://locahost:8080](http://locahost:8080/) in your browser and you should see a `hello world!`

Congrats!, you have wroted a nice contained NodeJS application. One of the greatest advantage is that you can do this without installing NodeJS and you can use this capability to install other kind of software like DB's, other microservices, etc.

## Some Quick Tips

In my day to day I always need to integrate with MongoDB and Redis, but installing those are usually a painful process, I have solved this problem by creating some bash scripts in my .zshrc.
    
    
      docker run -d --name mongodb -p  27017:27017 mongo
    
    
    # the : here means image tag, usually if the image is done correctly 
    
    
    # like in this case tag version match the Redis version
    
    
      docker run -d  --name redis  -p 6379:6379 redis:3.2

After adding this line to the bottom of your .bashrc
.zshrc , then just execute `source ~/.bashrc || source ~/.zshrc`, then you should be able to do this.

Now you will be able to deploy a local MongoDB or Redis instance on-demand with zero configuration, and one advantage (at least in my view) is that the data in these instances are ephemeral, meaning that when you terminate the container it will reset the database as well, releasing the occupied space.

If you execute to mount a folder by using **v** parameter in Fedora you may get this error:
    
    
    sudo docker run -it -v "$(pwd)":/app busybox ls app/text

This is because [SELinux](https://en.wikipedia.org/wiki/Security-Enhanced_Linux) default policy will protect any read/write in the Host, in case an attacker can get out of the container, SELinux will hold your back by enforcing security rules at Kernel level.

To mount the folder in a SELinux aware machine you need to pass the **z** parameter, this will change the SELinux context and will allow the container to perform the mounting.
    
    
    # "$(pwd)" will get the actual directory, is equivalent to do pwd
    
    
    docker run -it -v "$(pwd)":/app:z busybox /bin/sh

Another way (but not recommended) to do this is to temporarily disable this protection with:

Then after you finish you can enable it by doing:
