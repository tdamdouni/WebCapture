# The Birth of Automated Testing at Google in 2005

_Captured: 2017-06-06 at 10:35 from [dzone.com](https://dzone.com/articles/case-study-the-birth-of-automated-testing-at-googl)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

By implementing the right principles and patterns, Development and QA are using production-like environments in their daily work, and we are successfully integrating and running our code into a production-like environment for every feature that is accepted, with all changes checked into version control.

However, we are likely to get undesired outcomes if we find and fix errors in a separate test phase, executed by a separate QA department only after all development has been completed. And, if testing is only performed a few times a year, developers learn about their mistakes months after they introduced the change that caused the error. By then, the link between cause and effect has likely faded, solving the problem requires firefighting and archaeology, and, worst of all, our ability to learn from the mistake and integrate it into our future work is significantly diminished.

Automated testing addresses another significant and unsettling problem. Gary Gruver observes that "without automated testing, the more code we write, the more time and money is required to test our code -- in most cases, this is a totally unscalable business model for any technology organization."

Although Google now undoubtedly exemplifies a culture that values automated testing at scale, this wasn't always the case.

In 2005, when Mike Bland joined the organization, deploying to Google.com was often extremely problematic, especially for the Google Web Server (GWS) team.

As Bland explains:

> "The GWS team had gotten into a position in the mid-2000s where it was extremely difficult to make changes to the web server, a C++ application that handled all requests to Google's home page and many other Google web pages. As important and prominent as Google.com was, being on the GWS team was not a glamorous assignment -- it was often the dumping ground for all the different teams who were creating various search functionality, all of whom were developing code independently of each other. They had problems such as builds and tests taking too long, code being put into production without being tested, and teams checking in large, infrequent changes that conflicted with those from other teams."

The consequences of this were large -- search results could have errors or become unacceptably slow, affecting thousands of search queries on Google.com.

The potential result was not only loss of revenue, but customer trust.

Bland describes how it affected developers deploying changes, saying that "fear became the mind-killer. Fear stopped new team members from changing things because they didn't understand the system. But fear also stopped experienced people from changing things because they understood it all too well."

Bland was part of the group that was determined to solve this problem.

Bland explained further that at Google, one of the consequences of having so many talented developers was that it created "imposter syndrome," a term coined by psychologists to informally describe people who are unable to internalize their accomplishments. Wikipedia states that "despite external evidence of their competence, those exhibiting the syndrome remain convinced that they are frauds and do not deserve the success they have achieved. Proof of success is dismissed as luck, timing, or as a result of deceiving others into thinking they are more intelligent and competent than they believe themselves to be."

GWS team lead Bharat Mediratta believed automated testing would help. Bland describes:

> "They created a hard line: no changes would be accepted into GWS without accompanying automated tests. They set up a continuous build and religiously kept it passing. They set up test coverage monitoring and ensured that their level of test coverage went up over time. They wrote up policy and testing guides, and insisted that contributors both inside and outside the team follow them."

The results were startling.

As Bland notes:

> "GWS quickly became one of the most productive teams in the company, integrating large numbers of changes from different teams every week while maintaining a rapid release schedule. New team members were able to make productive contributions to this complex system quickly, thanks to good test coverage and code health. Ultimately, their radical policy enabled the Google.com home page to quickly expand its capabilities and thrive in an amazingly fast-moving and competitive technology landscape."

But GWS was still a relatively small team in a large and growing company.

The team wanted to expand these practices across the entire organization. Thus, the Testing Grouplet was born.

They were an informal group of engineers who wanted to elevate automated testing practices across the entire organization. Over the next five years, they helped replicate this culture of automated testing across all of Google.

The story of how they did this is presented in Part 5. Over the next three years, they created training programs, pushed the famous Testing on the Toilet newsletter (which they posted in the bathrooms), the Test Certified roadmap and certification program, and led multiple "fix-it" days (i.e., improvement blitzes), which helped teams improve their automated testing processes so they could replicate the amazing outcomes that the GWS team was able to achieve.

Now, when any Google developer commits code, it is automatically run against a suite of hundreds of thousands of automated tests.

If the code passes, it is automatically merged into trunk, ready to be deployed into production. Many Google properties build hourly or daily, then pick which builds to release; others adopt a continuous "Push on Green" delivery philosophy.

The stakes are higher than ever -- a single code deployment error at Google can take down every property, all at the same time (such as a global infrastructure change or when a defect is introduced into a core library that every property depends upon).

Eran Messeri, an engineer in the Google Developer Infrastructure group, notes:

> "Large failures happen occasionally. You'll get a ton of instant messages and engineers knocking on your door. [When the deployment pipeline is broken,] we need to fix it right away because developers can no longer commit code. Consequently, we want to make it very easy to roll back."

What enables this system to work at Google is engineering professionalism and a high-trust culture that assumes everyone wants to do a good job, as well as the ability to detect and correct issues quickly.

Messeri explains:

> "There are no hard policies at Google, such as, 'If you break production for more than ten projects, you have an SLA to fix the issue within ten minutes.' Instead, there is mutual respect between teams and an implicit agreement that everyone does whatever it takes to keep the deployment pipeline running. We all know that one day, I'll break your project by accident; the next day, you may break mine."

What Mike Bland and the Testing Grouplet team achieved has made Google one of the most productive technology organizations in the world.

By 2013, automated testing and continuous integration at Google enabled over four thousand small teams to work together and stay productive, all simultaneously developing, integrating, testing, and deploying their code into production.

All their code is in a single, shared repository, made up of billions of files, all being continuously built and integrated, with 50% of their code being changed each month. Some other impressive statistics on their performance include:

  * 40,000 code commits/day.
  * 50,000 builds/day (on weekdays, this may exceed 90,000).
  * 120,000 automated test suites.
  * 75 million test cases run daily.
  * 100+ engineers working on the test engineering, continuous integration, and release engineering tooling to increase developer productivity (making up 0.5% of the R&D workforce).

The story that Mike Bland told about the genesis of automated testing at Google in 2005 was so amazing that I asked him to tell this story at the [DevOps Enterprise Summit](http://events.itrevolution.com/) in 2015. [You can find his video here](https://www.youtube.com/watch?v=ahtihwxgriA).

Endnotes and citations:

  * Gary Gruver, personal correspondence with Gene Kim, 2014.
  * Mike Bland, "[DOES15 Mike Bland Pain Is Over, If You Want It](http://www.slideshare.net/ITRevolution/does15-mike-bland-pain-is-over-if-you-want-it-55236521)," Slideshare.net, posted by Gene Kim, November 18, 2015.
  * Eran Messeri, "What Goes Wrong When Thousands of Engineers Share the Same Continuous Build?," presentation at the GOTO Conference, Aarhus, Denmark, October 2, 2013. [Notes posted by Gene Kim](http://scribes.tweetscriber.com/realgenekim/206).

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

### Like This Article? Read More From DZone
