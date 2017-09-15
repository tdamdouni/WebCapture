# Benefits of Continuous Testing

_Captured: 2017-08-19 at 11:12 from [www.infoq.com](https://www.infoq.com/news/2015/04/benefits-continuous-testing?utm_content=buffer3223d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

At [Unruly](http://tech.unruly.co/) teams have been applying eXtreme Programming (XP) since being founded in 2006. Software development at Unruly is done in small teams with no dedicated testers. These teams take a test-first approach to developing code, investing in automated checks that can be run in live environments rather than relying on manual testing in staging.

[Rachel Davies](http://www.infoq.com/author/Rachel-Davies), Agile Coach at Unruly, gave a [keynote on continuous testing](http://www.slideshare.net/RachelDavies/agile-testing-days-nl-keynote-on-continuous-testing) at the [Agile Testing Day Netherlands 2015](http://www.agiletestingday.nl/). InfoQ interviewed Davies about the importance of a continuous approach to testing, how this has evolved and the business advantage that it delivers to Unruly.

**InfoQ: Can you explain why automated testing is so important for your teams?**

> **Davies**: It's so important because automated checks are faster and more reliable than people checking the software manually. Manual testing is often a boring job. We want to be able to deploy product changes on the same day that our Sales people ask for them. To make this possible we automated our deployment scripts, which also run our automated tests. A computer can carry out repeatable steps much faster than a human so automation helps us deliver valuable solutions more quickly.

**InfoQ: Can you give some examples how automated testing is helping teams at Unruly to deliver value to the business?**

> **Davies**: A sales person can ask for a change to live systems and we want to be able to turn this around in hours not days. We have the unusual situation that we do not have any interim staging environment that code must be pass through. Instead we put changes directly into production environments because we want to deliver value faster. Although new code changes are deployed into our production environment, we have several ways not reveal them to all users of our live system straight away. What we do is to work in small deployable steps with automated tests to check expected behaviour is in place. Any problems with slow or brittle tests do get discussed in team retrospectives.

**InfoQ: During the years you invested in continuous testing. What made it worthwhile to do this, which benefits does continuous testing give you?**

> **Davies**: By taking a test-first approach we have great test coverage to check that product features work as expected. We can quickly find out if changes break existing automated checks. Automated monitoring of our live services also helps us to spot whether conditions have arisen that we have not anticipated. Driving our product development with tests also helps our teams focus on what they need to deliver and keep running.

**InfoQ: At the Agile Testing Day Netherlands you talked about how you do automated testing by having checks that are running continuously in your live production environments. Can you describe how this works?**

> **Davies**: We have Nagios alerts configured to notify the team on various conditions of our live services. We get notifications via SMS when problems occur and we have big screens in our development area showing load and performance of our software in live environments. Maybe you will be interested to read a blog by one of our developers about [monitoring check smells](http://benjiweber.co.uk/blog/2015/03/02/monitoring-check-smells/).

**InfoQ: Can you elaborate how automated testing at Unruly has evolved over the years?**

> **Davies**: The company was founded in 2006 using XP practices of TDD and so tests were automated from the start. Over the years we have had to expand those tests to browser and device testing (as browsers and mobile platforms have evolved more capabilities). The product expanded and there's a been a big move to more "responsive" web sites on both desktop, tablet, and mobile. Tablets weren't really a consideration in 2006.
> 
> We did not adopt BDD style tests that can be read by non-technical people as we had bad experiences in the early days using FiTnesse to automate acceptance tests. Our developers talk directly with stakeholders not to business analysts. Tests are written and read by developers in the same programming language as the code so there's little benefit to us to capture examples BDD style.

**InfoQ: You talked about using chaos monkeys in testing. Can you elaborate on that?**

> **Davies**: Inspired by [Netflix infrastructure chaos monkeys](http://techblog.netflix.com/2012/07/chaos-monkey-released-into-wild.html) we have developed our own domain specific "monkeys" to inject potential failures at the application level in our production environments, such as unresponsive services in latency critical applications. This approach has help us to identify and fix issues that wouldn't manifest in a test environment. One of our developers, Alex Wilson, wrote a blog about [injecting application failures in production](http://probablyfine.co.uk/2015/04/09/injecting-application-failures-in-production/).

**InfoQ: Are there any other new testing techniques that look promising, techniques which your teams are thinking about trying?**

> **Davies**: We might benefit from spending more time on manual Exploratory Testing. The classic definition of this is "Simultaneous learning, test design, and test execution." from the well known book Lessons Learned in Software Testing by Cem Kaner, James Bach, and Bret Pettichord (2002). This is different from automated checking and instead actively explores behaviour of systems without a script to learn how the system behaves in unanticipated ways.

**InfoQ: If organization is interested to deploy continuous testing, can you give them some advice?**

> **Davies**: Start with automating all regression tests and don't get sidetracked by BDD. Begin automating basic health checks as smoke tests and gradually improve test coverage. Start with most business critical logic or with areas that break most often.
