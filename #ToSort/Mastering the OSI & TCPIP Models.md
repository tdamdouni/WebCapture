# Mastering the OSI & TCP/IP Models

_Captured: 2015-12-22 at 00:19 from [jaredheinrichs.com](http://jaredheinrichs.com/mastering-the-osi-tcpip-models.html)_

First what is the OSI model? The OSI model is a framework of protocols that allows two devices to communicate on a network or over the internet. Each layer of the OSI model makes each layer responsible for over looking and carrying out a specific task. I've made a cheat sheet that breaks everything down into it's most basic form. I will be referring to this chart throughout the rest of this post.

![osi-cheat-sheet-01](http://jaredheinrichs.com/wp-content/uploads/2013/10/osi-cheat-sheet-01.png)

The OSI layer is broken up into 7 layers. The top most layer is layer 7 and the lowest layer is Layer 1. Each layer has been given a name that helps identify what is happening on each layer.

### Let's go over the OSI Layer in more detail

**Layer 7** is the **Application layer**. This is the layer that us a humans interact with the most. This layer the application sets up rules on how an application will send and receive data. Much like Languages, if both people don't speak the same one, a conversation will not likely amount to anything.

**Layer 6** is is the **Presentation layer**. It helps the Application layer by formatting the data in such a way that both parties will be able to read it.

**Layer 5** is the **Session layer**. It helps ensure that the data is synchronized.

**Layer 4** is the **Transport layer**. It is responsible for creating and managing the packets that will go out on the network.

**Layer 3** is the **Network layer**. It is responsible for Addressing and Routing. This layer is in charge of the IP address of the hosts as well as knowing how to route information to another host. Because IP supports routing the destination host can be local or out the internet.

**Layer 2** is the **data link layer**. It is responsible for Data frames and the Management of those frames. Data frames deal with layer 2 addresses (MAC Address) which are non-routable addresses. Technically Layer 2 can actually be broken up into two sub-layers:

  * Logical Link Control
  * Media Access Control (NIC's Mac Address)

**Layer 1** is the **Physical Layer**. It is responsible for talking with a physical device like a NIC. In particular it's changing the data into electronic pulses that can be sent out on the wire.

### Device Type by Layer

To give you a better idea what layers the network devices work at I created the device type column.

**Layer 7** - I put gateway here. This is not the same as a "Default Gateway". This is a device that works kind of like a translator. It is able to understand application languages like HTTP, SMTP, etc. The term "Next Generation Firewalls" is some times applied to these devices.

**Layer 3** - Routers and "Swouters" devices go here. A Swouter is a layer 3 switch. It has more than a couple ports on the back and is capable of routing.

**Layer 2** - This is the typical layer where switches are put. Switches are able to look at traffic and filter data based on MAC addresses.

**Layer 1** - Typically Hubs and Repeaters are put here. You don't really see them anymore because they tend to be slow and pretty brain dead. Because of this they only work "well" in a very small network design.

### TCP/IP Model

You will notice that the TCP/IP model only has 4 layers. The four layers correlate to one or more of the OSI Model. Later versions have 5 and have different names. From what I've read we need to know both.

TCP/IP Stands for Transmission Control Protocol/Internet Protocol. It is the basic communication protocol of the Internet. It can be used on the internet as well as private networks. TCP/IP is based off the 4 layer Darpa model. Looking back at the "Cheat sheet" you will notice that I've filled in a column with what protocols are used at each layer.

### Transmission Protocols

There are two types of transmission protocol types in TCP/IP. These protocols are called TCP and UDP. TCP is like Certified Mail and UDP is like 1st class Mail. Only Certified mail tells you if the other side has received all packages.

TCP (Transmission Control Protocol)

  * One to One
  * Connection Oriented
  * Reliable Communication

UDP (User Datagram Protocol)

  * Multicast (one to many)
  * Connectionless
  * Unreliable

Connection orientated communication means that connection must be established before data can be exchanged. TCP uses a three-way handshake to establish this connection.

  1. Hi I'd like to talk
  2. Hi I got the info. Here's how to talk to me
  3. Okay, Let's begin talking

### Internet Layer Protocols

IP

  * Protocol of the internet
  * Addressing
  * Routing

Arp

  * Type of Address Resolution Protocol
  * Resolves IP addresses to Hardware Address (MAC)

ICMP - Internet Control Message Protocol

  * Diagnostic and error reporting.
  * Ping uses ICMP

IGMP - Internet Group Management Protocol

  * Manages IP multicast group membership. Is NOT the same as ICMP!
