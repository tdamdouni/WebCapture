# API Transit Basics: Deprecation

_Captured: 2018-01-26 at 18:16 from [dzone.com](https://dzone.com/articles/api-transit-basics-deprecation?utm_source=Top%205&utm_medium=email&utm_campaign=Top%205%202018-01-263)_

_This is a series of stories I'm doing as part of [my API Transit work](http://basics.apievangelist.com/), trying to map out a simple journey that some of my clients can take to rethink some of the basics of their API strategy. I'm using a subway map visual, and experience to help map out the journey, which I'm calling [API transit](http://basics.apievangelist.com/)-leveraging the verb form of transit, to describe what every API should go through._

This is a simple one. All APIs will eventually need to be deprecated. This is how you avoid legacy systems that have been up for over decades. Make sure the lifespan of each service is discussed as part of its conception, and put some details out about the expected timeline for its existence. Even if this becomes an unknown, at least you thought about it, and hopefully discussed it with others.

Here are just a few of the common building blocks I'm seeing with API operations that respect their users enough to plan for API deprecation:

  * **Releases** \- Have a set release schedule, and think about what will be deprecated along with each release, allowing for future planning with push.
  * **Schedule** \- Have a deprecation schedule set for each API. You can always extend, or keep versions of your API beyond the date, but at least set a minimum schedule.
  * **Communication** \- Make sure you have a communication strategy around deprecations. Post to the blog, Tweet out notices and send emails.
  * **[The Sunset HTTP Header](https://tools.ietf.org/id/draft-wilde-sunset-header-03.html)** \- This specification defines the Sunset HTTP response header field, which indicates that a URI is likely to become unresponsive at a specified point in the future.

Another valuable concept this process will introduce is the possibility that APIs can be ephemeral and maybe only exist for days, weeks, or months. With CI/CD cycles allowing for daily, weekly, and monthly code pushes, there is no reason that APIs can evolve rapidly, and deprecate just as fast. Make sure deprecation is always discussed, and thought about in the context of other legacy systems, and technical debt that exists at the organization.

API deprecation is inevitable. We might as well start planning for it from day one. Every API definition upon inception should have an API deprecation target date, 12 months, 18 months, or whatever your time frame is. You may have future versions of the API in place, and in some cases extend the life of an API, but having a deprecation strategy shows you are thinking about the future, considering change, as well as considering the impact on your consumers.
