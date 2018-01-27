# We Need to Talk, Says One Microservice to Another

_Captured: 2017-12-15 at 03:44 from [dzone.com](https://dzone.com/articles/we-need-to-talk-says-one-service-to-another?edition=342136&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202017-12-14)_

Share, secure, distribute, control, and monetize your APIs with the platform built with performance, time-to-value, and growth in mind. [Free 90 day trial](https://dzone.com/go?i=257321&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Ftechnologies%2Fjboss-middleware%2F3scale%2Fget-started%3Fsc_cid%3D701f2000000tnttAAA) 3Scale by Red Hat

"But how?" asks the other service!

Ever wondered how we communicate? One would not believe how complex and multi-step process it is. It involves some very complex terms like perception, encoding, medium, and decoding. Let us take a look at a diagram explaining this:

![Process of Communication](https://dzone.com/storage/temp/7315650-process-of-communication.png)

> _Process of Communication_

So how does this relate to microservices? Communication between two services is not much different. It follows through a process very similar to this; in fact, it can be explained with the exact same steps! Consider two services a ShippingService written in Java requesting the preferred address of a user identified by Id, from a UserAddressService over REST a call:

![Process of Microservice Communication](https://dzone.com/storage/temp/7315656-process-of-microservice-communication.png)

> _Process of Microservice Communication_

Okay, so human communication can be used as an analogy to understand inter-service communication in a microservices stack. So what? Basically, it tells us that the scenarios of failure can be the same, and we can understand microservice communication by relating it to human communication.

## Why

Before we deep dive, we should quickly consider why it matters at all in microservices. It is basically the difference between inter-process and intra-process communication. Consider this: intra-process, meaning communication between components of a single process, is like talking to oneself. You understand yourself (well, usually!), at least, there is a whole lot less "miscommunication" when talking to oneself. This is the kind that happens in monoliths, and why it was not so much of an issue until we started working on microservices, which have inter-process communication.

To relate to this, consider talking to people instead, known or unknown (API, authentication, etc), people of a different race, origin, nationality (perception), at a distance or near you (response time), on a phone versus in person (medium/network, protocol), direct versus indirect, or at a different time (whoa, yeah! for example, sync vs. async, like leaving a note), speaking an unknown language (encoding-decoding, JSON/XML/binary like gRPC), and of a different background or upbringing (perception again) and in different mental states (well, stateless vs stateful services), telling them a secret or casual gossip (secure vs. insecure). Now you know why working in teams is so difficult, and so is microservices!

## Types

Let us break down all the phases and see the types of potential problems. This is not standard classification, but I have found this method effective when understanding the issues with analogies.

  1. **Encoding:** Failure to encode the object correctly by missing attributes or encoding with a different name. For example, frameworks in Java allow for choosing different attribute names in JSON/XML format; these are specified as strings and there is no real validation on these other than tests. Also, how do we ensure both services are using the same message structure? This can, in part, be ensured by sharing a common object model library. But then, this goes against the principle of knowing models by views; not every service needs to know what all the attributes of a Customer object are! You might as well use queues for communication, then.
  2. **Sending the message:** This includes the whole set of issues which can occur due to not sending the message on the correct protocol, address, port or path- all address related issues. Integration testing cannot always help here, as some of these depend on the production infrastructure, as well.
  3. **Decoding:** This process is the reverse of encoding and comes with all the same issues.
  4. **Perception:** These are some of the serious issues which you tend to miss even in unit and integration tests, and can be caught only in later phases, when working against live services. If you encounter these, you can most certainly assume that apart from inter-service, you also have some team communication issues.
  5. **Feedback:** One of the most important steps in communication is the feedback- the acknowledgment of receipt of the message. There can be plenty of causes for a service to not respond, including all of the issues discussed above, and adding potential networking and issues related to the health of the service.
  6. **Cascading failures:** A very serious situation which is merely an outcome of failure to identify the issues in service communication and safeguarding against them.

Now that we are acquainted with the terms, I want to tell you a couple of stories: really scary, real stories.

## Case Study 1

I know of a Value Added Services (VAS) company (you know the services you never want yet your carriers charge you for? Yeah, those). This company was one of the few trying to build a useful service you may want to pay for, trying to play fair and by the rules, even at a revenue loss. The VAS industry suffers from a considerable frequency of fraud, so it was said that the biggest crime is charging your users twice. Such incidents would be immediately flagged as fraud by the carriers and the service would be banned.

We had a call flow where a "Billing Service" makes a call to a "Carrier Integration Service" for charging which, in turn, makes a call to an external-internal Notification Service (a shared service hosted by a different unit) to send a notification to user, after firing the charging request to the carrier. It worked fine for years, until one day this external-internal service suddenly slowed down, timing out all the calls from the Carrier Integration Service, which in turn caused a timeout on the Billing Service, which treated it as a failure and "retried" the billing call. The issue got flagged in minutes, but hundreds of users were charged multiple times that day before the team could respond.

![Case Study 1 pictorial depiction](https://dzone.com/storage/temp/7315659-multiplecharging-block-diagram.png)

> _Case Study 1 pictorial depiction_

There were a whole lot of things that went wrong here. There were feedback issues, which likely occurred due to a network issue, giving rise to perception issues and finally causing a cascade. The worst thing, though, was the cascade.

## Case Study 2

Another such story, not so grave, was when the Billing Service sent a request for partial charging, but the Carrier Integration Service denied honoring it. Both services used enums to identify the keyword used, both had integration tests, and all worked fine. It was only after the services were tested against working instances of one another, in a pre-prod environment on a crunch day, that it was identified. The issue was stupidly simple; both services used a different value for the constant! Again, of a whole lot of things that went wrong here, most important was the perception issue caused due to the miscommunication between the teams working on these two services.

## The Solutions

Discussing every step identified to fix the case studies we saw will be a story in itself, we shall discuss the first solutions applied to the most glaring causes in both cases. For the cascade, we made it a point that every service would implement [Hystrix](https://github.com/Netflix/Hystrix) for every single inter-service communication call. Hystrix is a circuit breaker, meaning it wraps a chunk of logic (say, a method) and on exception, it can flag, throttle, block, and bypass the method in question. The idea is to wrap the calls to external services, aka dependencies, and when something goes wrong give them time to recover by bypassing calls and safeguard the sender service from cascading the issue. We had Hystrix in some services, but some teams had argued that it is an unnecessary complication for internal services and services that have been working fine. Well, that was before the incident. Everyone just jumped on it as the first change once we recovered from the impact. In my view, a circuit breaker is a tool microservices should never be built without. As an additional safety net, we also ensured that the Carrier Integration Service builds a temporary cache of all the users it processed and validate against it before it fired any call (not every solution to any problem is purely technical!).

For the perception issue, we needed to ensure that post encode-decode the receiver understands the same thing as the sender meant. We had hosted stubs against which we tested the services in automation testing phase. These stubs were dumb services implementing the same API as the service they stubbed. These were developed by whichever team needed them- essentially, the Billing Service team would never develop the stub for the Billing Service- which caused the discrepancy in the stub and actual service behavior. This had to change. The team developing Billing Service was to be responsible for developing the stubs for Billing Service and the team for Carrier Integration Service for its service stubs. This way, the stubs always perceived the same as the actual service did.

Now, how do we address intra-team communication problems; anyone?

Discover how you can [achielve enterpriese agility](https://dzone.com/go?i=257322&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Fresources%2F3scale-enterprise-agility-with-microservices-api-management-whitepaper%3Fsc_cid%3D701f2000000tntUAAQ) with microservices and API management
