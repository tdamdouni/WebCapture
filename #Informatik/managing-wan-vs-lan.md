# Managing WAN vs. LAN

_Captured: 2017-12-11 at 20:21 from [dzone.com](https://dzone.com/articles/managing-wan-vs-lan?edition=342127&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-11)_

[Download Red Hat's blueprint for building an open IoT platform](https://dzone.com/go?i=250323&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Fresources%2Fintelligent-systems-solution-internet-things)--open source from cloud to gateways to devices.

The internet and rise of mobility mean that business users and the information systems they rely on are rarely in the same place anymore. Users depend on their own devices, virtualization means their desktop isn't always on their desktop, applications run remotely and even simple telecom services are delivered via the internet. In addition, API-based services, Big Data, and device-to-device communication mean that networks need to handle more east-west traffic than in the past, as well as more north-south traffic.

Traditional networks, designed when most traffic was internal to a company, weren't built to handle these traffic patterns. There's more usage now on the WAN vs. LAN to support remote users, but using the internet to reach the cloud doesn't provide dedicated connections and guarantee the speed users need.

## Monitor the Network Endpoint to Endpoint

Network monitoring that recognizes WAN vs. LAN can help you keep an eye on your entire infrastructure and focus on the issues specific to each network. Intelligent monitoring that spans the end-to-end network gives you the details needed to optimize each network component without losing sight of the bigger picture.

Monitoring needs to cover every endpoint, not just traditional north-south communication channels. Most WANs are optimized for north-south traffic, but big data can cause issues due to east-west traffic the network wasn't built to handle. Big data places bigger demands on bandwidth for live traffic.

This monitoring needs to be continuous to allow you to react to problems and address them before they impact users and business operations. You should also look for a tool that can evaluate the entire network, rather than individual paths. Because of the unique quality demands of VoIP and video applications, the monitoring tool should be able to focus on those needs as well as general network issues.

The tool should [generate metrics for all paths](http://info.appneta.com/The-5-Network-Metrics-You-Should-Keep-to-See-Into-the-Cloud.html), so you are able to effectively identify the root cause of problems and resolve them faster. You need to be able to get measurements in both directions, too, because upstream and downstream data flows don't always experience the same performance and traffic patterns.

Along with performance monitoring, you should keep an eye on network usage--which applications are using your bandwidth? Real problems need technical fixes, while other problems can be addressed by reminding users of corporate policies on resource use.

You also need tools that don't just collect statistics but help you use them meaningfully--not only in graphing trends, but also in troubleshooting. The variable routes traffic now takes means that figuring out exactly where issues are arising is no easy task, especially due to reliance on hard-to-debug wireless network connections. Because you have little insight into what's happening at one end of the conversation (up in the cloud), synthetic transactions can help you understand the full round-trip processing time. With metrics for those transactions, you can figure out if your timing issues are due to noisy neighbors in the cloud, resource contention on the public internet or a poor-quality local network.

## Balancing WAN vs. LAN Needs

You need to balance the performance needs of your WAN and LAN to make sure users get a good experience wherever they are. Look for tools that give you the information you need to:

  * Identify the cause of network problems
  * Correlate application performance and user experience
  * Compare bandwidth across applications
  * Evaluate whether provider SLAs are being met
  * Recognize trends and plan for future demand

Making decisions about [network capacity, as always, requires balancing performance](https://www.appneta.com/blog/network-capacity-vs-bandwidth-dont-waste-it-budget/) and cost. While much of cloud use is driven by the perception that it offers lower cost, cloud also makes network performance more important. Investing appropriately in your WAN requires monitoring utilization to make sure you don't over- or under-build your network. This requires understanding traffic patterns and making a conscious decision about sizing your links to handle short periods of peak demand or the more typical, lengthier periods of lower demand. Besides measuring utilization, evaluate uptime percentage and latency. You can always start with ping, but better tools provide a more analytical approach to measuring your WAN performance.

Use the data you collect to optimize your bandwidth usage, rather than wasting money investing in unnecessarily expanding capacity. Quality of Service (QoS) metrics are critical here. Sometimes problems can be solved by prioritizing traffic differently to improve voice and video performance without impacting other applications.

[Build an open IoT platform](https://dzone.com/go?i=250322&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Fresources%2Fintelligent-systems-solution-internet-things) with Red Hat--keep it flexible with open source software.
