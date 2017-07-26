# The New Battleground: Car Operating Systems

_Captured: 2016-11-19 at 09:46 from [humanizing.tech](https://humanizing.tech/the-new-battleground-car-operating-systems-609592e07a31?source=userActivityShare-c79006fee040-1479545197)_

#### I. Overview

Apple has been pushing CarPlay as a Trojan Horse into our daily driver for a few years now. Android Auto has been doing the same and recently released a mobile app to have the functionality in your hand everywhere you go, not just during your drive. Samsung, this week, spent $8B on acquiring Harman, an infotainment company with major relationships across the entire automotive spectrum. BlackBerry announced a few weeks back that their QNX system will power much of Ford's infotainment and OS needs. And finally, Tesla is on v8 of their electric car's operating system, complete with a big screen TV in the front dash powering everything from sun roof, climate, radio, maps, smart phone interaction and yes, even self-driving.

What does this all add up to? Simply put, the battleground for every car's operating system.

Much like the competitiveness rages between the Mac and Windows OS on desktops, and iOS and Android OS continued that rage on mobile, the future battleground will be owning the in-car experience as it moves from a traditionally mechanical machine to a software-laden one.

#### II. A Note on Hardware

Whomever owns the operating system, controls the entire ecosystem. Incidentally, it's also why Apple and Google are investing in self-driving cars, including hardware. The hard part with car hardware, however, is that it's not as "simple" as a mobile phone.

As Tesla has shown with their own closed ecosystem (the new Apple?), it requires you to build machines that build machines and they're only making about 100,000 electric cars annually. Tesla can't build cars fast enough to keep up with supply. But another revenue source for them could be to license their currently v8 operating system and infotainment system and self-driving system to the other car manufacturers. My guess is they won't, but it's an interesting thought experiment.

But it also means a variety of new sensors like ultrasonic sonar, manometers, highly precise GPS units with centimeter precision (called GNNS), and high resolution video cameras for object detection. As a result, the bandwidth required from CDNs and cellular services is going to continue to explode (along with the other types of [streaming video](https://humanizing.tech/tagged/video)).

The CEO of [Intel](https://medium.com/u/fb610dd2569b) announced yesterday at the LA Auto Show argued that we will be pushing 4,000 GBs of data every day through this new world of connected car hardware.

If you're streaming all of that, then you need reliable 5G connection speeds and enough bandwidth to handle it all. To put the mathematical cost into perspective, say your CDN price per GB is $0.01 (likely less with a bandwidth commitment to Akamai), you're looking at:

4,000 GB per day * $0.01 per GB * 365 days per year = $14,600.

Are you really going to pay an additional $15K for your car to be connected on top of the $10K cost of self-driving hardware and software (per Tesla's latest pricing)? Granted, not all of this is going to be submitted to the cloud in the short-term due to cost, but in the future you can bet it all will be.

No, you're not.

That's why Big Auto is investing very big bucks into very high end, highly connected cars for autonomous ride-sharing. You won't buy one of these $250,000 cars (as much as a Ferrari). You will pay a subscription fee to rent it for a period of time.

Maybe to get back all that wasted time you spend on your daily commute.

#### III. How Future Car OS's Will Work

I've spent time imagining what the future of the car ecosystem will look like and have [alluded to my thoughts previously](https://humanizing.tech/ar-apps-are-interactive-live-video-33882e91dfe0#.y525w8sre) as they relate to live video. I will restate them here for perpetuity's sake.

The software stack of the future will look like something like this from the top down:

> _User Interface:_ CarPlay, Android Auto, etc as the InfoTainment system, which is really just H.264 live video streamed from the phone mimicking a real app installed on the phone.

> _Self-Driving App(s):_ these will have to be certified by the NHTSA. The deep learning approaches currently employed by the industry isn't enough to get to true Level 5 self-driving because they'll never capture enough training data to handle every [Black Swan](https://en.wikipedia.org/wiki/Black_swan_theory) event. We need a different approach that handles chaos. It's highly likely that the consumer will choose which app to use from the various providers that have passed approval. Maybe one auto manufacturer will choose one over the other and force that app, but maybe not. Either way, building a brand with consumer trust will become incredibly important.

> _Operating System:_ like BlackBerry's QNX, which Ford is using, but also Apple's CarOS and Android Auto extended to full OS. Currently folks are just running a fork of Ubuntu or the [Robot Operating System](http://www.ros.org) (pretty scary right, that your entire life is in the hands of some open source robotics software?).

> _Normal Car Mechanical Parts: _all the moving parts like axles, wheels, etc.

What I believe is you will have one of two things happen:

  1. Every car manufacturer has their own independent operating system that attempts to continue their systems integrator mindset. It will require every software vendor who comes along to integrate with a myriad of different OSs complete with confidentiality agreements and ideally non-competes. Oh boy, you can see the trouble brewing already.
  2. They will use a standard operating system across different brands and manufacturers like Ford, GM, BMW, VW, Mercedes, etc. It's already happening with the open-source [ROS (Robot Operating System)](http://www.ros.org). Of course that's not a great solution either due to quality concerns. And there's where big tech like Apple and Google can really make a dent.

That's why I see these 5 major players going after the OS in cars. It allows software developers an easy platform to integrate with, that they're already known for. iOS devs use Swift. Android devs use Java. And all the machine learning folk use Python, etcetera.

Interestingly, Tesla is in the best position to use their strategic advantage of developing the entire hardware to software package. License their OS and it becomes a sharp wedge into a consumer relationship even while current people are driving other branded cars.

iTunes was a glass of ice water in hell for Windows users. It was also the Trojan Horse to steal Windows users over to the Mac.

Tesla could employ the same strategy. Don't count it out.

But the real market leader here is BlackBerry's QNX. There's not much chance of anyone cutting them out as they're already working in about 40 automakers.

#### IV. The World Is Changing

After speaking with a number of folks around the industry, from media to investors to big auto to OEM suppliers to software product people and academic researchers, I have a pretty decent sense of where the world is headed.

**Today**

  * People lease their own cars
  * People drive themselves
  * People use Uber/Lyft sometimes
  * People use CarPlay/Android Auto sometimes

**Tomorrow**

  * People "subscribe" for a monthly fee to a class of car. Leases already kind of work this way but you don't get to pick like you currently do with Uber.
  * They are self-driven for their commute. 1 hour each way, 5 days per week is about 500 hours per year. That's about 20 days or almost an entire month working of your free time back you didn't have before. That's where consumer willingness to pay comes in.
  * People install their preferred self-driving app (trust). See above for more.
  * Everything is tied to the user's phone (infotainment). See above for more.

Here's a weird thought experiment. Instead of every auto manufacturer having their own operating system, what if instead they are run off a user's phone that he or she brings with them?

So, if you have an iPhone, your car runs Apple's CarOS. If you have an Android, your car runs Android Auto. But if you have a Samsung Galaxy, then it runs Samsung's new OS?

I think this approach breaks down, however, because what OS does the self-driving car run when nobody's in it? It's too fundamental to the car. Which brings us to the alternative strategy Samsung is employing.

#### V. Samsung's Alternative Strategy

Samsung is different from Apple and Google. Instead of trying to build an operating system, self-driving, and hardware from scratch, they acquire the various pieces they need, including the industry relationship and spend their time and effort on integrating cultures, operations and people.

It's a faster way into the market, but means less quality due to the fragmented nature of products and people that have to come together in order to produce a unified customer experience.

> [Samsung Electronics](https://my.pitchbook.com/n/16601.2179971.926632) (KRX: 005930) has agreed to acquire connected products manufacturer [Harman International Industries](https://my.pitchbook.com/n/16601.2179972.926632) (NYSE: HAR) for $8 billion, a move that gives Samsung a significant presence in the field of automotive electronics. Like its rival [Apple](https://my.pitchbook.com/n/16601.2179973.926632), Samsung has never been much of one to use M&A to fuel growth. But that could all change now that the automotive space has spawned several significant deals as chipmakers pivot away from flagging smartphone sales and into the broader IoT market. Most notably, October ended with [Qualcomm](https://my.pitchbook.com/n/16601.2179974.926632) (NASDAQ: QCOM) agreeing to buy [NXP Semiconductors](https://my.pitchbook.com/n/16601.2179975.926632) (NASDAQ: NXPI) for $38 billion, **[citing a desire to enter the automotive market that NXP dominates**](https://my.pitchbook.com/n/16601.2179976.926632) as part of its rationale.

> Samsung has offered $112 per share in cash for Harman, a 28% premium to the target company's closing price on Friday -- and the price may have been boosted by Harman's acquisition strategy. Purchases since the start of last year include [Symphony Teleca](https://my.pitchbook.com/n/16601.2179977.926632) (tech services), [Red Bend](https://my.pitchbook.com/n/16601.2179978.926632)(software management for connected devices) and [TowerSec](https://my.pitchbook.com/n/16601.2179979.926632) (automotive cybersecurity). Samsung shares traded down 2.8% on the news, with Harman closing up 25% at $109.72. The deal is expected to close in 2017.

As you can see, it seems they're employing all the pieces necessary to begin building their own car operating system. The next step would be the business development relationships necessary to put it into the cars. Of course, that's why the Harman acquisition was so critical. Those relationships are already in place.

#### VI. Future Business Model for Self-Driving

I put together a quick little spreadsheet to show how subscribing to a commuting car service will work and broke down the price for hardware, software and how much it will cost for a [Tier 1 self-driving app](http://prome.ai).

I believe that consumers will want to have a relationship with their self-driving app of choice and it will come down to trust, especially if the user is the one to choose the app through the car's infotainment system (e.g., install this self-driving app through Apple's CarOS).

So the next time you're in your self-driving car, maybe you can just speak up and just tell the car which song you want to play and also tell it which self-driving app you want to use. Me? I'll stick with Big Willy.

#### Read More
