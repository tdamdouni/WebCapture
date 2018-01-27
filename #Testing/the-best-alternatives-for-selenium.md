# The Best Alternatives for Selenium

_Captured: 2017-11-28 at 09:55 from [dzone.com](https://dzone.com/articles/the-best-alternatives-for-selenium?edition=337920&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-27)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

In today's world, having stable and robust automated tests is absolutely mandatory.

For a long time, Selenium has been the first option when it comes to creating UI automated tests. The problem is that in recent years, it has failed to keep up with the ever-growing complexity of web applications and diversity regarding browsers and mobile devices.

Some have turned to hybrid solutions involving Selenium and [BrowserStack](https://www.browserstack.com/) or Selenium and [Sauce Labs](https://www.saucelabs.com/), but these solutions can be expensive and unstable.

We wanted to know if there is a better approach, similar to how companies have turned to AWS from bare-metal servers. Surely, there must be some elegant and miraculous solution for our automated tests, right?

Our team has evaluated more than fifteen solutions and we have decided to share our experience with you.

**Disclaimer: **This is just our opinion, and opinions can sometimes be subjective. All of these solutions are pretty good in their own way, it mostly depends on the needs and budget of each potential user.

Here are those solutions:

## 1\. Endtest

We managed to create our first automated tests with [Endtest](http://endtest.io/) in less than five minutes, and we were also able to run those tests directly on their cloud infrastructure.

![](https://cdn-images-1.medium.com/max/1200/1*RvIXvSkG2lEEz4HgoQ1ZdA.png)

![](https://cdn-images-1.medium.com/max/1200/1*2T0sy7wVgaId81xPpRtJUg.png)

Their interface is pretty clear and easy to use, we didn't even need to check out their documentation section.

You don't have to download or install anything- everything is done in their cloud. We just signed up and started working on the tests.

![](https://cdn-images-1.medium.com/max/1200/1*vPnZmfT0FIRX6A9B-ASsFQ.png)

Everything went pretty smoothly. We did get a few errors when running the first drafts of the tests, but that was mostly because we weren't targeting the correct HTML elements.

![](https://cdn-images-1.medium.com/max/1200/1*KNhrMsoZsqcAj1RQ80m1Og.png)

Each step is defined by an action. By putting together different actions, you're creating a test case.

Another thing we really liked was the possibility to run our tests across different operating systems, browsers, and mobile devices.

![](https://cdn-images-1.medium.com/max/1200/1*KRWScBejW0JbpKAM1gFWEA.png)

> _Their UI is absolutely gorgeous._

Even with responsive design and ever-improving standards support, cross-browser issues are not a thing of the past. It's neither possible nor feasible to manually test your site in the galaxy of popular browsers and OS's in broad use today; luckily, Endtest came to the rescue.

![](https://cdn-images-1.medium.com/max/1200/1*AVLySuGMxEIMCsKAc5UvFA.png)

_Our list of test suites._

![](https://cdn-images-1.medium.com/max/1200/1*BTn8mg9no7q5gbikhZhlgg.png)

> _Running a test in Endtest and getting instant results._

One thing we didn't like was the lack of video tutorials for this platform. We understand that it was launched in 2016, but that shouldn't be an excuse.

Here's a short video demo for Endtest that we found on YouTube:

_A cute video demo for Endtest._

After reading some articles, we found out that Endtest was a pretty huge surprise for the testing world, stealing important customers from competitors. We can understand why.

Surprisingly, it's actually quite cheap. They offer a FREE Plan which offers unlimited tests runs and a PRO Plan ($79) which offers some advanced features (such as using their API and granting access to your automated tests to other team members).

We sent them a message via the Contact Us section, asking a pretty generic question, and they replied in less than one hour. We also contacted them on Twitter and Facebook, and they replied in less than ten minutes. Awesome!

Their homepage says that they have over 50,000 customers.

What made this solution a winner in our eyes was that it's a complete, stable, and robust all-in-one platform for automated testing.

## 2\. Ghost Inspector

Second place goes to [Ghost Inspector](http://ghostinspector.com/), a solution developed by Justin Klemm.

![](https://cdn-images-1.medium.com/max/1200/1*S-Npe7AhbHBr4QCZv8owdA.png)

> _This looks cute._

Similar to Endtest, this is a cloud solution, so you don't have to download or install anything to get started, except for the test recorder.

It does have nice documentation and useful video tutorials. Their user interface is a bit too heavy for our tastes, but it's decent.

We downloaded the test recorder, hoping that it might save us some precious time. The recorder is actually a Chrome extension. We tried recording a test on the Google search engine page, but it failed when we ran it.

Anyway, we continued to write the tests using their visual test editor, which seems a bit built for developers because you just have to guess that you're locating the elements by CSS Selectors. They should really try to add the option to select elements by Id, Class Name, XPath, Tag Name, Text, etc (basically, all the options that Selenium has, plus others).

After four hours, we managed to finish almost all of the test cases.

They do have a cloud infrastructure on which you can run your tests, but it's PhantomJS, Chrome, and Firefox; they're probably going to extend it in the near future.

It's okay for a quick smoke test, but I wouldn't bet my cross-browser regressions on their cloud.

The worst part about using Ghost Inspector? Even if you have a paid plan, you cannot run a test for longer than 10 minutes. This is also mentioned in their FAQ.

![](https://cdn-images-1.medium.com/max/1200/1*4-2c5Z6PgBLqdvY1EsXkJA.png)

_SAD_.

Guys at GhostInspector, if you're reading this, please try to remove that limitation in the future.

Also, thank you for building this platform! I saw a lot of love for you on Twitter.

One problem we had was with the pricing. Those prices are just way too expensive for such a basic solution.

![](https://cdn-images-1.medium.com/max/1200/1*MjVduyvdXk3CSsPF9TIIyA.png)

> _This is what we needed and it was a bit too expensive for us._

## 3\. TestCraft

Third place goes to [TestCraft](http://testcraft.io/), a startup coming from Israel.

![](https://cdn-images-1.medium.com/max/1200/1*MN7NH4C_utLDQayJchjHoA.png)

> _That's just their opinion._

While their interface does look okay, it's lacking usability. I'm saying this because if you have fifty steps in one test case, it will take you some time to scroll through them.

After an annoying signup process, we managed to create a trial account, because we had to validate our email address. This is unacceptable in 2017, when you have so many solutions that can help you prevent getting random signups from bots.

We didn't have so much time to look through their platform, but you could give it a try, it looked interesting.

We don't know the pricing, since we couldn't find it anywhere on their website. We usually do not give too much attention to solutions that do not list their pricing in a clear manner, because we don't like dealing with sales teams.

TestCraft, thank you for trying to help us get rid of coding in automated testing! We appreciate that!

## 4\. Testim

[Testim](http://testim.io/) is one of those SaaS solutions that has machine learning which enables self-healing tests.  
We were very excited about that and thought it was the real deal since their pricing is a bit high ($240/month for what we needed).

![](https://cdn-images-1.medium.com/max/1200/1*6zUo1J1ExaW3q6mpgpI_AA.png)

> _Testim is just too expensive for our pockets._

But we were a bit disappointed to find out what this "machine learning" actually was.

While recording and running a test, their engine is saving 4-5 locators for each element (ID, Class Name, XPath, CSS Selector) and if that step fails the next time, it will just try with a different locator (by using different tactics).

But I have to admit, it does have some cool features. If you don't want to use their test grid, you can use SauceLabs or BrowserStack; that is the kind of "openness" that we like to see.

Hopefully, this will be a really awesome solution when they have real AI, which will write test cases for us.

We liked what we saw, Testim! Keep up the good work!

We did try other solutions as well, but they were not worth reviewing (Ranorex, Sahi Pro, Test Complete, Screener, Katalon, Screenster).

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**
