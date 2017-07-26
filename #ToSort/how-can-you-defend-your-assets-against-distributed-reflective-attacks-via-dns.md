# How Can You Defend Your Assets Against Distributed Reflective Attacks via DNS?

_Captured: 2017-05-12 at 00:41 from [dzone.com](https://dzone.com/articles/how-can-you-defend-your-assets-against-distributed?oid=twitter&utm_content=buffera2693&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

DNS servers are necessary for finding resources on the internet. They are also a source of vulnerabilities and are often poorly defended. The DNS protocol listens on port 53, and this port is, therefore, open in most firewalls. This combination of an open listening service and little security focus makes the protocol interesting to hackers; especially if they want to perform denial-of-service attacks because they can use some of the features of DNS to amplify their attack vectors.

## How DNS Works

DNS servers are used on the internet to translate between human-friendly domain names and IP addresses. DNS stands for Domain Name System and is a database of IP addresses. For an overview of how DNS works, see this Microsoft Technet [article](https://technet.microsoft.com/en-us/library/cc958978.aspx).

DNS usually receives a recursive name query from a web browser. One specific DNS server can only hold a limited amount of information. When a query is recursive it will query other DNS servers on the internet for the correct address lookup before returning the IP address to the client. The way this works is that when the web browser queries the DNS and the DNS doesn't have the right information it gives a referral back as the result; which happens to be the address of a DNS server further down the namespace tree.

![](https://safecontrols.files.wordpress.com/2017/03/030117_0546_howcanyoude1.png?w=466&h=364)

In the above illustration of a recursive DNS lookup, the resolver queries the DNS server with a request. The DNS server cannot find the information requested in its cache or zone and queries the root server. It is then referred to the domain DNS server, which again points to the Example domain DNS server.

## Attacking Through Recursive Open DNS

Using recursive DNS servers to flood a target with traffic is effective for attackers because the request package sent to the DNS server is very small compared with the response (hence the term "amplified" attack). All the attacker has to do is to spoof the sender address of the DNS request package, and submit the spoofed package to open recursive DNS servers from a large number of machines under his or her control, and voila - a DoS condition occurs for the target because the DNS server will direct all those responses to the spoofed IP. So what you need to perform this attack is:

  * A list of open recursive DNS servers.
  * A spoofed UDP request package to the DNS server.
  * A botnet under your control.

The first point of the list is easy enough - go to [https://duckduckgo.com](https://duckduckgo.com/) and search for 'public dns' and it will give you a list as an instant answer.

Spoofing the IP can be done using any library that can write IP headers (or you can craft the header manually). Here's an example using scapy, a Python module for low-level network operations:
    
    
    spoofed_packet = IP(src='spoofed_ip', dst='the dns you are trying to reach') \
    
    
    / TCP(sport=sourceport, dport=53) / payload

So, then you only need a botnet. You can go ahead and create one by spreading malware to thousands of victims, or you can hire a botnet on the dark web - both are equally illegal and immoral, but the bad guys do this.

## Defending Against This Mess

Using an old-fashioned IP table's firewall won't do the job because you cannot drop traffic on port 53 (this is your DNS traffic). The DNS server can be configured to mitigate some of these attacks - but the open public ones are outside of your control. Some of them have rate control, limiting the frequency with which they can be queried for the same target, as well as per source IP.

So what can you do locally to protect against this type of attack?

  1. **Ensure you have sufficient capacity to take peak traffic loads**. It is probably infeasible to build capacity for very large DDoS attacks (~ 300 Gbps) but many attacks are much smaller than this and can be absorbed by high bandwidth capacity.
  2. **Filter your traffic** - especially unexpected traffic types. Filter out all DNS traffic for all equipment not dependent on sending DNS requests. Filter out IP's from identified botnets and use a robust threat intelligence solution to obtain information on botnets.
  3. **Use anomaly detection** and **use dynamic throttling of traffic** from name servers. If there are sudden spikes in traffic from unusual resolvers, it may be a sign of a reflective amplification attack.
  4. For key resources, **build in redundancy to redirect traffic** when necessary and allowing the service to remain operational. Potentially contract with a very-high-bandwidth provider to act as a buffer against large DDoS floods.
