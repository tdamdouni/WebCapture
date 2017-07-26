# Why Managing QoS Matters More Than Ever

_Captured: 2017-03-28 at 20:47 from [dzone.com](https://dzone.com/articles/why-managing-qos-matters-more-than-ever?edition=286932&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-28)_

There are plenty of technology details that have gone through major changes in the cloud era. One networking detail in particular, tracking and managing quality of service (QoS), is an essential one to master for modern IT. QoS is a way of marking traffic prioritization over networks in an attempt to guarantee a certain level of performance. So, QoS priority levels are at their peak with "expedited forwarding" (DSCP 46) for real-time apps like VoIP and video, then move down in priority order till the default "best effort" (DSCP 0) category for non-business-critical apps (your employees' streaming music, for example).

QoS ensures that when there isn't enough capacity, the highest-priority workloads get through first without slowing down. QoS also makes sure that routing priorities don't change -- QoS changes can lead to jitter, data loss, and latency. But it has to be enforced all the way to the end of the network path. If different-priority workloads merge at any point along the way, that will slow down the high-priority apps and lead to poor user experience.

QoS is important for both parties in the [cloud equation--users and providers](https://www.researchgate.net/publication/282085451_A_Survey_on_Quality_of_Service_in_Cloud_Computing). Users need QoS policies that ensure good performance, and providers have to first promise reasonable QoS expectations, then enforce them in their SLAs. When QoS is working right, there's no bandwidth hogging, and network bottlenecks and packet drops never affect end users. Well-managed QoS results in better call quality for VoIP apps and other bandwidth-heavy critical apps.

Getting QoS to work well can be a balancing act. QoS management in cloud computing is complicated. If an IT team can only see part of the network connecting their data center and users to the cloud, they can only ensure QoS for that part of the network. The general loss of infrastructure control that IT is experiencing with cloud adoption extends to metrics like QoS. Applications, networks and their related metrics were easy to track in on-premises legacy systems, but they're now so distributed that it's become much harder.

The concept behind QoS is really important today -- maybe even more important than it was in the pre-cloud days since so many recreational and low-priority apps are now competing for attention. Those apps can easily clog up the QoS priority order, while at the same time slowing down the call center's VoIP app.

There may be some [metrics you lose when you move to the cloud](http://info.appneta.com/The-5-Network-Metrics-You-Should-Keep-to-See-Into-the-Cloud.html?Ref__c=20680), but we recommend keeping QoS as one of the ones you continue to track.

## **How to Stay on Top of QoS**

QoS should be part of the SLAs you sign with your internet service providers--it's a common part of most business-class ISP contracts--but you'll likely need to do some setup and management to make sure QoS is working for your business.

To make sure QoS works for SaaS apps and cloud services, several things have to be done correctly:

  * QoS queues must be set up right. This can be challenging since many businesses don't know every app that's in use and how much capacity they each use.
  * QoS has to be enforced end-to-end to work properly.
  * QoS should be monitored over time as a key troubleshooting tool.

We've spent a lot of time here at AppNeta considering QoS and the ways it's previously been measured and managed (and often still is). The old tools that monitor QoS inside your network only just don't see past the walls of your data center. They're missing entire swaths of network action that can show a lot of information about where a slowdown happened. Other tools check QoS only at the endpoints, which offers partial information about changes, but not who changed it or how many times. ISPs may also offer this type of partial detail on QoS in your SLA.

Instead, you should use a tool that checks QoS at every layer 3 hop and identifies if QoS changed -- by whom and to what. If you get those ducks in a row in the first place, it'll make your monitoring and troubleshooting that much easier.
