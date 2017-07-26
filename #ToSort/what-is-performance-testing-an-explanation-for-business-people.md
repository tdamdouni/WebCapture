# What Is Performance Testing? An Explanation for Business People

_Captured: 2017-06-06 at 09:56 from [dzone.com](https://dzone.com/articles/what-is-performance-testing-an-explanation-for-bus?utm_source=MVB&utm_medium=email&utm_campaign=Monday%202017-6-05)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Performance testing is a form of software testing that focuses on how a system running the system performs under a particular load. Performance testing should give organizations the diagnostic information they need to eliminate bottlenecks. You can find more information about types, steps, and best practices [here](https://stackify.com/ultimate-guide-performance-testing-and-software-testing/). This article provides insights and scenarios on performance testing from a business perspective.

## How Performance Testing Impacts Your Business

The world of enterprise IT neatly divides concerns between two camps: IT and the business. Because of this division, an entire series of positions exists to help these groups communicate. But since I don't have any business analysts at my disposal to interview, I'll just bridge the gap myself today. From the perspective of technical folks, I'll explain performance testing in the language that matters to the business.

### A Tale of Vague Woe

To prove it, let me conjure up a maddening hypothetical. You've coordinated with the software organizations for months. This has included capturing the voice of the customer and working with architects and developers to create a vision for the product. You've seen the project through conception, beta testing, and eventual production release. And you're pretty proud of the way this has gone.

But now you find yourself more than a little exasperated. A few scant months after the production launch, weird and embarrassing things continue to go wrong. It started out as a trickle and then grew into a disturbing, steady stream. Some users report agonizingly slow experiences while others don't complain. Some report seeing weird error messages and screens, while others have an average experience. And, of course, when you try to corroborate these accounts, you don't see them.

You inquire with the software developers and teams, but you can tell they don't quite take this at face value. "Hmmm, that _shouldn't_ happen," they say to you. Then they concede that maybe it could, but they shrug and say there's not much they can do unless you help them reproduce the issue. Besides, you know users, amirite? Always reporting false issues because they have unrealistic expectations.

Sometimes you wonder if the developers don't have the right of it, but you know you're not imagining the exasperated phone calls and negative social media interactions. Worse, paying users are leaving, and fewer new ones sign up. Whether perception or reality, the users' experience hits you in the pocketbook.

### The Nature of Performance Issues

At the risk of painting with a broad brush, let's talk performance issues. Anyone participating heavily in the software development process understands bugs. When you click on "sign up," does the software sign you up, or does it spit out some cryptic error message? If you add $20 to your checking account with a balance of $100, do you then have $120, or some incorrect number? These fall under the heading of "does the software comply with the requirements?"

Everyone in the business likes these types of bugs. Well, relatively speaking. If we have to contend with bugs, we have a much easier time dealing with predictably wrong behavior. Reproduce the issue to confirm it, then fix it and verify that you've solved the problem. Then grab a beer to celebrate.

But performance issues prove far more bedeviling. _Sometimes_, weird things happen. _Occasionally_, the login screen hangs for a while. _This one time, _all of the menus loaded on the side of the page instead of at the top. You try half a dozen times and can't get these things to happen in production, let alone in your internal sandbox environment. Do they happen randomly? Only every third Thursday of the month? Or maybe only when lots of people go on social media?

Performance issues usually don't occur with any kind of predictable cadence because they don't directly involve the software's behavior, _per se_. Rather, they involve the way that the software reacts with the unpredictable, chaotic world of production environments. Maybe the developers made some kind of mistake in design that presents efficient scaling. But maybe your data center stuck your app on a server with issues. Good luck figuring this out based on sporadic, frustrated user reports.

## Why You Need Performance Testing

How can you even begin to address all of the possibilities? It seems hopelessly daunting. In the bad news department, you can't address all possibilities, since the world is a chaotic place. But you can certainly limit your exposure. And you can do this via performance testing.

Almost every shop out there has some sort of QA process. Software developers write the code, deploying it to some production-representative environment. Once there, the QA group bangs away at it according to some kind of test plan. They do so to ensure that it behaves properly, both in terms of expected behaviors and reasonable response to odd user interactions, like typing their name into a field that says "phone number." But all too often, the testing effort stops here.

Instead, these shops should make more effort to simulate the harsh conditions of production. This presents a nice two-pronged benefit. First, this effort can expose deficiencies in the software that make it prone to performance problems. And secondly, these tests can show you what to expect when conditions stress your application. You'll learn the telltale signs so that, even when you can't directly address them, you can workaround and manage the situation as it occurs. This is far superior to getting caught flat-footed and unaware.

So what goes into performance testing, exactly? How can a shop inoculate itself, at least partially, against these sorts of problems?

## The Kinds of Performance Testing You Want

Well, put simply, performance testing involves seeing how the application performs under production-like conditions. Whereas most QA testing involves seeing how your app behaves with a single person using it, performance testing means simulating a situation with production-like traffic, for instance. To get more detailed, let's look at a few common performance testing situations.

You'll want a strategy for what's known as load testing. Load testing means that you pick a so-called load to place on your application. In your testing environment, this might mean simulating 1,000 users at a time performing normal operations and measuring how the application behaves. Does it remain responsive? Or does it slow down or even crash? Of course, you won't do all of this by having 1,000 actual people start messing around with your pre-production environment. You buy or build software that helps you simulate the load. Check out our recent post on the fifty most useful load testing tools [here](https://stackify.com/top-load-testing-tools/).

In addition to load testing, you should also look at having stress testing and endurance testing. With the former, you create a load designed to break your application. This lets you understand at what point it breaks and what bottlenecks you have. Every app has a breaking point, so you may or may not make changes after a stress test failure. But now you know what to look for and when to expect problems.

With endurance testing, you apply a load for a certain amount of time -- preferably a long time. Just as you want to know how it behaves with many users, you want to know how it behaves over weeks or months. Better to find out in your own environment than to find out alongside your users in real time.

## Operationalize Performance Testing for Success

Now you understand the concept if you didn't before. You need to go beyond correct behavior in isolation and verify fitness for operation in the wild. And the types of performance testing I mention here should serve only as table stakes. Once you start thinking of the specifics of your application and users, you'll probably have further ideas for your needs.

But before you run off to secure budget for load testing tools, understand one final thing. You don't want to make these efforts _ad hoc_. Rather, you want to operationalize them and make them part of your overall approach to quality. And that means discipline.

You need to automate this performance testing and make it a first-class part of your standard process. You then need to get into the habit of understanding, to prioritize, and addressing failures and issues. And, perhaps most importantly of all, you need to start doing it as early in project development as humanly possible. If you start performance testing an app that's 90% complete, you may find failures caused by systemic architectural decisions. Better to know that earlier than later.

If your group doesn't currently do performance testing, go start building the case for it as soon as you can. It'll make the software better in the long run, and it will make you a lot less likely to spend all of your time chasing phantom issues on behalf of frustrated users.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
