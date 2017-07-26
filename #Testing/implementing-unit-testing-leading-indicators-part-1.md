# Implementing Unit Testing: Leading Indicators (Part 1)

_Captured: 2017-06-06 at 09:59 from [dzone.com](https://dzone.com/articles/implementing-unit-testing-leading-indicators-part?utm_source=MVB&utm_medium=email&utm_campaign=Monday%202017-6-05)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Now that we've talked about what [we want to achieve](https://dzone.com/articles/implementing-unit-testing-outcomes), we better spread out some sensors. After all, we're about to embark on a long and winding road. We want to know if we're still going the right way, and if not, make a turn.

Leading indicators raise the red flag _before_ the worst has happened. In our case, we don't want to check in after six months and see no one's written any tests for the last three months. We'd like to know sooner.

## So What Should We Track?

If you're thinking "coverage," hold your horses. Coverage by itself is not a good progression metric. We sometimes mix simplicity of measurement with effectiveness, and coverage is one of those things.

Coverage as a number doesn't have context - are we covering the right/risky/complex things? Are we exercising code but not asserting (my favorite gaming process)? Are we testing auto-generated code? Without the context, the coverage number has no applicable meaning.

Before we mandate tracking the entire software coverage or setting a coverage goal, remember that while it is easy to track exercised code lines, the number doesn't mean anything by itself.

## So What Do We Look For?

The first metric to start tracking is the simplest one: number of tests. (Actually two: tests written, and test running).

Our first indicator if people are writing tests is to count the tests. For that, we need to require a convention of test location, naming, etc. Guess what? These are needed also to run them as part of a CI build. Once everything is set up, we can count the tests where they count (pun!).

Then we want to look at the trend over time. The number should go up as people add more tests. If the trend flatlines, we need to investigate.

One thing about this metric - if you never see a drop in the number of tests, something's wrong. That probably means tests just stay there, and are not getting re-reviewed, replaced or deleted. In the short term, starting out, we want to see an upward trend. But over the long haul, code changes, and so do the tests. We want to see at least some fluctuations.

## So What About That Coverage?

Okay, we can measure coverage. We get that out of the box, right?

But we need to know what we're measuring. Coverage means executed lines of code. So we can look at coverage (or lack of) as an indicator in the context we care for.

That could be any of the following:

  * Important flows in the system.
  * Buggy code.
  * Code we return to over and over.
  * New components we want to cover.

Or any other interesting bit. When we measure coverage, we want to see a trend of increasing coverage over these areas.

Now, how do you manage that? That requires more tricks, since we want to make sure we measure the right code and the right tests. If the code architecture already supports it, it's easy: 75% of a library, for example.

If, however, you want to measure coverage of a set of classes, excluding the other parts of the library, that requires more handling and management. Usually, people don't go there.

The funny thing is, the more specific you want to get, the less regular tools stop helping. And the broader numbers lose meaning.

By the way, the coverage metric should go away once you get to sufficient coverage. Once again, it's not a number, but what we want to achieve - stability over time, or regression coverage. We can stop measuring then (and maybe look at other areas).

Okay, we'll continue the indicators discussion in the next post.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).

### Like This Article? Read More From DZone
