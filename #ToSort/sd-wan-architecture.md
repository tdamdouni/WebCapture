# SD-WAN Architecture

_Captured: 2018-05-22 at 21:19 from [dzone.com](https://dzone.com/articles/sd-wan-architecture?edition=376341&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-05-22)_

SD-WAN is the technology that allows enterprise companies to manage networks as software-based (SDN). Traffic and control layers are separated using virtualization technology at network management.

## Network Management Problems and the Benefits of SD-WAN Technology

  * High cost of MPLS technology used by corporate companies as a standard access network.

  * Activation of manual processes to add a new branch for networking.

  * Complex and static network configuration management.

  * High-cost, non-standard network equipment (CPE).

  * SD-WAN solutions are access-agnostic to transport type. In addition to MPLS, broadband internet and LTE technology can be used together.

  * Applications' infrastructure use can be managed on a rule-based basis. For example, while MPLS is used to delay sensitive voice applications, broadband internet could be used for CRM/ERP applications. Private internet access for employees can be restricted.

  * The network is constantly monitored so that the network can be used effectively and at oprtimal levels. With active network management, when there is a slowdown or a problem in part of the network, the traffic can be diverted to alternative routes.

  * Vendor-independent and low-cost X86 standard hardware can be used instead of customized software and hardware solutions provided by major vendors in the WAN network.

  * New branch additions or changes of configuration can be done with central management. 

  * Provide secure access to applications such as Office 365 and Salesforce CRM that companies use over the cloud.

  * Security services to the data center and branch offices (vCPE) can be uploaded via programmable structure. Firewalls, IDP/IPS, URL Filtering, and DDos protection can be provided with software instead of special hardware for UTM solutions.

  * The activation, monitoring, and management of CPEs in the branches.

  * Installation of network policies on devices.

  * Secure connection and management of network over VPN.

## VNF Manager

The VNF manager manages the installed virtual functions in branch and central CPEs.

Functionalities:

  * Configuration and activation of Layer 4-Layer 7 services.
  * Managing the lifecycle of services.
  * CPE authorization and network enrollment.
  * Template-based management of branches with similar configurations.
  * REST API integration for OSS/BSS.
  * High availability management.

## Data Analysis (Optional)

Analyzes the traffic and application data received from the devices in the offices. By reporting this data, it's possible to manage active/passive capacity management and dynamic traffic management policies.

## ![SD-WAN Architecture](https://dzone.com/storage/temp/9096692-figure-1.png)

**SD-WAN Use Cases**

### **Dual Path**

In addition to MPLS access to the branch, low-cost broadband internet access is provided. Non-critical traffic is directed to the Internet. In addition, if there is a problem in the MPLS network, access to the DC is securely provided over the internet.

![Image title](https://dzone.com/storage/temp/9096770-figure-2.png)

### **Cloud Access**

The branch has access to cloud services such as Office 365, Skype, and Salesforce CRM via VPN. Alternative ways of accessing the data centers are established by MPLS and the service provider LTE/broadband.

![Image title](https://dzone.com/storage/temp/9096776-figure-3.png)

## **Conclusion**

The increased traffic and variety of internet use by corporate companies have also increased the complexity of current WAN networks. The use of cloud-based applications has also increased, and secure internet access has become a necessity.

Service providers should be able to offer SD-WAN solutions and value-added services to their customers as access service.

Opinions expressed by DZone contributors are their own.
