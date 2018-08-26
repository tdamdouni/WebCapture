# Why Developers Don’t Use TDD

_Captured: 2018-03-09 at 17:11 from [dzone.com](https://dzone.com/articles/why-developers-dont-use-tdd?edition=366226&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-03-09)_

In response to accelerated release cycles, a new set of testing capabilities is now required to deliver quality at speed. This is why there is a shake-up in the testing tools landscape--and a new leader has emerged in the just released [Gartner Magic Quadrant for Software Test Automation](https://dzone.com/go?i=265440&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fgartner-magic-quadrant-software-test-automation%2F%3Futm_source%3DDZone_Post_Roll%26utm_medium%3DText_Ads%26utm_campaign%3DDZoneDevOps%26utm_content%3D2017GartnerMQ).

Although the number of acronyms in the programming industry has probably already exceeded the number of stars observable in the moonless night sky, only a subset has gained popularity and recognition. TDD definitely belongs to this group. Judging by numerous conference lectures, books, podcasts, and blog posts, the fact that Test Driven Development is a widely known technique is undeniable. Yet, when you consider its adoption and actual usage the reality might look a bit different. In this article, we will take a look at the different reasons for avoiding TDD that have been presented by candidates during several conducted technical interviews and try to disprove if they are real obstacles.

## 1\. "Management Doesn't Allow Us"

The question here is why management decides whether TDD should be used by developers. Does a doctor ask a hospital director if he's allowed to use medical gloves? Of course not, because he uses them for his own protection. He also doesn't consult on each drug he prescribes to his patients. As a specialist, he is allowed to make own decisions in the area of his accountability.

By the same token developers can look at their toolset and techniques. **Your goal is to effectively deliver software and as a professional, it's your responsibility to find out how to achieve that.** Nothing prevents you from making a dry run on a small feature in order to assess whether the technique works for you or is it more like a ball and chain.

Nontechnical managers can't actually grasp what TDD is all about. Many of them associate the word Test with Quality Analysis and since in many organizations there are dedicated QA people for that job, they don't understand why developers should duplicate their efforts. There is no point in trying to explain what the difference is. After adding a new feature, you probably don't explain to your manager which data structures have been chosen to fulfill the task, because it isn't the level of details they are interested in. TDD belongs to the same level.

## 2\. "Not Enough Time to Write Tests"

The second excuse (which applies to all kinds of automated testing, not only TDD) is very similar to the first one, but it deserves a separate look because the reason might not be the same. While managers often try to set tight deadlines, developers are responsible for evaluating their exaggerated optimism and disagreeing when appropriate. You are the best one to assess the amount of work needed to complete a task. Make sure that your estimates include writing automated tests.

The issue here is that developers like to impress others with their effectiveness and sometimes accept more assignments than can actually be completed in the estimated time. If a task takes more than initially expected, instead of admitting their underestimation, they very often resign from writing tests in order to meet the "promised" delivery time. If you don't postpone writing a set of tests for a feature to the end, but write them together with production code as TDD suggests, you will never have a chance to resign from testing.

## 3\. "My Team Disagrees on Whether We Should Use TDD"

When working on a software project, there are decisions which affect each team member (like picking a framework or package organization) and should be agreed by everyone or imposed by a team leader. But is TDD one of those decisions? Is it possible that only a few team members work with TDD?

![](http://dolszewski.com/resources/post/2018-02-18/tdd-disagreement.png)

[In one of Uncle Bob's articles](http://blog.cleancoder.com/uncle-bob/2014/06/17/IsTddDeadFinalThoughts.html), we can read that it's rather impossible. If a part of such team values TDD and other relies on integration tests, the end result will always be the same - separation. Eventually, developers will seek for teams which share their values - if needed in a different company.

Fortunately, there is also a positive variant for disagreement which wasn't mentioned by Uncle Bob. Some teams split between those who value automated tests and those who don't write any kind of tests. In such a scenario, TDD can be successfully introduced by some team members without starting a conflict. **There is a chance that by giving an example, more teammates will get interested in TDD over time.**

## 4\. "Return on Investment in TDD Isn't Proven"

Many people ask for the scientific proof of the effectiveness of TDD, and they absolutely have the right. After all, they are going to spend their own time on the technique, so evaluation of the investment seems reasonable. The statement about the lack of evidence isn't, however, correct as there are several trustworthy sources which can be presented to TDD skeptics.

The first one is a [paper from North Carolina State University created by Boby George and Laurie Williams in 2003](https://collaboration.csc.ncsu.edu/laurie/Papers/TDDpaperv8.pdf). TDD opponents often demonize the technique as extremely time-consuming, but this document demonstrates that the studied group of TDD practitioners spent only 16% more time on the overall development process.

Another [experiment documented in 2008 by Nachiappan Nagappan et al.](https://link.springer.com/article/10.1007%2Fs10664-008-9062-z), which was conducted on three Microsoft and one IBM development teams shown a significant decrease (between 40% and 90%) in the total number of pre-release bugs in comparison with similar projects.

You can find much more studies on the web, but we can't forget it's impossible to generalize as each software project is different, some domains are hard to compare, and hence the exact numbers won't be the same in various cases. The real takeaway from such papers is the observable fact that TDD is beneficial for software quality, but you should decide if the required time investment is the price worth paying in your particular case. When a brand can suffer because of bugs in software it's better to find them as early as possible. But for back-office tools, fixing issues found by users is probably more acceptable. Test Driven Development isn't a silver bullet.

## 5\. "We Tried but It Didn't Work"

A bad learning experience can effectively discourage software developers from using any technique. Such an effect can be observed when TDD is applied to legacy code which wasn't designed with testability and modularity in mind. [God objects](https://en.wikipedia.org/wiki/God_object), which commonly occur in older systems, are sworn enemies of unit tests. Legacy code isn't the best place for the evaluation of TDD.

The problem also happens when TDD is applied to code which doesn't need unit tests. Purists can say that you should aim for 100% code coverage, but in real life, such a goal is a waste of time. Every application consists of some kind of business logic and rather brainless glue code. While TDD is great for the first group, for the second, it's like using a sledgehammer to crack a nut. Such code usually coordinates the sequence of operations and may have many dependencies which require a lot of mocks in order to test. A long list of mocks and indirect result assertions can also lead to a bad impression of TDD, which in this case is simply a misuse of the technique.

## 6\. "Slow Build Process"

One possible reason for slow tests is the complexity of their setup. If units selected for testing are too big, preparation of the starting state may take a significant amount of time. Slow running tests can be treated as a red flag which indicates that you should look more carefully into the application's design and assess the coupling between elements which are under tests. The longest running tests can be easily found and addressed separately.

![](http://dolszewski.com/resources/post/2018-02-18/tdd-slow.png)

It's also worth to mention that **there is no reason to run all application tests as part of the Red Green Refactor process**. In a [properly designed project structure](http://dolszewski.com/architecture/project-package-organization/), there shouldn't be a problem to select only these tests which are dedicated to the currently changed part of the code base.

Another cause for slow running tests is their total number. As already mentioned, some parts of every application simply don't need tests. **Code coverage metric boosting is simply lying to oneself that software quality has improved.** Automated tests should focus on code that changes a lot - business logic, calculations, etc. Learn to assess in which cases they aren't needed.

## 7\. "I Don't Know All the Requirements Upfront to Write All Tests"

This is an example of misunderstanding the concept of the technique. **TDD isn't about creating all possible test scenarios for a given code unit before writing production code, but rather about discovering test cases together with implemented requirements**. The whole beauty of TDD is that the gradual addition of new logic can be done with confidence because the regression of the requirements covered previously is guided by tests. TDD is an iterative process in which production code and tests are created alternately.

Naturally, there's nothing wrong with speeding up the cycle by writing a few tests in a row. In his book "Test-Driven Development: By Example," Kent Beck admits that as long as you understand the problem you are trying to tackle, you don't have to strictly stick to the Red Green Refactor cycle. Just remember, you can always slow down while working on more complex challenges if you feel the need.

## Tips for TDD Adepts

A bad impression of TDD can be severely minimized by learning from others' mistakes. If you're at the beginning of your journey with TDD, below you can find a few general hints which should simplify the learning process.

  * Let's start with a truism: All beginnings are hard. Expect the initial increase in time spent on developing new features. Learning a new thing, whether it's a framework, a musical instrument, or an unfamiliar technique, takes time. In order to improve, you need to overcome the temptation to return to old habits.
  * Focus on writing tests before production requirement implementation. It will force you to think about code modularity and impact the way you design classes and their relationships.
  * Legacy code isn't the most pleasant playground for TDD. A new feature shouldn't cause any problem, but adding tests to the existing monolith code base can quickly cool down your aspirations for the technique, as it's definitely more challenging.
  * The aim of 100% code coverage is a myth, and the reason TDD disbelievers describe it as a waste of time. Concentrate on the most crucial part of your software where the business logic resides.
  * There is plenty of material available on the web, but if you are looking for recommendations, you should check out "Test-Driven Development: By Example," written by Kent Beck, who is a leading TDD advocate.
  * Improve your unit testing skills. Frameworks come and go, but investing your time in learning how to write proper automated tests will always be useful.
  * Opinionated side mark: Making changes in code which isn't covered by tests is stressful. TDD is good for your health!

## What Would You Add?

The test-first approach has been around for almost 20 years now, yet doubts about its productivity are still pretty common. Hopefully, the presented examples will persuade some of those who hesitate with TDD adoption. If you observe any other excuse that isn't covered by this post, or have a tip for beginners, the comment section is waiting for you. Maybe you experienced harmful effects of the technique and the story is worth sharing? Your knowledge can help avoid problems by other developers. Feel invited to the discussion.

[Read and learn](https://dzone.com/go?i=280423&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fcontinuous-load-testing-devops%2F%3Futm_source%3DDZone_Pre_Roll%26utm_medium%3DWhitepaper%26utm_campaign%3DDZoneDevOps%26utm_content%3DContLoadTesting) why and how to "shift left" load testing and start Continuous Load Testing.
