# When Good Clouds Go Bad

_Captured: 2017-03-07 at 02:12 from [dzone.com](https://dzone.com/articles/when-good-clouds-go-bad?edition=273885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-06)_

Download the [Essential Cloud Buyer's Guide](https://dzone.com/go?i=123025&u=http%3A%2F%2Fpd.internap.com%2Fcloud-buyers-guide-DZ) to learn important factors to consider before selecting a provider as well as buying criteria to help you make the best decision for your infrastructure needs, brought to you in partnership with [Internap](https://dzone.com/go?i=123025&u=http%3A%2F%2Fpd.internap.com%2Fcloud-buyers-guide-DZ).

Recently (February 28th, 2017), the largest cloud provider in the galaxy and possibly the universe--we're unsure how far alien technologies have progressed--suffered a huge outage

![iStock_servers_data_center_cloud](http://www.internap.com/internap/wp-content/uploads/2013/11/iStock_servers_data_center_cloud1.jpg?x10144)

that affected a massive number of customers. This isn't meant to throw stones at AWS (Amazon Web Services); all technologies are at risk of suffering downtime be it at the datacenter, in your network, through your cloud provider, or the physical equipment you utilize. AWS isn't the first cloud provider to have a failure and I can promise you that they won't be the last. They're a good fit for many folks which is why they've become an industry leader.

What this recent catastrophic crash does do, however, is raise the all-too-important point that **single points of failure are everywhere**.

If you're in charge of making sure your customers or employees have access to your online presence, it's your job to eliminate them. It's a tall task, no doubt--but it's achievable. This is going to be a hot topic for the remainder of 2017 and likely part of many job descriptions moving forward.

Let's take a look some of the most common portions of Internet infrastructures builds to identify and suggest ways to eliminate these single points of failure.

## **How to Remedy**

  * Move static portions of your cloud load to geographically dispersed edge datacenters in colocation builds. Clouds are great for flexibility but don't offer the performance, reliability, and significant cost-savings that having your own hardware housed in premium datacenter do.
  * Use more than one cloud provider. This may sound like an obvious fix, but don't put all of your eggs in one basket. The physical location of the computers that house these cloud instances has a significant impact on latency and therefore customer experience, so make sure they're close to where your customers are.
  * Ensure that the cloud/hosting instances are housed in datacenters that are highly redundant.
  * Make sure you're either currently in or can move to a colocation provider with multiple geographically diverse edge datacenters close to one or more of your customers' physical presence. Make sure to have more than one datacenter/colocation presence to protect against catastrophic failure.
  * If you don't have an on-site engineer, make sure that the facilities you're considering offer remote hands service from an actual engineer. If your hardware fails or you need a reboot, not being able to access your failed hardware is the most helpless feeling in the world.
  * At a minimum, you want to be connected to more than one Network Service Provider (NSP). Just like all cloud providers go down, all network service providers have issues and can go down. Very few offer Service Level Agreements (SLAs) higher than four nines - 99.99%, let alone 100% (shameless plug, [we do](http://www.internap.com/network-services/performance-ip/)).
  * Alternatively, you can connect to an optimized IP service that ensures your traffic is traveling the best possible route all of the time. These technologies work by optimizing for latency, packet loss and jitter, and directing your traffic to the optimal path over a handful of different NSPs. What's more, if any one of those NSPs has any issues at all, your customers won't feel it as they'll be routed around the problem to a different NSP.
  * If you're already multi-homed (connected to more than one NSP) and are running BGP, consider a route optimization appliance that will automatically flip you to the best performing NSP--or away from one which is failing.
  * You want to make sure that your hardware is current and has sufficient life left. This is commonly referred to as a "refresh" and depending on the type of servers you're using and what they're asked to do, a refresh will likely be required anywhere from every six months to every five years.
  * Make sure you have several spare servers housed in your cage or storage area at the datacenter just in case you need your on-site engineer or colocation provider's remote hands service to remedy the situation.

The Cloud Zone is brought to you in partnership with [Internap](https://dzone.com/go?i=109853&u=http%3A%2F%2Fpd.internap.com%2Fbare-metal-101-pr). [Read Bare-Metal Cloud 101](https://dzone.com/go?i=109853&u=http%3A%2F%2Fpd.internap.com%2Fbare-metal-101-pr) to learn about bare-metal cloud and how it has emerged as a way to complement virtualized services.
