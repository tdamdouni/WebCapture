# Docker For Developers

_Captured: 2017-03-13 at 13:52 from [dzone.com](https://dzone.com/articles/docker-for-developers?utm_source=Docker%20Bundle&utm_campaign=Monday%20Email%202017-03-13&utm_medium=email)_

Docker is a container technology which wraps up a piece of software in a complete filesystem that contains everything it needs to run: code, runtime, system tools, system libraries -- anything you can install on a server. This guarantees that it will always run the same, regardless of the environment it is running in.

Docker is a tool that is designed to benefit both developers and system administrators, making it a part of many DevOps (developers + operations) toolchains. For developers, it means that they can focus on writing code without worrying about the system that it will ultimately be running on. It also allows them to get a head start by using one of the thousands of programs already designed to run in a Docker container as a part of their application.

As a developer you do not need to know every detail Docker administration, all you need to know is going to be cleared in this article.

I assume you can download, install docker for your box using the Docker official page.

Docker runs behind a virtual machine both on Windows and Mac. So we first have a look at docker-machine which manages Docker's virtual machine.

We use `docker-machine ls` for checking our docker-machine/s.

The "default" docker-machine is created as a result of the installation process. You can drop it and create a new one if you want.

In order to drop it, we use the following command.

As we run the "ls" command again, we will see nothing.

Now we will create a new docker-machine in order to proceed with our tutorial. Here, I'll name it "softlab". We will use Oracle's VirtualBox as the driver -- for other drivers, you can check [here](https://docs.docker.com/machine/drivers).

If you want to dive into the newly created softlab docker-machine, we use the 'docker-machine ssh softlab'

We use the `stop` command to stop the docker-machine and `start` to start the docker-machine. See the following shell samples.

We need the environment variables set in order to configure our shell to use Docker. We can get those variables with the 'env' command.

As stated in the output, we need to set these variables via eval `$(docker-machine env softlab)`.

Now we are ready to run Docker containers on our docker-machine. First, we will run the hello world container.

Let's check our containers with the `ps` command.

Nothing, because the 'hello world' container just started and stopped, and the 'ps' command shows only the running containers. If we want to see all the containers regardless of whether they are running, we should pass the '-a' parameter.

Now let's try a web server,

Here:

  * -d means the container should run detached. The container will run in the background and print the container ID.

  * -p is used to configure the container's port reflection on the host. Remember, the host is the docker-machine, not your localhost. Here, the 80 port of the container will be reflected to the host's 80 port. If we hit to the host:80 it would hit to the container's port 80.

  * \--name is used to assign a name to our container. If you omit this parameter, Docker will make it up for you, like in the previous example.

Let's run ps again;

See the status column, it says that our webserver containers, which are created from the nginx image, are still running. Now I am going to hit the host's port 80 and hope to see nginx's welcome page. Before that, I need to find the host's IP. I will use the ip command on the docker-machine.

In order to stop the webserver container, we will use the `docker stop` command.

If you want to dive deeper, please see my article about [Developing a Java 8 Spring Boot App in Docker](https://dzone.com/articles/developing-java8-springboot-application-in-docker).
