# 5 Docker Utilities You Should Know

_Captured: 2017-05-30 at 13:40 from [dzone.com](https://dzone.com/articles/5-docker-utilities-you-should-know?edition=301096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-26)_

Learn how API management supports better integration in [Achieving Enterprise Agility with Microservices and API Management](https://dzone.com/go?i=126027&u=http%3A%2F%2Fpages.3scale.net%2Fmicroservices-api-management-dzinteg.html), brought to you in partnership with [3scale](https://dzone.com/go?i=126027&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper)

You can find a lot of cool [Docker](https://xebialabs.com/plugins/docker/) utilities on the web. Most of these are open source and available on Github. Over the last two years, I have become quite active with Docker, using it for most of my development projects. As you start using Docker, you will find it is suitable for more use cases than you may have initially envisioned. You will want Docker to do a little more for you--and it will not disappoint!

The Docker community is very active, with a lot of useful utilities popping up daily. It is difficult to keep check of all the innovation happening in the community. To help you, I have collected some interesting and useful Docker utilities, which I use in my daily work. These utilities make me more productive, eliminating what otherwise would have been manual work.

Let's go through each of the utilities I find useful in my journey to Dockerize stuff.

## 1\. [watchtower](https://github.com/v2tec/watchtower): Automatically Update Docker Containers

Watchtower monitors running containers and watches for changes to the images those containers were originally started from. When Watchtower detects that an image has changed, it automatically restarts the container using the new image. I use it in my local development where I would like to try out the latest built image.

Watchtower is itself packaged as a Docker image so you can run it just the way you would run any other container. To run Watchtower, you would run the following command:

![Docker utilities - docker run](https://i1.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-9.50.47-AM.png?resize=1456%2C164&ssl=1)

In the command above, we started Watchtower container with a mounted file `/var/run/docker.sock` . This is required so that Watchtower can interact with Docker daemon API. We passed an option `interval` of 30 seconds. This option defines the Watchtower poll interval. Watchtower supports a few more options, which you can use as described in their [documentation](https://github.com/v2tec/watchtower#options).

Let's now start a container that Watchtower can monitor.

![Docker utilities - docker run](https://i1.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-9.56.47-AM.png?resize=1470%2C168&ssl=1)

Now, Watchtower will start monitoring `friendlyhello` container. When I push the new image to Docker Hub, Watchtower, in its next run, will detect that a new image is available. It will gracefully stop the container and start the container using the new image. It will pass the options that we passed to the run command. In other words, the container will be started with `4000:80` publish ports option.

By default, Watchtower will poll the Docker Hub registry to look for updated images. You can configure Watchtower to poll private registry by passing the registry credentials in environment variables REPO_USER and REPO_PASS.

To learn more about Watchtower, I recommend reviewing the [Watchtower documentation](https://github.com/v2tec/watchtower/blob/master/README.md).

## 2\. [docker-gc](https://github.com/spotify/docker-gc): Garbage Collection of Container and Images

The docker-gc utility helps clean up your Docker host by removing containers and images that are not required. It removes all the containers that existed more than an hour ago. Also, it removes images that don't belong to any remaining containers.

You can use docker-gc both as a script and container. We will run docker-gc as a container. Let's use docker-gc to find all the containers and images that can be removed.

![Docker utilities - docker run](https://i0.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-10.11.43-AM.png?resize=1468%2C176&ssl=1)

In the command shown above, we mounted Docker socket file so that docker-gc can interact with Docker API. We passed an environment variable DRY_RUN=1 to find which containers and images will be removed. If we don't provide this option, docker-gc will remove all of them. It is good to first verify everything docker-gc will clean. The output of the above command appears below.

![Docker utilities - docker run](https://i1.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-10.13.25-AM.png?resize=1468%2C964&ssl=1)

If you are fine with the docker-gc clean up plan, you can again run docker-gc without DRY_RUN flag to perform the clean up.

![Docker utilities - docker run](https://i0.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-10.14.53-AM.png?resize=1460%2C180&ssl=1)

The output of the above command will tell you all the images and the containers that docker-gc removed.

There are few more options that docker-gc supports. I recommend you read the [docker-gc documentation](https://github.com/spotify/docker-gc/blob/master/README.md) to learn more about it.

## 3\. [docker-slim](https://github.com/docker-slim/docker-slim): Magic Diet Pill for Your Containers

If you are worried about the size of your Docker images, you will be blown away by docker-slim.

The docker-slim utility uses static and dynamic analysis to create skinny image variants of your fat images. To use docker-slim, you have to download its binary from [Github](https://github.com/docker-slim/docker-slim/releases). Binaries are available for Linux and Mac. Once you download the binary, add it to your PATH.

I created a Docker image for example application `friendlyhello` used in the [Docker official documentation](https://docs.docker.com/get-started/). The image size, as you can see below, is 194 MB.

![Docker utilities - docker slim](https://i0.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-10.22.14-AM.png?resize=1456%2C164&ssl=1)

> _As you can see for a simple application, we have to download 194 MB of data. Let's use docker-slim to see how much fat it can remove._

![Docker utilities - docker slim](https://i1.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-10.24.39-AM.png?resize=1464%2C116&ssl=1)

The docker-slim utility will carry out a series of steps-inspecting fat image, instrument fat image, finally creating a slim version of the image. Let's look at the size of the slim variant.

![Docker utilities - docker slim](https://i2.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-10.24.50-AM.png?resize=1462%2C276&ssl=1)

As you can see above, the image size was reduced to 24.9 MB. You can start the container and it will behave in the same manner. The docker-slim utility works well with Java, Python, Ruby, and Node.js application.

Try it yourself and see how much you can gain. In my personal projects, I have found that it worked for most cases. You can learn more about docker-slim from its [documentation](https://github.com/docker-slim/docker-slim/blob/master/README.md).

## 4\. [rocker](https://github.com/grammarly/rocker): Breaks the Limits of Dockerfile

Most of the developers using Docker use Dockerfile for building images. Dockerfile is a declarative way to define all the commands a user could call on the command line in order to assemble an image.

[Rocker](https://github.com/grammarly/rocker) adds new instructions to the Dockerfile instruction set. Rocker was created by [Grammarly](https://tech.grammarly.com/blog/posts/Making-Docker-Rock-at-Grammarly.html) to solve problems they faced with Dockerfile format. The Grammarly team wrote an [in-depth blog](https://tech.grammarly.com/blog/posts/Making-Docker-Rock-at-Grammarly.html) explaining their reasons for creating it. I recommend you read it to better understand Rocker. The two problems they highlight in their post are:

  1. Size of Docker images.
  2. Slower builds.

The blog also mentions some of the new instructions added by Rocker. Refer to [Rocker documentation](https://github.com/grammarly/rocker/blob/master/README.md) to learn about all the instructions Rocker supports.

  1. MOUNT is used to share volumes between builds so they can be reused by dependency management tools.
  2. FROM instruction exists in the Dockerfile as well. Rocker makes it feasible to add more than one FROM instruction. This means you can create more than one image from a single Rockerfile. The first set of instructions will build the artifact using all the dependencies. The second set of instructions can use the build artifact. This reduces the image size drastically.
  3. TAG is used to tag the image at different stages of the build. This means you don't have to tag images manually.
  4. PUSH is used to push images to a registry.
  5. ATTACH allows you to run an intermediate step interactively. This is useful for debugging.

To use Rocker, you must install it on your machine. For Mac users, it is as simple as running couple of brew commands:

![Docker utilities - rocker](https://i1.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-10.32.32-AM.png?resize=1464%2C168&ssl=1)

> _Once installed, you can use Rocker to build an image by passing it to Rockerfile:_

![Docker utilities - rocker](https://i2.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-10.32.39-AM.png?resize=1464%2C512&ssl=1)

> _To build an image and push it to Docker Hub, you can run the following command:_

![Docker utilities - rocker](https://i1.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-10.32.46-AM.png?resize=1460%2C122&ssl=1)

Rocker has a good set of features. To learn more about it, refer to its [documentation](https://github.com/grammarly/rocker/blob/master/README.md).

## 5\. [ctop](https://github.com/bcicen/ctop): Top-like interface for containers

The utility I have started using lately is ctop, which provides a real-time metrics view of multiple containers. If you are a mac user, then you can install ctop using brew as shown below.

![Docker utilities - ctop](https://i1.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-10.41.24-AM.png?resize=1452%2C122&ssl=1)

Once installed, you can start using ctop. It only needs the DOCKER_HOST environment variable configured.

To view the state of all the containers, you can run `ctop` command.

![Docker utilities - ctop ](https://i0.wp.com/blog.xebialabs.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-08-at-10.41.31-AM.png?resize=1452%2C258&ssl=1)

To view the running containers only, you can use `ctop -a` command.

The ctop is a simple utility and very useful to learn about containers running on your host. You can read more about it in the [ctop documentation](https://github.com/bcicen/ctop/blob/master/README.md).

These are some of the Docker utilities I find useful. Do you use any Docker utilities in your daily work? If so, let us know in the comments section below.

Unleash the power of your APIs with future-proof API management - [Create your account](https://dzone.com/go?i=126028&u=http%3A%2F%2Fpages.3scale.net%2Ffuture-proof-api-management-dzinteg.html) and start your free trial today, brought to you in partnership with [3scale](https://dzone.com/go?i=126028&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper).
