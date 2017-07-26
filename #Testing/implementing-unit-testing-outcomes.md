# Implementing Unit Testing: Outcomes

_Captured: 2017-06-06 at 10:00 from [dzone.com](https://dzone.com/articles/implementing-unit-testing-outcomes?utm_source=MVB&utm_medium=email&utm_campaign=Monday%202017-6-05)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

We've discussed what the [goals of the implementation](https://dzone.com/articles/implementing-unit-testing-goals) are, and now it's time to talk details.

What do we expect to happen? When will we know that we have achieved our goals? We're looking for evidence that will tell us if the implementation has reached its goals.

However, the goal of the implementation is not the goal of the team. When the implementation reaches its goals, it has an impact on the team. We're are not doing it just for the sake of writing tests.

The first outcome we expect to see is quality improvement in the product. It's true that better quality may not be impacted solely by unit tests (that holds true for the other outcomes, too), but nonetheless, it is an outcome we're looking for.

So how does the implementation achieve the outcome?

If there are tests around buggy code, and the team continues to run them and address test failure as an important issue, the bugs get fixed early. That leaves more time for wider and exploratory testing to be done, rather than spending time on the simple bugs that could have been caught earlier. We are better informed on what we release, and confident that the quality is good enough to release. As a side effect, there are also fewer firefights and emergencies that keep us focused on quality.

Something we can actually measure as a result of this rise in quality is better "ready to test" builds. If we have an automated sanity suite (integration and/or system), we'll see an increase in the number of builds that pass the sanity suite. That is simply because the unit tests find those early stupid bugs before they enter the testing cycle.

Product quality is one outcome; we can see also improvement in code quality.

While writing unit tests alone may not result in better code, the tests are just part of the program. Training and coaching also focus on better code and design, not just as a focus for better and easy to write tests. If the material catches on, people will eventually write better code, and sustain it as a team convention. Code is going to be more readable, and with tests that are easy to refactor, so people will improve their code.

Finally, we go back to the goal of the implementation itself. We do want to see the testing effort becomes a regular part of development. While it's not the main outcome we're going for, it is definitely a proxy of whether our implementation is successful.

Outcomes come out at the end. We don't want to wait that long to see what happens. Next time we're going to discuss what metrics we can track as _leading_ indicators, to see if we're on the right track.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
