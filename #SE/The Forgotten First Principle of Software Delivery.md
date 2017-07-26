# The Forgotten First Principle of Software Delivery

_Captured: 2016-03-23 at 15:50 from [medium.com](https://medium.com/p/b1540ad6000e)_

#### We have an industry-wide blindspot for the most important metric in software, and now is the time to change that.

![](https://cdn-images-1.medium.com/max/800/1*CRslYiLS4aER31Eg9c1SdQ.png)

Hi. I'm Sam, and I am obsessed with delivering higher quality software, faster.

What does that mean? Well, like you, I'm passionate about innovation. But more specifically, I'm passionate about delivering innovation as quickly as possible, without compromising quality.

Most teams start with the best intentions and deliver features to customers very quickly. But soon they are slowed down by support issues and fixing bugs -- one of the 7 **wastes** of lean -- while management continuously increases the pressure to deliver even more features, even more quickly.

### Every team in the world wants to deliver faster

And going faster is now easier than ever -- or so it seems…

  * Developers are able to release features more quickly than ever, thanks to application frameworks like [Meteor](https://www.meteor.com/), UI frameworks like [Semantic](http://semantic-ui.com/), and the flurry of SaaS services that do the heavy-lifting for you like [Stripe](https://stripe.com/).
  * Cloud based automated deployments help push out releases faster and more frequently using technologies like [Docker](https://www.docker.com/) and services like [Amazon's BeanStalk](https://aws.amazon.com/elasticbeanstalk/).
  * Most critically, Agile practices give us methods for iterating quickly and measuring speed, or rather the **flow** of work. It's common to hear management say things like _"we need to find a way to increase our velocity"_ and _"let's scale our development team"._

### We have become obsessed with the flow principle

As someone with [10 years of experience as an Agile practitioner and coach](https://www.linkedin.com/in/samhatoum), I can tell you that constantly measuring flow is a good thing as it allows you to track your team's progress. If you are not already doing it, then you should be.

  * If you are a SCRUM team, you are likely measuring velocity with story points, and tracking your progress against this metric.
  * If you are a Kanban team, you might be measuring throughput and analyzing cumulative flow diagrams to spot bottlenecks.

But there's a problem of only optimizing for flow. Let's first explore what **flow** really means.

#### The Flow principle

Flow is simply _units over time_. With water, you might use _liters per second_. In software, the unit is the value. I will discuss the nuances of how to measure value in another post, but for now let's make it easy and say that a single unit of value is a complete feature that has successfully been deployed to production.

In SCRUM this is known as velocity, eg. 15 story points per iteration, and in Kanban it's known as throughput, eg. 3 features per week.

With such an intense focus on the flow of value alone, it seems that most teams consider Flow and Value to be first principles of software delivery.

The problem is that when you only optimize for flow, you are encouraging your team to deliver features faster, but you're not encouraging the team to delivery **higher quality** features faster.

### The missing principle is Quality

Quality is a loaded term. It can mean accuracy, precision, excellence, fit-for-purpose, efficiency, reliability, maintainability and many other terms depending on who you ask. The reality is that quality is not easy to define.

> Quality cannot be defined because it empirically precedes any intellectual construction of it.

![](https://cdn-images-1.medium.com/max/800/1*3gCo6dVnbdM2KfMQGs7uhw.png)

#### Quality is hiding in plain sight

Quality does not really have a dedicated measure of its own, however everybody that works in software development instinctively knows that quality is a critical factor of the delivery equation.

![](https://cdn-images-1.medium.com/max/600/1*lFepwoye7obOjVleBqLzsA.png)

> _This team is not delivering any value_

In SCRUM, the velocity measure contains an implicit indicator of quality. For example, if your team were to spend a few sprints fixing bugs and not delivering any story points, the velocity would be zero, which indicates poor quality elsewhere.

![](https://cdn-images-1.medium.com/max/600/1*N-p6G6Dro2RI9f9dQXgp2w.png)

> _Activities flat-lining in the middle -- source_

In Kanban, cumulative flow diagrams also contain an indicator of quality. A flat line of activities can be an indicator that the team is doing wasteful work, which in turn indicates poor quality.

You can see that quality is not being directly measured above, but the effects of poor quality are being observed through other indicators. Therefore **we can measure quality through proxy indicators**.

We can do something about the "poor quality" and see if we are improving through the proxy indicators. For example, if the team is constantly being bogged down with regression bugs (proxy indicator), they can apply practices such as automated testing to catch those bugs at development time. After they have applied the practice, they can monitor the number of regression bugs and see an improvement in quality.

The same principle applies further up the product development phase. For example, if the business owners are creating features that users don't like (proxy indicator), they can employ methods such as [user testing and market research](http://xolv.io/product-market-fit-consulting/?utm_source=medium&utm_medium=sh-blog&utm_campaign=quality-articles) to validate their ideas before spending time and money developing them. They can then check back with users and see that the features are being used.

The methods and practices that are put in place in response to the poor quality can be seen as functions that are needed to ensure quality. I call these **_Quality Functions_,** which are essential for the continued delivery of value.

### Quality is a fundamental function of value

Let's consider the team from the example above that is getting bogged down with fixing regression bugs. Let's assume they spend 90% of their time fixing the bugs. This means, the lack of _quality functions _like automated testingresults in the team only working 10% of their time on delivering value. If they had high test coverage, they might only spend 20% of their time fixing regression bugs.

Let's apply the same principle to the business owners that are creating features that the users don't want. The lack of _quality functions _likeuser testing and market research_, _is reducing their delivery of value by 100%!

> You simply cannot go faster if you don't prioritize quality.

And when you don't apply the necessary _quality functions_ to all aspects of your product development lifecycle, the resulting poor quality acts like a giant parachute that drags behind you. As the poor quality builds up, it becomes increasingly difficult to move forward.

![](https://cdn-images-1.medium.com/max/800/1*bi4irLy6QA2aCbGRWvSUwA.png)

### We don't have a holistic measure for quality. And that is a problem.

> Does it surprise you that 50% of developer time is spent fixing bugs? ([source](http://undo-software.com/wp-content/uploads/2014/10/Increasing-software-development-productivity-with-reversible-debugging.pdf))

How does that compare to your software team? Do you even know?

> We have created an industry-wide blind spot for what in my opinion is the most important first principle of software delivery: Quality

Any battle scarred developer or experienced team already knows this.

We have many great advancements in tools and techniques to help developers create better quality software like TDD, BDD etc. I have started to write about some of these on our [automated testing best practices repository on GitHub](https://github.com/xolvio/automated-testing-best-practices).

But it is difficult to improve what you can't measure. And it is even harder to create a business case for investing in quality, if there are no measures to base it upon.

I have built my career and reputation on being the guy that the world's best companies call when they can't deliver and don't know why. I have performed this role for companies like Audi, The BBC, Nike and Sky, working with some of the most respected consultancies in the world.

The underlying theme of the problem is just always the same: Lack of good quality practices, too many bugs and too many impediments to delivering value.

We can work to improve flow, but without improving quality, nothing improves.

### Our industry-wide focus on flow is giving diminishing returns.

Throwing more testers at regression bugs, and pushing out features that nobody wants does not make you go faster. It's just more air trapped in your parachute.

> If you only optimize for flow, poor quality will hold you back

And sometimes, you won't even know why. But,

> If you optimize for quality, you will get faster flow for free!

### Now is the time to refocus on quality

[I have built my company to do exactly this](http://xolv.io/?utm_source=medium&utm_medium=sh-blog&utm_campaign=quality-articles). We are already working with some world-class companies to help them deliver higher quality software, faster. We have a selection of products that make a tangible difference to the cost of their bugs, but more importantly we are working with our clients to rebuild the whole software delivery process with quality, not just flow, influencing everything.

This is the first of a series of posts that I will be writing about measuring and prioritizing quality. In my next post I'll be showing you how you can apply **different quality functions** to your process both to increase flow and reduce costs.

#### Join our mission

We at Xolv.io are out to fix this problem. If, like me, you are passionate about quality, or if your bugs have held you back for too long, join us.

Click the button below to follow me here on Medium, [here](https://twitter.com/sam_hatoum) on Twitter, and [here](http://xolv.io/blog/?utm_source=medium&utm_medium=sh-blog&utm_campaign=quality-articles) at the Xolv.io site and blog where I will update you on our progress. You can also [contact me](http://xolv.io/contact-us/?utm_source=medium&utm_medium=sh-blog&utm_campaign=quality-articles) or comment below if you have any thoughts or ideas.

I look forward to helping you deliver higher quality software, faster.

Sam.
