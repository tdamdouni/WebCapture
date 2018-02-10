# The Microservices Paradox

_Captured: 2018-02-05 at 21:08 from [dzone.com](https://dzone.com/articles/the-microservices-paradox?edition=358117&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-05)_

Learn the Benefits and Principles of [Microservices Architecture for the Enterprise](https://dzone.com/go?i=274453&u=http%3A%2F%2Ftransform.ca.com%2FAPI-microservice-architecture-for-the-enterprise.html%3Fcid%3DNA-DSP-API-AEL-000195-00001674-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dmicroservices_api_acquire%26utm_content%3Dna_eb1-microservice-arch-ent-ddc-preroll%26mrm%3D)

Gianna has joined Avidoo Inc., a productivity platform, as a senior software engineer. In a kick-off meeting with the rest of her team, she brings up the subject of [microservices](https://xebialabs.com/solutions/microservices/) and whether the team has adopted them in any way. She immediately gets a strong reaction.

"We have tried adopting microservices, but they don't work," Byron offers.

"It became a terrible mess!" Kary adds.

Gianna blinked her eyes three times expecting some kind of elaboration, but none followed. After an uncomfortable silence, Gianna asks: "So what happened?"

"At first it was great. Every time we were asked to create something new, we had the opportunity to add a service and use whatever languages and frameworks we wanted to experiment with. We exposed REST APIs on systems it needed to collaborate with or worked on their databases directly. But after a while, things started to break more and more often, and development slowed to a crawl."

Gianna sighs. It sounds to her like her team had been building a distributed [monolith](https://blog.xebialabs.com/2017/01/17/the-7-spices-of-a-continuous-delivery-pipeline/), while what they had meant to build were microservices.

## Distributed Monoliths and Other Monstrosities

What Gianna has run into at Avidoo Inc., which is, of course, a fictional company, is unfortunately all too common. Drawn by the idea that microservices are a panacea, IT managers and engineers tend to skip identifying what advantages are a good fit with their organization.

People forget that there is no such thing as a free lunch. As well as advantages, well-built microservices architectures have tradeoffs. There are no "wrong" microservices, only microservices that do not deliver the advantages they were built for or pose unacceptable risks through their disadvantages.

## Advantages of Using Microservices

Choosing to adopt microservices should start with deciding which of its advantages are a good fit for your organization. Below are some of those advantages.

### Increased Team Autonomy

Many companies organize teams around their member's discipline or components. When creating real customer value, this asks for a lot of coordination between teams and makes it next to impossible to work on one feature in parallel.

![Image title](https://dzone.com/storage/temp/8026740-img1.png)

> _Creating value with single-disciplinary teams._

Microservices facilitate autonomy by covering one feature. Therefore one team can fully own it instead of multiple teams. This helps reduce cross-team coordination.

![Image title](https://dzone.com/storage/temp/8026745-img2.png)

> _Creating value with a multi-disciplinary team._

## Greater Fault Tolerance

Where there is autonomy of a team there should also be the autonomy of a feature. Features often depend on one another. In most environments, communication is on-demand and pull-based, often over a REST interface. When this interaction is mission critical, the service depending on this communication either has to have a sensible fall-back or it will, in turn, fail. This unhealthy pattern is often illustrated by system health checks that fail when one of its dependencies is unhealthy. Aside from causing deployment order to be difficult to manage, it illustrates hard system dependency.

![Image title](https://dzone.com/storage/temp/8026749-img3-e1500310390319.png)

> _Run-time dependencies._

Using the right software architectures like event sourcing, possibly complemented by CQRS, it is possible to erase run-time dependency between most features completely. This is mainly due to the transition from a pull-based system to a push-based one.

## Granular Software Lifecycle Management

A common wish is to replace a certain feature within an application with a shiny new one. This is because, either the requirements have diverged so far as to warrant a rewrite or development speed has been run into the ground by technical debt contracted by strenuous time-to-market demands. It might be naively thought that these should be replaceable as fast as it took to write them in the first place, but this mostly proves to be untrue. All too often replacing one feature results in having to make changes to many systems it depends on or vice versa.

![Image title](https://dzone.com/storage/temp/8026758-img4.png)

> _Lack of granular software lifecycle management._

By highly regulating inter-system communications, it is possible to switch out one or more features completely without having to touch any of its dependent systems.

## Flexible Technology Choices

Admittedly this is a tricky one. Onboarding and training people to switch to a common technology helps with inter-team mobility, driven by demand or personal interest. But reshuffling staff from several departments using different technology stacks that, frankly, they are quite religious about, can result in mass walk-outs.

![Image title](https://dzone.com/storage/temp/8026765-img5.png)

> _Forcing technology choices._

As long as the technologies can be integrated into your automated testing and deployment workflow, a team's technology choices can remain their own. Why change a winning team that's united around their love for everything C# as long as they produce an artifact that adheres to your platform's monitoring, logging and communication rules?

## So Why Do They Fail?

There isn't one way to do microservices. Adopting microservices doesn't fail because people don't know how to do them but rather because they don't remember what problems they were solving in the first place. As with any other decision, adopting certain aspects of microservices comes with a cost. Software architects tend to forget that they shouldn't be helping their employer adopt microservices but should help them solve real business problems. Properly weighing the costs and benefits of these aspects against an organization's need is of vital importance. None the less, there is a default set of choices that can form a sensible inception from which to start this bold adventure.

Microservices for the Enterprise eBook: [Get Your Copy Here](https://dzone.com/go?i=274454&u=http%3A%2F%2Ftransform.ca.com%2FAPI-microservice-architecture-for-the-enterprise.html%3Fcid%3DNA-DSP-API-AEL-000195-00001674-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dmicroservices_api_acquire%26utm_content%3Dna_eb2-microservice-arch-ent-ddc-postroll%26mrm%3D)
