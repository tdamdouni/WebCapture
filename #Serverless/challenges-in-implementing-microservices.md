# Challenges in Implementing Microservices

_Captured: 2018-09-18 at 07:35 from [dzone.com](https://dzone.com/articles/challenges-in-implementing-microservices?edition=397198&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-09-17)_

The new [Gartner Critical Capabilities report](https://dzone.com/go?i=299477&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921) explains how APIs and microservices enable digital leaders to deliver better B2B, open banking and mobile projects.

We live in a world of microservices. "Monolith to microservices" is a phrase we hear from more than 70% of technology leaders today. The benefits are well-documented: increased resilience, improved scalability, faster time to market. Like most transformational trends, implementing microservices poses its own challenges. It is imperative that these challenges are well understood, or be prepared for your project to never see the light of day, or finish it to only see that many of the foreseen benefits are not being achieved.

Here are some of the top challenges that organizations face in their microservices journey:

![](https://lh4.googleusercontent.com/IkHh-oiAWb7GrxHtEruGoQKEl_RncxHVYpcVF_4j1RFcaca_eJ5UMKSEl4pawzP9XtcvmkEuX43RIOcw3b8zBJkQfK8QmSvbE5LNVsQzJEI6LWePYoiN6xTvCTBwLeMWams2FCy_)

## **Managing Microservices**

As the number of microservices increases, managing them gets more challenging. It is important that management is planned before or while microservices are being built. While the modularity helps, things can very quickly get out of hand if not managed well. Many engineering leaders have stated that the mismanagement of these services is as much a problem as problems faced during the initial stages of the transformation from monolithic applications.

Developing microservices management tooling on your own, although a valid option, can be complex and cumbersome. We recommend looking to acquire a platform whose capabilities include microservices management.

## **Monitoring**

The traditional forms of monitoring and diagnostics will not align well with microservices since you have multiple services making up the same functionality previously supported by a single application. When a problem arises in the application, finding the root cause can be challenging if you do not have a means of monitoring and tracking the path a specific request took, like how many and which microservices were traversed for a specific request coming from a user interface.

We have seen customers who struggle to analyze the chain of communication across these services and where issues were potentially introduced. [This](https://www.youtube.com/watch?v=smEuX-Hq6RI) video is a good watch on this topic.

## **Embracing DevOps Culture**

Separate teams need agility, autonomy, and continuous delivery to be able to deliver initial releases and subsequent iterative changes. A lack of DevOps culture can bottle up releases and impact the overall time to market and the response to business requests and issues.

## **Fault Tolerance**

It is important that individual services do not bring down the overall system. Fault tolerance at the service level, and more importantly, at the overall solution level, is critical. Given the complexity of a microservices environment and the complex dependency chains, failure is inevitable. Microservices need to be able to withstand both internal and external failures. Robust resiliency testing is key to successful issue preparedness.

## **Testing**

Testing is much more complex in a microservices environment due to the different services, their integration, and interdependencies. The team members responsible for quality assurance need to be knowledgeable on the order and channels of communications between services to have full coverage in their test cases. The asynchronous aspect of microservices also makes it harder to test in lower environments. Indistinct behaviors from microservices are harder to predict and validate.

More details on microservice testing challenges can be found [here](http://www.alohatechnology.com/blog/testing-challenges-in-a-microservices-environment.html) and in [this insightful post](https://bit.ly/2meWzaF).

## Design With Failure in Mind

While this is counter-intuitive to many, expecting failure scenarios and building a robust set of microservices is imperative to a successful implementation. When more failure situations are predicted during design, the more exception handling mechanisms will be built and seamless resolution of issues will be handled better. This is easier said than done.

## **Cyclic Dependencies**

![](https://lh6.googleusercontent.com/ZhCvtGNoBKObGUCivkYqNv8mQO1ft6K2-YKXT3f2TdglJWH6PvDySR_mN8K57DabaZAYAUUoNzWpOQ8M-6MFB13T9SmN8mMEEnQ24X5xPsTzh5hMrLNcFPHVquVk6Riln8ADc-pZ)

> _Source: queue.acm.org._

Dependency management across different services and their functionality is very important and cyclic dependencies can be a headache if not identified and resolved promptly. In microservice architecture, you're even more vulnerable to errors coming from dependency issues. Decisions made around upgrades on related services with these dependencies are critical. [This post](https://queue.acm.org/detail.cfm?id=3277541) discusses tracking and controlling dependencies in detail.

Good luck with your microservices journey!

The new [Gartner Critical Capabilities for Full Lifecycle API Management report ](https://dzone.com/go?i=299478&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921) shows how CA Technologies helps digital leaders with their B2B, open banking, and mobile initiatives. [Get your copy from CA Technologies.](https://dzone.com/go?i=299478&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921)
