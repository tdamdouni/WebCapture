# Ikea Tradfri Hacking

_Captured: 2018-05-05 at 16:35 from [hackaday.com](https://hackaday.com/2017/06/14/ikea-tradfri-hacking/)_

![](https://hackadaycom.files.wordpress.com/2017/06/bulb1.png?w=800)

Smart lighting is all the rage right now. Sure, Phillips Hue is the giant player in the market, but there are plenty of ZigBee, Bluetooth, and WiFi light bulbs out there. Ikea-known for cheap furniture, meatballs, and waffles-is a recent addition to the field with their Tradfri system. Like most things from Ikea, they are effective and inexpensive. [Andreas] [takes a Dremel to the controller](https://www.youtube.com/watch?v=olxPqiJcUAQ) and shows how to hack the system to use MQTT. You can check out the video below.

Once he had the device opened, the used the [German Make magazine article](https://hackaday.com/2017/02/06/reverse-engineering-ikeas-new-smart-bulbs/) we talked about earlier, to help understand what he had. Armed with the pinout, he was able to solder a wiring harness to the controller. He then connected a WeMos board. A little Arduino code later, and he was controlling the light with MQTT.

From MQTT, it was simple to connect the lights to a variety of systems without having to use a separate hub as they do for the default. [Andreas] notes, though, that the system doesn't offer any feedback which can make things difficult. However, he has plans to further hack the devices in the future.

If you want to know [more about MQTT](https://hackaday.com/2016/05/09/minimal-mqtt-building-a-broker/), by the way, [Elliot Williams] did a good series that will help you get started.
