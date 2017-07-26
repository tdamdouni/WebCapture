# Reinventing Performance Testing

_Captured: 2017-04-04 at 00:14 from [dzone.com](https://dzone.com/articles/reinventing-performance-testing?edition=286971&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-03)_

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

_[This article is featured in the new DZone Guide to Performance: Optimization & Monitoring. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/performance-optimization-and-monitoring)_

As the industry is changing with many modern trends, performance testing should change, too. A stereotypical, last-moment performance validation in a test lab using a record-play backload testing tool is no longer enough.

## Cloud

Cloud practically eliminated the lack of appropriate hardware as a reason for not doing load testing while also significantly decreasing the cost of large-scale tests. Cloud and cloud services significantly increased a number of options to configure the system under test and load generators. There are some advantages and disadvantage of each option. Depending on the specific goals and the systems to test, one deployment model may be preferred over another.

For example, to see the effect of a performance improvement (performance optimization), using an isolated lab environment may be a better option for detecting even small variations introduced by a change. For load testing the whole production environment end-to-end to make ensure the system will handle the load without any major issue, testing from the cloud or a service may be more appropriate. To create a production-like test environment without going bankrupt, moving everything to the cloud for periodical performance testing may be your best solution.

When conducting comprehensive performance testing, you'll probably need to combine several approaches. For example, you might use lab testing for performance optimization to get reproducible results and distributed, realistic outside testing to check real-life issues you can't simulate in the lab.

## Agile

Agile development eliminates the primary problem with traditional development: you need to have a working system before you may test it. Now, with agile development, we've had a major "shift left," allowing us to start testing early.

Theoretically, it should be rather straightforward -- every iteration you have a working system and know exactly where you stand with the system's performance. From the agile development side, the problem is that, unfortunately, it doesn't always work this way in practice. So, such notions as "hardening iterations" and "technical debt" get introduced. From the performance testing side, the problem is that if we need to test the product each iteration or build, the volume of work skyrockets.

Recommended remedies usually involve automation and making performance everyone's job. Automation here means not only using tools (in performance testing, we almost always use tools), but automating the whole process including setting up the environment, running tests, and reporting/analyzing results. Historically, performance test automation was almost non-existent as it's much more difficult than functional testing automation, for example. Setups are more complicated, results are complex (not just pass/fail) and not easily comparable, and changing interfaces is a major challenge -- especially when recording is used to create scripts.

While automation will take a significant role in the future, it only addresses one side of the challenge. Another side of the agile challenge is usually left unmentioned. The blessing of agile development, early testing, requires another mindset and another set of skills and tools. Performance testing of new systems is agile and exploratory in itself. Automation, together with further involvement of development, offloads performance engineers from routine tasks. But, testing early -- the biggest benefit being that it identifies problems early when the cost of fixing them is low -- does require research and analysis; it is not a routine activity and can't be easily formalized.

![Performance Guide](https://dzone.com/storage/temp/2579425-performanceguide.jpg)

> _Performance Guide_

_Find this article and much more in..._

**[DZone's Guide to Performance: Optimizaton and Monitoring](https://dzone.com/guides/performance-optimization-and-monitoring?oid=performanceplug)**

Including:

  * Survey findings from over 500 developer responses

  * Articles written by top Performance experts

  * "What Ails You Application" Infographic

  * Directory of performance optimization and monitoring tools

## Continuous Integration

Performance testing shouldn't just be an independent step of the software development life-cycle where testers get the system shortly before release. In agile development/DevOps environments, it should be interwoven with the whole development process. There are no easy answers here to fit every situation. While agile development/DevOps is becoming more and more mainstream, their integration with performance testing is just making its first steps.

What makes agile projects really different is the need to run a large number of tests repeatedly, resulting in the need for tools to support performance testing automation. The situation started to change recently as agile support became the main theme in load testing tools. Several tools recently announced integration with Continuous Integration Servers (such as Jenkins and Hudson). While initial integration may be minimal, it is definitely an important step toward real automation support.

It doesn't look like we'll have standard solutions here, as agile and DevOps approaches differ significantly and proper integration of performance testing can't be done without considering such factors as development and deployment processes, system, workload, and the ability to automate gathering and the analysis of results.

## New Architectures

Cloud seriously impacts system architectures, having a lot of performance-related consequences.

First, we have a shift to centrally managed systems. Software as a Service (SaaS) are basically centrally managed systems with multiple tenants/instances.

Second, to get the full advantage of cloud, such cloud-specific features as auto-scaling should be implemented. Auto-scaling is often presented as a panacea for performance problems, but, even if it is properly implemented, it just assigns a price tag for performance. It will allocate resources automatically, but you need to pay for them. Any performance improvement results in immediate savings.

Another major trend involves using multiple third-party components and services, which may be not easy to properly incorporate into testing. The answer to this challenge is service virtualization, which allows one to simulate real services during testing without actual access.

Cloud and virtualization triggered the appearance of dynamic, auto-scaling architectures, which significantly impact collecting and analyzing feedback. With dynamic architectures, we have a great challenge ahead of us: to discover configuration automatically, collect all necessary information, and then properly map the collected information and results to a changing configuration in a way that highlights existing and potentialissues -- and potentially, to make automatic adjustments to avoid them. This would require very sophisticated algorithms and sophisticated Application Performance Management systems.

## New Technologies

New technologies may require other ways to generate load. Quite often, the whole area of load testing is reduced to pre-production testing using protocol-level recording/playback. Sometimes, it even leads to conclusions like "performance testing hitting the wall" just because load generation may be a challenge. While protocol-level recording/playback was (and still is) the mainstream approach to testing applications, it is definitely just one type of load testing using only one type of load generation; such equivalency is a serious conceptual mistake, dwarfing load testing and undermining performance engineering in general.

Protocol-level recording/playback is the mainstream approach to load testing: recording communication between two tiers of the system and playing back the automatically created script (usually, of course, after proper correlation and parameterization). As far as no client-side activities are involved, it allows the simulation of a large number of users. But, such a tool can only be used if it supports the specific protocol used for communication between two tiers of the system. If it doesn't or it is too complicated, other approaches can be used.

UI-level recording/playback has been available for a long time, but it is much more viable now. New UI-level tools for browsers, such as Selenium, have extended the possibilities of the UI-level approach, allowing the running of multiple browsers per machine (limiting scalability only to the resources available to run browsers). Moreover, UI-less browsers, such as HtmlUnit or PhantomJS, require significantly fewer resources than real browsers.

Programming is another option when recording can't be used at all, or when it can, but with great difficulty. In such cases, API calls from the script may be an option. Often, this is the only option for component performance testing. Other variations of this approach are web services scripting or the use of unit testing scripts for load testing. And, of course, there is a need to sequence and parameterize your API calls to represent a meaningful workload. The script is created in whatever way is appropriate and then either a test harness is created or a load testing tool is used to execute scripts, coordinate their executions, and report and analyze results.

## Summary

Performance testing should reinvent itself to become a flexible, context-, and business-driven discipline. It is not that we just need to find a new recipe; now, we need to be able to adjust on the fly to every specific situation in order to remain relevant.

_[This article is featured in the new DZone Guide to Performance: Optimization & Monitoring. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/performance-optimization-and-monitoring)_

Learn tips and best practices for optimizing your capacity management strategy with the [Market Guide for Capacity Management](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html).

Opinions expressed by DZone contributors are their own.
