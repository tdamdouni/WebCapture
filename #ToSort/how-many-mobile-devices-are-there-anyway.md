# How Many Mobile Devices Are There, Anyway?

_Captured: 2017-04-12 at 20:12 from [dzone.com](https://dzone.com/articles/how-many-mobile-devices-are-there-anyway?edition=290884&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-12)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190139&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190139&u=https%3A%2F%2Fwww.wakanda.io%2F).

You've probably seen this image about the form factor of mobile devices, before and after the iPhone launched in 2007.

![Different mobile devices since iPhone](https://az184419.vo.msecnd.net/sauce-labs/blog-images/devices_00.png)

_Source: CultOfMac.com_

It's clear that the iPhone has led to a lot of standardization in the form factor of mobile devices. If you've been an observer of the mobile ecosystem, you may assume there is a lack of innovation in the space since the iPhone's launch. However, the next generation of mobile devices is being born in a silent revolution. In this post, we look at the high-level trends that are prevalent in the mobile device landscape, and what they mean for application development and testing.

## **Consolidation in Mobile Operating Systems**

There is a great deal of standardization in mobile operating systems.

![Market share of mobile web by mobile OS](https://az184419.vo.msecnd.net/sauce-labs/blog-images/devices_03.png)

[WeAreSocial](http://wearesocial.com/uk/blog/2017/01/digital-in-2017-global-overview) reports that Android is on 71.6% of all mobile devices, and iOS and Android together make up more than 90% of mobile operating systems. This is significant considering the number of mobile OSs that have tried hard to gain a foothold in this competitive space. Microsoft Windows Phone, Firefox OS, Ubuntu mobile, Samsung's Tizen- all have tried hard, but have failed to even come close to the dominance of these two OSs.

Yet, despite the consolidation, operating system versions are numerous. Android is especially guilty of OS fragmentation because of its open approach to OEM vendors. Many OEMs in under-developed parts of the world still ship devices with an Android OS version that was released in 2013. Statista notes that [KitKat (v4.4) is the most popular Android OS](https://www.statista.com/statistics/271774/share-of-android-platforms-on-mobile-devices-with-android-os/) version despite Android Nougat (v7) as the current version.

![Distribution of Android OS used by Android phone owners](https://az184419.vo.msecnd.net/sauce-labs/blog-images/devices_04.png)

_Source: [Statista](https://www.statista.com/statistics/271774/share-of-android-platforms-on-mobile-devices-with-android-os/)_

This is a nightmare for app developers who need to draw the right balance between leveraging cutting-edge features of the OS, while ensuring backward compatibility.

Still, with Android and iOS covering almost the entire smartphone market, mobile development and testing teams can cover all bases with just these two OSs. They can respond to other lesser-known OSs reactively.

### **Of Form Factors and Phablets**

The number of mobile devices in use today, according to Cisco's extensive [Visual Networking Index](http://www.cisco.com/c/en/us/solutions/collateral/service-provider/visual-networking-index-vni/mobile-white-paper-c11-520862.html), is at 8 billion, and is growing at a rate of 8% per year. This number is expected to reach 11.6 billion by 2021.

![Chart of devices from 2016 to 2021](https://az184419.vo.msecnd.net/sauce-labs/blog-images/devices_07.png)

Source: [Cisco](http://www.cisco.com/c/en/us/solutions/collateral/service-provider/visual-networking-index-vni/mobile-white-paper-c11-520862.html)

There are many types of devices in this chart, but at first glance, what stands out is that smartphones will retain their lead in the overall device mix.

According to [Flurry's 2016 State of Mobile](http://www.mxmindia.com/2017/01/yahoos-flurry-analytics-announces-2016-state-of-mobile-report/) report, in 2016, phablets have replaced mid-sized smartphones as the preferred display size for mobile devices. Even Apple has bit the bullet and now ships an iPhone 7S.

![Global Form Factor Distribution in 2016](https://az184419.vo.msecnd.net/sauce-labs/blog-images/devices_09.png)

_Source: [Flurry](http://www.mxmindia.com/2017/01/yahoos-flurry-analytics-announces-2016-state-of-mobile-report/)_

### **Wearables and M2M Devices Power the IoT**

The real disruption in the mobile ecosystem isn't happening with smartphones, but with connected devices that make up the Internet of Things (IoT).

Going back to Cisco's report, wearables and M2M (machine to machine) devices are expected to grow fastest among mobile devices. Wearables are devices like smart watches, health monitoring devices, and smart clothing.

Wearables will grow at 23% per year till 2021, and most of them will be connected to the Internet directly without depending on a smartphone.

![Graph of wearable devices from 2016 to 2021](https://az184419.vo.msecnd.net/sauce-labs/blog-images/devices_06.png)

_Source: [Cisco](http://www.cisco.com/c/en/us/solutions/collateral/service-provider/visual-networking-index-vni/mobile-white-paper-c11-520862.html)_

Among wearables, VR headsets are expected to be the fastest-growing device type, with a 40% annual growth rate.

![Graph of VR headsets from 2016 to 2021](https://az184419.vo.msecnd.net/sauce-labs/blog-images/devices_05.png)

_Source: [Cisco](http://www.cisco.com/c/en/us/solutions/collateral/service-provider/visual-networking-index-vni/mobile-white-paper-c11-520862.html)_

Even as [Jawbone and Fitbit](http://gizmodo.com/the-fitness-tracker-fad-appears-to-be-dying-1788536125) see declining sales figures, the wearables market is in heavy flux, and it's only a matter of time before we see some breakthrough devices being launched.

M2M devices are wireless devices that communicate with each other over a network and can be used to control complex processes like warehouse management, supply chains, and smart cities. M2M will grow at a healthy growth rate of 18% per year. This is much higher than the 8% projected growth for mobile devices overall.

![Graph of device growth](https://az184419.vo.msecnd.net/sauce-labs/blog-images/devices_08.png)

_Source: [Cisco](http://www.cisco.com/c/en/us/solutions/collateral/service-provider/visual-networking-index-vni/mobile-white-paper-c11-520862.html)_

With this explosion of device types and volumes, mobile apps will no longer be confined to just smartphones, but will need to support a plethora of varied devices in the IoT. It will become more and more challenging to build native apps for each mobile platform. The "build once, run anywhere" approach of hybrid and mobile web apps will gain traction, even though [native mobile apps now account for 90%](http://flurrymobile.tumblr.com/post/127638842745/seven-years-into-the-mobile-revolution-content-is) of all time spent on mobile devices.

### **IPV6 Technology and Security Challenges**

Apart from operating systems and device hardware, mobile-specific technologies will impact the development of mobile apps. [IPv6](https://en.wikipedia.org/wiki/IPv6) is a major change that affects mobile devices. It is a new Internet protocol that can support the explosion of IoT devices by having enough IP addresses to allot to each unique device.

With the advent of IPv6, security will take center stage. The peer-to-peer nature of IPv6 will expose new vulnerabilities like the recent one that [Dyn experienced](https://www.wired.com/2016/10/internet-outage-ddos-dns-dyn/). In-built support for [IPSec](https://en.wikipedia.org/wiki/IPsec) is critical to ensuring the slew of new IoT devices is secure. However, IPSec can't prevent attacks on the OSI layers (like DDoS attacks, and brute-force password guessing). As we enter uncharted waters, there are new challenges waiting for mobile Dev and QA teams.

If you thought testing coverage for applications is hard today, it's only going to get harder with the IoT. Operating systems, hardware devices, and mobile-specific technologies all have a bearing on how mobile apps are built, tested, and deployed. By understanding the lay of the land, you can be well equipped to make the most of the mobile revolution that's underway.

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190140&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190140&u=https%3A%2F%2Fwww.wakanda.io%2F).
