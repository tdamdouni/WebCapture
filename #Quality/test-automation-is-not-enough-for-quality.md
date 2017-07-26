# Test Automation Is Not Enough for Quality

_Captured: 2017-06-06 at 09:56 from [dzone.com](https://dzone.com/articles/test-automation-is-not-enough-for-quality?utm_source=MVB&utm_medium=email&utm_campaign=Monday%202017-6-05)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

The vast majority of enterprises we talk to say that they want to increase their test automation efforts. While test automation is critical to successful testing in an Agile world, the truth is that simple "test automation" is only part of the solution.

The "Shift-Left" movement works to fill in the missing pieces by addressing and compensating for the limitations around test automation. Shift-Left prioritizes testing earlier in the development process, taking testing (and test automation) to an API level - which often leads to the introduction of service virtualization.

This is where [Bas Dijkstra](https://twitter.com/_basdijkstra?lang=en) comes in. Bas is a test automation and service virtualization consultant specializing in finding more intelligent ways to use tools to improve test processes and software quality. His years of hands-on expertise and consulting work have given him unique insight into the software testing challenges that enterprises are facing today. For more from Bas, make sure to read his blog [here](http://www.ontestautomation.com/).

**Chelsea: **Lots of companies talk about increasing their test automation rates, but they are often only talking about UI test automation. Do you see UI testing as a limiting factor in a company's ability to adopt automation?

**Bas:** UI testing in itself is definitely not a limiting factor! There is a place and time for this type of test automation, however hard to write and slow to execute it is. Sadly, the way it is all too often implemented IS a limiting factor in the overall test automation strategy. For me, there are two main reasons for this:

  1. Using user interface-driven automated tests where other types of automated tests are better suited. Here, teams write automated tests against the UI, even though the functionality or business logic that's being verified is exposed on another level, for example via an API.
  2. Untrustworthy tests. Writing stable and maintainable user interface-driven tests is a skill that not everybody masters. As a result, teams end up with a lot of false positives ('flaky tests') that are eventually ignored or suffer from 'retry until green' (where tests are run multiple times until they pass at least once. Needless to say, this is fatal when you rely on the results of these tests as part of a CI / CD pipeline…

**Chelsea: **The "Shift Left" movement requires testing before the UI is fully available. Do you believe "Shift Left" is simply a "fad," or is it an evolutionary change in the traditional approach to test automation?

**Bas:** The term is a bit of a fad, the concept behind it is definitely NOT. Being able to test early and often (call it Shift Left, call it continuous testing, call it whatever you want) is pretty much a requirement nowadays if you want to be able to deliver high-quality software at speed. Just as with testing as a whole, failing to start with test automation until the end of a project will slow teams and organizations down and will end up costing them time, money, and market share.

**Chelsea: **For many in the software testing world, service virtualization is still a very abstract idea that they have yet to see in action. What do you think are the biggest obstacles to service virtualization being as widely implemented as, say, Agile?

**Bas:** This is a very good question, and one I have been discussing with peers quite often as of late! The most important reason for service virtualization not being as widely adopted as Agile (and test automation, to throw in another example) is because, for a lot of organizations, the pain of NOT implementing service virtualization is not (yet) big enough. These organizations are somehow still getting by:

  * building their own stubs,
  * putting a lot of effort in setting up and maintaining physical test environments,
  * postponing integration testing until the very end.

If that does not change, service virtualization will remain a hard sell, no matter how big the potential benefits (and they're definitely there, I've seen them).

**Chelsea: **Does the maturity of a company's testing strategy or test automation make a significant impact in how viable service virtualization is as a solution?

**Bas:** Not in how VIABLE it is as a solution, but definitely in how LIKELY it is an organization is to adopt and succeed with service virtualization. In my opinion, service virtualization can bring benefits no matter the maturity of a testing strategy. I've worked in projects where test automation wasn't introduced until there was service virtualization, simply because it was not an option with the then existing test environments. However, generally speaking, organizations do not start to think about adopting service virtualization until they reach the limits of what they can do with 'traditional' dependency and test environment management.

**Chelsea: **One point of confusion in service virtualization is the question of ownership. Should virtualization belong to Dev, Testing, or Ops?

**Bas:** Most projects I've worked in, I've been responsible for the implementation of service virtualization myself, as the Subject Matter Expert. The role of the test team was pretty clear in these cases:

  * To provide me with the necessary input on what to simulate (in the end, service virtualization should be supporting the testing to be executed, so for it to be effective you'll need a testers' point of view).
  * To verify whether the simulation indeed exerts the required behavior (testing the service virtualization implementation).

It doesn't really matter how "technical" (for lack of a better term) the testers are that interact with the Subject Matter Expert responsible for service virtualization implementation. Testers with more technical or development experience can maybe contribute in a little more 'hands on' way, but the input given by non-technical testers (for example on the requirements of the service virtualization implementation) is just as valuable.

Again, service virtualization should support testing, so make sure your testers are involved as much as possible.

**Chelsea: **Most companies have massive and complex technology landscapes. Do you ever find that they are virtualizing so much that it becomes difficult to manage?

**Bas:** Yes, virtualizing too much is definitely happening. It is quite easy to get lost in service virtualization land, so to say, and build all kinds of complex simulations that support even the edgiest of edge cases. What you're essentially doing in that case is rebuilding your dependency. And that should never be the goal of service virtualization! The Pareto Principle definitely applies to service virtualization as well: 80% of the gains come from 20% of the efforts. Be bold and dare to stop at 80% (or 90%, or…) instead of putting lots of effort into coming closer to simulating 100% of the dependency behavior. Always consider the tradeoff between time invested in simulating edge case behavior and time won as a result of doing so. Are those edge cases even part of the tests that are run? If so, how often are they run? Can they maybe run less often, therefore leading to less complex service virtualization? There is an optimum for every service virtualization implementation, and it's almost always somewhere "in between," never at 100%.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

### Like This Article? Read More From DZone
