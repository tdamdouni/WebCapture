# What Is DNS and Why Does It Make the Internet Break?

_Captured: 2016-10-22 at 09:39 from [gizmodo.com](http://gizmodo.com/what-is-dns-and-why-does-it-make-the-internet-break-1788065317?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+gizmodo%2Ffull+%28Gizmodo%29)_

Today, [half of America’s internet shut down](http://gizmodo.com/this-is-
probably-why-half-the-internet-shut-down-today-1788062835) when hackers
unleashed a large distributed denial of service (DDoS) attack on the [servers
of Dyn](https://www.dynstatus.com/incidents/nlr4yrr162t8), a major DNS host.
It’s still unclear exactly who carried out the attack and why, but regardless,
the event served as a demonstration of how easily large swaths of the web can be wiped out if attacked by determined hackers.  

Dyn [released this
statement](https://www.dynstatus.com/incidents/nlr4yrr162t8) following the
outage:

> Starting at 11:10 UTC on October 21th-Friday 2016 we began monitoring and
mitigating a DDoS attack against our Dyn Managed DNS infrastructure. Some
customers may experience increased DNS query latency and delayed zone
propagation during this time. Updates will be posted as information becomes
available.

It’s horrific to know that major websites like Twitter, Spotify, Reddit, Etsy,
Wired, and PayPal can all be taken offline in an instant. The exact process
hackers used is so far unknown—aside from the DDoS detail—but it’s important
for every internet user to understand because it has to do with how exactly
the internet works. With that in mind, here is how some of the most popular
websites in the world can be taken offline in a flash.

* * *

### What is the technology?

![](data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==
)

Domain Name Servers (DNS) act as the internet’s phone book and facilitate
requests to specific webpages. They make sure you end up in the right place
every time you type a website into your browser. Hackers will occasionally
attack DNS providers in order to bring down the sites they are serving. Today,
that happened to be Twitter, Reddit, PayPal and more.

That’s a really basic overview. But if you really want to understand how DNS
works at a deeper level, you have to follow the complete order of operations.
A typical internet user starts at one of many computers in a large network
connected through underground cables (such as your laptop). The individual
nodes on these networks communicate by referring to each other with numbers
known as IP addresses. DNS is used to translate a request like a URL into an
IP address.

When you enter a URL—such as [www.Gizmodo.com](http://www.gizmodo.com/#_ga=1.2
176624.1573483110.1468589968)—your browser starts trying to figure out where
that website is by pinging a series of servers. It’s very detailed, and we
won’t bore you with the complete chain of events. There are [resolving name
server](https://www.dnsknowledge.com/whatis/resolving-name-
server/)[s](https://www.dnsknowledge.com/whatis/resolving-name-server/),
[authoritative name servers](https://www.dnsknowledge.com/whatis
/authoritative-name-server/), [domain registrar](https://en.wikipedia.org/wiki
/Domain_name_registrar)[s](https://en.wikipedia.org/wiki/Domain_name_registrar
), and so on. The system is precisely configured to get you from browser bar
to website seamlessly. The process is a little crazy, but perhaps the most
insane part is that it all happens almost instantly. Anytime you’re browsing
the web, opening dozens of tabs, requesting a bunch of different websites,
your computer is pinging servers around the world to get you the right info.
And it just works—until it doesn’t.

* * *

### **How does it break?**

A DDoS attack is a common hack in which multiple compromised computers are
used to attack a single system by overloading it with server requests. In a
DDoS attack, hackers will use often use infected computers to create a flood
of traffic originating from many different sources, potentially thousands or
even hundreds of thousands. By using all of the infected computers, a hacker
can effectively circumvent any blocks that might be put on a single IP
address. It also makes it harder to identify a legitimate request compared to
one coming from an attacker.

In the case of this morning’s attack, hackers brought down the servers of Dyn,
a hugely popular DNS host that manages sites like Basecamp, CNN, Etsy, Github,
Grubhub, HBO Now, Imgur, Paypal, Playstation Network, Reddit, Squarespace, and
Twitter.

When the servers of Dyn were taken down, browsers essentially couldn’t figure
out where to go to find the information to load on the screen. This type of
attack happens every so often when hackers create a little army of private
computers infected with malicious software known as a
[Botnet](http://searchsecurity.techtarget.com/definition/botnet). The people
that are often participating in the attack don’t realize their computer has
been compromised and is part of a zombie army of attackers. In 2014, a hacker
group called Lizard Squad [shut down the Playstation Network and Xbox
Live](http://gizmodo.com/hackers-who-shut-down-psn-and-xbox-live-now-
attacking-t-1675331908) using this method. In 2015, a trojan virus called [XOR
DDoS](http://gizmodo.com/a-new-botnet-hits-servers-with-150-gbps-ddos-
attacks-1733743786) helped hackers create a powerful botnet capable of taking
down almost any server or website.

Defending servers against DDoS attacks can be difficult, but there are ways to
prevent outages. According to [Network
World](http://www.networkworld.com/article/2905115/network-security/the-best-
way-to-stop-ddos-attacks.html), one of the most common methods used is flow
sampling, in which the system samples packets and identifies trends in network
traffic. A flow analytics device evaluates traffic streams and identifies
potentially bad traffic.

* * *

### How do we protect ourselves?

Looking ahead, one big question stands out. How can we avoid attacks like this
stealing internet access away from millions of Americans and losing companies
millions of dollars in revenue?

The answer is complicated. As soon as security companies come up with new ways
to protect companies like Dyn, hackers come up with new ways to attack them.
In the case of DNS infrastructure, however, many point out that the best way
for a website to avoid getting brought down by an attack on one host is simply
to subscribe to multiple hosts. This is called DNS redundancy, and it’s
probably the reason that some sites ([like
Pornhub](https://news.ycombinator.com/item?id=12759653)) survived the attack
unscathed.

In the case of the Dyn servers, it’s unclear exactly how they solved the
problem, but the company is now reporting the [issue
resolved](https://www.dynstatus.com/incidents/nlr4yrr162t8)—about one hour
after the problem started.

**[Michael Nunez**](https://kinja.com/michaelfnunez)[m.nunez@gizmodo.com](mailto:m.nunez@gizmodo.com)[@MichaelFNunez](https://twitter.com/MichaelFNunez)

