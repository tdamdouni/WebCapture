# Future Electronics – How to successfully connect IoT devices to the cloud: NB-IoT and LoRaWAN technologies compared

_Captured: 2017-11-12 at 11:58 from [www.my-ftm.com](http://www.my-ftm.com/2017/11/future-electronics-how-to-successfully-connect-iot-devices-to-the-cloud-nb-iot-and-lorawan-technologies-compared/)_

By Amar Abid-Ali  
Vertical Segment Manager  
Future Connectivity Solutions (a division of Future Electronics)

**For the past few years, Machine-to-Machine (M2M)and Internet of Things (IoT) applications have relied on 2G and 3G cellular telephone networks for wide-area connectivity. Consumer demand for high-speed broadband coverage on the smartphone has led network providers to supplement these older protocols with the new high-bandwidth 4G, also called LTE, technology. While LTE networks provide an excellent service for consumers who wish to stream high- quality video on the move and who are prepared to pay a premium for it, M2M users need a different, price-sensitive network for their low-power, low data-rate, long-range applications.**

This means that an opportunity has arisen for dedicated Low-Power Wide-Area Networks (LPWANs) to fill the void. There are many contenders in this space, but two network technologies have taken a lead: LoRaWANTM, and Narrowband-IoT (NB-IoT), a cellular LTE technology developed by the 3GPP industry consortium which also defines the 3G and LTE network standards.

There are distinct differences between the performance and features of these two competing standards. Is there room for both of them in the market, and is one more likely to take more market share?

**Competitor 1: LoRaWAN**  
LoRaWAN is an LPWAN specification intended for 900MHz wireless sensor nodes in local private networks or in regional and nationwide public networks. The protocol provides interoperability among nodes without the need for complex local installations. The network architecture is laid out in a star topology, in which gateways relay messages between sensor nodes, network servers and application servers.

![Pg22_Fig1](http://www.my-ftm.com/wp-content/uploads/2017/11/Pg22_Fig1.jpg)

> _Fig. 1: LoRaWAN network topology_

The LoRaWAN gateway is connected to the network server by way of Ethernet, cellular or WLAN (Wi-Fi®) routers, while sensor nodes use chirp modulation to connect to the gateways, as shown in Figure 1. The span between a node and a gateway can stretch to many miles. The LoRaWAN air protocol uses different frequency channels and data rates, and uses wideband linear frequency-modulated pulses (chirps), the frequency of which increases or decreases over a certain period of time to encode information.

The protocol's maximum data rate ranges from 0.3kbits/s to 50kbits/s. To maximise the battery life of sensor nodes and to make the best use of network capacity, the network server uses an adaptive data rate to manage the effective data rate and the RF output for each node.

LoRaWAN has three classes of end-point devices to address different applications. It implements several layers of encryption, including a network-level unique network key (EUI64), an application-level unique application key (EUI64), and a device-specific key (EUI128) at the node level.

Class A devices have bi-directional communications: one transmission is followed by two receive slots. This is the lowest-power option and would typically be used in a Smart City application.

Class B devices are similar, but have an option for additionally scheduled receive slots. This option means the server can be notified when the end node is receiving. A typical use case would be an automatic irrigation system.

Class C nodes transmit periodically, but are otherwise in receive mode. Typically they would be used in a smart street-lighting application.

Modules for implementing a LoRa sensor node are available from Microchip, Murata, MultiTech and Laird, as shown in Figure 2. LoRaWAN gateways are available from MultiTech, as shown in Figure 3.

Public LoRaWAN networks are now in operation in parts of Europe and North America. Information about LoRaWAN network installations can be found via the LoRa AllianceTM, a consortium of hundreds of technology companies and network service providers which promotes and regulates the LoRaWAN standard (www.lora-alliance.org).

![Pg22_Fig2](http://www.my-ftm.com/wp-content/uploads/2017/11/Pg22_Fig2.jpg)

> _Fig. 2: Laird's RM1 LoRa module_

**Competitor 2: NB-IoT on LTE networks**  
LTE technology is notably different from previous generations of cellular networks with regard to carrier frequency and bandwidth, as shown in Figure 4. A number of 4G LTE bands are specified by the standard, and they vary depending on country as well as carrier. These licensed spectrums are split into Frequency Division Duplexing (FDD) and Time Division Duplexing (TDD) types where the FDD spectrum requires pair bands, one for uplink and one for downlink, and the TDD uses a single band as uplink and downlink on the same frequency but separated in time.

Some 31 pairs of LTE bands operate at frequencies between 452MHz and 3.6GHz, and an additional 12 TDD bands are between 703MHz and 3.8GHz. The higher frequencies allow for faster transmission in urban areas, while lower frequencies offer additional range but less bandwidth in rural areas. These bands typically offer between 10MHz and 20MHz of bandwidth for data transfer, although they can be split up into smaller 1.4MHz, 3.0MHz and 5.0MHz bands.

As its name suggests, a Narrowband-IoT network uses smaller, 200kHz bands. Maximum Transmit power is 23dBm, and the maximum data rate on an NB-IoT link is 200kbits/s.

One of the advantages of NB-IoT is that it operates within a licensed spectrum, which means that it provides a secure and established public network for use by IoT businesses, without the risk of interference or jamming to which the LoRaWAN unlicensed frequency bands are exposed.

![Pg22_Fig3](http://www.my-ftm.com/wp-content/uploads/2017/11/Pg22_Fig3.jpg)

> _Fig. 3: MultiTech's MultiConnect® Conduit™ LoRaWAN gateway_

What is more, NB-IoT technology was developed specifically for use by IoT applications that have low data usage and by devices which require long battery lifetimes. In Europe, network carrier Vodafone has been taking the lead in NB-IoT network deployment: it has clearly calculated that the technology allows it to extend usage of its LTE network infrastructure by providing cost-effective support for low data-rate applications, such as sensing and monitoring devices.

**Head-to-head comparison**  
The choice between using a LoRaWAN or an NB-IoT network for a particular application can involve the consideration of many parameters. The first thing to consider is whether public infrastructure is available in the area in which the application's nodes are to operate. If an application is to run in an urban or suburban area which already has good LTE network coverage, then support for NB-IoT service might be relatively easy to secure.

Conversely, in tightly defined areas of operation such as a university campus, or in remote rural areas with no LTE coverage, a quicker or more cost-effective option might be to install a private LoRaWAN network. Even if there is LTE coverage available, the business case might still favour LoRaWAN: it is a matter of balancing capital expenditure against operational expenditure. There is an upfront cost to installing a private LoRaWAN network, but once in place it is normally cheap to run and is free of subscription fees. This requires the private network owner to have the skills and resources to perform network commissioning and management.

By contrast, the use of a public NB-IoT network has no upfront cost, because the network has already been put in place by a mobile phone network operator, but continuing operation requires the payment of regular subscription charges to the carrier.

![Pg22_Fig4](http://www.my-ftm.com/wp-content/uploads/2017/11/Pg22_Fig4.jpg)

> _Fig. 4: LTE networks use multiple frequency bands to optimise for coverage and data rate_

Another issue to consider is regulatory and carrier certification costs. In both cases, products with LoRaWAN and NB-IoT embedded modules will require CE regulatory certification in Europe for intentional and unintentional emissions. NB-IoT devices will also require carrier certification from the network service provider.

Other considerations are the cost and size of the embedded module for the application, as well as data rate and range. In the case of both LoRaWAN and NB-IoT, chip suppliers and module manufacturers have brought prices and sizes in line with existing technologies such as Wi-Fi®, ZigBee® and Bluetooth® technologies. Modules are now available that measure just 24mm x 24mm, and prices are on target to fall to a level similar to those of other RF protocols as adoption of the technologies widens.

And while the capabilities of LoRaWAN and NB-IoT are equally suitable to many applications, at the margins either technology might be a clearly superior choice. For instance, at a very low data rate of 300bits/s, LoRaWAN can achieve an extraordinarily long range of 15km in open space. Some applications with a low data requirement might need this long range, which could mean that NB-IoT would be unsuitable.

Alternatively, some applications might need a guaranteed 150kbits/s data rate over the entire coverage area, a requirement which NB-IoT can meet and a LoRaWAN network cannot.

**Is there a winner?**  
It is clear from the above that both the LoRaWAN and NB-IoT network technologies have features which will appeal strongly to developers and manufacturers of IoT devices and systems. The choice between the two comes down largely to a mix of:  
• technical requirements, such as range and coverage, and data usage  
• implementation and management considerations - carriers such as Vodafone will make it easy to get a customer's NB-IoT connection up and running quickly. Other carriers will provide a similar service to users of public LoRaWAN networks. Setting up and running a private LoRaWAN network requires some expertise in network management.  
• cost - is it more profitable to minimise capital or operational expenditure?  
• timing - LoRaWAN network roll-outs are under way, but in Europe LTE networks are already widely available, and some will quickly be ready to run NB-IoT services.

In either case, the Future Connectivity Solutions division of Future Electronics is on hand to provide advice to OEMs and systems developers, and to support them in development and volume production by supplying components, modules and cloud connectivity services.

LoRaWANNB-IoT

Spectrum
Unlicensed
Licensed

Bandwidth
500kHz to 125kHz
180kHz

Peak Data Rate
300bits/s to 50kbits/s on downlink and uplink
500bits/s to 200kbits/s on downlink 300bits/s to 180kbits/s on uplink

Number of Messages per Day
Unlimited
Unlimited

Duplex Communication
No
Half-duplex

Power Efficiency
Very high
Medium

Peak Current at Maximum Transmit Power
32mA
120mA to 300mA

Sleep Current
1μA
5μA

Latency (Maximum Guaranteed)
<10s
1.6s to 10s
