# Radio Solutions of IoT

_Captured: 2018-05-08 at 19:39 from [dzone.com](https://dzone.com/articles/radio-solutions-of-iot?edition=376254&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-05-08)_

![](https://image.slidesharecdn.com/powerpointupdate002-180424160304/95/radio-frequencies-for-iot-1-638.jpg?cb=1524585887)

The [Internet of Things](https://bridgera.com/internet-of-things/) is a collection (or "stack") of different components that connect software, systems, and people via internet technology. One of these crucial components is the communication network, enabled by IoT wireless technology, the communication network is the gateway between an IoT device (a "thing") and a software platform ([Bridgera IoT for example](https://bridgera.com/internet-of-things)).

![](https://bridgera.com/wp-content/uploads/2018/04/IoTStackArrow-1024x576.png)

IoT Wireless Technology in its simplest form requires a radio capability that can receive and broadcast radio waves as a means for transmitting signals or data. Below and in the above Slide Share is an overview on radio frequencies and how they support IoT wireless technology solutions.

## **What Is a Radio Wave?**

A radio wave is an electromagnetic frequency used for long distance communication. IoT solutions rely on IoT wireless technology, leveraging radio waves that follow a specific protocol based on the design intent of the IoT system. Radio protocols are used by IoT devices to transport data to cloud platforms where a physical or wired connection does not exist. There are many different protocols to choose with characteristics varying in areas of power consumption, physical size, travel distance, data size, and transport technology availability.

### **Basics of Radio Waves**

There's a good chance that you haven't thought about radio waves since your last science fair project, so let's go over the basics before we dive further.

![radiowave graphic](https://bridgera.com/wp-content/uploads/2018/04/graphics2-1024x576.png)

A radio wave is an electromagnetic wave that travels at the speed of light. The wavelength of an electromagnetic signal is inversely proportional to the frequency.

Amplitude indicates the strength of the RF signal. This varies depending on whether a 1 or 0 is present in the digital signal. This modulation is not ideal due to the amount of noise in the transmission medium. Frequency-Shift Keying ("FSK") makes slight changes to the frequency of the carrier signal to represent data in a manner that's suitable for propagation through the air at low-to-moderate data rates. FSK also avoids the impacts of common noise.

Another type of modulation is Phase-Shift Keying ("PSK"). PSK causes changes in the signal's phase, while the frequency remains constant. Like FSK, PSK is mostly immune to common noise that is based in shifts in amplitude.

Frequency is the number of times per second the signal repeats itself, and is measured in hertz ("Hz"). Phase represents how far the signal is offset from the reference point.

### **Wireless Radio Technologies**

![radio frequency chart](https://bridgera.com/wp-content/uploads/2018/04/graphics7-1024x614.png)

Radio frequency bands are, quite simply, any of the electromagnetic wave frequencies that are used in radio communication. They range from 3khz to 300Ghz and encompass everything from amateur radio bands to mobile phones and beyond. There are multiple types of bands as well:

  * Unlicensed Bands have become popular for many commercial solutions (Bluetooth, WiFi, etc)
  * Licensed bands require a license from a local regulatory authority, and are used primarily by TV and cellular networks
  * Forbidden Bands are used by government agencies and public service organizations

Radio frequencies are versatile, but like any job, it's up to you to choose the right tool that suits your IoT wireless technology needs. Does your device frequently transfer massive amounts of data? You'll want a high-bandwidth solution. Does your device need to transmit data over a long distance? A lower frequency will do the job. There are many factors to consider when choosing a radio solution, but there are also many choices available for whatever your needs may be.

## **Long Range IoT Radio Solutions**

### **Cellular Networks**

For [long range connectivity](https://bridgera.com/long-range-iot-radio-solutions/), many IoT wireless technology solutions will leverage cellular networks, since they typically have readily-available development hardware and well-defined protocols. Cellular technologies like 3G and 4G (and soon, 5G) are widely used in IoT systems. 2G was also used, but has largely been retired since AT&T shut down the 2G service in 2016.

However, cellular networks are not without disadvantages. They are expensive, first and foremost. They're also designed for voice and low-latency communications, which are not typical requirements of most IoT wireless technology solutions. Finally, the cellular device certification processes are time-consuming and expensive, which can be prohibitive for some smaller IoT solutions.

### **Low-Power Wide-Area (LPWA) Networks**

New LPWA networks are entering the IoT space to address some of the unique needs of IoT devices. For example, LPWA networks extend coverage into difficult radio environments. They also support very low power operation, thus enabling long battery life. Two of these emerging solutions are Licensed Spectrum LPWAs and Unlicensed Spectrum LPWAs.

### **Long-Range (LoRa)**

LoRa (short for Long Range) continues to gain attention in the marketplace. It offers a compelling mix of long range, low power consumption, deep indoor coverage, and secure data transmission. LoRa operates in the unlicensed <1GHz frequency range. It uses spread spectrum technology so that adjacent transmitters are less likely to interfere with each other. This increases the capacity of each gateway. Spread spectrum communications also provide a "coding gain" over narrow band communications. This results in a stronger communications link, which can support longer range communications. LoRa data rates range from 0.3 kbps to 50 kbps and can support a range of up to 15km.

![LoRaWAN network architecture](https://bridgera.com/wp-content/uploads/2018/04/graphics11-1024x391.png)

While the range of the LoRa system is attractive, there are trade offs. To achieve the longest range, you must use very low data rates. For example, a 15km range uses a data rate of around 100-300 bps and the range drops quickly as data rates increase. The lower the data rate, the longer it takes to transmit data which, in turn, drains battery power. A solid LoRa design balances data volume and transmission speed with power consumption and range requirements. This IoT wireless technology system is best for applications that send only a few bytes of data, a few times per day. It is not ideal for wireless systems that send large amounts of data, require guaranteed quality of service (QoS), or require low latency or tight synchronization.

### **SigFox**

Sigfox uses low data rate transmission and sophisticated signal processing to effectively avoid network interference, and ensures the integrity of the

![sigfox logo IoT systems](https://bridgera.com/wp-content/uploads/2017/09/kuqkV4fO_400x400.jpg)

transmitted data. This IoT wireless technology solution allows bidirectional communication, but always initiated by the device. As such, Sigfox is effective for communications from endpoints to base stations (uploads). However, it is not effective for communications from base stations to endpoints (downloads). Sigfox consumes a fraction (1%) of the power used through cellular communication. This network solution would be ideal for one-way systems including basic alarm systems, simple metering, and agricultural and environmental sensors.

### **Ingenu**

Ingenu is another proprietary LPWA solution. This IoT wireless technology originally focused on smart meter and oil and gas applications. It has since expanded into other IoT wireless applications including urban and agricultural environments.

![Ingenu logo IoT systems](https://bridgera.com/wp-content/uploads/2017/09/ingenu-600px.png)

The Ingenu solution uses Random Phase Multiple Access (RPMA) technology. RPMA enables data rates in the hundreds of thousands of bits per second (50x other LPWA solutions). The system utilizes the 2.4 GHz unlicensed and universal frequency band. This offers larger bandwidth, greater flexibility, and reduces the chance of interference. Ingenu also uses channel coding (Viterbi algorithm) to guarantee data delivery and provide high quality of service (QoS). It is tightly synchronized to support low latency applications and uses 256-bit encryption and two-way authentication to provide enterprise level security.

These great features offered by Ingenu enable higher data throughput rates than Sigfox and LoRa. However, when combined, these benefits consume significantly more power than their IoT wireless technology counterparts. Operating in the 2.4 GHz band, Ingenu encounters more data loss from obstructions, like water or packed earth. Fortunately, RPMA technology exists to counter this issue. RPMA, or Random Phase Multiple Access, is one of the more complex IoT wireless technologies. It utilizes antenna diversity and requires much more processing power than other solutions. While this does enable applications not possible with LoRa or Sigfox, it also increases system complexity, power consumption, and hardware expenses.

Using RPMA, Ingenu claims to require fewer access points than cellular, LoRa, and Sigfox, while providing the same coverage area. The protocol also enables precise location tracking, which Sigfox and LoRa do not. Like LoRa, Ingenu is capable of effective bidirectional transmission. Overall, in weighing the pros and cons, Ingenu may be one of the best IoT wireless technology solution options.

### **Satellite**

All LPWA networks require some terrestrial infrastructure for IoT device communication. In some cases, such as maritime applications or extremely remote areas, there may be no available gateways (cell towers for example) and therefore satellite is one of the few viable IoT wireless technology options available. Unlike the IoT wireless technology solutions we have discussed up to this point, satellite solutions can be very expensive. The higher cost is due to a low volume market and the expense involved in satellite deployment. Satellite enabled devices require higher power and may also require a sizable antenna.

## **Medium Range IoT Radio Solutions**

We define [medium range](https://bridgera.com/iot-systems-medium-range-radio-signals/) as a radio solution with signal range no greater than 100 meters. Some of these technologies may use a star or mesh node architecture to acquire greater range. Nevertheless, no single link will span more than 100 meters. These technologies are sometimes referred to as "Local RF." The most common medium range IoT wireless technologies include ZigBee, Wi-Fi, z-Wave, and Thread.

### **ZigBee**

Designed on top of the IEEE 802.15.4 standard, ZigBee is a self-healing, secure, robust, and mesh-capable protocol. It can scale to thousands of nodes across large areas. ZigBee has been around for ~10 years and has ~1 billion devices deployed globally. The specification continues to evolve.

![zigbee architecture](https://bridgera.com/wp-content/uploads/2018/04/graphics13-1024x906.png)

Within a ZigBee system architecture, there are 3 device types. The ZigBee Coordinator (ZC), ZigBee Router (ZR), and ZigBee End Device (ZED). There is only one Coordinator in the network. The Coordinator selects the network topology, establishes the network, and administers configuration information. It acts as the gateway in and out of the network, so it must have the power to be on and running at all times. ZigBee routers relay information and move data through the network. They may also function as a sensor node. Since the routers represent the backbone of the network, they must always be on. The End Device is at the edge of the network and is the source or user of the network data. It is usually battery powered and can be placed in low power, sleep mode for long periods of time. The End Device is normally the least expensive device in the network.

### **Thread**

Thread is an IoT wireless technology that is primarily used to connect and control products in the home. For ease of integration with an IoT system, it provides a simplified bridge between a Thread mesh network and the Internet. It is an open, IPv6 based protocol built on the IEEE802.15.4 link layer and other standards (like 6LoWPAN).

Thread uses 6LoWPAN to add large IP packets to smaller 802.15.4 packets using segmentation and compression. This approach allows IP packets to pass directly between the Internet and the local network without the need for custom

![thread architecture iot network](https://bridgera.com/wp-content/uploads/2018/04/graphics15-1024x838.png)

software. Unlike ZigBee, Thread is not an application protocol. It defines how to send data within the network but not how to interpret it. Thread can support IP-based application layers, but it does not define one specifically. This allows customers with different application needs to customize their application layers. In this sense, Thread can be thought of as a low-power, mesh networking equivalent to Wi-Fi that improves upon some of the inherent limitations of Wi-Fi for home automation applications.

Thread is driven by Google and Nest and is gaining traction in home automation. It will likely be the first 6LoWPAN protocol standard to hit the market and see wide adoption, realizing much of the potential of the smart home. Because it uses the same link layer solution as ZigBee and because hardware suppliers are choosing sides, Thread could be a ZigBee-killer.

### **Z-Wave**

Z-Wave is a low-power, IoT wireless technology, primarily designed for home automation. It is a proprietary solution, originally developed by Zen-Sys and later acquired by Sigma Designs. As of 2017, there were around 375 companies in the Z-Wave Alliance with over 35 million enabled products deployed. This has made it one of the more successful home automation protocols out there.

Z-Wave offers reliable and low-latency communication with data rates up to 100kbit/s. It is based on the ITU-T G.9959 standard and operates on a single channel in the <1GHz band (868MHz band for Europe and 915MHz band for North America and Australia).

Z-Wave has a large market presence, but suffers from a couple of technical issues. First, all chips are sole-source meaning there is no competition to drive costs down. Second, the use of a single frequency makes the entire network susceptible to interference from other radios.

### **Wi-Fi**

Wireless Fidelity or Wi-Fi is the go-to standard for moving large amounts of data across a wireless network. It is based on the IEEE 802.11 family of standards. Wi-Fi is primarily a local area networking (LAN) technology designed to serve as a wired Ethernet replacement for computer-to-computer communications. Given its popularity within the home and other environments, Wi-Fi is a convenient choice as an IoT wireless technology for developers.

All Wi-Fi networks are contention-based TDD systems, where the access point and the mobile stations compete to use the same channel. Because of the shared media operation, all Wi-Fi networks are half duplex. A Wi-Fi station will transmit only when it detects that the channel is clear. While transmitting, the Wi-Fi station cannot hear making it impossible to detect a collision. All Wi-Fi transmissions are acknowledged. If a station does not receive an acknowledgment, it assumes a collision occurred and retries after a random waiting interval.

Wi-Fi operates as a star network where there is one central hub to which all nodes/ devices connect. There is a lot of bandwidth, but you may experience a poor signal if you are not close to the access point or if there are a lot of connected devices.

## **Short Range IoT Radio Solutions**

[Short range IoT wireless technology solutions](https://bridgera.com/iot-solutions-and-short-range-radio-signals/) have a signal range that does not exceed 30 meters. The most common technologies in use include Bluetooth (or its evolution Bluetooth LE) and RFID.

### **Bluetooth**

Bluetooth has become common in computing and consumer product markets. The Bluetooth standard is generally intended as a "cable replacement" technology. It is used for transferring medium amounts of data over a relatively short distance (30m). Bluetooth is widely accepted in audio applications, such as cell phone headsets and wireless speakers.

Adapted from the Bluetooth standard, Bluetooth Low-Energy (BLE) (marketed as Bluetooth Smart) has become common for wearable products through smartphone connections. Different from the original Bluetooth, BLE sends small amounts of data, requiring very little energy.

![bluetooth network architecture](https://bridgera.com/wp-content/uploads/2018/04/graphics-1-1024x491.png)

> _Bluetooth Network Architecture_

BLE's range is similar to the traditional Bluetooth's range. However, it offers improvements in latency, power consumption, and data robustness. These improvements come at the cost of reduced effective data rates, maxing out at several hundred kbps. Despite this, BLE has the potential to support many IoT wireless technology applications.

Bluetooth is already integrated into smartphones and many other personal, mobile devices. This is a major advantage Bluetooth has over many competing IoT wireless technologies. Today, most Bluetooth-enabled smartphones (iOS, Android, and Windows-based models), are 'Smart Ready.'

Devices that employ Bluetooth Smart features incorporate the Bluetooth Core Specification Version 4.0 (or higher) with a combined low-data-rate and low-energy core configuration. Version 4.2's Internet Protocol Support Profile allows Bluetooth Smart sensors to access the Internet directly via 6LoWPAN connectivity. This IP connectivity makes it possible to use existing IP infrastructure to manage Bluetooth Smart 'edge' devices.

Other enhancements will also enable enterprises to use Bluetooth beacons for indoor location applications. BLE has a mechanism allowing devices to broadcast information about identity and capability. This enables coordination between devices. Google's Physical Web concept uses BLE beacons. BLE allows the broadcasting of rich data, like location information, URLs, and multimedia files.

Lacking a mesh network protocol and having a short range are two limitations for Bluetooth. In fact, not having a mesh network is one factor keeping Bluetooth out of larger distributed sensor networks. Although a mesh solution is in development, it is significantly behind others.

### **RFID**

Radio-frequency identification (RFID) uses electromagnetic fields to automatically identify and track tags attached to objects. The tags contain electronically stored information. Passive tags collect energy from a nearby RFID reader's interrogating radio waves. Active tags have a local power source (such as a battery) and may operate hundreds of meters from the RFID reader. Unlike a barcode, the tag need not be within the line of sight of the reader, so it may be embedded in the tracked object.

RFID tags are used in many industries, for example, an RFID tag attached to an automobile during production can be used to track its progress through the assembly line; RFID-tagged pharmaceuticals can be tracked through warehouses; and implanting RFID microchips in livestock and pets allows for positive identification of animals.

## **What's Next?**

The goal of this post is to illustrate the versatility and utility of the IoT wireless technology and radio solutions available to enable a communication network in the IoT stack. Once you've chosen the best radio protocol for your device, the software platform comes next.
