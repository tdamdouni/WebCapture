# Break the Monolith! Loosely Coupled Architecture Brings DevOps Success

_Captured: 2017-09-22 at 13:49 from [dzone.com](https://dzone.com/articles/break-the-monolith-loosely-coupled-architecture-br?edition=325534&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202017-09-22)_

### Speed and stability are the keys to unlocking high-performing DevOps capabilities. Loosely coupled, microservice-oriented architecture helps you achieve both.

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

Puppet and DORA's [State of DevOps Report](http://electric-cloud.com/blog/2017/06/top-5-takeaways-2017-state-devops-report/) keeps growing. The report aims to show the changes and growth across DevOps in the enterprise this past year and to help IT leaders understand the trends in the industry. In fact, in the four years Puppet has published the report, there have been over 25,000 responses from people working across all industries and verticals -- not just tech companies, but highly regulated industries like insurance, healthcare, and government. Furthermore, 25% of responses came from large enterprises with more than 10,000 employees.

One of the most useful ways to interpret this report is to look for commonalities among organizations using DevOps to successfully deploy quality products. This year, the report shows that a loosely coupled architecture and team is one of the strongest indicators of continuous delivery and DevOps success. This points to an emerging pattern regarding one of the most effective ways to structure your architecture toward this goal -- in the form of microservices.

So, how can you decompose monolithic applications into microservices to power your business forward? Based on a [recent discussion I had with Jez Humble](http://electric-cloud.com/resources/webinars/get-loose-microservices-and-loosely-coupled-architectures-featuring-jez-humble/), CTO of DevOps Research and Assessment and a principal author of the State of DevOps Report, there are some key points to share.

## Low Performers Sacrifice Stability for Speed

Before diving full-steam ahead into the world of microservices, let's quickly look at some of the numbers from the report. One of the most amazing statistics to come out this year is the fact that high-performing teams are doing releases 200 times more frequently than their low-performing counterparts. Not only are they releasing much more frequently, but the same high-performing teams are able to move 3,000 times faster in terms of lead teams. This means releases now happen in the span of hours, not months.

While these numbers are staggering, it is worth noting that the gap has actually closed somewhat. Humble attributed this not to actual improvements, but a sacrifice in stability.

We're seeing that what's happening is the low performers are moving faster, but they're not yet actually finding ways to create more stability. And they're not putting in the work to actually make sure that those fast releases are more stable. You see that when companies are like, 'We must go faster, but we're not going to invest in test automation and deploying automation,' this is the result. You end up going faster by actually breaking things because you've got to do the work of actually improving the culture and implementing the practices.

## Architecture Comes First

So, the evidence is there -- DevOps works, especially when organizations are invested in the tools, organizational structure and processes to make it successful. One of the key steps toward achieving this type of success is establishing a loosely coupled architecture through the use of microservices. Architecture is the single strongest predictor of the ability for an organization to effectively practice continuous delivery -- it's stronger than test automation, deployment automation and continuous integration.

At its highest level, and in the words of Humble, microservices are "a suite of services -- each service focused on doing one thing well." It is the process of attempting to break down a complex problem into constituent pieces, each of which have their own area to focus on, allowing organizations to divide and conquer, develop expertise that allows faster development times and, ultimately, streamline their development pipeline and produce better releases, faster.

But if you are currently servicing a monolithic application, the prospect of achieving a loosely coupled architecture, or breaking it up into microservices, can be daunting. Some of the challenges you will face are state management, transactional boundaries and, simply, headcount for managing a great number of microservices.

## Getting a grip on your loosely coupled architecture

But like the premise behind microservices themselves, the best way to walk a journey of a thousand miles is one step at a time. By focusing on one service and getting it to the point that it's functional before moving on, it can make breaking up a monolith simpler.

One of the ways to do this is through an approach called Martin Fowler's Strangler Application pattern. Though this methodology was [first defined in 2004](https://www.martinfowler.com/bliki/StranglerApplication.html), before the development of microservices, it is well suited as an approach to breaking up monoliths into microservices.

The Strangler Application is based around the analogy of a vine that strangles the tree it is wrapped around. By using the structure of the application itself, you can divide an application into different functional domains, and then replace them with microservices one at a time. When you do this, you essentially create two separate applications that live side by side, and, over time, the new application will replace (or strangle) the old one -- at which point you can shut it off. The Strangler Application helps you to divide and conquer by using the monolithic applications inherent divisions and building within that framework.

## Trust in Automation

Another good starting point to approaching microservices and a loosely coupled architecture is to try to break your application up into as many small microservices as possible. By keeping the bites small, it will have less impact on the overall application as you began to break it into pieces. Of course, that also means you will have that many more services to support. With that in mind, it will be helpful to bake in as much automation as possible, particularly with automated testing. Another way to make microservices more manageable as you attempt to break apart you monolith is by employing self-service automation. By empowering your development teams, they won't have to wait for environments and you can work much more efficiently.

Overall, microservices are an outstanding way to approach continuous delivery and help power your DevOps transformation. If you find yourself faced with the challenge of breaking up a monolithic application, taking a bite-sized and iterative approach will help make the transition easier, keep your application moving forward and help you take a crucial step toward making continuous delivery a part of your business strategy.

For more on how the right architecture choices help teams achieve Continuous Delivery, microservices, and loosely-coupled architecture, [check out the full webinar video of my conversation with Jez Humble.](http://electric-cloud.com/resources/webinars/get-loose-microservices-and-loosely-coupled-architectures-featuring-jez-humble/)

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).
