# Aggregate Pattern

_Captured: 2017-03-31 at 20:12 from [dzone.com](https://dzone.com/articles/aggregate-pattern?edition=286955&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-31)_

Learn how to troubleshoot and diagnose some of [the most common performance issues in Java today](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

I've recently done some reading on [DDD](http://amzn.to/2nGLUXU) and Aggregates in particular. Since many people struggle to understand the pattern, I decided to try to explain it myself.

## Problem

Imagine that you're writing yet another e-commerce application and you're tasked with writing the all-important Order class:

Until the order is packed and ready to ship, customers are allowed to add a position to it:

Now, the business has asked you to limit the possibility to order more than 100 hundred items or for more than $5,000. How do you ensure that these criteria are met, considering the fact that you're working in a concurrent environment and using a relational database?

## Aggregate Pattern

This is a classic usage example of the famous Aggregate Pattern. Although some try to identify aggregates by looking for matching domain concepts, the pattern's real purpose is to help you ensure transactional consistency between your entities. We're doing this by deeming one of the entities responsible for ensuring the consistency and performing persistence operations just on this entity. We call such entity an aggregate root. Any other entities that are "ensured" consistent have to be saved in a single transaction by saving the aggregate root itself.

![](http://tidyjava.com/wp-content/uploads/2017/03/ss2017-03-27at06.38.43.png)

Applying this to our example, we could say that the Order class should be an aggregate over the OrderPosition class. This implies the following:

  * The Order class is responsible for ensuring the maximum amount of positions and their maximum balance.
  * The Order class requires some concurrency mechanism e.g. optimistic locking (AKA versioning).
  * There will be an OrderRepository class in the system, but not an OrderPositionRepository class.
  * The addPosition operation has to be performed in a transaction.

## One Aggregate Per Transaction

There's a good rule for working with aggregates that says that **we should not update more than one aggregate per transaction**. It makes perfect sense. Look, if I'm saying that consistency rules lie within the aggregate, then I should be able to save only this one, single aggregate -- and everything should stay consistent. If that's not the case, maybe I'm missing an "uber-aggregate" on top of the two that I want to update in a single transaction. Or maybe these rules don't call for transactional consistency at all!

The rule of one aggregate per transaction has also a usability argument on its side. Imagine the following scenario:

![](http://tidyjava.com/wp-content/uploads/2017/03/ss2017-03-28at06.42.46.png)

If our users are trying to deal with the same aggregates at the same time, the risk of having a failed transaction grows. User 2 could prevent the two other users from saving their work and, at the same time, any of the two other users could prevent User 2 from saving his or her work. That's not a desirable state of things. By limiting the transactions to one aggregate, we reduce the risk of failed concurrent transactions and therefore improve the usability of our application.

## Keep The Aggregates Small

The rule above and the way programmers think combine in a pretty strong force towards big aggregates. Let's say that someone added a status field to the Order class:

(Let's avoid the discussion whether such enum is a good idea. We just need an example.)

The business asks you to change the status to PAID once 99% of the order value is paid, to IN_DELIVERY once the guy at the warehouse starts to fill the parcels, and to COMPLETED once all parcels are delivered. Does that mean that the Order class should now take care of payments, parcels, and tracking the guy at the warehouse? The resulting aggregate would be a giant class with lots of responsibilities, just for the sake of maintaining consistency. Also, performance would suffer badly and the risk of a failed transaction would grow significantly. That's a pretty extreme vision, but it shows the limits of the Aggregate pattern's applicability.

### Eventual Consistency

Things are usually not that bad. If you go and ask the business whether it's okay for the order status to be updated a few seconds after the payment has been received or the parcel is delivered, they will most likely answer positively. Programmers often envision temporary lack of consistency as something evil and dangerous. That's a nerd point of view. When the business guys say consistent, they usually mean eventually consistent, and often, it could be even later than a few seconds.

**Therefore, talk to the business guys and embrace eventual consistency, when the domain allows it, to keep your aggregates small and your code simple.**

## Reference by ID

Taking the concepts above even further, if we only want to update one aggregate per transaction and we strive to keep the aggregates small, one could employ the practice of referencing other aggregates only by ID. It further reduces the aggregate, as we're keeping an ID instead of an object, and allows for better scaling, as we're no longer forcing ourselves to load multiple aggregates in the same database query. Plus, we're less tempted to update multiple aggregates at once.

## Summary

Aggregates are all about **transactional** consistency. When there is a strong consistency rule between multiple entities, we can deem one of them an aggregate root and make it responsible for maintaining consistency. At the same time, we're limiting persistence operations to only the root itself, so that it's not possible to put the aggregate in an inconsistent state by modifying and saving an entity by itself. For the best maintainability and scaling, we should strive to update only one aggregate per transaction, keep the aggregates small, and make them reference each other only by ID.

For more information about aggregates and DDD in general, I recommend the two great books: [DDD by Eric Evans](http://amzn.to/2nGLUXU) and [IDDD by Vaugh Vernon](http://amzn.to/2obBjSz). For a shorter read dedicated to aggregates, one could check out [Vernon's online series about aggregates](https://vaughnvernon.co/?p=838).

Understand the needs and benefits around implementing [the right monitoring solution for a growing containerized market](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics.](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital)
