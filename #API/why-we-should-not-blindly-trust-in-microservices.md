# Why We Should Not Blindly Trust in Microservices

_Captured: 2017-06-01 at 00:41 from [dzone.com](https://dzone.com/articles/why-we-should-not-blindly-trust-in-microservices?edition=304109&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-31)_

Today's data climate is fast-paced and it's not slowing down. [Here's why your current integration solution is not enough.](https://dzone.com/go?i=188126&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fdata-inspired-future-e-guide%2F%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%25252520-%25252520Data-Inspired%25252520Future%26utm_source%3DDZONE) Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=188126&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fdata-inspired-future-e-guide%2F%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%25252520-%25252520Data-Inspired%25252520Future%26utm_source%3DDZONE)

Today, a great deal is written every week about microservices on the Internet. I myself think that microservices offer many advantages, so I also build such services in my own [open source workflow engine project](http://www.imixs.org). But today, I read an article about microservices which contained a funny picture. The picture should underpin the advantages of separating functions into a microservice architecture with an almost non-existent centralized management. The picture looks something like this:

![Image title](http://ralph.soika.com/wp-content/uploads/2017/05/microservice_vs_monolithic.png)

I asked myself: Which of the two diagrams appears to me, as a software architect, as the clearer one...?

Have we not worked out for years an architecture that allows us to reduce complexity? With Java EE, which seems to be a synonym for the evil monolithic architecture, we now have a concept which allows us to combine and connect different components (services) in an easy way. And with Java EE application servers we have a professional platform to control all these kinds of services.

Of course, it is painful to learn all the concepts about EJBs, Transactions, JNDI Resources, and Pool-Management. And yes, as a beginner you are confronted with all these concepts if you try to succeed with the Java EE platform. But after that, you have a highly scalable, easy to manage platform running your piece of software.

When I am reading all the adulation for having separated databases, with services implemented in different languages, connected to each other without explicit contracts, I'm pretty sure that in the next few years we have a lot of work to bring back systems to the left side of the image.

[Is iPaaS solving the right problems?](https://dzone.com/go?i=171134&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-ipaas-plus-e-guide%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DeGuide%252520-%252520iPaaS%252520vs%252520iPaaS%252520%252520) Not knowing the fundamental difference between iPaaS and iPaaS+ could cost you down the road. Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=171134&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-ipaas-plus-e-guide%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DeGuide%252520-%252520iPaaS%252520vs%252520iPaaS%252520%252520)

Opinions expressed by DZone contributors are their own.
