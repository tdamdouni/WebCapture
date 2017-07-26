# Automakers Tackle the Massive Security Challenges of Connected Vehicles

_Captured: 2015-06-27 at 20:49 from [www.wsj.com](http://www.wsj.com/articles/BL-DGB-42472)_

The National Highway Traffic Safety Administration is accelerating its efforts to mandate vehicle-to-vehicle communications, a step that could help lower the number of traffic deaths in the U.S., but also creates a major challenge for data security and privacy.

NHTSA plans to submit a proposed connected car rule by the end of the year. New cars equipped with the communications technology could hit the market by the early 2020s, the Transportation Department estimates. The technology could have great public benefits, potentially reducing the 30,000-plus crash related deaths that occur in the U.S. every year. But the technology would emit a stream of data broadcasting the location of millions of cars, a potential security dilemma.

A group of eight automakers already has put years of work into developing an unprecedented system to manage such risks. The system is a form of so-called public key infrastructure, which employs encryption and authentication and is widely used by online shopping sites and banks. The idea is to let two vehicles that have no existing relationship securely exchange data.

PKI technology is effective, but not infallible. Attackers stole credentials from a heating and air conditioning contractor to breach [Target](http://online.wsj.com/public/quotes/main.html?type=djn&symbol=TGT) 's network and point of sale system in 2013. A software flaw called Heartbleed, discovered in April 2014, potentially exposed secret encryption keys used by servers. The Canada Revenue Agency [blamed the bug](http://blogs.wsj.com/digits/2015/06/26/automakers-tackle-the-massive-security-challenges-of-connected-vehicles/SB10001424052702303873604579491350251315132) for the 2014 theft of hundreds of social security numbers from its website.

The data stream that will come from vehicles is bound to attract a broad range of hackers. "A terrorist might want to shut down a major bridge or tunnel in a major urban area by causing a whole bunch of vehicles to misbehave," said Steven Shladover, a program manager for California Partners for Advanced Transportation Technology, a research and development program at the University of California, Berkeley. Such manipulation might be accomplished by sending fake safety messages from one vehicle to the next.

Designers of the new security system for connected cars are trying to guard against that possibility. The system would be larger than anything in use today, creating a new set of technical challenges. A PKI system for connected cars ultimately will need to scale to 200 million or more vehicles, while maintaining driver privacy and fending off hackers.

Automakers including [Ford Motor](http://online.wsj.com/public/quotes/main.html?type=djn&symbol=F) , [General Motors](http://online.wsj.com/public/quotes/main.html?type=djn&symbol=GM) , [Nissan Motor](http://online.wsj.com/public/quotes/main.html?type=djn&symbol=NSANY) ,Mazda Motor Corp., [Honda Motor](http://online.wsj.com/public/quotes/main.html?type=djn&symbol=HMC) , [Volkswagen](http://online.wsj.com/public/quotes/main.html?type=djn&symbol=VOW.XE) and its luxury brand [Audi](http://online.wsj.com/public/quotes/main.html?type=djn&symbol=NSU.XE) **, **Daimler AG's Mercedes-Benz and _Hyundai_ Motor Co. and its affiliate _Kia_ Motors plan to finish a proof of concept for a security credential management system by August of next year**.** The automakers, part of a Crash Avoidance Metrics Partnership consortium, have a cooperative agreement with the Transportation Department to build the system. CAMP has already invested 11 years researching and testing various security approaches.

"The unique challenge that is addressed in the CAMP security system is: Developing a system which meets the security technical requirements while also satisfying the privacy goals," said Michael Shulman, a technical leader at Ford, and program manager for CAMP's Vehicle Safety Communications Consortium. "Other PKI systems, such as the system in operation by the Department of Defense, do not have the same privacy goals," said Shulman, who spoke to CIO Journal both on the phone and via email. Vehicle-to-vehicle communications, as envisioned by U.S. regulators, would broadcast the position of every equipped vehicle 10 times per second to similarly equipped cars and trucks within 1,000 feet of each other for the purposes of crash avoidance, he said.

PKI makes use of encryption and pairs of digital keys to encode and decode messages. The sending party in a communication uses a private key to digitally sign its message, embedding information that validates its identity. An associated public key is used by a receiver to verify the sender's digital signature.

The use of PKI is transparent to most online shoppers, because their Internet browser comes equipped with public keys that help verify the authenticity of websites. The shopper simply sees the letters "https" in the Web address, often alongside the image of a padlock. Drivers won't need to worry about the technology either, because it will be managed automatically. Connected vehicles will broadcast messages that contain their position and speed. Security credentials known as certificates are sent along with those messages. A third-party known as a certificate authority validates those credentials to prove that a particular message did indeed originate from a specific vehicle.

The architecture of the system is designed from the start with privacy and security in mind. Certificates will be changed frequently, about 12 times per hour at irregular intervals, to prevent tracking by outsiders, according to Shulman. The messages will be signed, to verify that they weren't changed between the time one vehicle sent it and another received it. "We're using some standard cryptography, but we're transforming it in a way to maintain privacy," Shulman said.

Inside the security credential management system, a technological division of labor helps maintain security: one element creates a bundle of certificates, but doesn't know which device will receive them. Another part of the system knows where the bundle is going, but doesn't know which certificates are in the bundle. "Policies will be adopted to prevent the operation of these … parts by the same organization," he said.

No personally identifiable information is contained in the certificates or in the basic safety messages, he said. And devices that are out of compliance or have been tampered with can be revoked.

Vehicles will communicate with one another using a modified version of Wi-Fi, called dedicated short range communications, which automakers including Ford and GM have been collaborating on for more than a decade. The technology works by letting vehicles exchange messages, up to 10 times per second, which contain basic safety data such as a car's speed and position. For example, a driver who is about to make a left-hand turn at an intersection would receive a warning about an oncoming truck running a red light. Vehicles need to be within 1,000 feet of one another to receive the messages.

GM acknowledged that security of the radio frequency is a "significant issue," but one that CAMP is addressing. GM plans to introduce vehicle-to-vehicle communications in its 2017 Cadillac CTS. "We're confident that we can resolve this issue prior to the introduction of the technology with the 2017 Cadillac CTS," a spokesman said.

During the first year that new vehicles are equipped with communications technology, the security credential management system will only need to scale to a few million equipped vehicles. That will require roughly 30 high-end servers and is comparable to the scale of existing IT systems. But 25 years after connected cars are mandated, there will be roughly 300 million equipped vehicles on the road, according to an [August 2014 NHTSA report](http://blogs.wsj.com/digits/2015/06/26/automakers-tackle-the-massive-security-challenges-of-connected-vehicles/UserskingrDownloadsReadiness-of-V2V-Technology-for-Application-812014%20\(1\).pdf).

"When it is fully operational, this PKI system will be the largest in the world in terms of the number of certificates generated per year and the number of equipped devices," Shulman said.

The sheer size of the system may make it difficult to manage. "Given the scale and size of this, it's very complex architecture," said Joshua Corman, CTO of Sonatype, a security firm, adding that problems occur frequently with much simpler systems such as email certificates in corporations. One challenge may be issuing and revoking certificates at such a large scale, said Corman who is also an automotive security specialist and has done work with a grassroots organization called I Am The Cavalry, which focuses on issues in which computer security intersects with public safety.

Automakers say that the potential safety advances of the technology outweigh the challenges. For example, vehicle-to-vehicle communications may help reduce deaths that occur in intersections by alerting drivers to an oncoming vehicle running a red light or stop sign, said Shulman. About 26% of 32,719 people killed in vehicle crashes in 2013 were killed in intersections, [according to a December 2014 report](http://www-nrd.nhtsa.dot.gov/Pubs/812101.pdf) from the NHTSA.

Write to rachael.king@wsj.com

______________________________________________________

For the latest news and analysis, [follow @wsjd](https://twitter.com/wsjd) and [like us on Facebook](https://www.facebook.com/WSJD) to get our news right in your feed:

Get breaking news and personal-tech reviews [delivered right to your inbox](http://online.wsj.com/public/page/email-setup.html#Technology).

**More from WSJ.D:** And make sure to [visit WSJ.D](http://www.wsjd.com/) for all of our news, personal tech coverage, analysis and more, and [add our XML feed](http://online.wsj.com/xml/rss/3_7455.xml) to your favorite reader.
