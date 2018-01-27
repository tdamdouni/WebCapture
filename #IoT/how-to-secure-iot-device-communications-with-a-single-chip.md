# How to Secure IoT Device Communications with a Single Chip

_Captured: 2017-11-21 at 10:07 from [www.digikey.com](https://www.digikey.com/en/articles/techzone/2017/oct/how-to-secure-iot-device-communications-with-a-single-chip?WT.z_sm_link=TZIoT)_

Contributed By Digi-Key's North American Editors

Locking down an IoT design requires more than encrypted messaging. Developers need to extend security from the underlying secret keys through authentication, secure sessions and secure messaging. Yet, the complexity of the design, implementation, and functional aspects of an intact security chain leads many projects to compromise security for the sake of cost and schedules.

This need to compromise is diminishing, however, in large part due to devices that developers can use to easily implement comprehensive security features in IoT devices and other deeply embedded systems. One such device is the [MAXQ1061](https://www.digikey.com/product-detail/en/maxim-integrated/MAXQ1061EUD-/MAXQ1061EUD--ND/7100952) from [Maxim Integrated](https://www.digikey.com/en/supplier-centers/m/maxim-integrated).

This feature will describe how IoT security systems work before introducing the MAXQ1061 and showing how it can be used to quickly solve for security at the transport layer.

## Security is fundamental to the IoT

Underlying the vision of the IoT, users expect applications to process data streams to provide detailed information about the user, their environment, and their equipment. The ability to protect these applications and ensure the integrity and authenticity of data is inherent in this vision. Yet, well-publicized attacks on systems and data continue to call into question that ability. Accordingly, interest has grown rapidly for more effective solutions for securing data and systems.

At the device level, designers can already find MCUs that integrate hardware accelerators for encrypting and decrypting data using a wide variety of ciphers including AES, SHA, and 3DES, among others. Yet, data encryption/decryption is only one piece of a larger set of capabilities required to secure IoT applications using standard security protocols such as TLS (Transport Layer Security).

TLS provides a standard protocol for secure communications across networks between servers and clients such as Web browsers and IoT devices. In this protocol, communications occur as a series of individual secure sessions that include security parameters that are typically established uniquely for each individual session. It's noteworthy that TLS also includes methods of reusing session security parameters from one session to the next, but those methods can expose IoT applications to additional security threats and are not included in this discussion.

In using TLS, clients and servers begin a TLS session by using the TLS handshake protocol (Figure 1). This authenticates each device-to-server connection and creates a "master secret" - a private cryptography key used in common during the TLS record protocol for encrypting and decrypting data exchanged during that session. At each step within this handshake protocol, clients and servers ensure the security of the process by using several fundamental security mechanisms including private key storage, true random number generation, and standard encryption/decryption algorithms.

![Image of TLS handshake protocol](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/October/How%20to%20Secure%20IoT%20Device%20Communications%20with%20a%20Single%20Chip/article-2017october-how-to-secure-iot-fig1.jpg?ts=9dc188cc-9202-49fd-b3de-d30510a11806&la=en-US)

> _TLS handshake protocol_

_Figure 1: The TLS handshake protocol relies on security mechanisms including secure storage, true random number generation, and cryptography to perform the series of steps required for mutual authentication and creation of a shared master secret key for subsequent data exchange using the TLS record protocol. (Image source: Wikimedia)_

When a client such as an IoT device needs to connect to a server, it begins the TLS handshake by sending a _client_hello_ message, which includes information about the client's ability to support specific TLS methods as well as a random number. The server responds with the selection of TLS methods to be used, its certificate (server public key), and other details that depend on the nature of the cipher suite and security policy being used.

For example, although Web applications typically authenticate the server alone, secure IoT applications demand that both client devices and servers authenticate each other to mitigate threats such as man-in-the-middle attacks. Without client authentication, unauthorized devices could pretend to be legitimate devices and connect to the IoT network to provide an entry point for bad actors. To implement mutual authentication, the server adds a request for the client certificate to this particular phase.

In the next phase of the handshake negotiation, the client sends its certificate as well as a signature hash of the previous set of messages created using its private key. The server uses the client certificate (device public key) and signature hash to verify that the requesting client device actually possesses its private key. In doing so, it also verifies the device's ownership of the client certificate. In some cases, the client might also send a pre-master secret created using the server's certificate (server public key).

Finally, the client and the server each use the random number (and pre-master secret if included) to calculate a "master secret," which serves as the private key for data exchange using the TLS record protocol. With this procedure, the TLS handshake protocol provides a secure key for use by both client and server during data exchange without ever passing private keys across the network. With the master secret in hand, client and server each signal the end of the handshake phase and begin exchanging messages, using the master secret as the key to encrypt and decrypt those messages for the duration of that particular connection session.

To maintain security throughout the process, the client device and server each face fundamental requirements for secure storage of secrets including their individual private keys and the session's master secret. In addition, both require the ability to generate true random numbers needed to prevent attacks based on predictable generation of random number sequences.

To maintain performance, the client and server need the ability to perform encryption and decryption rapidly. Although the handshake process itself is largely limited by network performance, subsequent data exchange can be limited by the speed of the underlying cryptography.

Although server systems commonly provide the required combination of computational horsepower and protection, IoT device developers have struggled to meet these requirements with designs able to provide these capabilities without adding significant cost and complexity to the final IoT design.

Dedicated cryptography devices such as the Maxim Integrated MAXQ1061, integrate the full set of features and capabilities required to implement TLS communications in IoT designs.

## Integrated security

The Maxim Integrated MAXQ1061 is a crypto controller that meets general requirements for IoT device security. Along with secure storage and crypto engines, the device includes firmware that builds on hardware security mechanisms to implement high-level security measures for TLS and other algorithms as well as security methods such as secure boot.

The MAXQ1061 builds in security starting at the most fundamental level with provisions built into the die and circuit to protect against side-channel attacks. Side-channel attacks draw on deep analysis of the details of a design and its performance characteristics. At the system level, one of the earliest examples of side-channel attacks against data centers was the use of variations in electromagnetic radiation emanating from terminals and other devices to penetrate security. TEMPEST-secure facilities use physical protection and EM shielding to defeat these threats. Unlike data centers, however, IoT devices rarely enjoy physical protection from all possible threats. In fact, given easy access to these devices, bad actors can at their leisure employ a wide variety of side-channel attacks using power monitoring, timing, acoustics, and other methods. As with many security devices, the MAXQ1061 employs a series of countermeasures built into the die and incorporated into the circuit design to mitigate these various threats.

Side-channel attacks often require sophisticated lab setups and analysis equipment typically available only to large enterprises and national organizations. In contrast, one of the simplest methods of breaking security in designs built around crypto devices occurs through the interception of secret data. This can occur at one of many stages of its use within and between the host MCU, memory, and its crypto device companions.

Hackers seek to access data at one or more of its three usual states: at rest, in transit, or in use. The MAXQ1061 removes these attack surfaces by providing secure storage to protect data at rest and by ensuring that any use of secret data remains within the device itself, eliminating intercepts of data in transit or in use. With its 32 Kbytes of integrated secure EEPROM, the device provides storage for all keys, certificates, and critical data through a flexible filesystem designed to support custom security policies. At the same time, the device provides the flexibility needed to support custom security implementations, allowing developers to export the master secret, for example, for use during message processing.

Although other crypto devices offer secure storage, the MAXQ1061 differentiates itself by integrating hardware engines and firmware needed to execute cryptography algorithms and perform higher-level protocols such as TLS (Figure 2). Secure data never need leave the chip, effectively removing the associated attack surfaces.

![Diagram of Maxim Integrated MAXQ1061 cryptographic controller](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/October/How%20to%20Secure%20IoT%20Device%20Communications%20with%20a%20Single%20Chip/article-2017october-how-to-secure-iot-fig2.jpg?ts=9fa09687-2cc3-411b-85ea-60a92ce47739&la=en-US)

> _Maxim Integrated MAXQ1061 cryptographic controller_

_Figure 2: The Maxim Integrated MAXQ1061 cryptographic controller integrates fundamental security mechanisms required for secure TLS communications, providing developers with a simple solution to complex challenges of secure communications. (Image source: Maxim Integrated)_

The integrated crypto accelerators address another practical concern in TLS implementation. TLS performance depends on the speed of the underlying cryptography. The nature of the TLS protocol deployment often itself reflects this issue through the use of highly secure (but slower) asymmetric crypto such as Elliptic Curve Digital Signature Algorithm (ECDSA) with the TLS handshake protocol, and use of less secure (but faster) symmetric crypto such as Advanced Encryption Standard (AES) with the TLS record protocol. The MAXQ1061 supports this approach, not only speeding TLS execution but also dramatically simplifying its implementation in IoT designs.

Built into the MAXQ1061, the crypto toolbox combines hardware-accelerated cryptography with protected firmware that implements critical layers of TLS as well as SSL (Secure Sockets Layer) and DTLS (Datagram Transport Layer Security). In performing TLS handshake and TLS record protocols, the MAXQ1061 offloads the host MCU by performing the detailed transactions associated with each series of operations (Figure 3). For TLS, the device provides the client certificate and handles the authentication sequence with the remote server. For general crypto requirements including TLS record exchange, the device uses its integrated hardware AES engine to speed encryption and decryption.

![Image of MAXQ1061 offloads the host MCU](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/October/How%20to%20Secure%20IoT%20Device%20Communications%20with%20a%20Single%20Chip/article-2017october-how-to-secure-iot-fig3.jpg?ts=e73ced5d-4b72-4b30-9b79-646def8e259e&la=en-US)

> _Figure 3: The MAXQ1061 offloads the host MCU, performing critical sequences in the TLS handshake and record protocols required for mutual authentication and subsequent secure data exchange. (Image source: Maxim Integrated)_

Designed to work directly through the device's SPI channel, an integrated 128-bit AES engine offloads a host processor by performing fast stream encryption and decryption. In this mode, a dedicated DMA controller streams data to and from the AES engine directly through the SPI interface, allowing on-the-fly crypto.

The device provides a simple hardware and software interface for integrating the device with a host MCU in an IoT design. Maxim Integrated demonstrates the basic hardware interface with its [MAXQ1061-KIT](https://www.digikey.com/product-detail/en/maxim-integrated/MAXQ1061-KIT-/MAXQ1061-KIT---ND/7100953) evaluation kit (Figure 4). As documented in the provided schematic, the kit supports both SPI and I2C interfaces and shows the simple circuits used to support the device's wakeup and tamper detection mechanisms. The kit also provides circuits that let developers toggle different operating modes and connect the board to an external host processor.

![Diagram of Maxim Integrated MAXQ1061-KIT eval kit \(click to enlarge\)](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/October/How%20to%20Secure%20IoT%20Device%20Communications%20with%20a%20Single%20Chip/article-2017october-how-to-secure-iot-fig4.jpg?ts=088a6160-f69c-4a08-a796-b336153b1222&la=en-US)

> _Figure 4: The Maxim Integrated MAXQ1061-KIT eval kit provides a basic reference design for integrating the MAXQ1061, combining SPI and I2C interface connections with basic circuits for other device capabilities including wakeup and tamper detection. (Image source: Maxim Integrated)_

## Software interface

As with the hardware interface, the device employs a simple approach on the software side. At the lowest level of the software interface, the device uses a straightforward communication protocol to communicate with the host MCU through the SPI or I2C hardware interfaces. To communicate with the device, a host processor sends a byte string formatted as follows:

AA CMD LENGTH DATA CRC

So to ping the device, for example, the host MCU would send the following byte string:

AA 00 F7 00 04 00 01 02 03 E1 09

In response, the device returns a similar byte sequence with the following fields:

55 ERR_CODE LENGTH DATA CRC

So in response to the ping request, the MAXQ1061 would send the following byte string:

55 00 00 00 04 00 01 02 03 22 32

Of course, the Maxim Integrated software package abstracts these low-level operations into a series of functionally intuitive calls to the provided library and underlying application programming interface (API). Additionally, the Maxim Integrated software further simplifies the software architecture by building its API on existing SPI and I2C drivers within a target platform (Figure 5).

![Diagram of Maxim MAXQ1061 software package](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/October/How%20to%20Secure%20IoT%20Device%20Communications%20with%20a%20Single%20Chip/article-2017october-how-to-secure-iot-fig5.jpg?ts=309d9b46-77bb-4805-8c85-d8fa3650ebe1&la=en-US)

> _Figure 5: The MAXQ1061 software package includes a full TLS stack built to take advantage of the device's hardware-based TLS mechanisms and uses an API built on each target host platform's standard device driver set. (Image source: Maxim Integrated)_

For TLS operations, the MAXQ1061 software environment uses a version of mbed TLS modified to take advantage of the device's specialized security features. For software developers, mbed TLS provides an abstraction layer on top of the target platform's TCP/IP network stack.

For experienced software developers, use of mbed TLS is simply a matter of changing familiar calls to the network layer to mbed TLS function calls - for example, changing _read_ calls to the network layer to _mbedtls_ssl_read_ and _write_ calls to _mbedtls_ssl_write_. To take advantage of the MAXQ1061 features, experienced mbed TLS developers need only use the Maxim Integrated version of the mbed TLS stack.

## Conclusion

For IoT devices and any connected system, the ability to perform authentication and to communicate securely emerge as increasingly important requirements in the face of more sophisticated security threats. For developers, the MAXQ1061 and supporting software provide a simple way to implement fundamental security measures in their applications. Although key security, high-speed crypto, TLS communications are only part of a comprehensive security policy, the MAXQ1061 provides the kind of solid foundation of security required to implement higher level policies needed to counter emerging threats.

Disclaimer: The opinions, beliefs, and viewpoints expressed by the various authors and/or forum participants on this website do not necessarily reflect the opinions, beliefs, and viewpoints of Digi-Key Electronics or official policies of Digi-Key Electronics.
