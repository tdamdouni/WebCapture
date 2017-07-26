# The Smoke and Mirrors of UX vs. Application Performance

_Captured: 2017-04-21 at 18:32 from [dzone.com](https://dzone.com/articles/the-smoke-and-mirrors-of-ux-vs-application-perform-1?oid=twitter&utm_content=bufferae456&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

_[This article is featured in the new DZone Guide to Performance: Optimization & Monitoring. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/performance-optimization-and-monitoring)_

Can a better UX simultaneously deliver a worse user experience? It sounds like a paradox, but it may be more common than you think. It describes a category of UX design practices that have little to do with improving the actual experience and everything to do with suggesting that the experience is a good one.

The difference can be subtle, but true user experience improvement begins with precision application performance optimization that only an APM solution can provide. APM diagnoses the cause of a slowdown, allowing developers to address the root cause and not the surface symptoms. Ignoring the underlying performance bottlenecks and tricking the user with a UI band-aid is akin to placing tape over a crack in your drywall -- you're only covering up the symptom of an underlying problem. That's the difference between improving the quality of the software and generating economic waste for short term gains.

## Defining Perceived Performance

UX designers commonly deploy a set of techniques related to "[perceived performance](http://mercury.io/blog/the-psychology-of-waiting-loading-animations-and-facebook)." This is the principle that the user's perceptions about the app's performance need to be managed. One real world example involves a test of loading screen animations for the mobile version of Facebook. The test demonstrated that users reported an improved perception of the app's loading speed when developers changed the design of the loading animation.

As iOS developer, Rusty Mitchell reported, "A Facebook test indicating that when their users were presented with a custom loading animation in the Facebook iOS app, they blamed the app for the delay. But when users were shown the iOS system spinner, they were more likely to blame the system itself."

Perceived performance techniques are part a larger trend in design beyond the world of software known as "[benevolent deception](https://psmag.com/how-should-we-program-computers-to-deceive-eedbf653805a#.y59nxsj22)."

## A Study of Benevolent Deception

In a report by Microsoft and university researchers, author Eytan Adar said his team found increasing use of "[benevolent deception](https://psmag.com/how-should-we-program-computers-to-deceive-eedbf653805a#.y59nxsj22)" in a range of software applications. Adar said that these deceptions arise from the stress of opposing market forces. While enterprise and consumer apps are growing more complex, users increasingly prefer apps with a simpler, more intuitive interface. The complexities must be simplified on the front end and deception is the most direct route.

Adar wrote, "We're seeing the underlying systems become more complex and automated to the point where very few people understand how they work, but at the same time we want these invisible public-facing interfaces. The result is a growing gulf between the mental model (how the person thinks the thing works) and the system model (how it actually works). A bigger gulf means bigger tensions, and more and more situations where deception is used to resolve these gaps."

## Beyond Benevolent Deception

One step beyond benevolent deception is "[volitional theater](https://www.fastcodesign.com/3048770/no-ui-designs-next-move-fake-ui)," which refers to functions and displays that don't correspond to the underlying processes. Outside the world of software-defined businesses, you can see these techniques at work in the fact that elevator "[Close Doors" buttons](https://www.nytimes.com/2016/10/28/us/placebo-buttons-elevators-crosswalks.html?_r=2) don't do anything at all. They just give impatient riders something to do until the doors close on their own.

Pretty shocked? Yep, you better believe it.

_The New York Times_ cited several other examples of volitional theater, such as the "Press to Walk" button on street corners. Remember all those times you kept the crosswalk pedestrian button to cross the street? You were most likely pushing a button [designed to calm your nerves](https://www.nytimes.com/2016/10/28/us/placebo-buttons-elevators-crosswalks.html) that didn't have any actual impact on the timing of the street lights. Designers refer to non-operation controls as "placebo buttons." They shorten the perceived wait time by distracting people with the imitation of control.

## Three Types of Volitional Theater

Adar's research identified three major trends in the way that volitional theater is being used in modern UX application design:

### System Images Deception: Designed to Reframe What the System Is Doing

This category of deceptive UX includes "Sandboxing." That's where developers create a secondary system that operates in a way that's different from a full application. The example Adar gave is the Windows Vista Speech Tutorial. This works as a separate program from the main speech recognition system. In reality, the tutorial is a "safe" version of the environment that was built to be less sensitive to mistakes to simplify the learning process.

### Behavioral Deceptions: Designed to Offer Users the Appearance of Change

This category goes back to the idea of placebo buttons. By giving users an "OK" or "Next" button, the system can smooth over performance delays. UX designers use a host of optical illusions and cinematographic techniques like blurring to suggest motion when nothing is happening on screen. Examples include pattern emergence, reification (fill-in-the-gaps), image multi-stability, and object invariance. These often cover over issues related to slow-performing software.

### Mental Model Deceptions: Designed to Give Users a Specific Mental Model About How the System Operates

Explainer videos may be the worst offenders in this category, since they apply dramatic and distracting metaphors in an attempt to engage distracted prospects. Many times, the more outlandish the model, the more memorable it is. These mental models help sales, but support teams then have to explain how things really work to frustrated customers. It also covers popular skeuomorphs, like the sound of non-existent static on Skype phone calls.

![Performance Guide](https://dz2cdn2.dzone.com/storage/rc-covers/4759565-dzone-performancecover-lg.jpg)

> _Performance Guide_

_Find this article and much more in..._

**[DZone's Guide to Performance: Optimization and Monitoring](https://dzone.com/guides/performance-optimization-and-monitoring?oid=performanceplug)**

Including:

  * Survey findings from over 500 developer responses

  * Articles written by top Performance experts

  * "What Ails Your Application" Infographic

  * Directory of performance optimization and monitoring tools

## Better Practices in UX

Despite these trends, there are many developers who remain strongly opposed to benevolent deception and volitional theater. Some of their insights and arguments are presented on the [Dark Patterns website](http://alistapart.com/article/dark-patterns-deception-vs.-honesty-in-ui-design).

These developers don't feel that it's ethical to trick the user or remove their freedom to know what's going on with the software. Instead of masking issues, they feel that slowdowns or clunky design can and should be eliminated. What developers need to achieve that is a comprehensive monitoring solution that pinpoints the causes of latency. Then engineering teams can go in and make the necessary code and infrastructure optimization necessary for software to actually perform better. They consider volitional theater to be sloppy design. One way to start correcting those design flaws is by evaluating the software and corresponding infrastructure dependencies.

## UX and Business Transactions

The first step in approaching application performance monitoring is identifying an entirely new unit of measuring the success of your applications. At AppDynamics, we've solved this by introducing the concept of a [Business Transaction](https://www.appdynamics.com/product/business-transaction/).

Imagine all the requests that are invoked across an entire distributed application ecosystem necessary to fulfill a specific request. For example, if a customer wants to "check out" their shopping cart, they click the "Checkout" button. Upon that single click, a request is made from the browser through the internet to a web server, probably a front-end Node.js application which then calls an internal website, a database, and a caching layer. Each component within that call that's invoked is responsible to fulfill that click, so we call the lifeline of that request a Business Transaction.

The Business Transaction perspective prioritizes the goals of the end user. What are your customers really trying to achieve? In the past, developers argued over whether [application monitoring or network monitoring](https://blog.appdynamics.com/product/ux-monitor-the-application-or-the-network/) were more important. Here's how an AppDynamics engineer [reframed the problem](https://blog.appdynamics.com/product/ux-monitor-the-application-or-the-network/):

"For me, users experience 'Business Transactions' -- they don't experience applications, infrastructure, or networks. When a user complains, they normally say something like, 'I can't log in,' or, 'My checkout timed out.' I can honestly say I've never heard them say, 'The CPU utilization on your machine is too high,' or, 'I don't think you have enough memory allocated. Now think about that from a monitoring perspective. Do most organizations today monitor business transactions, or do they monitor application infrastructure and networks? The truth is the latter, normally with several toolsets. So the question 'Monitor the application or the network?' is really the wrong question. Unless you monitor business transactions, you're never going to understand what your end users actually experience."

Starting from the business transactions will help DevOps teams view your system as a function of business processes vs. individual requests firing off everywhere. This is how you can start solving the problems that matter most to customers. It's always better to diagnose and solve performance issues instead of merely covering them up or distracting the user with UX techniques.

## Isolating Causes

This approach is much closer to approximating the true UX of an average user. Starting from the business transaction, you can use APM solutions to drill down from end user clients to application code-level details. That's how you isolate the root cause of performance problems that matter most to specific users.

Of course, isolating the problem doesn't matter unless you resolve it. We've discussed this with application teams who have isolated problems related to runtime exceptions for Java-based applications in production, but they tended to gloss over those that didn't break the application.

That's a mistake we addressed in a series about [Top Application Performance Challenges](https://blog.appdynamics.com/engineering/exceptional-performance-improvement/). Bhaskar Sunkar, AppDynamics co-founder and CTO, concluded that, "Runtime Exceptions happen. When they occur frequently, they do appreciably slow down your application. The slowness becomes contagious to all transactions being served by the application. Don't mute them. Don't ignore them. Don't dismiss them. Don't convince yourself they are harmless. If you want a simple way to improve your application's performance, start by fixing up these regular occurring exceptions. Who knows, you just might help everyone's code run a little faster."

This approach is becoming even more critical as smaller devices attempt to crunch higher volumes of data. A good example is how applications built for the [Apple Watch](https://blog.appdynamics.com/product/why-its-so-difficult-for-devs-to-create-apps-for-the-apple-watch/) are expected to provide the same level of performance as those built for a tablet or smartphone. Users don't lower their expectations to compensate for processing power. In the end, users care about the benefits of the application, not the limitations of the device.

## The Age of Experience

Gartner reported that 89 percent of companies expected to compete based on [customer experience](https://www.gartner.com/marketing/customer-experience) by 2017. However, customers want more from their software than just great UX. Beautiful design and clever tricks can't distract these time-sensitive users from being very aware of application performance issues.

As data volumes accelerate and devices shrink, it will grow harder to maintain optimal performance and continuous improvement schedules. Applications teams need speed and precision tools to pinpoint areas for improvement. At the same time, more businesses are undergoing their own digital transformations and discovering the importance of performance management for the first time.

Developments in user hand movement recognition and motion control mapping have been accelerating along multiple fronts, such as VR best practices by Leap Motion and [Google's Project Soli](https://atap.google.com/soli/), which uses micro-radar to precisely translate user intent by the most minute finger gestures. These advancements likely represent what's coming next in terms of UX, but they will demand IT infrastructures with access to a great deal more data-processing power.

## Drilling Down to Maximum Impact

Excellence in UX for the next generation of applications has to start by troubleshooting business transaction performance from the user's point of view. From there, you'll be able to drill down to the code level and intelligently capture the root cause that impacts the user.

_[This article is featured in the new DZone Guide to Performance: Optimization & Monitoring. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/performance-optimization-and-monitoring)_

Learn tips and best practices for optimizing your capacity management strategy with the [Market Guide for Capacity Management](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html).
