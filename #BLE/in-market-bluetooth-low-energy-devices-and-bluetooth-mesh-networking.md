# In-Market Bluetooth Low Energy Devices and Bluetooth Mesh Networking

_Captured: 2017-09-19 at 20:21 from [blog.bluetooth.com](https://blog.bluetooth.com/in-market-bluetooth-low-energy-devices-and-bluetooth-mesh-networking)_

Chapter 7 of the Bluetooth Mesh Networking Series

## Bluetooth Low Energy in the World

[Bluetooth Low Energy (LE)](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-p2p?utm_campaign=mesh&utm_source=bluetooth&utm_medium=blog&utm_term=proxy-nodes&utm_content=bluetooth-blog-link) is an exceptionally successful wireless technology. It's hard to find a smartphone or tablet which doesn't support it, and it's a key ingredient in the rise of wearable technology. It's in medical devices, smart home devices, sensors, and more.

Consequently, there are billions of devices already in use which support Bluetooth Low Energy. Can these devices be used as part of a [Bluetooth mesh network](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/?utm_campaign=mesh&utm_source=bluetooth&utm_medium=blog&utm_term=proxy-nodes&utm_content=bluetooth-blog-link)? That's the question we'll answer in this article. But for those of you currently screaming at your monitor_, tablet or phone, for goodness sake, just tell me!_, I will cave immediately and answer the question right now.

**The answer is YES. Probably.**

Bluetooth Low Energy devices can participate in a Bluetooth mesh network, provided they have the right set of Bluetooth Low Energy capabilities and some additional software, which, in the case of a smartphone, could simply be a normal application that knows how to talk to a Bluetooth mesh network. In other words, an application which any developer could write.

Let's examine this exciting possibility in more detail.

## Bearers

To understand how standard, non-mesh Bluetooth Low Energy devices can be part of a Bluetooth mesh network requires us to revisit the Bluetooth mesh stack, which I introduced in my article, [An Introduction to Bluetooth Mesh - Part 2](https://blog.bluetooth.com/an-intro-to-bluetooth-mesh-part2?utm_campaign=mesh&utm_source=bluetooth&utm_medium=blog&utm_term=proxy-nodes&utm_content=bluetooth-blog-link), earlier in this series.

![The Bluetooth mesh stack](https://blog.bluetooth.com/~/media/images/blog%20images/mesh%20blogs/proxy_fig1.ashx?la=en&hash=12A1DEEB39334FCD542E8D57703CB14786FDC299)

> _Figure 1 - The Bluetooth mesh stack_

Bluetooth mesh networking uses Bluetooth Low Energy as its radio communications stack. Exactly how it uses it is the concern of the [bearer layer](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#bearer_layer) at the very bottom of the Bluetooth mesh networking stack.

At present, there are two bearers defined: the [advertising bearer](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#advertising_bearer) and the [GATT bearer](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#gatt_bearer). The default bearer, used by Bluetooth mesh networking devices, is the advertising bearer that sends and receives Bluetooth mesh packets inside Bluetooth Low Energy advertising packets.

Devices with a Bluetooth Low Energy stack that allows them to both advertise and scan have the basic, prerequisite Low Energy features required to support the advertising bearer and, ultimately, a complete Bluetooth mesh networking stack.

Devices which do not support the advertising bearer, and cannot be upgraded to use it, must use the GATT bearer. Using the GATT bearer involves encapsulating Bluetooth mesh Protocol Data Units (PDUs) inside a protocol called the [Proxy Protocol](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#gatt_bearer), which we'll learn more about later in this article.

**FEATURED RESOURCE**

### [Bluetooth Mesh Networking - An Introduction for Developers](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-tech?utm_campaign=mesh&utm_source=blog-cta&utm_medium=blog-cta&utm_term=proxy-nodes&utm_content=blog-cta-middle)

Download this comprehensive technology overview to learn more about the key concepts and terminology, system architecture, and security mechanisms, as well as the unique message publication and delivery technique behind Bluetooth mesh networking.

## Nodes and Features

Devices which are a member of a Bluetooth mesh network are referred to as _nodes_. A wide variety of product types can be nodes: lights, light switches, thermostats, window locks, occupancy sensors, and so on. Regardless of the product type, however, a node may provide certain special Bluetooth mesh network services over and above its product-specific capabilities.

The [Bluetooth mesh specification](https://www.bluetooth.com/specifications/mesh-specifications) defines the _features_ a node may possess. Having one or more of these features indicates that the node can play corresponding special roles in the network. The defined features are:

**Relay**

A Relay Node receives and retransmits Bluetooth mesh messages using the advertising bearer. The relay feature makes it possible for Bluetooth mesh messages to make multiple hops between devices and travel beyond the direct radio range of two devices, right across the network.

**Friend**

A Friend Node can store and later forward messages addressed to an associated Low Power Node.

**Low Power Node (LPN)**

An LPN is a power-constrained node, which can operate within the Bluetooth mesh network efficiently by exploiting the support of a Friend Node and, consequently, using a substantially reduced duty cycle.

**Proxy**

A Proxy Node can receive messages over one bearer (advertising or GATT) and retransmit them over the other (advertising or GATT).

## The Proxy Node

![](https://blog.bluetooth.com/~/media/images/blog%20images/mesh%20blogs/fig2_proxy_node.ashx?h=225&w=81&la=en&hash=5AB97C50B70439872B2925CAD6C3A471522043CE)

> _Figure 2 - Proxy Node_

The Proxy Node is the key to enabling non-mesh Bluetooth Low Energy devices to be part of a Bluetooth mesh network. The fundamental purpose of the Proxy Node is to perform bearer conversion. It can convert from the advertising bearer to the GATT bearer and vice versa. Therefore, a device which does not support the advertising bearer may instead send and receive various types of Bluetooth mesh messages over a GATT connection.

A node indicates that it can act as a Proxy Node by setting the proxy feature bit in the features field, which is part of the composition data state which all nodes possess.

## The Bluetooth Mesh Proxy Service

Proxy Nodes implement a GATT service called the Mesh Proxy Service and, in this context, are known as Proxy Servers. The Mesh Proxy Service contains two GATT characteristics, **Mesh Proxy Data In** and **Mesh Proxy Data Out**. Proxy Clients use the GATT Write Without Response sub-procedure to write Proxy Protocol (see below) PDUs to the Mesh Proxy Data In characteristic and receive Proxy Protocol PDUs from the Mesh Proxy Data Out characteristic in GATT notifications. This, therefore, is the mechanism by which connected GATT devices exchange data with a Bluetooth mesh network via a Proxy Node.

![Proxy Server and Proxy Client](https://blog.bluetooth.com/~/media/images/blog%20images/mesh%20blogs/proxy_fig3.ashx?la=en&hash=62CABD2F39D9F8E1D3C64728E35A1B4827B15550)

> _Figure 3 - Proxy Server and Proxy Client_

## Discovering Proxy Nodes

Bluetooth Low Energy devices use GAP advertising to facilitate their discovery by other devices. Bluetooth mesh Proxy Nodes use exactly the same technique, advertising their availability, their role as a Proxy Node, and their identity in GAP connectable advertising packets.

GAP advertising packets contain fields of various types, known as _AD Types_. These are defined in the Core Specification Supplement. Proxy Nodes include the following fields in advertising packets:

Table 1 - Mesh Proxy Advertising

**AD Type**

**Comment**

Flags

Indicates General Discoverable Mode.

Complete List of 16-bit Service UUIDs

or

Incomplete List of 16-bit Service UUIDs

Includes the UUID of the Mesh Proxy Service.

Service Data

Contains data relating to the Mesh Proxy Service which identifies the network or node that the Proxy is providing the service for.

The contents of the Service Data AD Type bear further examination.

**Service Data Field**

**Comment**

Identification Type

The value in this field lets us correctly interpret the content of the Identification Parameters field.

0x00 : Network ID type

0x01 : Node Identity type

Identification Parameters

A Network ID or a Node Identity, depending on the Identification Type.

A Network ID is a unique, public identifier derived from a Network Key (NetKey - see [Mesh Network Management](https://blog.bluetooth.com/management-of-devices-bluetooth-mesh-network?utm_campaign=mesh&utm_source=bluetooth&utm_medium=blog&utm_term=proxy-nodes&utm_content=bluetooth-blog-link)). Node Identity is derived from a combination of the Proxy Server node's Unicast Address and a network identifier, such as the network ID for one of the subnets it is enabled on.

If a Proxy Server is a member of more than one subnet, it will interleave advertising packets containing each subnet's network ID, one advertising packet at a time.

A primary use of Node Identity advertising is to allow a Provisioner to quickly connect directly back to a newly provisioned node, so that configuration of the new node may be completed.

## The Proxy Protocol

The Proxy Client and Proxy Server communicate using the Proxy Protocol and send each other Proxy PDUs. These PDUs can be thought of as containers for various types of Bluetooth mesh PDU.

Bluetooth mesh access messages use the core Bluetooth mesh stack and messages are therefore contained within Network PDUs. Network PDUs can be encapsulated within Proxy PDUs.

A variety of [beacons](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#mesh_beacon) are defined in the [Bluetooth Mesh Profile Specification](https://www.bluetooth.com/specifications/mesh-specifications), including the unprovisioned device beacon and the secure network beacon. Bluetooth mesh beacons can be accommodated by the Proxy Protocol.

The provisioning process involves its own protocol and Provisioning PDUs can also be exchanged within Proxy PDUs.

Finally, the Proxy Client and Proxy Server may exchange special proxy configuration messages, which we'll cover shortly. These too may be encapsulated within Proxy PDUs.

As you can see, most types of mesh data can be exchanged using the Proxy Protocol and therefore be sent and received by a GATT client connected to a Proxy Node.

Proxy PDUs vary in size across different devices, with the size of PDUs dynamically set according to the Maximum Transmission Unit (MTU) of the Bluetooth Low Energy Attribute Protocol (ATT), which is the underlying basis for transporting Proxy PDUs over a GATT connection. Furthermore, the Proxy Protocol can accommodate long Bluetooth mesh messages by allowing either complete Bluetooth mesh messages to be encapsulated in a Proxy PDU or individual segments of multi-segment messages.

An important point to note is that any Bluetooth mesh node may implement the [Proxy Protocol](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#gatt_bearer) and therefore support direct interactions over a GATT connection, not just Proxy Nodes. This can be useful in provisioning scenarios.

Further information on the Proxy Protocol, including the format of Proxy PDUs can be found in the [Bluetooth Mesh Profile Specification](https://www.bluetooth.com/specifications/mesh-specifications?utm_campaign=mesh&utm_source=bluetooth&utm_medium=blog&utm_term=proxy-nodes&utm_content=bluetooth-blog-link).

## Proxy Filters and Proxy Configuration 

[Proxy Clients](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-glossary#proxy_client) can exercise fine control over precisely what network traffic they receive by configuring a filter which the Proxy Server applies. Filters take the form of white lists and black lists and they each specify lists of destination addresses. Addresses in the list may be any mix of the supported address types, namely unicast, group, or virtual addresses. Messages with destination addresses not included in a white list filter are dropped by the Proxy Server's proxy filter. Similarly, messages with destinations which are included in black list filters are dropped.

Proxy configuration messages are exchanged between the Proxy Client and Proxy Server and allow the configuration of the proxy filter.

## Provisioning using a Bluetooth Low Energy Smartphone or Tablet

The Provisioning process, by which new devices are added to a Bluetooth mesh network, is typically carried out using a smartphone or tablet. Most such devices will not implement the full Bluetooth mesh networking stack and it's likely they will use the Proxy Protocol for all interactions with the Bluetooth mesh network, including provisioning. As stated earlier, Provisioning PDUs can be encapsulated within Proxy PDUs and therefore can be exchanged over a GATT connection via a Proxy Server node. This use of the Provisioning Protocol with the Proxy Protocol is given the name PB-GATT in the [Bluetooth Mesh Profile Specification](https://www.bluetooth.com/specifications/mesh-specifications?utm_campaign=mesh&utm_source=bluetooth&utm_medium=blog&utm_term=proxy-nodes&utm_content=bluetooth-blog-link).

The provisioning process was described in a previous article on our series entitled [Bluetooth mesh network management](https://blog.bluetooth.com/management-of-devices-bluetooth-mesh-network?utm_campaign=mesh&utm_source=bluetooth&utm_medium=blog&utm_term=proxy-nodes&utm_content=bluetooth-blog-link) and we'll look under the hood at the associated security details of provisioning later in this series.

## What's Required to Use the Proxy Protocol with a Proxy Node?

For a device, such as a smartphone, to use the Proxy Protocol to communicate with a Bluetooth mesh network via a Proxy Node, the device must scan and connect to the Proxy Node. In other words, it must support the GAP Central role.

Furthermore, the smartphone must first be provisioned. No device may interact with nodes in the Bluetooth mesh network without having first been provisioned.

## Summary

Support for in-market [Bluetooth Low Energy](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-p2p?utm_campaign=mesh&utm_source=bluetooth&utm_medium=blog&utm_term=proxy-nodes&utm_content=bluetooth-blog-link) devices via GATT, the Proxy Protocol, and Bluetooth mesh Proxy Nodes is big news and opens the world of [Bluetooth mesh networking](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/?utm_campaign=mesh&utm_source=bluetooth&utm_medium=blog&utm_term=proxy-nodes&utm_content=bluetooth-blog-link) to enormous numbers of devices which people already own. I'd say that's pretty exciting. Hope you feel the same way!

**FEATURED RESOURCE**

### ![](https://blog.bluetooth.com/~/media/images/page-content/case-mesh-dl-thumb.ashx?h=300&w=208&la=en&hash=B9563C75B69F352C02E671D00060C410FD034693)

### [Bluetooth Mesh Networking - An Introduction for Developers](https://www.bluetooth.com/what-is-bluetooth-technology/how-it-works/le-mesh/mesh-tech?utm_campaign=mesh&utm_source=blog-cta&utm_medium=blog-cta&utm_term=proxy-nodes&utm_content=blog-cta-bottom)

In this comprehensive technology overview, Bluetooth Technical Program Manager Martin Woolley examines the key concepts and terminology, system architecture, and security mechanisms, as well as the unique message publication and delivery technique behind Bluetooth mesh networking.
