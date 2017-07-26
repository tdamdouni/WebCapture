# Incremental Design: Part I

_Captured: 2017-02-06 at 12:29 from [dzone.com](https://dzone.com/articles/incremental-design-part-i?oid=twitter&utm_content=bufferd2995&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

Continuous Delivery is all about making small changes. Work flows more easily, planning is simpler, error detection is helped, and the time from idea to value is reduced when we make changes in small increments. However, how do you solve big problems in small pieces? How do you maintain a coherent design when each change is small?

There are many facets to this problem. The organizations that are best at it tend to take a very broad view of design and think about things like how teams are structured, how work is defined, and how design works when delivering a flow of many small features.

The traditional approach seems, on the face of it, sensible -- but is not. "Let's think very hard and design everything in detail before we start." Big, upfront design has a long history of not working very well, principally because at the point when you do the design, you know the least about the problem that you ever will.

For a while, we tried something else.

## "We're Agile; We Don't Need Your Stinking Design"

(This is a quote from Andrew Phillips of XebiaLabs - with tongue firmly in cheek.)

In the early days of Agile adoption, there were some very naive things said about software design. This was largely as a reaction to the failures of big-up-front design. Some of the advice used to remind me of the President of the Universe from Douglas Adams' _The Restaurant at the End of the Universe_. In this excellent book, it had been decided by the advanced civilizations of the universe that the desire to become a politician should exclude anyone from becoming one. They had taken this to its logical conclusion and decided that the senior person should have no preconceived ideas about anything. So, the President of the Universe lived in a shack on a beach and started every day making no assumptions at all. Upon waking, he would wonder at the big hot thing in the sky, muse on the nature of existence, and so on. This left no time at all for any decision-making -- ideal for a politician, not quite so good for a software developer.

Some people advised a similar approach to design. We should dump our assumptions and previous experience and instead go straight to code and not think about design at all. If you weren't sure what to do next, write a test!

Now there are few bigger fans of TDD than me, but I have always thought that this fear of design was stupid.

My own view on design is that we, as software developers, do it. There is no distinction between coding and design. Coding _is_ design, but it is not all that there is to it. Software development is an intriguing, difficult exercise in design and we should use all of the tools and experience at our disposal to accomplish it. We should also value good design and strive for elegance and simplicity in all that we do.

## A More Experimental Approach

If you are building a large complex system, or indeed any system, design is important. However, we have learned through painful experience that trying to do all of the design upfront doesn't work. Does this mean that we have reached an impasse?

Not really! Agile development practices are all about being experimental. So, we should be experimental in our approach to design. If we want to be experimental what will that take?

Perhaps the most important thing is to allow for failure. By definition, not all experiments succeed.

This need to allow for failure has several implications:

  * If a design choice fails, how do we limit the impact of this failure?

  * If we expect some of our design choices not to work, how do we tell?

  * How do we organize our work to allow us to build upon what we have learned from our experiments?

I am going to suggest approaches to dealing with each of these in my subsequent blog posts. As a teaser, here are some of the factors that I think are important in enabling a more incremental approach to design:

  * Team structure.

  * Business alignment.

  * Modeling and models.

  * Bounded context.

  * Isolation.

  * Reactive architectures

  * Loose coupling.

  * Separation of concerns.

  * There may be more!

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

### Like This Article? Read More From DZone
