# CAN lower- and higher-layer protocols

_Captured: 2015-10-12 at 13:42 from [www.can-cia.org](http://www.can-cia.org/can-knowledge/)_

![](http://www.can-cia.org/fileadmin/resources/images/knowledge/knowledge01.png)

According to the Open System Interconnection (OSI) seven-layer model, the lower layers cover the data link and the physical layer. The upper layers are normally referenced as higher-lower protocols. Often, the CAN-based application layer includes functional elements of other upper layers, too.

The knowledge pages provide technical information on the CAN (Controller Area Network) data link layer protocols and several CAN physical layer options. The CAN protocol description covers both the Classical CAN data link layer and the newly introduced CAN FD data link layer. Both are internationally standardized in [ISO 11898-1](http://www.iso.org/iso/home.html).

Besides these lower-layers, the CAN knowledge pages give an overview of several higher-layer protocols. This includes, in particular, the CANopen application layer and the related device, interface, and application profiles. Additionally, some basic information on other CAN-based higher-layer protocols such as DeviceNet, [SAE J1939](http://www.sae.org/), Isobus (ISO 11783), ISO 11992 series, etc can be found here.

## CAN data link layer

CAN is a very reliable multi-master serial bus system with multi-drop capabilities. The bus arbitration method is the same for both CAN data link layer protocols. The CAN messages are broadcasted. This means every node is able to consume any message produced by any other node in the network.

Originally developed for use as an in-vehicle network in passenger cars, nowadays CAN is used in many other industries. This includes applications in any kind of transportation system (rail vehicle, aircraft, marine, etc.), in industrial machine control systems, in home and building automation (e.g. HVAC, elevators), in mobile machines (construction and agriculture equipment), in medical devices and laboratory automation, as well as in many other embedded and deeply embedded electronics. Each year, more than 800 million CAN nodes are sold. The price for CAN controllers is very reasonable.

Originally, there was just what we today call the Classical CAN called data link layer protocol. Introduced by Bosch as CAN 2.0 A/B, it has been internationally standardized in the ISO 11898 series since 1993. CiA doesn't use the term CAN 2.0 anymore, we call it Classical CAN.

A couple of years ago, Bosch and other CAN experts improved the CAN protocol to what is known as the CAN FD protocol. The Classical CAN and CAN FD protocols are backward compatible. Any CAN FD compliant node understands Classical CAN frames. However, Classical CAN nodes destroy a consumed CAN FD frame by means of an error frame.

Both protocols feature a high reliability. All single-bit failures are detectable. Multi-bit failures are found with a very high probability. One of the unique features is the fault confinement, which provides a network-wide data consistency.

## Physical layer options

> _CAN is one of the most robust network technologies, especially if you are using a line-topology with very short stubs and a twisted-pair of cable_

A twisted-pair copper cable with common ground usually realizes the physical transmission. Of course, all connected nodes need to support the same data-rate and the same bit-timing settings.

Most common is the high-speed transmission as standardized in ISO 11898-2. It supports data-rates up to 1 Mbit/s. There are also high-speed transceivers with low-power capability (ISO 11898-5) and selective wake-up functionality for partial networking (ISO 11898-6). The three standards mentioned above will be merged into one standard. The robustness of high-speed CAN networks is excellent.

In-vehicle networks often use star-topologies, sometimes with multiple stars. In some applications, hybrid topologies are used, combining line and star. However, the most robust topology is a bus-line with very short stubs.

The other physical layer standard used in the automotive industry is ISO 11898-3, a so-called fault-tolerant, low-power transmission. It is not widely used in other industries, and it is limited to 125 kbit/s. An application-specific physical layer is standardized in ISO 11992-1, which is also limited to 125 kbit/s. It is only used in European truck-trailer point-to-point networks. The single-wire transmission as specified in SAE J1411 has some restrictions regarding the robustness and the transmission rate. It is not widely used in Europe.

Other medias are also in use: Fiber-optical and power-line transmissions, for example. However, their specifications are proprietary.

## Standardized higher-layer protocols

There are several CAN-based higher-layer protocols. The most generic one is CANopen. It comprises the CiA 301 application layer standardized internationally in EN 50325-4 and several device, interface, and application profiles (CiA 400 series). Additionally, there are other protocol specifications for additional communication functions (CiA 300 series). CANopen is used in many embedded and deeply embedded control applications.

The family of J1939-based application profiles is another approach. The original J1939 specifications were designed for in-vehicle networks in trucks and buses. The Society of Automotive Engineers (SAE) develops and maintains these recommended practices. The internationally standardized ISO 11783 series (also known as Isobus), one of the J1939 derivatives, is dedicated to implementing communication in agriculture tractors. It can also be used for forestry mobile machines. The IEC 61162-3 (also known as NMEA2000) is another J1939 derivate; it is optimized for CAN-based marine navigation networks. The ISO 11992 series standardizes the communication between trucks and trailers. This J1939 derivative is a base for the European regulation of towed vehicles.

In the passenger car industry, application layers are normally proprietary. An exception is the CAN transport layer and the diagnostic services, which are internationally standardized in ISO 15765-2 respectively in the ISO 15031 series. Another exception is an open network for add-on devices. This is specified in the CiA 447 CANopen application profile.

Another CAN-based higher-layer protocol is DeviceNet, originally developed for factory automation. It also comprises a broad set of profile specifications. DeviceNet is internationally standardized in IEC 62026-3. The ODVA nonprofit association maintains this standard and the related profiles.
