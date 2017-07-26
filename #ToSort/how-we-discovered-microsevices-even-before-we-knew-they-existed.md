# How We Discovered Microsevices Even Before We Knew They Existed

_Captured: 2017-06-05 at 02:24 from [dzone.com](https://dzone.com/articles/how-we-discovered-microsevices-even-before-we-knew?edition=304121&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-04)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

We can't deny that in the past several years, the term "[microservices](https://dzone.com/articles/what-are-microservices-actually)" has become widely used, if not over-used. But do we even know what they really are, how they were created, and what the main benefit from using them is? This emerging technology will reshape how software is built and delivered in the "era of the cloud."

'The concept of microservices is not new. Google Inc., Amazon.com Inc., and Facebook Inc. have been running microservices for over a decade. In fact, every time you search for a term on Google, it calls out to roughly 70 microservices before it returns your results," says Matt Miller in an [article in The Wall Street Journal.](https://blogs.wsj.com/cio/2015/10/05/innovate-or-die-the-rise-of-microservices/)

The team behind Microtica share their story on how they first [discovered microservices ](http://www.microtica.com/2016/10/discovering-microservices/)before knowing they existed- specifically, how they benefited from them while creating Dox Bee**,** the platform for document collaboration.

![Image title](https://dzone.com/storage/temp/5487513-screen-shot-2017-06-02-at-122006-pm.png)

## The Creation of Dox Bee, The Document Collaboration Platform With No Hiccups

Roughly four years ago, still in the era of [monolithic infrastructure](http://whatis.techtarget.com/definition/monolithic-architecture), almost no one had used external services outside of the monolith. Today, these external services are known as _microservices_. We were also using monolithic infrastructure, and everything was functioning perfectly up until the creation of Dox Bee.

To make it clearer, Dox Bee is a platform for online document collaboration that consists of multiple key functions, including editing and commenting, working in parallel, and external collaboration. It also includes the main function: the "compare function," i.e., fast and accurate comparison of multiple documents. Here's a very brief description of how it works: the user uploads multiple documents to compare, and the system identifies and highlights the differences and mistakes. Sounds easy, right? But what happens to the server when a heavier document is uploaded?

At the time, we were using Node.js to build all of our software in a monolithic architecture. Everything was working perfectly fine until we uploaded 700 pages for comparison on our monolith module.

### What Happened When We Put 700 Pages to Compare on a Monolith Structure in Node.js?

With the testing of Dox Bee's MVP, we had to make sure that our platform would be able to handle anything. To test our "compare function," we uploaded 700 pages for comparison to the monolith. You can assume what happened during the six-second process. In those six seconds, everything got blocked, including our server. All the running applications in the background stopped working.

Well, okay, you might say six seconds is not a long time, but imagine facing this problem over and over again, every time a user requires a "heavier" function.

That's when we decided to completely move the "compare function" to a different machine outside of the monolith, so that when the job was scheduled, the monolith would function without hiccups and, at the same time, all the "heavy lifting" will be left aside. This worked perfectly!

At that time, we named our innovation "the external service."

## If This Is Possible, Then…What If?

So imagine, if only one "external service" had such a disruptive impact, then what if we created more external services which would function separately and individually? In the era of instant gratification, we are all chasing that one extra second.

The horizons and possibilities are wide open.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
