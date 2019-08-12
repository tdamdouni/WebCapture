# Control GPIO with Docker Swarm

_Captured: 2017-11-18 at 14:29 from [blog.alexellis.io](https://blog.alexellis.io/gpio-on-swarm/)_

If you've ever used add-ons with your Raspberry Pi before then you'll know they rely on the GPIO pins. Most GPIO libraries need elevated system privileges to access the pins and devices created by the Linux Kernel. The [Docker Swarm project](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/) (codenamed SwarmKit) currently [does not support running privileged containers](https://github.com/docker/swarmkit/issues/1244).

![Raspberry Pi pinout diagram](https://blog.alexellis.io/content/images/2017/02/Raspberry-Pi-Model-Zero-Mini-PC.jpg)

In this post I outline a hack for using add-ons with Docker Swarm - without running in privileged mode using something called `sysfs`.

> Thanks goes to [Stefan Scherer](https://twitter.com/stefscherer) for suggesting and testing out the following method.

### Demo video

In the video you can see a Docker Swarm cluster with five hosts. Each host is a Raspberry Pi Zero and is connected over a USB-ethernet dongle.

I created Docker Swarm service with [my Golang progress bar animation](https://github.com/alexellis/blinkt_go_examples/blob/master/sysfs/progress/app.go) and told the swarm to replicate one container per host. Read on for more details.

You can also learn about [Swarm Services here in the Docker docs](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/).

### Using GPIO with Docker

There are three ways to use hardware with the Raspberry Pi and Docker:

  * Pass `\--privileged` to the `docker run` command:
    
    
    $ docker run --privileged -d blinkt
    

This works fine with the previous Swarm offering from Docker but not the version released in June last year with 1.12. If you don't need clustering the above is the simplest way to use GPIO and Docker.

  * Add the `/dev/gpiomem` device at runtime

This is another method that works with some GPIO libraries - a recent version of Raspbian added the `/dev/gpiomem` device and this can be mounted into a container with `docker run`.
    
    
    $ docker run --device /dev/gpiomem -d blinkt
    

Unfortunately this still doesn't work with Swarm Services, but it may do in the future. If your add-on board uses i2c or serial then you may need to wait or use the [previous Docker Swarm](https://github.com/docker/swarm) version.

  * Use the sysfs GPIO interface

The third and last option is to use what is called the `sysfs` filesystem. You can perform GPIO with user privileges by interacting with the virtual files under `/sys/class/gpio`.

A drawback to this method is that not all libraries support it and it's also slower than `/dev/gpio`.

### Getting it working with sysfs

I recently ported Pimoroni's Python library for their Blinkt LED board over to Golang and made use of the WiringPi library. It was not hard to convert it to using `sysfs` \- it involved using standard syscalls such as stat/open and write.

#### Find a library

You need to find or create a library that uses sysfs instead of /dev/gpiomem or /dev/mem. Here's the code for my Golang Blinkt library for sysfs:

If you want to perform GPIO with a different device, then you could adapt the code above or search to find out whether someone has already used sysfs in the library you're using right now.

#### Build or port an application

If you're building a new application, then reference the new library and test it out on one device first. I already had a code sample so I just updated the Golang package.

  * [app.go](https://github.com/alexellis/blinkt_go_examples/blob/master/sysfs/progress/app.go) \- gives a progress bar-style red LED animation

#### Build a Dockerfile

Once your application is working you can package it into a Dockerfile. Here's my example:

  * [Dockerfile](https://github.com/alexellis/blinkt_go_examples/blob/master/sysfs/progress/Dockerfile)

#### Create a Swarm

You may already have a Pi swarm - if you don't then checkout [these tutorials and videos](http://blog.alexellis.io/tag/swarm/).

If you have a Blinkt plugged in then you can try my Docker image right away:
    
    
    $ docker service create --name sys --mount type=bind,source=/sys,destination=/sys --mode=global alexellis2/progress-blinkt:red
    

> This image contains a single Golang binary so the total size of the image is a tiny 1.81 MB uncompressed. Even smaller on the [Docker Hub](https://hub.docker.com/r/alexellis2/progress-blinkt/tags/) where it's a 655 KB download.

Breaking this down we have two important parts:
    
    
    --mount type=bind,source=/sys,destination=/sys
    

Mounts the virtual `/sys/` filesystem from the Pi where the service is running into the container so we can access GPIO.
    
    
    --mode=global
    

This runs the container a maximum of once per Raspberry Pi. We don't want to run this animation more than once at the same time or it will go out of sequence.

### Rolling updates

You can also perform rolling image updates with Docker Swarm. This means the swarm will deploy a new version of the image into the service.

Try this out to turn the LEDs green:
    
    
    $ docker service update sys --image=alexellis2/progress-blinkt:green
    

Have swarm deploy the blue version of the progress app:
    
    
    $ docker service update sys --image=alexellis2/progress-blinkt:blue
    

You can even type in `docker swarm update sys --rollback` to return to the original image. These features are purpose-built for web applications but also work well with GPIO.

### Wrapping up:

![](http://blog.alexellis.io/content/images/2017/02/ideas.jpg)

Follow me on Twitter [@alexellisuk](https://twitter.com/alexellisuk) and send your comments, questions and suggestions.

See also:
