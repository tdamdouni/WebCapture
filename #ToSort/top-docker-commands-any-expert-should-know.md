# Top Docker Commands Any Expert Should Know

_Captured: 2018-08-09 at 15:29 from [dzone.com](https://dzone.com/articles/top-docker-commands-itsyndicate?edition=388196&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-06)_

[Docker](https://www.docker.com/) is an evolving system with developers proactively working to improve usage and performance. So the commands are always changing. Docker commands often get deprecated and replaced with new or more efficient ones. You can use the help option to check the latest available commands on your Docker installation:

To check options for a particular command, you can use the help option for that command. For example, in order to check the `docker run` command options, you can use the following:

As a Docker expert, there are certain tasks you have to perform regularly. So, we'll organize the information into smaller parts. It will give you better context for running the various commands.

At the moment, there are 13 management commands and 41 general commands. Here are the top Docker commands we are going to use for our lessons:

  * `docker attach` \- Attaches your local input/output/error stream to a running container.
  * `docker commit` \- Creates a new image from the current changed state of the container.
  * `docker exec`\- Runs a command in a container that is active or running.
  * `docker history`\- Displays the history of an image.
  * `docker info`\- Shows system-wide information.
  * `docker inspect`\- Finds system-level information about docker containers and images.
  * `docker login`\- Logins to local registry or Docker Hub.
  * `docker pull`\- Pulls an image or a repository from your local registry or Docker Hub.
  * `docker ps`\- Lists various properties of containers.
  * `docker restart`\- Stops and starts a container.
  * `docker rm`\- Remove containers.
  * `docker rmi`\- Remove images
  * `docker run`\- Runs a command in an isolated container.
  * `docker search`\- Searches the Docker Hub for images.
  * `docker start`\- Starts already stopped containers.
  * `docker stop`\- Stops running containers.
  * `docker version`\- Provides docker version information.

You can find more detailed descriptions [here](https://docs.docker.com/engine/reference/commandline/docker/).

Let's dive into the various actions that you can perform with these Docker commands.

_Note: For partial information dumps, we have used three dots (...)._

## Finding Docker Version and System Information

Whether you are working on your own machine or working on the cloud, you'll often need to check the Docker version and the Docker system information. You can find out your Docker version using the command:

Another important command is `docker info`:

It will show you various important information like Server Version, Storage Driver, Kernel Version, Operating System, Total Memory and more. The information can be useful when you are trying to spin up new resources for your current Docker installation or trying to figure out a system-level resource allocation problem. It is also a quick way to check the number of running, paused and stopped containers and the number of images downloaded to your system.

## Searching and Downloading Docker Images

You can search for already available images on [Docker Hub](https://hub.docker.com/) with the `docker search` command.

The above search for `ubuntu` is showing the available images and their descriptions, stars, official statuses, and automated statuses. The stars, official and automated statuses are useful ways to figure out the reputation of the image.

Let's download the most reputable `ubuntu` image. You can use the `docker pull` command:

## Playing Around With Docker Images

You can use the `docker info` command to find out the number of images you have:

But the `docker images`command will list in detail the images you have:

Suppose you decide to download an [NGINX](https://www.nginx.com/) image. You can just run another `docker pull` command:

Now if you check your Docker images, you'll see something like this:

You can find out more about these images here:

You can use these pages to find out a particular version of an image. On the [Ubuntu](http://www.ubuntu.com/) page, you'll notice that the latest version of Ubuntu is 18.04. If you are looking for 16.04 version of Ubuntu, you can use the 16.04 tag to download that particular version:

Then you'll have two Ubuntu image versions on your machine:

_Note: You don't need to register with [Docker Hub](https://hub.docker.com/) to pull images. But if you want to push images to [Docker Hub](https://hub.docker.com/), you'll need to register and then login using the `docker login` command:_

## Running Docker Container for Images

Let's suppose you want to run an NGINX server on docker. Run the following command:

You have used the run command to create an NGINX container from the nginx image that you previously pulled from Docker Hub. The `'-p 8080:80'` is telling Docker to map your localhost port 8080 to Docker container's port 80. You should be able to access you NGINX server from `http://localhost:8080`.

The NGINX container is attached to your command line. So if you exit the command line, the container will die. You can start the NGINX container with the detach (`'-d'`) option, so it can keep running even if you exit the command line.

The above command will start the container in the detached mode and return back to the command line.

## List Docker Containers with the `docker ps` Command

The `docker ps` command allows you to look up all the containers you are running.

It shows the various properties of the containers. You can see that it has been created from the nginx image and the port forwarding information is also shown. The CONTAINER ID and NAMES property require special mention. You can use these properties to uniquely identify the containers. Both of these properties are auto-generated. But you can also name the container during the container creation process. Let's create an NGINX container with the name _"my_nginx"_:

Let's list Docker containers again:

> Notice the new container has the name **"my_nginx"**. When you are dealing with a lot of containers, you can use a naming convention. This will help you better organize the containers.

The `docker ps` command only shows running containers. If you use the `docker info` command for the above case:

You can see that there are 2 containers running. If you have a paused or stopped container, you will not see those containers with the `docker ps` command only. You'll have to use the all ( `'-a'`) option:

## Starting, Stopping, Restarting and Killing Containers

You can start and stop containers with use of next Docker commands.

Suppose, you want to stop the _'my_nginx'_ container. You can either use the CONTAINER ID or the NAME. In this case, let's use the name:

Let's list Docker containers:

If you run `docker ps` without the `-a` option, it only shows the running container. In the second case, you can see that the _'my_nginx'_ container is in exited status.

Let's `docker start` container:

If you check the list of Docker containers:

You can see that STATUS is showing that the container _'my_nginx'_ is up again.

If you want to stop and start a container due to some issue, you can use the restart command. It's faster than stopping and starting the containers individually:

You can kill a docker container like a process. Let's kill the _'my_nginx'_ container:

List Docker containers again:

The container _my_nginx_ is not operating. Also, you can see in the info that you have a running container and a stopped container:

Use the start or restart Docker commands to start the killed container.

## Docker Exec Bash and Docker SSH into Container

You'll often need to interact with a container's shell to create a service or solve problems. You can use the `docker exec` command to create an interactive shell. Let's start a container from the ubuntu image with a bash shell:

The `root@hash#` means that you are in the bash shell of the Docker container. You can run shell commands:

From another command prompt of your local machine, you can list Docker containers:

You can see _'my_ubuntu'_ is running. Suppose you want to Docker ssh into container _'my_ubuntu'_. You can use the `docker exec` bash method:

> Notice the CONTAINER ID and hash of the command prompt matches. So your effort to docker [SSH](https://www.ssh.com/) into container 'my_ubuntu' was successful.

Use `docker exec` to issue commands into your container. For example, you can run the `ls` command on your _'my_ubuntu'_ docker container directly from the command prompt:

## Launching Containers in Detached Mode and Using `docker attach`

In the above example, you started the ubuntu container in attached mode. Instead, you can start it in a detached mode:

Verify the container is running:

Use the `docker attach `command to get the `docker exec` bash-like effect:

## Checking History of Docker Image

The Docker community builds the docker images. These images are created in layers. You can use the Docker history command to see how the images were created. Let's first find out what images you have:

Let's check the history of _'nginx'_ image:

You can use the history command of the image to find out what changes happened recently. If you notice a problem after spinning up a container from a new version of an image you were already using, this command can help you find the cause. Alternatively, you can use the following version of the command too:

## Docker Inspect Containers

You can use the `docker inspect `command to find out low-level information about your system. Run the `docker ps` command to list Docker containers:

Let's use the CONTAINER ID to inspect the container (You can use the container name also):

The command will provide a lot of information in a JSON format. Here is a trick to find the IP address of a container:

## Using `docker cp` to Copy Files from Your Local Machine to a Container

Let's list Docker containers:

The NGINX container is running on port 8080. So, if you go to `http://localhost:8080`, you will see the following:

"Welcome to nginx!"

_If you see this page, the nginx web server is successfully installed and working. Further configuration is required. For online documentation and support please refer to [nginx.org](http://nginx.org/).  
Commercial support is available at [nginx.com](http://nginx.org/). Thank you for using nginx._

Let's create this index.html in your local directory:

Let's check the folder that has the index.html file in the NGINX container using `docker exec` command with `ls`:

Overwrite the container's index.html file with the local file you created:

Now if you check `http://localhost:8080` again, you should see the greeting _"Hello world"_.

You can use the `docker cp` command to move files between your local machine and the containers you create. This method can be used to overwrite configuration files or other assets.

## Creating Your Own Docker Images

Suppose you want to create future containers from the _"Hello World"_ container you created. But you can only spin containers from images. In order to make more _"Hello World"_ containers, you have to save the current _"Hello World"_container as an image.

First, stop the container:

Now list all Docker containers:

From the STATUS, you can see that the NGINX _'hardcore_torvalds'_ container is stopped. Use the `docker commit`command to create a new image:

Now if you check the images, you'll see the new image:

You can use this image just like other images and spin up new Docker containers. Instead of the _"Welcome NGINX"_ page, the newly created containers will have the _"Hello world"_ page. Example use:

## Removing Docker Containers and Images

Docker containers and images take up space on your hard disk, so it's a good idea to clean them periodically. Let's first stop all the Docker containers and then list all the containers, we will use these next Docker commands to perform this:

There are 4 containers in stopped state. You can use the `docker rm` command to remove containers:

Instead of the CONTAINER ID, you can also use the NAMES. Your container list should be clean now:

Let's list Docker images:

You can remove the docker images using the `docker rmi` command and IMAGE IDs:

Now your Docker images list should be clean:

## Congratulations!

Hopefully, this mini-guide will help you gain confidence in using all the top Docker commands. Use this article as a how-to guide to practice regularly and the commands will become second nature to you.
