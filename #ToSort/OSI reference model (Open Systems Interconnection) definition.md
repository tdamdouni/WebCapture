# OSI reference model (Open Systems Interconnection) definition

![](http://cdn.ttgtmedia.com/rms/onlineImages/rouse_margaret.jpg)

Posted by: [Margaret Rouse](http://www.techtarget.com/contributor/Margaret-Rouse)

[WhatIs.com](http://whatis.techtarget.com)

[ __ ](https://twitter.com/whatisdotcom) [ __ ](https://plus.google.com/115059452925708684879#115059452925708684879/posts) [ __ ](https://www.linkedin.com/in/margaretrouse) [ __ ](mailto:mrouse@techtarget.com)

Contributor(s): Daniel Kroon

  * Share this item with your network:
  * __
  * __
  * __
  * __
  * __
  * __

__Sponsored News

  * [The Cloud’s Dirty Little Secret: Lack of Data Portability](http://searchstorage.techtarget.com/NetAppSponsoredNews/The-Clouds-Dirty-Little-Secret-Lack-of-Data-Portability?asrc=SS_snet_SN-212725) -NetApp
  * [Buckle Up! The Top Storage Technology Trends for 2015](http://searchstorage.techtarget.com/NetAppSponsoredNews/Buckle-Up-The-Top-Storage-Technology-Trends-for-2015?asrc=SS_snet_SN-212725) -NetApp
  * [See More](http://searchnetworking.techtarget.com/sponsored_communities)

__Vendor Resources

  * [2015 Global DDoS Threat Landscape Report](http://searchnetworking.bitpipe.com/detail/RES/1443546872_863.html) -Imperva __
  * [Security through Maturity: A Brief on Securing iSCSI Networks](http://searchnetworking.bitpipe.com/detail/RES/1242230181_697.html) -Dell, Inc. __

Product ReviewsPowered by IT Central Station

  * ![](http://cdn1.itcentralstation.com/vendors/logos/x50/SolarWinds.PNG?1420105242) [SolarWinds NPM](http://www.itcentralstation.com/products/comparisons/ca-unified-infrastructure-management_vs_solarwinds-npm?aid=TechTargetRef&lp=comparison1&tid=category1771_topic1175266_sitesearchNetworking_contentDefinition-definition_widget2)

vs.

![](http://cdn1.itcentralstation.com/vendors/logos/x50/CA2.jpg?1421828364) [CA Unified Infrastructure Management](http://www.itcentralstation.com/products/comparisons/ca-unified-infrastructure-management_vs_solarwinds-npm?aid=TechTargetRef&lp=comparison1&tid=category1771_topic1175266_sitesearchNetworking_contentDefinition-definition_widget2)

  * ![](http://cdn1.itcentralstation.com/vendors/logos/x50/3gaoi2h254k0canb4hxj_400x400.jpeg?1420721953) [Nagios](http://www.itcentralstation.com/products/comparisons/nagios_vs_optiview-xg?aid=TechTargetRef&lp=comparison1&tid=category1771_topic1175266_sitesearchNetworking_contentDefinition-definition_widget2)

vs.

![](http://cdn1.itcentralstation.com/vendors/logos/x50/FlukeNetworks.jpg?1390805518) [OptiView XG](http://www.itcentralstation.com/products/comparisons/nagios_vs_optiview-xg?aid=TechTargetRef&lp=comparison1&tid=category1771_topic1175266_sitesearchNetworking_contentDefinition-definition_widget2)

  * ![](http://cdn1.itcentralstation.com/vendors/logos/x50/sevone.jpg?1374384800) [SevOne](http://www.itcentralstation.com/products/comparisons/sevone_vs_visual-truview?aid=TechTargetRef&lp=comparison1&tid=category1771_topic1175266_sitesearchNetworking_contentDefinition-definition_widget2)

vs.

![](http://cdn1.itcentralstation.com/vendors/logos/x50/FlukeNetworks.jpg?1390805518) [Visual TruView](http://www.itcentralstation.com/products/comparisons/sevone_vs_visual-truview?aid=TechTargetRef&lp=comparison1&tid=category1771_topic1175266_sitesearchNetworking_contentDefinition-definition_widget2)

  * ![](http://cdn1.itcentralstation.com/vendors/logos/x50/rDLv51OC_400x400.png?1426157262) [ITRS Geneos](http://www.itcentralstation.com/products/comparisons/itrs-geneos_vs_zabbix?aid=TechTargetRef&lp=comparison1&tid=category1771_topic1175266_sitesearchNetworking_contentDefinition-definition_widget2)

vs.

![](http://cdn1.itcentralstation.com/vendors/logos/x50/zabbix_logo_twitter_bigger.png?1371111734) [Zabbix](http://www.itcentralstation.com/products/comparisons/itrs-geneos_vs_zabbix?aid=TechTargetRef&lp=comparison1&tid=category1771_topic1175266_sitesearchNetworking_contentDefinition-definition_widget2)

  * __
  * __
  * __
    * __
    * __
    * __
    * __
    * __

OSI (Open Systems Interconnection) is reference model for how applications can communicate over a [network](http://searchnetworking.techtarget.com/definition/network). A reference model is a conceptual framework for understanding relationships. The purpose of the OSI reference model is to guide vendors and developers so the digital communication products and software programs they create will [interoperate](http://searchsoa.techtarget.com/definition/interoperability), and to facilitate clear comparisons among communications tools. Most vendors involved in telecommunications make an attempt to describe their products and services in relation to the OSI model. And although useful for guiding discussion and evaluation, OSI is rarely actually implemented, as few network products or standard tools keep all related functions together in well-defined layers as related to the model. The TCP/IP protocols, which define the Internet, do not map cleanly to the OSI model.


[ISO](http://searchdatacenter.techtarget.com/definition/ISO)

### OSI Layers

The main concept of OSI is that the process of communication between two endpoints in a telecommunication network can be divided into seven distinct groups of related functions, or layers. Each communicating user or program is at a computer that can provide those seven layers of function. So in a given message between users, there will be a flow of data down through the layers in the source computer, across the network and then up through the layers in the receiving computer. The seven layers of function are provided by a combination of applications, [operating system](http://searchcio-midmarket.techtarget.com/definition/operating-system)s, network card device drivers and networking hardware that enable a system to put a signal on a network cable or out over [Wi-Fi](http://searchmobilecomputing.techtarget.com/definition/Wi-Fi) or other [wireless protocol](http://searchmobilecomputing.techtarget.com/definition/IEEE-802-Wireless-Standards-Fast-Reference)).

The seven Open Systems Interconnection layers are:

[Layer 7: The application layer](http://searchnetworking.techtarget.com/definition/Application-layer). This is the layer at which communication partners are identified (Is there someone to talk to?), network capacity is assessed (Will the network let me talk to them right now?), and that creates a thing to send or opens the thing received.  (This layer is _not_ the [application](http://searchsoftwarequality.techtarget.com/definition/application) itself, it is the set of services an application should be able to make use of directly, although some applications may perform application layer functions.)

[Layer 6: The presentation layer](http://searchnetworking.techtarget.com/definition/presentation-layer). This layer is usually part of an operating system ([OS](http://whatis.techtarget.com/definition/operating-system-OS)) and converts incoming and outgoing [data](http://searchdatamanagement.techtarget.com/definition/data) from one presentation [format](http://whatis.techtarget.com/definition/format) to another (for example, from clear text to encrypted text at one end and back to clear text at the other).

[Layer 5: The session layer](http://searchnetworking.techtarget.com/definition/Session-layer). This layer sets up, coordinates and terminates conversations. Services include authentication and reconnection after an interruption. On the Internet, [Transmission Control Protocol](http://searchnetworking.techtarget.com/definition/TCP) (TCP) and [User Datagram Protocol](http://searchsoa.techtarget.com/definition/UDP) (UDP) provide these services for most applications.

[Layer 4: The transport layer](http://searchnetworking.techtarget.com/definition/Transport-layer). This layer manages packetization of data, then the delivery of the packets, including checking for errors in the data once it arrives. On the Internet, TCP and UDP provide these services for most applications as well.

[Layer 3: The network layer](http://searchnetworking.techtarget.com/definition/Network-layer). This layer handles the addressing and [routing](http://searchnetworking.techtarget.com/definition/router) of the data (sending it in the right direction to the right destination on outgoing transmissions and receiving incoming transmissions at the packet level). IP is the network layer for the Internet.

[Layer 2: The data-link layer](http://searchnetworking.techtarget.com/definition/data-link-layer1). This layer sets up links across the physical network, putting packets into network [frames](http://searchnetworking.techtarget.com/definition/frame). This layer has two sub-layers, the [Logical Link Control Layer](http://searchnetworking.techtarget.com/definition/Logical-Link-Control-layer) and the [Media Access Control Layer](http://searchnetworking.techtarget.com/definition/Media-Access-Control-layer). Ethernet is the main data link layer in use.

[Layer 1: The physical layer](http://searchnetworking.techtarget.com/definition/physical-layer). This layer conveys the [bit stream](http://searchnetworking.techtarget.com/definition/bit-stream) through the network at the electrical, optical or radio level. It provides the [hardware](http://searchnetworking.techtarget.com/definition/hardware) means of sending and receiving data on a [carrier network](http://whatis.techtarget.com/definition/carrier-network).

![Seven layers of the OSI model](http://media.techtarget.com/digitalguide/images/Misc/osi.gif)

This was first published in August 2014 


