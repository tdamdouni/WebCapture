# Solar-Powered, Internet-Connected Lawn Sprinkler Project

_Captured: 2017-11-15 at 19:26 from [bit.ly](http://bit.ly/2jtgeFg)_

![Solar-Powered, Internet-Connected Lawn Sprinkler Project](https://hackster.imgix.net/uploads/attachments/378374/esp8266-patio.jpg?auto=compress%2Cformat&w=900&h=675&fit=min)

More info about solar powered automatic sprinkler at [www.movingelectrons.net](http://www.movingelectrons.net/)

I've been looking for an excuse to do a little project with [Adafruit's Feather HUZZAH](http://amzn.to/2x8fPcr) board and [MicroPython](http://micropython.org/). As an engineer who graduated some years ago, having a Wi-Fi enabled micro-controller which runs (Micro) Python 3 and costs [less than $20](http://amzn.to/2x8fPcr) is really amazing.

My initial plan was to use this automatic lawn sprinkler to be a rodent deterrent to keep rabbits and squirrels out of my lawn, but I have also used it to keep flower beds and newly planted trees hydrated. It can also be used to [prank your friends](https://www.youtube.com/watch?v=XJPLDycAGyM). In any case, those are just excuses; I really wanted to tinker with electronics and Python.

This project has several moving parts, but I'll go through each step in detail and will link to key tutorials and instructions. If you have any questions, feel free to leave a comment below.

Here is a general diagram showing the general process:

![](https://hackster.imgix.net/uploads/attachments/378369/esp8266-diagram.png?auto=compress%2Cformat&w=680&h=510&fit=max)

[Adafruit](http://www.adafruit.com/) was an invaluable resource for this project. In addition to the geeky products and electronics they sell, which are the backbone of this project, Adafruit makes available _Learning_ posts, Python libraries and forums that saved me a lot of time on this project. They offer their most popular products on Amazon and they even accept amazon payments through their website.

Here is a detailed list of the hardware used:

  * 9V Battery
  * Weather sealed plastic box
![](https://hackster.imgix.net/uploads/attachments/378370/esp8266-parts.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

> _Components partially assembled._

A fundamental part of this project is the [MQTT protocol](http://mqtt.org/), which is a Client-Server _Internet of Things_ connectivity protocol. It's fast, easy to implement and allows communication between the Feather Huzzah (MQTT client) and the MQTT Server/Broker.

MQTT comes bundled within MycroPython, and since it's widely used, it allows the Feather Huzzah to talk with several automation services like [IO - Adafruit](https://io.adafruit.com/), [Cayenne](https://mydevices.com/cayenne/projects/) or [Initial State](https://initialstate.com/). I'll be using [Home Assistant](https://home-assistant.io/) which is a popular home automation system built on Python that runs on Unix/Linux based computers and NAS devices (I'm running it on a Mac Mini) . Although Home Assistant comes with an MQTT server, it's fairly bare bones, so I'll be using [Mosquitto](https://mosquitto.org/) to be the link (i.e. broker) between the MQTT client on the Feather Huzzah and Home Assistant.

I tried several configurations and settled on this one because of its versatility: the lawn sprinkler can be operated manually from the host computer or mobile devices running Home Assistant. It can also be activated through automation setup on Home Assistant or even through standalone python scripts interacting with _Mosquitto_. My final goal is to have it operate based on image recognition/computer vision, but that's going to take me some time to implement.

I'm assuming both Home Assistant and Mosquitto are installed on the server machine (instructions [here](https://home-assistant.io/getting-started/) and [here](https://mosquitto.org/download/)). Also, you need to create a _Switch_ on Home Assistant by including the following lines in the configuration file (_configuration.yaml_):
    
    
    mqtt:
      broker: 127.0.0.1
    switch:
      platform: mqtt
      name: "Outside Sprinkler"
      command_topic: "home/sprinkler"
      payload_on: "on"
      payload_off: "off"
    

Since Mosquitto and Home Assistant are installed on the same machine, the MQTT broker IP is _127.0.0.1_. If everything is configured correctly, you should be able to see something like this on the Home Assistant's main screen:

![](https://hackster.imgix.net/uploads/attachments/378371/esp8266-homeassistant.png?auto=compress%2Cformat&w=680&h=510&fit=max)

> _Home Assistant screenshot._

Now that the server side is done, let's move to the client side and the script that should be put on the _Feather Huzzah_.

The _Feather Huzzah_ is based on the [ESP8266 chip](https://en.wikipedia.org/wiki/ESP8266), which is a fairly fast (for a chip) Wifi enabled microcontroller capable of running MicroPython among other languages.

There is a huge online community supporting this chip offering tutorials and instructions on how to build a wide variety of hobby and IoT projects. Since I got [adafruit's board](http://amzn.to/2xtKfuM), I decided to follow their tutorials. [This one](https://learn.adafruit.com/micropython-basics-how-to-load-micropython-on-a-board?view=all) and [this one](https://learn.adafruit.com/micropython-basics-load-files-and-run-code) are key to quickly getting up and running on MycroPython, transferring scripts back and forward and running scripts on the board using [Ampy](https://github.com/adafruit/ampy). However, I would recommend going through all the [MicroPython Basics Series](https://learn.adafruit.com/users/tdicola) by Tony DiCola. He does a fantastic job explaining the process and the series include videos on which he goes in detail over each step of the tutorials.

All the needed files can be downloaded from the [GitHub repository](https://github.com/Moving-Electrons/connected-sprinkler). There is only two files that need to be placed on the _Feather Huzzah_:

**config.json**

This is the configuration file. It holds all the information needed to connect to the WiFi network and the MQTT server in Json format as follows:
    
    
    {
        "ESSID": "WiFi network name (SSID)",
        "PASSWD": "Insert the WiFi password",
        "MQTT_Broker": "Internal IP of the MQTT Server.",
        "TOPIC": "home/sprinkler",
      "DURATION": 8
    }
    

Notes:

All constants must be between quotes (""), except the _DURATION_ value.Change the _TOPIC_ per the way you have configured your MQTT server/broker. I have used _home/sprinkler_ as the topic to subscribe to on this tutorial._DURATION_ indicates the duration the sprinkler will be on in seconds. 8 Seconds is more than adequate in my case.

**main.py**

This is the actual MicroPython script. It performs the following tasks in sequence:

  * Attempts to connect to the pre-configured WiFi network. The _Feather Huzzah_ red LED stays red while attempting to connect. Once the board is authenticated by the WiFi router, the LED turns off.
  * It connects to the MQTT server and watches the _TOPIC_ specified in the configuration file for changes.
  * If the _TOPIC_ values changes to _on_, it activates the sprinkler for the _DURATION_ value indicated in the configuration file.

Since one of the goals is consuming the least possible amount of current, I went with the [latching mini relay feather wing](http://amzn.to/2ycttPP) which requires two different signals to be sent to the relay (set/unset) to turn it on and off. Although this involves soldering an additional wire and a couple more lines of code, it's well worth the current savings.

Assembly does require some soldering and it might be the most challenging part of this project, but it isn't that difficult to do. If you are a beginner, I would recommend getting an inexpensive [practicing kit on amazon](http://amzn.to/2gG9KyG). You would need a soldering iron, [solder wire](http://amzn.to/2z7NOmM) and some sort of [vise](http://amzn.to/2zo7aoy) to hold your board.

![](https://hackster.imgix.net/uploads/attachments/378372/esp8266-builtSide.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

> _Assembled parts. Note the Feather Wing stacked on top of the Feather Huzzah._

The [Feather Header Kit](http://amzn.to/2xFEFRg) should be soldered on top of the _Feather Huzzah_ to allow for the [Latching Mini Relay Feather Wing](http://amzn.to/2ycttPP) to be placed on top (see picture above for final result).

The _Feather Wing_ comes disassembled, so the included header should be soldered to it. Additionally, a couple of cable wires should be soldered to this board to allow for the Set/Unset pins to actuate the mini relay. These are the short red wires next to the relay on the picture above.

Make sure the wires are soldered as follows:

  * Pin 13 to the _Set_ pin on the Feather Wing.
  * Pin 14 to the _Unset_ pin on the Feather Wing. 

The correct arrangement can be seen on the picture taken directly above the open weather-proof box.

**Important**: Make sure the wires are soldered to the correct pins, as these are the ones used on the MicroPython code.

The rest of the assembly process is pretty straightforward. Adafruit's boards clearly indicate where connections and wiring should go. The diagram and pictures in this post should serve as guidance as well. A couple of items that proved to be really useful were [Sugru](http://amzn.to/2yxRqj5) and [Mack's Silicone Earplugs](https://www.amazon.com/gp/product/B003LZQGN6/&tag=movinelect0e-20). I used Sugru to attach the solar panel to the weatherproof box lid. Since both have irregular surfaces, using double-sided tape was not practical and hot glue is a bit messy. I put 4 round pieces of Sugru on each of the solar panel's corners and adjusted as needed before it curated. On the other hand, I used the soft silicone earplugs to seal the box penetrations and put all components in place inside the box. The material is malleable, high-temperature resistant, waterproof and doesn't leave much residue when removed. I could have used Sugru or [double sided tape](http://amzn.to/2x5WyZZ), but I wanted to be able of swaping components out or changing their position.

Here is a quick video showing the final result. The lawn sprinkler is activated by tapping on the _sprinkler switch_ on Home Assistant's iOS App.

Putting this project together was both a fun and a learning experience. If you have any questions, feel free to leave a comment in the [original post](http://www.movingelectrons.net/blog/2017/10/18/solar-powered-internet-connected-lawn-sprinkler.html) at [www.movingelectrons.net](http://www.movingelectrons.net/).

![](https://hackster.imgix.net/uploads/attachments/378373/esp8266-built.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

> _Final assembly._
