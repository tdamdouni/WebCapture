# Holiday lights that harmonize around the globe

_Captured: 2017-11-24 at 01:27 from [blog.alexellis.io](https://blog.alexellis.io/festive-docker-lights/)_

Make this festive season one to remember with a project you can build for around $25 over a weekend and share in with your your friends and family.

Grab a mince pie and a cup of coffee as we build your very own Festive Lights decoration that is powered by a [Raspberry Pi Zero W](https://blog.alexellis.io/pizerow-first-impressions/) and [Docker containers](https://www.docker.com). It'll synchronise its colour globally across the world in real-time and is controllable through Twitter using the [Cheerlights](https://twitter.com/cheerlights) platform.

We'll customise a small festive decoration by adding in a Raspberry Pi Zero W and colourful, low-power lights from Pimoroni, then use Docker to build, ship and run the code without any guess-work.

> This blog post is inspired by my _Holiday Lights_ project from 2016:

> I made the above decoration for my mum last year. It was triggered by a mention sensor and gave an effect like a candle by running through warm colours at different brightness levels. This year my wife has asked for me to make one her one too.

## Bill of materials

You can add the following to a single basket and save on shipping with Pimoroni:

> You will also need a micro-USB phone charger or [official power adapter](https://shop.pimoroni.com/products/raspberry-pi-universal-power-supply).

The Raspberry Pi Zero W is equipped with 512mb RAM and has Bluetooth and WiFi built-in.

Now this is the fun part.. once your Raspberry Pi arrives take it with you around the shops and stores and find a decoration with a cavity big enough to hold the RPi.

> Last year I used a snowman decoration designed to take a tea-light candle and installed a motion sensor and a set of [Adafruit NeoPixels](https://www.adafruit.com/category/168).

## How it works

[Cheerlights](https://twitter.com/cheerlights) is an online service that handles traffic from hundreds of thousands of IoT devices in real-time to synchronise the chosen colour.

> Just tweet "#cheerlights blue" for instance 

## Prepare the Raspberry Pi

This tutorial is split up into several sections, we'll start by preparing the Raspberry Pi and then move onto the software.

**Important disclaimer**: By following this tutorial you agree to take full responsibility and liability for your Raspberry Pi decoration.

### Add the headers

You will need to solder a header to the top of your Raspberry Pi. If you don't have access to a soldering iron then you can buy them pre-soldered or a version that can be hammered-in from Pimoroni.

  * Plug your Pimoroni blinkt in on top of the Raspberry Pi

Don't power on yet.

### Flash the Operating System

  * > This is a version of the OS which has no UI built-in, it is well-suited to IoT devices.

  * Use [Etcher.io](https://www.etcher.io) to flash the zip file you downloaded to the SD card. Make sure you pick the right drive so you don't overwrite any other drives.

  * Write an `ssh` file to the boot partition / drive. This is so we can log in remotely

  * Configure WiFi by adding a file to the boot partition / drive called `wpa_supplicant.conf`:
    
    
    country=GB  
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev  
    update_config=1  
    network={  
        ssid="OurWiFiAtHome"
        psk="SecretPassword"
    }
    

Make sure you update the values for `ssid` and `psk`. I've just provided examples.

  * Plug in the SD Card and power on the Raspberry Pi

### Install your software

  * Log into your Raspberry Pi using `ssh` \- the hostname will be `raspberrypi.local`

  * `ssh pi@raspberrypi.local`

  * Optional step: change the hostname using the `raspi-config` tool.

  * Important: change the password
    
    
    $ passwd
    Changing password for pi.  
    (current) UNIX password: 
    Enter new UNIX password:  
    Retype new UNIX password:  
    passwd: password updated successfully  
    

  * Install Docker

There is a "one-liner" which can setup and configure Docker:
    
    
    curl -sL get.docker.com | sh  
    

Once it's done type in `usermod pi -aG docker` so that your user can access the Docker back-end. Now log out and back in again.
    
    
    usermod pi -aG docker  
    logout  
    

Now re-connect with `ssh`.

  * Clone the code

We'll download my code examples written in Go - Go is a light-weight programming language written at Google for modern systems. It requires far fewer resources or tooling than the Python library from Pimoroni, so we'll get up and running even faster.

> The Docker image only needs 5MB on your SD card and the download is a fraction of that size.

Install git and clone the repo:
    
    
    sudo apt-get install git -qy --no-install-recommends
    
    git clone https://github.com/alexellis/blinkt_go_examples  
    

### Optional: build a container

Let's build and run the example code called "cheerlights"

This step is optional if you want to make changes to the code:
    
    
    cd blinkt_go_examples/cheerlights  
    docker build -t alexellis2/cheerlights:0.1 .  
    

### Run the container

Now before continuing place the Raspberry Pi Zero with Blinkt into the decoration. Here's an example of one I made for the office which uses a £1 candle-light/tea-light holder from Poundland.

> New holiday blog coming soon. Keep your eyes peeled. [pic.twitter.com/yU0SjuLFTp](https://t.co/yU0SjuLFTp)
> 
> -- Alex Ellis (@alexellisuk) [November 23, 2017](https://twitter.com/alexellisuk/status/933728726751301632?ref_src=twsrc%5Etfw)

Use this command to run the container:
    
    
    docker run --name iot --restart=always --privileged -d alexellis2/cheerlights:0.1  
    

Now that the code is started up in a Docker container it will synchronise automatically to whatever the latest tweet was to the #cheerlights hashtag.

Explaining the flags:

  * `\--name iot` gives the container a name so we can remove or check it later i.e. (`docker rm -f iot`)
  * `\--restart=always` means the image will restart when the RPi restarts
  * `\--privileged` allows us to access the GPIO from Docker
  * `-d` runs the container in the background

  * Read the Dockerfile

The Dockerfile uses the latest developments by the Docker team including multi-architecture official images and [multi-stage builds](https://blog.alexellis.io/mutli-stage-docker-builds/).

Multi-architecture images means that we can use the `FROM golang:1.9.2` instruction on any supported platform.

The [multi-stage build](https://blog.alexellis.io/mutli-stage-docker-builds/) helps us leverage Go's ability to build tiny static binaries with no other dependencies. This means building and shipping relatively tiny Docker images.

The final image has a size of 5.03MB, but can be made even smaller with some additional flags.

### Make it permanent

Now that you have tested your setup you can use use hot glue, bluetac or tape to permanently install the Raspberry Pi inside the decoration.

If you want to diffuse the light you can tape a coffee filter or several layers of paper to the windows or openings in the decoration. A piece of clear plastic Milk carton might also do the trick.

### Wrapping up

So we've put together an Internet-enabled festive IoT decoration having made use of the versatile Raspberry Pi Zero W and consumer electronics. It runs a full Linux Operating System with WiFi so we're just scratching the surface of what could be done.

You may ask why use a 10 dollar Raspberry Pi Zero W when a basic electronic component like a [555 timer](https://en.wikipedia.org/wiki/555_timer_IC), an [Arduino Nano](https://store.arduino.cc/arduino-nano) or a similar device could be used instead? Well these are all valid options, but also more specialist, more limited in capabilities and harder to use. The Raspberry Pi's appeal has always been its ease of use, accessibility and way it has captured our imagination around the globe. Here are some of the device's highlights:

  * Modern Linux OS and Kernel
  * HDMI, 1x USB, 512mb RAM & camera interface
  * WiFi and Bluetooth and much more
  * 40-pin GPIO with dozens of commodity add-ons

### Over to you

Now it's over to you to customise your decoration, the code and to continue learning.

> Don't miss out on any cool blogs and tutorial - **follow me on Twitter [@alexellisuk](https://twitter.com/alexellisuk) today**

Get inspired and put your own twist on your IoT decoration with these related projects:

Keep learning:

  * Browse my [Raspberry Pi tutorials](https://blog.alexellis.io/tag/raspberry-pi) for ideas.
  * Learn more about [Docker](https://blog.alexellis.io/tag/docker)

### Want to build a Raspberry Pi Cluster?

Get started here:
