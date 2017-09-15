# Troubleshooting DNS Server Issues

_Captured: 2017-08-15 at 19:39 from [dzone.com](https://dzone.com/articles/troubleshooting-dns-server-issues?edition=310391&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-20)_

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

There are two big DNS issues that can come up and I'm going to walk you through how to fix both of them. Keep in mind that this isn't designed to be a comprehensive server troubleshooting guide and it's possible that what looks like a DNS problem might be something else.

For the purpose of this article, we'll assume that you know what the problem is and that it is an issue with your DNS.

## Incorrect nameservers

The internet is built with a lot of redundancy in place and that is true for DNS servers as well. There are many different copies of the same "phone book" in different places, but they are all getting their information from one authoritative source.

Your registrar will set their own nameservers as the default authoritative source, but you can change that to point to a different location, like the server where you are hosting your site.

If you upgrade your website and end up moving it to a new server, you might forget to update your DNS. That means that your domain will resolve to the old IP address and not the new location. This can be especially frustrating if a copy of your old site is still up and you are making changes to the new site. It will look like the changes you are making aren't being saved when in reality it's just that you aren't showing the version of the site that you are making changes to.

Here's how you can check to make sure that you are pointing to the right server. If you bring up the command prompt and type in "ping domain.com" your computer will tell you what IP address is tied to "domain.com." Compare that IP address to the IP address of your new server and see if they match.

If they don't match then you probably need to check the DNS information on your old server and also the name server settings from your registrar.

## DNS Request Overload

We compared DNS to a phone book, but it is probably more similar to a bank of operators who are taking calls and routing them to the correct location. A DNS server has a limit of how many lookups and connections it can perform at the same time.

A distributed denial of service (DDoS) attack is when someone maliciously tries to break your server by programming many different computers to request your web pages over and over again, but it's much more likely that you will overload your DNS server by creating some content that gets a spike of visitors.

Here are two ways to manage peak load times when you really kill it on marketing your content.

  1. Upgrade your server. If you can manage it, upgrading your server is also going to come with more dedicated resources for resolving your domain. This might not be the most cost effective method because you're paying an increased monthly amount for other upgrades besides DNS which you may not need.

  2. Get a dedicated DNS server. It's a little bit more effort to set up, but when you pay for a dedicated DNS server they specialize in preventing DDOS attacks so they'll be able to handle innocuous overloads from real website visitors as well. [Cloudflare](https://www.cloudflare.com/dns/) is a great example of a DNS service that can handle pretty much anything you throw at it.

When I'm not writing about technical subjects that go right up to the edge of my working knowledge, I manage growth at ZipBooks, an accounting software startup in American Fork, UT, USA. If you are in the US and are in the process of vetting [online bookkeeping services](https://zipbooks.com/bookkeeping-services/), feel free to reach out!

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

Opinions expressed by DZone contributors are their own.
