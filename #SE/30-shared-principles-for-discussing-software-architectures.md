# 30 Shared Principles for Discussing Software Architectures

_Captured: 2018-08-10 at 06:30 from [dzone.com](https://dzone.com/articles/30-shared-principles-for-discussing-software-archi-1?edition=387206&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-09)_

The new [Gartner Critical Capabilities report](https://dzone.com/go?i=299477&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921) explains how APIs and microservices enable digital leaders to deliver better B2B, open banking and mobile projects.

Imagine a fly-by architecture review. An architect walks in, looks over, glosses over, though his binoculars. He provides comments that are often too generic or out of context. Comments are often met with deafening silence or winding arguments. They rarely help anybody, if ever. Every programmer dreads it; every architect dreads it, too.

It is said that as a software architect, one should think like a Gardner rather than a commander. The former shapes, curates, and removes weed while the latter defines and dictates. An architect should curate rather than dictate, shape rather than define, and incite discussion than labeling. But, how to make it work?

At WSO2, I have done architecture reviews for more than eight years. WSO2 has had an extensive portfolio of products including [WSO2 ESB](https://wso2.com/integration), [WSO2 API Manager](https://wso2.com/api-management/), and [WSO2 SP](https://wso2.com/analytics) that are well known. In the last eight years, we have debated, designed, improved and redesigned many products and features.

A crucial part of our design process is that architecture is not done by architects. We do not have a set of architects who dictate architecture blueprints while others go and implement it. In contrast, the design is done by the team who will write the code. Architects fix, complain, curate, and improve the design. We have an architecture team, but they are guides and gatekeepers, not the dictators.

Gregor Hohpe captures this idea beautifully in [this talk](https://www.youtube.com/watch?v=qVyt3qQ_7TA\[/embed).

It is true. In the short term, dictating an architecture is faster and may even be cheaper. However, in the long run, we build better teams by letting them think for themselves, letting them evolve the architecture, and sometimes letting them make their own mistakes. When we focus on the team, they get better with time. Execution is much easier as architecture is the team's ideas in the first place.

Architecture reviews, however, have their pitfalls also. Paul ([@pzfreo](http://twitter.com/pzfreo)) used to call this drive by architecture where Architects walk in, listen, give comments, and move on. As an architect, It is easier to look, complain, and take the design apart. If you are not careful, you might leave the team bewildered and not sure what is the right thing to do.

We address this problem by having a list of shared architecture principals. Those are principles that everyone agrees. Architects give feedback by saying this is not good due to principal X. Principles guides us and keeps our discussions rooted. They also avoid philosophical battles that go on forever. Finally, if the designer has never heard of the Principle, it is easy for him to learn.

Following are some of those principals. Some are well-known, while some others, we picked up the hard way.

## Basic

**Principle 1: **[KISS (Keep it simple, stupid)](https://people.apache.org/~fhanik/kiss.html) and "Everything should be made as simple as possible, but not simpler." The idea is to use the simplest solution that does the job.

**Principle 2: **[YAGNI (_You aren't gonna need it)_](http://martinfowler.com/bliki/Yagni.html)_ -- _do not build it until it is needed.

**Principle 3:** Crawl, walk, run. In other words, make it work, make it better, make it great. Do Iterative Development -- do agile, iterative development. For every feature, create milestones (2 weeks maximum) and iterate.

**Principle 4: **The only way to build stable, high-quality products is via automated tests. Be creative with automated tests; everything can be automated! Think about this when you design.

**Principle 5:** Always think Return for Investment (ROI) and invest most attention on making the most impact.

**Principle 6:** Know your users and balance your efforts accordingly. For most products, there will be thousands of end users, 20 developers that extend the product, and 100 DevOp personals who set it up. For example, do not spend months building a UI forDevOp who is unlikely use it anyway ( they like scripts! instead). This is a special case of Principle 5.

**Principle 7:** Design and test features as independently as possible. Think about this when you design. It will save a lot of trouble in the long run, as otherwise, you can't test the system until everything is built. Also, with this principle, your releases will be smoother.

**Principle 8:** Look out for "Google envy." We all like shiny designs. It is easy to bring features and solutions into your architecture that you will never need.

## Choosing Features

**Principle 9:** It is impossible to fully think through how users will use our product. So embrace the MVP (Minimal Viable Product). The idea is to figure out few use cases, only do features that support those, ship the product, and shape the future product based on feedback and experience.

**Principle 10:** Do as few features as possible; when in doubt, leave it out. Many features are never used; maybe you leave an extension point instead.

**Principle 11:** Wait for someone to ask for it (e.g. for features that are not deal-breakers, wait until it is needed).

**Principle 12:** Have the courage to fight the customer if features he asks for mess up the big picture. Find out the bigger picture and try to find another way to handle the problem. Remember Henry Ford's quote: "If I had asked people what they wanted, they would have said 'faster horses.'" Also, remember you are the expert. You are supposed to lead. It is the leader's job to do what is right, not what is popular. Users will thank you later.

## Server Design and Concurrency

**Principle 13: **Know how a server works, from the hardware to the operating system, up to your programming language. Optimizing the number of IO calls is the first guiding lights towards the best architecture.

**Principle 14:** Know Amdhal's law about synchronization. Mutable data shared between threads slows your program. Use concurrent data structures if you can, and use synchronization only if you must. Try to hold the locks for as little time as possible. If you plan to block while holding a lock, make sure you know what you are doing. If it can break, it will.

**Principle 15:** If your design is a none-blocking, event-driven architecture, never block threads or do IO from those threads. If you do, the system will be as slow as a mule.

## **Distributed Systems**

**Principle 16:** Stateless systems are scalable and straightforward. Know and use [Shared Nothing Architecture](https://en.wikipedia.org/wiki/Shared-nothing_architecture) whenever possible.

**Principle 17:** Exactly once message delivery, regardless of failures, is hard unless you control code in both the client and server. Try to design your systems to need less (use Principle 18). Know that most systems that promise exactly-once-delivery cut corners somewhere.

**Principle 18:** Implement operations as idempotent operations whenever possible. Then it is easy to recover, and you can live with at least once delivery.

**Principle 19:** Know the CAP Theorem. Scaling transactions is hard. Use compensation when possible. RDBMS-based transactions do not scale.

**Principle 20:** Distributed Consensus does not scale, nor do group communication, nor cluster-wide reliable messaging. Maximum node limit for either is about eight nodes in a good day.

**Principle 21:** You can never hide latency and failures in a distributed system (see [Fallacies of Distributed Computing Explained](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)).

## **User Experience**

**Principle 22:** Know your users and know their goals: is he a novice, expert, or casual user? How much does he know computer science? Geeks love extension points, developers like samples and scripts, normal people like UIs.

**Principle 23:** The best products do not need a manual. Its use is self-evident.

**Principle 24:** When you cannot decide between two choices, do not pass on the problem by making it a configuration option. You are making the life hard for users and solution architects. If they know even less about how the system works than you, how can they decide? The best option is finding a choice that works every time; the next best is automatically making the choice, and the third best is adding a configuration parameter and setting a reasonable default.

**Principle 25:** Always have sensible defaults for configurations.

**Principle 26:** Poorly designed configurations can create a lot of confusion. Always document a few example values for the configuration.

**Principle 27:** Ask configuration values in terms of things the user can answer off his head without making calculations to set the value (e.g., do not ask for the number of max cache entries -- instead ask for maximum memory that should be used for cache)

**Principle 28:** Throw an error if you see an unknown configuration. Never ignore it silently. Silent configuration errors are the source of many lost hours while debugging.

## Hard Problems

**Principle 29:** Dreaming up new languages is easy, but getting them right is very hard. Try not to do it unless the team can spend at least ten person-years on it. If you are still not sure, read [Five Questions about Language Design](http://www.paulgraham.com/langdes.html).

**Principle 30:** Composable drag and drop UIs are hard, do not start one unless the team ready to invest ten person-years into it.

Finally, let me talk about something that I have changed my mind about over time. In an ideal world, a platform must be composed of orthogonal components -- components where each handles one aspect (e.g., security, messaging, registry, mediation, analytics). A system built with such features would be optimal.

Unfortunately, it is hard to get to that state. It is even hard to stay there. It could be a mistake to enforce this rigidly, especially at the initial state of new features where simple features can cascade into big changes because we try to make everything orthogonal. Sometimes we find that the feature we added was not useful after all and then all the additional work is spent for nothing. Finally, if this lead to negotiations between multiple teams, the feature might never get done.

With hindsight, now I am willing to live with duplication when trying to remove it lead to significant complexity. The cure can be worse than the disease.

## Conclusion

As the architect, one should think like a gardener, who shapes, curates, and removes weeds rather than defining and building. You should curate rather than dictate, shape rather than define, and incite discussion than labeling.  
Although it might be cheaper and easier in the short term to dictate the architecture, in the long term, guiding and letting the team finding their way pays dividends.

If you are not careful, it is easier to do fly by architecture, where the designer only told his architecture is wrong, but not why it is wrong. One way to avoid this is to have a set of principles that are generally accepted, which become the anchor for discussion as well as learning path for budding architects.

We discussed some principles that helped me handle some of the challenges. Following is a summary.

![](https://cdn-images-1.medium.com/max/1600/1*sVbG7e6LmlaBohy6V0y0IQ.png)

> _If you can think of any others, I will be thrilled to hear about them via comments._

I hope this was useful. If you enjoyed this post you might also like _[Mastering the 4 Balancing Acts in Microservices Architecture](https://medium.com/systems-architectures/walking-the-microservices-path-towards-loose-coupling-few-pitfalls-4067bf5e497a)_ and _[Concurrency ideologies of Java, C#, C, C++, Go, and Rust](https://medium.freecodecamp.org/concurrency-ideologies-of-programming-languages-java-c-c-c-go-and-rust-bd4671d943f)_.

I write at <https://medium.com/@srinathperera>.

The new [Gartner Critical Capabilities for Full Lifecycle API Management report ](https://dzone.com/go?i=299478&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921) shows how CA Technologies helps digital leaders with their B2B, open banking, and mobile initiatives. [Get your copy from CA Technologies.](https://dzone.com/go?i=299478&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921)

Topics:

software architecture ,software design ,distributed systems ,ux ,distributed computing ,architecture ,programming
