# Bluetooth history and the future of Bluetooth mesh networking

_Captured: 2017-09-22 at 19:13 from [www.iebmedia.com](http://www.iebmedia.com/index.php?id=12535&parentid=74&themeid=255&hpid=2&showdetail=true&bb=1&appsw=1&sstr=mesh)_

## Bluetooth mesh networking is most likely to be initially adopted for use in building automation, commercial lighting and sensor network. But as the latest chapter in Bluetooth development, it has potential uses in many new applications and provides a wide range of networking benefits.

BLUETOOTH TECHNOLOGY IS WELL-KNOWN and it is one of the most ubiquitous wireless communications technologies on the planet. It′s been in existence since 2000, and has found its way into billions of devices. Since then, Bluetooth has been carefully and systematically improved, enabling it to keep pace with market requirements, continuing to support and inspire innovation.

Bluetooth mesh networking is the latest chapter in the Bluetooth story, bringing with it many new applications, use cases and benefits for developers, businesses and consumers alike.

### Flavours and features

Those with a keen interest in Bluetooth technology will be familiar with regular new releases, typically equipping Bluetooth with additional features, or improving upon existing capabilities. Occasionally, however, an entirely new "flavour" of Bluetooth is released; a distinct variant, using radio in a different way, optimised in its design and implementation for broad sets of use cases.

Bluetooth Basic Rate/Enhanced Data Rate (BR/EDR) was the first flavour of Bluetooth to be released, and was intended to act as a cable replacement technology. It soon came to dominate wireless audio products, and turned into the enabler for new computer peripherals, such as wireless mice and keyboards.

Bluetooth Low Energy (LE) was the next truly distinct Bluetooth technology and was optimised to use as little energy as possible, able to operate and communicate wirelessly, powered by only a coin-sized battery which could often last for years. It′s hard to find a smartphone or tablet that doesn′t support Bluetooth LE nowadays.

So, with this in mind, is Bluetooth mesh networking a new flavour of Bluetooth, or is it a new feature? To be honest, it′s neither.

### The Crucial Three

It′s common to find both Bluetooth BR/EDR and Bluetooth LE available in devices like smartphones, but they do not rely on each other′s services and capabilities. Those two Bluetooth flavours work independently of each other, and whilst they′re quite happy to coexist in the same device, it′s not possible to use Bluetooth BR/EDR to communicate with a Bluetooth LE device, or vice versa.

In contrast, Bluetooth mesh networking uses, and is dependent upon, Bluetooth LE. Bluetooth LE is the wireless communications protocol stack which Bluetooth mesh makes use of.

At its most basic level, Bluetooth BR/EDR lets one device connect to and communicate with another device, establishing a point-to-point relationship which is reflected in the term "pairing". Some devices can have multiple point-to-point relationships with other devices, and can form a hub/spoke topology known as a "piconet".

Bluetooth LE devices can also form point-to-point and hub/spoke relationships with other devices, as well as work in a connectionless way, broadcasting data which any other device in direct radio range can receive. This is a 1:m topology, where m can be a very large number. If devices listening to broadcasts are not transmitting data themselves, then the broadcasting device has the radio spectrum to itself and there′s effectively no limit to the number of other devices that can receive and make use of its broadcasts.

Bluetooth mesh allows us to establish a many-to-many (m:m) relationship between wireless devices. Furthermore, devices may relay data to other devices not in direct radio range of the originating device. In this way, mesh networks can span large physical areas, and contain large numbers of devices.

### Motivation for mesh networking

Bluetooth mesh networking was created because mesh topologies offer the best way to meet various and increasingly common communications requirements, demanded by applications such as building automation and sensor networks. These requirements include coverage of large areas, the ability to monitor and control a large number of devices, and optimised low energy consumption, to name but a few.

There are other low-power wireless communications technologies which support mesh topologies, but these are believed to have unacceptable constraints and limitations, and are generally not supported by standard smartphone, tablet and PC equipment. They are thought to lack optimisation for the problems they are trying to address, and the products they want to create. Other issues include low data transmission rates, limited numbers of "hops" when relaying data across the mesh, scalability limits often caused by the way radio channels are used, and difficulties and delays when following procedures to change the device composition of the mesh network.

![](http://www.iebmedia.com/images/art_images/IEB102_p22_1.jpg)

> _Bluetooth mesh networking uses a publish/subscribe messaging system._

Creating an industry-standard mesh communications technology based on Bluetooth LE presented an opportunity to meet the requirements without the associated limitations and constraints.

### Message-oriented communication

Bluetooth mesh networking uses a publish/subscribe messaging system. Devices may send messages to addresses whose names and meaning correspond to high level concepts which users can understand, like "Garden Lights". This is publishing. Devices can also be configured to receive messages sent to particular addresses by other devices. This is subscribing. When a device publishes a message to a particular address, all the other devices that subscribed to that address will receive a copy of it, process it, and react in some way.

![](http://www.iebmedia.com/images/art_images/IEB102_p22_2.jpg)

> _Mesh networks allow devices to communicate with each other across a large area._

Imagine a set of outdoor lights. Each light is configured so that it subscribes to "Garden Lights" messages. Now, imagine a Bluetooth mesh light switch sending an "ON" message to the "Garden Lights" address. All of the lights in the garden will receive the "ON" message and react to it by switching on.

### Messages and device state

Devices in a Bluetooth mesh network have a set of independent state values, representing some condition of the device. Referring to the previous example, each light has a state value which represents whether the device is switched on or off. Changing it, by publishing a message of a type whose definition means that it acts upon "on/off" state values, is how a Bluetooth mesh light switch is able to control lights. Changing a state value modifies a physical condition of the device itself, like switching it on or off.

### Relaying

Mesh networks allow devices to be installed and communicate with each other across a large area. Consider a large space such as a shopping centre, airport or office building. With walls and other physical barriers, it may not be possible to achieve direct radio contact from a device on one side of a building, to a device installed on the far side of the same building, or even a device in an adjacent building. Bluetooth mesh networking solves this problem by allowing some of the devices in the network to be designated "relays".

![](http://www.iebmedia.com/images/art_images/IEB102_p22_3.jpg)

> _Mesh topologies offer the best way to meet various and increasingly common communications requirements._

Relay devices retransmit messages that they receive from other devices, and are able to communicate with devices that are not in radio range of the device which originally published the message. A message may be relayed multiple times, over a maximum of 127 "hops"; enough to relay a message across an enormous physical area.

### Managed flooding

Bluetooth mesh networking uses an approach known as "flooding" to publish and relay messages. This means that messages are not routed by a process which results in them being transmitted along a specific path comprising a sequence of only certain devices. Instead, all devices in range receive messages and those which are acting as relays, retransmit the message to all other devices in range. Flooding has its pros and cons, but with Bluetooth mesh networking it has been optimised to retain the strengths while addressing the weaknesses.

Flooding doesn′t need particular devices to have special responsibility to act as centralised routers, the failure of which could render the entire network inoperable. Specific routes being unavailable could also have a catastrophic impact on the network. This is avoided with a flooding approach to mesh networking. This also means there are multiple paths by which a message can arrive at its destination.

### Optimising the mesh network

All packets include a field known as the TTL. This may be used to limit the number of hops that a message takes as it is relayed. Heartbeat messages, transmitted by devices at intervals, include information which allows the network to learn about its topology and how many hops away each of the other devices is. This allows devices to set TTL to an optimal value, avoiding messages being relayed an unnecessary number of times.

Every device contains a message cache so that it can determine whether or not it has seen a message before, and if it has it will immediately discard the message, thus avoiding unnecessary processing higher up the stack. Perhaps most interestingly, devices which are very power-constrained, such as sensors, may be designated "low power nodes". These nodes work in conjunction with one or more devices, which are designated "friends". Friends are not power constrained and act on behalf of the low power node, storing messages addressed to it and only delivering them when asked. The relationship between a low power node and a friend is termed "friendship".

Low power devices usually spend the most significant proportion of their time not transmitting data. Sensors are a good example of this. Maybe a sensor only transmits a temperature reading whenever the temperature falls below or above a specified threshold, and this typically happens twice a day. Such an infrequent transmission schedule keeps the energy use of this type of device very low.

But what if the sensor needs to be able to receive data occasionally? It will need to keep up to date with the security keys being used in the network. And maybe those temperature thresholds need to be modified to use different values according to the season. For a sensor to receive messages directly, it needs to switch the radio on so that it can receive data. Most of the time it will receive nothing, but energy will have been expended nevertheless.

Working with a friend allows the low power node to schedule its use of the radio to receive messages to whatever frequency makes sense for the device, but importantly, a much lower frequency than it would have otherwise needed to if it had to "listen" for messages all the time.

Friends do the heavy lifting for low power nodes. They store messages, and deliver them when explicitly asked to, operating to a schedule which they control, and thus can make the most efficient use of the radio possible.

### Bluetooth device support

Bluetooth mesh networking may be new, but Bluetooth Low Energy (LE) is not, and many of the devices on the market already, including most modern smartphones and tablets, will be able to access a Bluetooth mesh network via proxy nodes.

These include a standard Bluetooth Low Energy GATT service which has two GATT characteristics; Mesh Proxy Data In, and Mesh Proxy Data Out. Bluetooth LE devices, like smartphones, can use these characteristics to send and receive data to and from the Bluetooth mesh network.

### Security

Security is mandatory in Bluetooth mesh. Every packet is encrypted and authenticated.

Replay attacks are prevented by judicious use of sequence numbers. Man-in-the-middle attacks are protected against by using asymmetrical cryptography during important procedures. Protection against trash-can attacks, which exploit discarded devices, is provided for. Security keys get refreshed when necessary.

Security of the network and security of individual applications such as lighting, heating or physical building security are independent of each other. Different security keys are used for securing network layer operations such as relaying vs securing the application-specific content of messages. A light bulb, for example, has full access to data in messages transmitted by light switches, because they have the same application key.

But while the same light bulb is able to relay messages from the Bluetooth physical access token to the lock in the front door, it is not able to see the application layer content of those messages.

### The stack

Bluetooth mesh networking introduces a new protocol stack, which sits on top of Bluetooth LE. Each layer of the stack is responsible for the following key functions:

  * _Bearer Layer:_ Defines how PDUs are transported using an underlying LE stack. Currently, two bearers are defined, the Advertising Bearer and the GATT Bearer.
  * _Network Layer:_ Defines various message address types and a network message format. The relay and proxy behaviors are implemented by the network layer.
  * _Lower Transport Layer:_ Where required, the lower transport layer handles segmentation and reassembly of PDUs.
  * _Upper Transport Layer:_ Responsible for the encryption, decryption and authentication of application data passing to and from the access layer. It also has responsibility for special messages known as transport control messages. These include heartbeats and messages related to the "friendship" relationship.
  * _Access Layer:_ Responsible for the format of application data, defining and controlling the encryption and decryption process which is performed in the upper transport layer and verifying that data received from it is for the right network and application, before forwarding the data up the stack.
  * _Foundation Model Layer:_ Responsible for the implementation of those models concerned with the configuration and management of a mesh network.
  * _Model Layer:_ Concerned with the implementation of models and, the implementation of behaviors, messages, states and so on.

### Future of Bluetooth mesh networking

Bluetooth mesh networking will initially be adopted for applications such as building automation, commercial lighting and sensor networks, but it is anticipated to be adopted across a broad range of industry sectors and applications.
