# Using LoRaWAN End Devices on The Things Network

_Captured: 2019-05-26 at 02:20 from [www.hackster.io](https://www.hackster.io/nootropicdesign/using-lorawan-end-devices-on-the-things-network-206a86?utm_source=Hackster.io+newsletter&utm_campaign=0961281202-EMAIL_CAMPAIGN_2019_02_14_02_53_COPY_01&utm_medium=email&utm_term=0_6ff81e3e5b-0961281202-141949901&mc_cid=0961281202&mc_eid=1c68da4188)_

![Using LoRaWAN End Devices on The Things Network](https://hackster.imgix.net/uploads/attachments/897924/lorawan_application_architecture_LrNz8sF7oO.png?auto=compress%2Cformat&w=900&h=675&fit=min)

In [part 1](https://www.hackster.io/nootropicdesign/configuring-a-lorawan-gateway-for-the-things-network-b3b1f2), I showed how to set up a simple LoRaWAN gateway, and in [a previous article](http://nootropicdesign.com/projectlab/2018/10/27/samd21-lora-gps/) described a simple but powerful LoRaWAN-capable end device that I designed. Now I'll demonstrate how these devices can be used in a real LoRaWAN application.

[The Things Network (TTN)](https://www.thethingsnetwork.org/) is the Internet infrastructure that allows us to use end devices to do something useful on the Internet. End devices (sometimes called nodes) talk to a nearby gateway, which is connected to the Things Network infrastructure. An application is anything you can imagine on the Internet that does something with the data provided by the end devices. The Things Network bridges the radio technology to Internet technology. The communication does not need to be one-way; applications can downlink data to end devices, too. A common example of an application is a [Cayenne dashboard](https://mydevices.com/cayenne/docs/intro/) which is an easy way to visualize data from your devices. You can also read data from TTN using [Node-RED](https://nodered.org/), a common tool for building IoT solutions.

![](https://hackster.imgix.net/uploads/attachments/897929/lorawan_application_architecture-1_c6xjMy5Idz.png?auto=compress%2Cformat&w=740&h=555&fit=max)

In [part 1](https://www.hackster.io/nootropicdesign/configuring-a-lorawan-gateway-for-the-things-network-b3b1f2) , showed how a gateway is registered to TTN. To connect end device nodes, we also have to define an application in TTN, even if the real functionality of our application is implemented elsewhere on the Internet. An application has a name and a unique ID called an Application EUI. It also creates an Application Access Key that you use to integrate other services like Cayenne or Node-RED to your application. I won't go into the integration details because there is plenty of info available about that.

After creating a TTN application, you need to add devices to the application so that your code on the devices can talk to TTN. There are 2 ways for a device to authenticate with TTN. The recommended and more secure way is called over-the-air-activation, or OTAA. This is the default mechanism when you create a device in TTN. With OTAA, a device negotiates with the network to establish a network session key and an application session key. The other mechanism is activation-by-personalization, or ABP. With ABP, the keys needed to communicate with the network are hard-coded in the device ahead of time. This makes it much easier and quick to connect, but is less secure.

Before we go any further with details about OTAA and ABP, let's define the many types of IDs and keys associated with LoRaWAN applications and devices. It can be very confusing, because some of them have very similar names!

**Gateway ID**: A unique identifier for your gateway. You specify this when you register a gateway with TTN.

**Application EUI**: A unique identifier for an application. It is provided by TTN when you create an application.

**Device ID**: A name that you assign to a device when you register it in TTN.

**Device EUI**: A unique identifier for an end device. This may be provided by your hardware so that you can specify it when registering a device in TTN. OR, you can have TTN generate one for you.

**Device Address**: An identifier for an end device that is used during communication between device and TTN. This is assigned dynamically when using OTAA, but is hard-coded when using ABP.

**Application Key**: A value that is used for secure communication between device and TTN. This is generated when a device is registered with a TTN application. Each device has a different Application Key.

**Network Session Key**: A value that is used for secure communication between device and TTN. This is assigned dynamically for a session when using OTAA, but is hard-coded when using ABP.

**Application Session Key**: A value that is used for secure communication between device and TTN. This is assigned dynamically for a session when using OTAA, but is hard-coded when using ABP.

Is everything clear now? I didn't think so. Let's break it down in terms of what information you need for the two approaches, OTAA and ABP.

After defining an application in TTN and registering a device, the device code needs some of important information in order to connect to the network successfully via a gateway. OTAA requires 3 pieces of information: **Application EUI**, **Device EUI**, and **Application Key**. The other information -- **Device Address**, **Network Session Key**, and **Application Session Key** -- will be determined dynamically during the activation process.

See the [OTAA example](https://github.com/nootropicdesign/samd21-lora-gps) on GitHub. Note the library dependencies required for the examples to work.

Although this method is secure and recommended, connecting to the network can take _several minutes or more_. The negotiation of session keys requires that the network communicate back down to to the end device during precisely timed receive windows, which can be tricky.

Using the ABP approach, the device code needs different information in order to connect to the network. ABP requires 3 pieces of information: **Device Address**, **Network Session Key**, and **Application Session Key**. This method of connecting is much faster and reliable, but for a number of reasons is less secure.

See the [ABP example](https://github.com/nootropicdesign/samd21-lora-gps) on GitHub. Note the library dependencies required for the examples to work.

When using an ABP device, it's important to disable the frame counter checks in the device settings on TTN. This is one of the things making it less secure.

![](https://hackster.imgix.net/uploads/attachments/897934/disableframecounter_7zkz6mNnWI.png?auto=compress%2Cformat&w=740&h=555&fit=max)

By driving around with a [custom-designed end device node](https://nootropicdesign.com/projectlab/2018/10/27/samd21-lora-gps/) in my car, I've tried to determine my communication range with my gateway. I've been a bit disappointed, but there are many things that affect signal propagation. First, despite having an 10-foot antenna mast, my antenna is still not even close to being higher than my house. And I'm hardly an RF engineer when it comes to designing my custom end devices.

![My custom-made end device with GPS](https://hackster.imgix.net/uploads/attachments/897936/lorawan_node_top_2FopGU3k9i.jpg?auto=compress%2Cformat&w=740&h=555&fit=max)

> _My custom-made end device with GPS_

They have a simple wire antenna, but my prior experimentation led me to think that this was just as good as any other LoRa antenna I've tried. In one test, my son and I each strapped a LiPo battery powered end device to our bikes and went for a long ride, having each node send GPS data every minute to my gateway (I realize that this test used far more duty cycle than one should in a real application). A Cayenne dashboard mapped the received data from each device. The smooth path on the map is the actual path as measured by GPS in my son's phone. Superimposed on this are two non-smooth paths defined by blue points at which the gateway "heard" the GPS data reported from the end-device. The gateway is in the southwest are of the map, and you can clearly see that it did not receive much data when we are on the northernmost part of our bike ride. The maximum distance for a received signal was about 1.2 miles.

![](https://hackster.imgix.net/uploads/attachments/897938/dataride1_oZGBnuoGEx.png?auto=compress%2Cformat&w=740&h=555&fit=max)

I also experimented between using confirmed vs. unconfirmed messages. Confirmed message get an acknowledgement from the gateway, whereas unconfirmed are more like "fire and forget". Counterintuitively, it seemed like confirmed messages were more reliable and had better range. Nonetheless, I will continue to do more range testing to try to improve the situation.

An online service like Cayenne makes it super easy to integrate with TTN, but you can also integrate with your own software via MQTT. Data uplinked from your devices to your TTN application are published to MQTT topics that you can connect to in your own application. I love using [Node-RED](https://nodered.org/) for all sorts of IoT fun. You can use MQTT nodes (here "nodes" refers to Node-RED components, not end devices) to receive the data published by TTN. To make it even easier, TTN has even [written custom nodes for TTN integration](https://www.npmjs.com/package/node-red-contrib-ttn). If you are a Node-RED junkie like me, I strongly recommend you look into this type of integration so that you can build just about anything based on data from LoRaWAN end devices.

![](https://hackster.imgix.net/uploads/attachments/897944/node-red-integration_xdJgMg9p1O.png?auto=compress%2Cformat&w=740&h=555&fit=max)

I hope you found these articles about LoRaWAN useful. The learning curve is significant but it's exciting when a technology is so new.
