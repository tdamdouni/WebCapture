# DNS for Developers

_Captured: 2018-04-15 at 21:14 from [dzone.com](https://dzone.com/articles/dns-for-developers-funky-sis-devops-diary?edition=374201&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-04-15)_

[Learn how](https://dzone.com/go?i=282429&u=https%3A%2F%2Fcraftersoftware.com%2Fresources%2Fwhite-papers%2Ffive-reasons-you-need-a-git-based-cms%3Fdzone) Crafter's Git-based content management system is reinventing modern digital experiences.

### What Is DNS?

DNS, or Domain Name System, is what translates domain names to IP addresses and vice versa.

### Wait, What Is an IP Address and What Are Domain Names?

You do realize this is a developer blog? An IP address is a unique address on the internet and a domain name is a user-friendly label for one or more of these.

An example might be google.com, which, for me, resolves to 216.58.204.14

### How it Works

![](https://i2.wp.com/www.funkysi1701.com/wp-content/uploads/2018/04/dns-rev-1.gif?resize=360%2C320&ssl=1)

When your browser makes a request to google.com, it makes a request to your ISP's DNS Servers. This resolves google.com to 216.58.204.14

In more detail, your ISP's DNS server will forward the DNS query to another DNS server and will cache the results for a set amount of time. This is the TTL or Time To Live. Next time the ISP DNS Server will be able to reply directly without needing to forward requests.

This forwarding and caching are what makes making a DNS change not instantaneous. The TTL needs to be reached so that no results are still being fetched from the cache of DNS servers across the globe.

### DNS Records

Now we know roughly how DNS works let's look at the most common type of records

#### A

A (Host) records are the most simple records which translate domain names to IPs, e.g., www.google.com to 216.58.204.14

#### CNAME

A CNAME (Canonical Name) record is different to an A record in that it maps a domain name to another domain name when no A record exists.

For example, www.google.com to somethingelse.google.com

Typically, Azure makes use of CNAMEs for many of its services especially adding a custom domain name.

#### MX

MX stands for Mail Exchange and is used for configuring email.

#### Name Server

Every domain has a number of Name Servers which tells you what servers control the DNS settings for that domain. If you change your Name Servers then the new Name Servers will be where you can change your DNS settings.

If you want to use a service like [DNSimple](https://dnsimple.com/) instead of [123reg](https://www.123-reg.co.uk/) or where ever you registered your domain then all you need to do is change your Name Servers.

#### AAAA

Like A records, but for ipv6.

### What Next?

Want to put some different DNS records into practice? Buy a domain name and publish some content to it. Check out my previous post about [programmatically adding records](https://www.funkysi1701.com/2017/10/16/creating-dns-records-programmatically/). Want an SSL certificate? Get a wildcard one and then you can apply it to any subdomain you add to your domain.

If you have a new website you want to publish, consider which of the following is better:

  * https://www.example.com/newsite

  * https://newsite.example.com

I much prefer the second option, it looks cleaner, there is no potential conflict with the parent site, and no subfolder issues between production and development.

Crafter CMS is a modern Git-based platform for building innovative websites and content-rich digital experiences. [Download this white paper now](https://dzone.com/go?i=282430&u=https%3A%2F%2Fcraftersoftware.com%2Fresources%2Fwhite-papers%2Ffive-reasons-you-need-a-git-based-cms%3Fdzone).
