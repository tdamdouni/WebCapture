# Microservices: The Good, the Bad, and the Ugly

_Captured: 2018-04-14 at 07:16 from [dzone.com](https://dzone.com/articles/microservices-the-good-the-bad-and-the-ugly?edition=374197&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-04-13)_

[Sysdig](https://dzone.com/go?i=278430&u=https%3A%2F%2Fsysdig.com%2F%3FUTM_Source%3DContent_Syndication%26UTM_SFDC_Campaign%3D701f1000001cgkm%26UTM_Offer%3DSysdig-website%26UTM_Campaign%3D%26UTM_Medium%3Dpre-roll%26UTM_Content%3DDzone-microservices-zone%26UTM_Term%3D%26UTM_Creativeid%3D) is the container intelligence company. The only unified platform for monitoring, security, and troubleshooting in a microservices-friendly architecture.

Microservices have been bandied about in the past couple of years, but what are the real advantages and disadvantages of implementing and running them? Like any service architecture, there are pros and cons, benefits and tradeoffs. So, how do microservices compare against other application architectures like monoliths, service-oriented architecture (SOA), and functions? We're here to break it all down and shed some light on why the developer and DevOps community is pushing back against the microservices-is-the-solution-for-everything mentality in 2018.

## **What Is a Microservice?**

It is beyond the scope of this article to provide an exhaustive definition of a microservice. That said, let me go ahead and give my best attempt at a simple definition: "Microservices are individual and distinct components of a software program that exist to fulfill the smallest possible function of an application while still remaining independent and serviceable. From a practical standpoint, each service is a small, highly defined, and discrete piece of code that is responsible for one task (e.g., end-user authorization)."

## The Good

Microservices, when implemented correctly, can greatly improve the reliability and scalability of software. One of the most compelling aspects of microservices, when compared against monoliths, for example, is that a flaw or bug in one service should not affect the ability of other services to carry on working as intended. Notice that I caveated it by saying should not, but more on that later.

Microservices have a number of advantages, such as…

  * Able to scale independently
  * Fault-tolerant
  * Can be swapped out or easily rewritten
  * Framework and language agnostic
  * Adhere to the KISS principle
  * 12-factor compatible

What this means from a practical standpoint is that an application should:

  1. Scale easily and in a highly efficient way.
  2. Have no single point of failure.
  3. Be retired, refactored, or rewritten without compromising the integrity of the entire application.
  4. Be written in many languages and frameworks to suit the requirement of each service.
  5. Be simple and discrete.
  6. Easily meet requirements for modern PaaS and SaaS environments.

Many well-known and well-respected engineering teams from companies like Amazon, Netflix, eBay, and others have adopted microservices. It makes sense, then, that every developer or new software startup should naturally ponder whether to embrace a microservice architecture. If we're all honest about this, who doesn't admire the engineering prowess of these forward-thinking companies? I know this nerd does.

If it's good enough for Netflix, then surely it must be good enough for us. Right? Right? Well maybe, and maybe not. As we'll see, the "why not us" mentality should be left at the door. Maybe it does make sense for your application or company, and maybe it doesn't.

## The Bad

Just because something is trending in the industry, does not necessarily mean it's a viable solution for each use case. One of the principal disadvantages is all the hype surrounding microservices. There are other drawbacks, too. Some of the more superficial discomforts with microservices include:

  * More complexity, thanks to the expertise required to maintain a microservice-based application with all its moving parts.
  * If the application doesn't need to scale or isn't cloud-based, microservice-based architecture may not provide any meaningful benefits.
  * No greenfield options because microservices need to connect to existing (and possibly monolithic) systems.
  * Smaller units of functionality communicating via APIs necessitate more robust methods of testing as well as buy-in from the entire engineering team.
  * The need for increased team management and communication to ensure everyone, not just certain engineers, understand each service and the system as a whole.

## The Ugly

And that's just touching the surface of the disadvantages. Just because Netflix or some young hot Silicon Valley darling has embraced microservices does not mean it is the correct architectural style for all applications. Application architecture should be based not just on what's in vogue at the moment but also on efficacy and fit. When it comes to it, the truly intrinsic pain points that microservices come hand-in-hand with are…

  * Dealing with distributed systems' development, deployment, and operational management overheads can be expensive requiring a high initial investment to run.
  * Choosing a different tech stack for different components leads to non-uniform application design and architecture.
  * Endless documentation in the form of updated schemas and interface documents for every individual component app.
  * The costs of maintenance, operational costs, and production monitoring are much higher, and the latter also suffers from a dearth of available tools.
  * Automation testing becomes difficult when each microservice component is running on a different runtime environment.
  * Increased resource and memory consumption from all the independently running components which need their own runtime containers with more memory and CPU.
  * Microservices, when implemented incorrectly, can make poorly written applications even more dysfunctional.

Microservices are a true double-edged sword for any application architecture consideration. If you're thinking of migrating, block out the noise surrounding all the hype and carry out your own due diligence to see if microservices is the right solution for your application's needs.

[Download our white paper:](https://dzone.com/go?i=278431&u=https%3A%2F%2Fgo.sysdig.com%2FSysdig-Architecture%3FUTM_Source%3DContent_Syndication%26UTM_SFDC_Campaign%3D701f1000001cgkm%26UTM_Offer%3Dsysdig-architecture%26UTM_Campaign%3D%26UTM_Medium%3Dtext-link%26UTM_Content%3DDzone-microservices-zone%26UTM_Term%3D%26UTM_Creativeid%3D) The Architecture of the Sysdig Container Intelligence Platform. Built for microservices and containers for monitoring, security, troubleshooting
