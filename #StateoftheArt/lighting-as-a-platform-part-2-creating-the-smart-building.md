# Lighting as a Platform Part 2: Creating the Smart Building

_Captured: 2017-12-26 at 18:28 from [blog.bluetooth.com](https://blog.bluetooth.com/lighting-as-a-platform-part-2?utm_campaign=other&utm_source=tw&utm_medium=organic&utm_term=lighting-as-platform&utm_content=lighting-as-platform-two)_

In a truly smart building, lights can be much more than just lights. These buildings are supported by lighting systems that have the potential to act as a distributed network of small computers and are capable of hosting all sorts of other applications, enabling the creation of true smart building services. Inherent interoperability, fundamental device behaviour models, and value-added capabilities are all critical to making the concept of the true smart building a reality.

In [part 1](https://blog.bluetooth.com/lighting-as-a-platform-part-1), we explored the concept of lighting as a platform and its capability to support multiple building services, from lighting automation to way finding and asset tracking. In this article, we'll discuss some of the critical requirements needed for designing a connected lighting platform capable of supporting a smart building.

## True Multi-Vendor Interoperability

Smart lighting systems only work seamlessly when the components of those systems -- lamps, switches, controllers, and sensors -- connect and communicate with each other. This can only happen if those components adopt and adhere to a common technical standard.

For true multi-vendor interoperability, you need a technology that defines everything across all layers of a full protocol stack, from the low-level technicalities of radio communication up to the application-layer behaviours relating to particular types of products. This way you're assured that products adopting this technology will work together. Their radios will take the same approach to encoding and transmitting digital information over an analogue, radio medium and use the right frequencies and timing rules. Dimmer switches will send wireless messages meaning _reduce your lightness level by this amount, _which luminaires will understand and respond to.

[Multi-vendor interoperability](https://blog.bluetooth.com/interoperability-for-smart-lighting-platforms) is not something to take for granted, as it doesn't happen by magic. It's possible only because of the rigorous and comprehensive specification and testing procedures provided and mandated by global standards organizations, such as the Bluetooth Special Interest Group (SIG).

## The Magic of Models

Models are standard software components inside devices which act as the fundamental, behavioural building blocks of a device. It falls to certain models to define how a switch can turn a light on or off. Other models define how the lightness transitions triggered by occupancy changes should behave. The [Bluetooth mesh specification](https://www.bluetooth.com/specifications/mesh-specifications) currently includes collections of models which can be used by any type of device in general (called _generics_), models which are defined specifically for lighting-related devices, models concerned with _scenes,_ and models concerned with the propagation of accurate time information across the network. Scenes make possible more advanced automation scenarios involving groupings of different types of device, usually belonging to entirely different building systems, like lighting, heating, and air conditioning.

The collection of models that a device incorporates determines what that device can do and how other devices can interact with it. Figure 1 depicts the models which we might find in light switches, lights, and associated sensors. The Generic ON/OFF Client model allows the switch to give orders to the light by sending defined messages to it or to find out its current state. The Generic ON/OFF Server model allows the light to respond to the switch's messages.

The Light Lightness Server model allows brightness control and the Light HSL (Hue/Saturation/Lightness) model allows colour control.

The Light LC Server model is where things start to get really interesting. LC stands for Lighting Control and it's this model which works in conjunction with the Sensor Model inside sensors, such as occupancy and ambient-light sensors, to implement the occupancy and daylight-saving behaviours that were described in [part 1](https://blog.bluetooth.com/lighting-as-a-platform-part-1).

![](https://blog.bluetooth.com/~/media/images/blog/lighting%20part%202-image%201%20\(1\).ashx?h=553&w=994&la=en&hash=661DDE0061797A78D82A058CF52F37C341FD26CB)

> _Figure 1 - Models potentially found in switches, lights, and sensors._

Models define the behaviour of devices on a network and are critical to creating smart lighting systems. Facilities that use lighting as a wireless platform will be better positioned to support automation and create a truly smart building.

## **Bluetooth Technology as a Platform for Smart Buildings**

For years, _Bluetooth®_ technology has been the global standard for reliable, secure wireless connectivity. Now, with the capability to create large-scale, smart lighting networks, your lighting system can double as a wireless platform and support a range of building services. A smart lighting system built on a [Bluetooth mesh](https://www.bluetooth.com/bluetooth-technology/topology-options/le-mesh) network offers inherent interoperability and a full-stack approach synonymous with Bluetooth technology, providing everything you need to create a truly smart building.

To learn more about how Bluetooth mesh is disrupting building automation, wireless sensor networks, asset tracking, and more, watch this [on-demand webinar](http://pages.bluetooth.com/mesh-webinar.html?utm_campaign=mesh&utm_source=homepage-cta&utm_medium=homepage-cta-on-demand&utm_term=homepage-hero&utm_content=homepage-hero&_ga=2.23152378.1569021496.1511197847-1039422551.1510158773).

**ON-DEMAND WEBINAR**

![Webinar](https://blog.bluetooth.com/~/media/images/blog%20images/mesh%20blogs/webinar-icon-vert.ashx)

### [What Makes Bluetooth Mesh so Disruptive?](http://pages.bluetooth.com/mesh-webinar.html?utm_campaign=mesh&utm_source=blog-cta&utm_medium=blog-cta-on-demand&utm_term=blog-lighting-as-a-platform-part-2&utm_content=blog-cta-bottom)

_The behind-the-scenes story of the making of Bluetooth mesh_

Watch our free on-demand webinar to discover how Bluetooth mesh is disrupting building automation, wireless sensor networks, asset tracking, and more.
