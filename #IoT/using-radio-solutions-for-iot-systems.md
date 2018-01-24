# Using Radio Solutions for IoT Systems

_Captured: 2017-10-10 at 15:12 from [dzone.com](https://dzone.com/articles/using-radio-solutions-for-iot-systems?edition=329543&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202017-10-10)_

Discover why [Bluetooth mesh](https://dzone.com/go?i=250336&u=https%3A%2F%2Fwww.bluetooth.com%2Fwhat-is-bluetooth-technology%2Fhow-it-works%2Fle-mesh%3Futm_campaign%3Dmesh%26utm_source%3Ddzone%26utm_medium%3Dpre-post-article-text%26utm_term%3Dbluetooth-mesh%26utm_content%3Doct-pre-post-mesh-section) is the next evolution of IoT solutions. Download the [mesh overview](https://dzone.com/go?i=250336&u=https%3A%2F%2Fwww.bluetooth.com%2Fwhat-is-bluetooth-technology%2Fhow-it-works%2Fle-mesh%2Fmesh-tech%3Futm_campaign%3Dmesh%26utm_source%3Ddzone%26utm_medium%3Dpre-post-article-text%26utm_term%3Dtech-overview%26utm_content%3Doct-pre-post-mesh-tech).

When it comes to choosing a network for IoT solutions, the most popular option is to use a cellular network. However, what happens when a cellular network doesn't get the job done? Fortunately, there are many alternatives to using a standard cell network. This blog post focuses on long-range IoT radio solutions.

Many early IoT applications leveraged existing cellular networks for long-range connectivity. The advantages of this approach include an established network with readily available development hardware and well-defined protocols and interfaces. Unfortunately, the following list of disadvantages associated with using cellular networks exceeds the advantages.

  * Using cellular networks can be expensive
  * These networks are designed for voice and high data throughput/low latency communications, which are not typical requirements of IoT applications.
  * The protocols and interfaces are difficult to customize for unique applications.
  * The cellular device certification processes are time-consuming and expensive
  * Cellular solutions are not equipped to handle the most difficult radio environments.
  * Cellular solutions are not designed for very low power
  * With the push to increase data rates and high data spectrum efficiency, older 2G and 3G infrastructure will likely begin to phase

Instead of focusing on existing cellular technologies, we will introduce alternative long-range solutions.

## Low Power Wide Area (LPWA) Networks

New LPWA networks are entering the IoT space to address some of the unique needs of IoT devices. For example, LPWA networks extend coverage into difficult radio environments. They also support very low power operation, thus enabling long battery life. Two of these emerging solutions are Licensed Spectrum LPWAs and Unlicensed Spectrum LPWAs.

## Licensed Spectrum LPWA Solutions

These mobile, operator-managed LPWA IoT networks are based on 3rd Generation Partnership Project (3GPP) standards. They leverage existing mobile networks, as well as their licensed spectrum. Utilizing existing networks helps to retain some of the key advantages of cellular systems including strong security, excellent coverage, and roaming capabilities, and assured quality of service (QoS) by operating in a licensed spectrum.

Recent changes in 3GPP standards are beneficial for IoT applications. Mass improvements have been made to increase power savings and extend battery life. Connectivity capabilities have also improved greatly. Connectivity is now capable of extending into subterranean locations and penetrating walls and floors.

The two most common licensed spectrum solutions are LTE-M (also referred to as LTE Cat-M1) and NB-IoT (Narrow-Band IoT). These networks efficiently connect devices to established mobile networks. They can handle small amounts of infrequent, 2-way data. They also consume minimal amounts of power and offer excellent radio coverage.

Like traditional cellular service, LTE-M and NB-IoT are Subscriber Identity Module (SIM)-based technologies. Thus, they deliver carrier-grade, best-in-class security measures. These measures cover user identity confidentiality, entity authentication, data integrity, and mobile equipment identification.

Similar to cellular, LTE-M and NB-IoT devices are both highly mobile. LTE-M and NB-IoT devices can move seamlessly throughout a wireless network without interruption. They also incur fewer signal disruptions from technologies using the same frequencies.

LTE-M and NB-IoT are similar evolutions of 3GPP, with very similar pros and cons. Given the similarity and that details for LTE-M are well defined and readily available, we will focus here on NB-IoT only.

NB-IoT is a 3GPP standards-based technology developed to enable a wide range of new IoT devices and services on existing mobile networks. The 3GPP changes for NB-IoT improve power consumption, increase system capacity and spectrum efficiency, and improve coverage. In many cases, devices can achieve battery life of more than 10 years.

New signals and channels added to the physical layer help to meet demanding coverage and device complexity needs. Initial cost of the NB-IoT modules is comparable to GSM/GPRS. However, the underlying technology is much simpler than today's GSM/GPRS devices. Because of this, we should see its cost decrease as demand increases.

All major mobile equipment, chip sets, and module manufacturers support NB-IoT. This allows the technology to co-exist with 2G, 3G, and 4G mobile networks. The first NB-IoT network trials are underway. We should see the first commercial launches take off early in 2017.

Advantages of NB-IoT:

  * _Leverage Existing Networks_

NB-IoT uses existing network infrastructure. This allows current systems to upgrade quickly, minimizing the need to deploy extra physical hardware. In addition, industries utilizing NB-IoT can rely on service providers to manage services so they do not have to do it themselves.

  * _Open Standards_

The open standard characteristic of NB-IoT reduces the risk of technology becoming redundant. It also helps to ensure that users of the technology are not "locked-in" to a specific vendor or operator.

  * _Industry Support_

NB-IoT is a product of existing 3GPP technologies. Thus, it will have long term support from a wide range of service providers, equipment providers, chipset and module makers.

Disadvantages of NB-IoT:

  * _Royalties_

One challenge with 3GPP standardization is the extra cost incurred by cellular solutions. This comes from royalties for intellectual property. At high volume, these royalties can add up.

  * _System Synchronization Effects on Battery Life_

Cellular networks operate synchronously. Therefore, individual devices must occasionally wake up, "check" for messages, and resynchronize. The synchronization process allows for low system latency. Unfortunately, this process also consumes a lot of energy, making it a major contributor to battery lifetime reduction.

## Unlicensed Spectrum LPWA Solutions

There are several LPWA solutions that are designed to operate on unlicensed frequency bands. Examples of unlicensed LPWA include LoRa, Sigfox, and Ingenu.

Some of these solutions are being standardized, whereas others are fully proprietary. Coverage in many cases is regional or limited.

### LoRa

LoRa (short for Long Range) continues to gain attention in the marketplace. It offers a compelling mix of long range, low power consumption, deep indoor coverage, and secure data transmission. LoRa operates in the unlicensed <1GHz frequency range. It uses spread spectrum technology so that adjacent transmitters are less likely to interfere with each other. This increases the capacity of each gateway. Spread spectrum communications also provide a "coding gain" over narrow band communications. This results in a stronger communications link, which can support longer range communications. LoRa data rates range from 0.3 kbps to 50 kbps and can support a range of up to 15km.

The LoRa Alliance has developed an open protocol based on LoRa technology called LoRaWAN. This protocol helps in the delivery of secure communications. It also ensures all devices, servers, and software components work efficiently with one another. The result is simple interoperability between IoT devices. The network architecture has a star-of-stars topology (shown below). The gateways (the outer star network connecting to IoT sensor nodes) act as a bridge, relaying messages between edge-devices and the central network server.

![AES Payload IoT system](https://bridgera.com/wp-content/uploads/2017/09/Capture.png)

Gateways connect to the network server via standard IP connections. End nodes/ devices use single-hop wireless communication to one or many gateways. End-point communication is generally bi-directional. It also supports multicast operation for software upgrades or for other mass distribution messaging.

The network server handles all the intelligence and complexity associated with managing the network. For example, the server filters redundant packets, performs security checks, and schedules acknowledgments. A limitation of the network server is the seamless handover for mobile nodes. The network server does, however, manage device transitions between gateways.

Communication between IoT end-devices and gateways uses different frequency channels and data rates. When choosing the data rate, you face a trade off between communication range and message duration. The LoRaWAN network server uses an adaptive data rate (ADR) approach. This allows the server to manage the data rate and RF output for each end-device, individually. In doing so, battery life is preserved for both the end-devices and the overall network.

To enable secure communication, LoRaWAN uses several layers of encryption at the device, network, and application levels. To address application-specific needs, LoRaWAN offers options for end-point devices, balancing power consumption with return (down-link) communications timing/synchronization. LoRaWAN is also an asynchronous protocol, which is beneficial for improved battery life.

Despite an emerging presence in Europe, LoRaWAN has not gained much traction in the United States. The slow progression can be attributed to competition from new cellular options and Sigfox.

LoRa operates in unlicensed frequency bands. This helps reduce the cost of transmitter nodes (devices) because royalties are not involved. Unlike transmitter nodes, gateway receivers are very expensive. They support the connections to many transmitters. Because of this cost, LoRa may not be ideal for applications where price is key, like home automation. However, it could be a good solution for applications that are not price sensitive, like rural meter reading. Efforts are underway to reduce the cost of gateway receivers. Unfortunately, efforts to reduce price would also reduce functionality (likely through reduced capacity).

While the range of the LoRa system is attractive, there are some trade offs. To achieve the longest range, you must use very low data rates. For example, a 15km range uses a data rate of around 100-300 bps and the range drops quickly as data rates increase. The lower the data rate, the longer it takes to transmit data which, in turn, drains battery power. A solid LoRa design balances data volume and transmission speed with power consumption and range requirements. This system is best for applications that send only a few bytes of data, a few times per day. It is not ideal for systems that send large amounts of data, require guaranteed quality of service (QoS), or require low latency or tight synchronization.

LoRa Key Features:

  * Operates in <1GHz band, with unique frequencies in different regions
  * Uses spread spectrum for increased range and noise immunity
  * Long range - up to 15 km
  * Supports data rates up to 50 kbps
  * High capacity of up to 1 million nodes
  * Long battery life - over 10 years
  * Reduced synchronization overhead and no hops in mesh network
  * Secured and efficient network

### Sigfox

Sigfox offers a proprietary, "complete LPWA solution" as a standalone operated telecommunication network. It uses a technology called Ultra Narrow Band (UNB) with binary phase-shift keying (BPSK) transmitted in the unlicensed bands below 1GHz.

Around since 2009, Sigfox is one of the older players in the IoT LPWA arena. Sigfox controls the back end, communications infrastructure and cloud management platform. Therefore, any customer who wants to use Sigfox must subscribe to both its communications infrastructure and its cloud platform. Radios and modules for endpoints are widely available from

![sigfox logo IoT systems](https://bridgera.com/wp-content/uploads/2017/09/kuqkV4fO_400x400.jpg)

manufacturers like Texas Instruments, Atmel, and Telit, and it is likely that hardware costs will be reduced as this solution scales.

Sigfox offers a robust, power-efficient, and scalable network able to communicate with millions of battery-operated devices that are several kilometers apart. It is well-suited for low-bandwidth (<100bps) and low-frequency (< 140 messages/day) applications.

Designed for low throughput transmission, the UNB, wireless technology benefits from a high level of sensitivity. This enables a communication range of up to 40km in open field and communication with buried, underground equipment becomes possible.

Sigfox uses low data rate transmission and sophisticated signal processing to effectively avoid network interference, and ensures the integrity of the transmitted data. The solution allows bidirectional communication, but always initiated by the device. As such, Sigfox is effective for communications from endpoints to base stations (uploads). However, it is not effective for communications from base stations to endpoints (downloads). Sigfox consumes a fraction (1%) of the power used through cellular communication. This network solution would be ideal for one-way systems including basic alarm systems, simple metering, and agricultural and environmental sensors.

In the Sigfox network, no negotiations take place between the device and a receiving station. Instead, the device emits in the available frequency band for the closest base station to detect. The base station will then decode the message and forward it to the control center. The network, itself, handles protocol operations and forwards messages to the customer application. A hash mechanism authenticates each message. The message then receives a private key, specific to the device, which is accessible using Sigfox's API.

An advantage of the sensitivity of UNB devices is network resource savings. By limiting the number of base stations, UNB allows Sigfox to deploy a low throughput communications network with approximately 1000 times fewer base stations when compared to the same level of coverage with a GSM cellular network. This reduces network deployment and operations cost. To further improve cost, Sigfox will setup base station antennas on existing cellular towers through partnerships with local mobile network operators.

Mobile operators have spent millions of dollars trying to develop a global network. To date, none have accomplished the feat. This is a reasonable concern for Sigfox. The inability to grow a global network would cause spotty regional coverage. This would present an issue for mobile or broadly deployed IoT devices. Another concern is relinquishing control. Some users may prefer more control over their data and do not want everything running through the Sigfox back end before making its way to them. Nevertheless, there are several undeniable benefits offered by Sigfox.

Sigfox Key Features:

  * Operates in <1GHz band with unique frequencies in different regions
  * Transmitters use Ultra Narrow Band (UNB) with binary phase-shift keying (BPSK)
  * Long range - up to 40 km
  * Very low data rates (on order of 100bps) and limited daily messages (max 140)
  * Long battery life - up to 20 years
  * Low cost network deployment
  * Sigfox defined application APIs

### Ingenu

Ingenu is another proprietary LPWA solution. It originally focused on smart meter and oil and gas applications. It has since expanded into other IoT applications including urban and agricultural environments.

The solution is proprietary in the sense that Ingenu is the sole developer and manufacturer of the hardware. In the past, Ingenu mainly sold hardware components to enterprises that built and controlled their own networks. However, the firm recently tweaked this business model and developed several public networks. It now also sells radio modules and recurring data subscriptions for these networks.

![Ingenu logo IoT systems](https://bridgera.com/wp-content/uploads/2017/09/ingenu-600px.png)

The Ingenu solution uses Random Phase Multiple Access (RPMA) technology. RPMA enables data rates in the hundreds of thousands of bits per second (50x other LPWA solutions). The system utilizes the 2.4 GHz unlicensed and universal frequency band. This offers larger bandwidth, greater flexibility, and reduces the chance of interference. Ingenu also uses channel coding (Viterbi algorithm) to guarantee data delivery and provide high quality of service (QoS). It is tightly synchronized to support low latency applications and uses 256-bit encryption and two-way authentication to provide enterprise level security.

These great features offered by Ingenu enable higher data throughput rates than Sigfox and LoRa. However, when combined, these benefits consume a significant amount of power. Operating in the 2.4 GHz band, Ingenu encounters more propagation loss from obstructions, like water or packed earth. Fortunately, the RPMA technology can counter this issue, providing excellent link margin. RPMA is one of the more complex radio technologies. It utilizes antenna diversity and requires much more processing power than other solutions. While this does enable applications not possible with LoRa or Sigfox, it also increases system complexity, power consumption, and hardware expenses.

Using RPMA, Ingenu claims to require fewer access points than cellular, LoRa, and Sigfox, while providing the same coverage area. The protocol also enables precise location tracking, which Sigfox and LoRa do not. Like LoRa, Ingenu is capable of effective bidirectional transmission. Overall, in weighing the pros and cons, Ingenu may be one of the best radio solution options.

Ingenu Key Features:

  * Operates in 2.4 GHz band with global coverage
  * Uses RPMA technology, requiring fewer access points than NB-IoT, LoRa, or Sigfox
  * Long range with excellent coverage (one application covers 2,000 square miles with 17 towers)
  * High data rates (>100k bps)
  * Provide precise location tracking
  * Highly scalable with support for up to 500k devices per tower
  * Enterprise level security through 256-bit data encryption and two-way authentication
  * Provides high QoS through channel coding
  * Synchronized system provides support for low latency applications

### Satellite

All LPWA networks require some terrestrial infrastructure for IoT device communication. In some cases, such as maritime applications or extremely remote areas, there may be no available gateways. Under these circumstances, satellite communications is an ideal alternative. Unlike the communication solutions we have discussed up to this point, satellite solutions can be very expensive. The higher cost is due to a low volume market and the expenses involved in satellite deployment. Satellite enabled devices require higher power and may also require a sizeable antenna.

Satellite communication technology has been added for completeness purposes. It may be one of the few viable options for some applications due to geography. Although it is an expensive solution, the cost may not be an issue for applications with infrequent data communication. Long-term, environmental monitoring studies is an application that may leverage satellite communications.

Read more about the IoT Technical Stack in "[A Reference Guide to IoT](https://bridgera.com/ebook/)" eBook.

Fill out our [contact form](https://bridgera.com/contact-form/) if you have questions about IoT. We may not have all the answers but with our cross-disciplined IoT network, we certainly can get you the help you need.

Take a deep dive into [Bluetooth mesh](https://dzone.com/go?i=250337&u=https%3A%2F%2Fwww.bluetooth.com%2Fwhat-is-bluetooth-technology%2Fhow-it-works%2Fle-mesh%3Futm_campaign%3Dmesh%26utm_source%3Ddzone%26utm_medium%3Dpre-post-article-text%26utm_term%3Dbluetooth-mesh%26utm_content%3Doct-pre-post-mesh-section). Read the [tech overview](https://dzone.com/go?i=250337&u=https%3A%2F%2Fwww.bluetooth.com%2Fwhat-is-bluetooth-technology%2Fhow-it-works%2Fle-mesh%2Fmesh-tech%3Futm_campaign%3Dmesh%26utm_source%3Ddzone%26utm_medium%3Dpre-post-article-text%26utm_term%3Dtech-overview%26utm_content%3Doct-pre-post-mesh-tech) and discover new IoT innovations.
