# An Intro to Bluetooth Mesh Part 1

_Captured: 2017-09-19 at 20:26 from [blog.bluetooth.com](https://blog.bluetooth.com/an-intro-to-bluetooth-mesh-part1)_

Chapter 1 of the Bluetooth Mesh Networking Series

## Introduction

_Bluetooth_® technology is one of the world's best known brands and one of the most ubiquitous wireless communications technologies on the planet. It's been in existence since 2000 and has found its way into billions and billions of devices. Last year alone, over three billion Bluetooth devices were shipped by manufacturers.

Bluetooth has not stood still. Since its first incarnation, Bluetooth has been carefully and systematically improved so that it has continued to keep pace with market requirement, and continued to support and inspire innovation.

[Bluetooth mesh networking](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh) is the latest chapter in this incredible technology story and 150 companies, all members of the Bluetooth SIG, have helped create it.

This is the first in a series of articles where we'll introduce you to Bluetooth mesh networking. We start with a two-part overview and will then proceed to explore aspects of the technology in greater detail in subsequent parts of the series.

## Flavors and Features

People interested in Bluetooth technology will be accustomed to seeing new releases adopted by the Bluetooth SIG at regular intervals.

Typically, new releases equip Bluetooth with additional features or they improve upon existing capabilities in some way. Every now and again though, an entirely new "flavor" of Bluetooth is released; a quite distinct variant of Bluetooth, which uses radio in a different way and is optimized in its design and implementation for broad sets of use cases.

Bluetooth Basic Rate/Enhanced Data Rate ([BR/EDR](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/br-edr)) was the first flavor of Bluetooth to be released. It was intended to act as a cable replacement technology and soon came to dominate wireless audio products and be the enabler for new computer peripherals, such as wireless mice and keyboards.

![wireless headphones](https://blog.bluetooth.com/~/media/images/blog%20images/mesh%20blogs/introtomesh_part1_fig1.ashx?la=en&hash=08BA6E5601BEAD21A3244AAACCEDEA070125AB5B)

> _Figure 1 - Bluetooth BR/EDR revolutionized wireless personal audio_

Bluetooth Low Energy (LE) was the next truly distinct Bluetooth technology to appear. It was optimized to use as little energy as possible with devices that incorporate it and able to operate and communicate wirelessly, powered by only a coin-sized battery, which could often last for many years. It's been very widely adopted. It's hard to find a smartphone or tablet that doesn't support Bluetooth LE. Health, sports and fitness devices, like activity trackers, rely on Bluetooth LE technology. So do wearables, like smart watches. The impact of this Bluetooth flavor has been impressive and widespread.

![fitness tracker watch](https://blog.bluetooth.com/~/media/images/blog%20images/mesh%20blogs/introtomesh_part1_fig2.ashx?la=en&hash=99B4C2810A2A8B26D9E022D17B4D3A512F94E0FE)

> _Figure 2 - Bluetooth Low Energy is a key enabler in wearables_

So is Bluetooth mesh networking a new flavor of Bluetooth? Or is it a new feature?

In fact, it's neither. Let's find out more about this exciting new Bluetooth technology, how it relates to other forms of Bluetooth, what it can do and how it works.

## The Crucial Three

It's common to find Bluetooth BR/EDR and Bluetooth LE both available in devices like smartphones, but they do not rely on each other's services and capabilities. To all intents and purposes, those two Bluetooth flavors work independently of each other. In fact, whilst they're quite happy to coexist in the same device, it's not possible to use Bluetooth BR/EDR to communicate with a Bluetooth LE device or vice versa. They're happy in each other's company, but they don't talk.

In contrast, [Bluetooth mesh networking](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh) uses and is dependent upon Bluetooth LE. Bluetooth LE is the wireless communications protocol stack which Bluetooth mesh makes use of.

**Bluetooth mesh is not a wireless communications technology. It's a networking technology.**

Figure 3 shows the relationship between Bluetooth BR/EDR, Bluetooth LE and Bluetooth mesh.

![Bluetooth radio options](https://blog.bluetooth.com/~/media/images/blog%20images/mesh%20blogs/introtomesh_part1_fig3.ashx?la=en&hash=4D6F0C95BE33F61C11A905A7A0EC909594592B49)

> _Figure 3 - The relationship between Bluetooth mesh and Bluetooth LE_

## A Tale of Topologies

At its most basic level, Bluetooth BR/EDR lets one device connect to and communicate with another device, establishing a 1:1 relationship which is reflected in the term "pairing", which most people will be familiar with. Some devices can have multiple 1:1 relationships with other devices and can form a kind of hub / spoke topology known as a "piconet".

![Bluetooth point-to-point connection](https://blog.bluetooth.com/~/media/images/blog%20images/mesh%20blogs/introtomesh_part1_fig4.ashx?la=en&hash=C72770499D56DE693B133EDA2E5620E4073A5A12)

> _Figure 4 - Bluetooth BR/EDR and one-to-one topologies_

Bluetooth LE devices can also form 1:1 and hub/spoke relationships with other devices, as well as work in a connectionless way, broadcasting data which any other device in direct radio range can receive. This is a 1:m topology where m can be a very large number! If devices listening to broadcasts are doing no transmitting of data themselves, then the broadcasting device has the radio spectrum to itself and there's no effective limit to the number of other devices that can receive and make use of its broadcasts. Bluetooth beacons are an excellent example of this capability in action.

![Bluetooth broadcast](https://blog.bluetooth.com/~/media/images/blog%20images/mesh%20blogs/introtomesh_part1_fig5.ashx?la=en&hash=2976DA772C74F87F6A2A2AA1D2D92C315286021A)

> _Figure 5 - Bluetooth LE and broadcasting_

Bluetooth mesh allows us to establish a many-to-many (m:m) relationship between wireless devices. Furthermore, devices may relay data to other devices not in direct radio range of the originating device. In this way, mesh networks can span very large physical areas and contain large numbers of devices.

![Bluetooth mesh network](https://blog.bluetooth.com/~/media/images/blog%20images/mesh%20blogs/introtomesh_part1_fig6.ashx?la=en&hash=F299277592562A0E59E2A02F57527978CFE68F59)

> _Figure 6 - Bluetooth mesh networking and a many-to-many topology_

## Motivation for Mesh Networking

Bluetooth mesh networking was created because mesh topologies offer the best way to meet various, increasingly common communications requirements, typified by applications such as building automation and sensor networks. Those requirements include:

  * Coverage of very large areas
  * "Just works interoperability"
  * The ability to monitor and control large numbers of devices
  * Optimized, low energy consumption
  * Efficient use of radio resources, leading to scalability
  * Compatibility with currently available smartphone, tablet and personal computer products
  * Industry-standard, government-grade security

There are other low-power wireless communications technologies which support mesh topologies, but our members often report that these technologies have unacceptable constraints and limitations, and that they are not optimal for the kinds of problems that they are trying to address and the types of products they want to create. Issues in other, comparable technologies, include low data transmission rates, limited numbers of "hops" when relaying data across the mesh, scalability limits often caused by the way radio channels are used and difficulties and delays when following procedures to change the device composition of the mesh network.

Other mesh technologies are, generally speaking, not supported by standard smartphone, tablet and PC equipment; a major constraint.

Creating an industry-standard mesh communications technology based on Bluetooth LE, gave the opportunity to meet the requirements, but without the associated limitations and constraints. Interoperability and energy efficiency are the hallmarks of Bluetooth LE after all.

## Message-Oriented Communication

Bluetooth mesh networking uses a [publish / subscribe](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#publish_subscribe) messaging system.

Devices may send [messages](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#message) to addresses whose names and meaning correspond to high level concepts which users can understand, like "Garden Lights". This is called "[publishing](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#publish_subscribe)".

Devices can be configured to receive messages which were sent to particular addresses by other devices. This is called "[subscribing](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#publish_subscribe)".

When a device publishes a message to a particular address, all the other devices that subscribed to that address will receive a copy of it, process it and react in some way.

Imagine a set of outdoor lights installed in the garden. Each light has been configured so that it subscribes to "Garden Lights" messages. Now, imagine a Bluetooth mesh light switch sending an "ON" message to the "Garden Lights" address. All of the lights in the garden will receive the "ON" message and react to it by.... you guessed it..... switching on.

It's that simple.

## Messages and Device State

"[State](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#state)" is a key concept in Bluetooth mesh networking. Devices in a Bluetooth mesh network each have a set of independent state values, representing some condition of the device. In our garden lights example, each light has a state value which represents whether the device is currently switched on or switched off. Changing it, by publishing a message of a type whose definition means that it acts upon "on/off" state values, is how a Bluetooth mesh light switch is able to control lights. Changing a state value modifies a physical condition of the device itself, like switching it on or off.

Messages, states and how devices behave with respect to these and other concepts are defined in specifications known as [models](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#model). Models are implemented by Bluetooth mesh devices.

We'll talk more about devices, states, messages, state changes and models in a more formal way, in another article later in this series.

## Next!

[Part 2](https://blog.bluetooth.com/an-intro-to-bluetooth-mesh-part2) of this article will take us deeper into the world of [Bluetooth mesh networking](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh) with an overview of the way messages find their way across large mesh networks, in-market device support, security and the mesh stack itself. I'll also describe some interesting performance optimisations in the design of Bluetooth mesh networking which make it highly efficient and an excellent fit for the mesh networking requirements of the age of the Internet of Things (IoT).

**FEATURED RESOURCE**

### [Bluetooth Mesh Networking - An Introduction for Developers](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-tech?utm_campaign=mesh&utm_source=blog-cta&utm_medium=blog-cta&utm_content=blog-cta-bottom)

In this comprehensive technology overview, Bluetooth Technical Program Manager Martin Woolley examines the key concepts and terminology, system architecture, and security mechanisms, as well as the unique message publication and delivery technique behind Bluetooth mesh networking.
