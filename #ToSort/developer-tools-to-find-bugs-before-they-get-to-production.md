# Developer Tools to Find Bugs Before They Get to Production

_Captured: 2017-02-04 at 01:49 from [dzone.com](https://dzone.com/articles/developer-tools-to-find-bugs-before-they-get-to-pr-1?edition=267882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-03)_

Discover 50 of the latest mobile performance statistics with the [Ultimate Guide to Digital Experience Monitoring](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE).

Developers love tools, and they tend to use a lot of them. Many of them are such a normal part of our daily lives and toolchain that we don't even think of them as tools anymore.

Your computer, the Internet, a simple text editor, and source code repositories are a good example of this. They are just fundamental things we use every day.

Developers now have access to free and inexpensive developer tools that can help find and fix many common application problems. These new tools are now an essential part of every developer's tool set.

## Find Bugs With Free Developer Tools While Writing Code

None of us enjoy firefighting production application problems. We would much rather be working on some awesome new feature for our app. So, let's learn how to prevent production fires!

Let's start out by saying nobody writes perfect code, and you can never prevent every unforeseen scenario. However, with a little more visibility into what your code is doing, you can find a lot of common problems early on.

Fact: The best time to find bugs is when you are creating them.

Finding, reproducing, and fixing bugs in production is hard, slow, and expensive. The earlier we can find them in the development cycle the better, of course.

You just joined a new team and you are trying to help fix some bugs and add some new features to an existing project. You have no idea what any of the code does. Sounds like fun, right?

Many apps have complicated layers of authentication, data access, integrations, etc. Not to mention the dozens of AJAX calls that can occur in modern web apps. It can be very hard to understand what your code is doing under the hood.

## What Is Your Code Doing, Anyway?

How do you know what database queries, web service calls, cache hits, exceptions, and more are happening?

Thanks to detailed transaction tracing, which is powered by lightweight code profilers or other technology, you can easily see these types of details -- and more.

![](https://stackify.com/wp-content/uploads/2017/01/img_5877c7930cfea.png)

> _Screenshot from Prefix (free for ASP.NET and Java developers)._

Depending on which programming language you are using, there are several different developer tools you could use for this. The features and functionality of these tools vary wildly. Some require a lot of code changes or configuration, while some don't require any.

These developer tools are primarily designed to run on your workstation, although some may also work on a server.

  * [Glimpse](http://getglimpse.com) (.NET).
  * [Miniprofiler](http://miniprofiler.com/) (.NET, Ruby, Go, Node.JS).
  * [XRebel](https://zeroturnaround.com/software/xrebel/) (Java -- paid).
  * [Stackify Prefix](http://stackify.com/prefix) (.NET, Java).
  * [Scout Devtrace](https://scoutapp.com/devtrace) (Ruby).
  * [Rack trace](https://github.com/paulasmuth/rack-trace) (Ruby).
  * [Zend Z-Ray](https://www.zend.com/en/products/server/z-ray) (PHP -- paid).
  * [New Relic developer mode](https://docs.newrelic.com/docs/agents/ruby-agent/developer-mode/developer-mode) (Ruby).

All of these are free except for the ones denoted paid. If I missed a tool, please let us know in the comments below and we will add it!

These types of tools are a lifesaver. Once you start using them, they will become part of your standard tool-chain. They are really good at answering that question of "What did my code just do?"

## Using Transaction Traces to Find Bugs

Using [Prefix](http://stackify.com/prefix) as an example, it can collect a ton of awesome details about what a single web request is doing. It is pretty amazing to see all of your logging statements along with all of the other details it collects like SQL queries, etc.

Prefix can do all of this without changing your code.

![](https://stackify.com/wp-content/uploads/2017/01/img_5877c7e6983f3.png)

This type of view makes it very easy to see what SQL queries are being executed and how long they take. You can quickly copy a query and rerun it in your SQL management tool.

![](https://stackify.com/wp-content/uploads/2017/01/img_5877c77415d62.png)

You can even use it to help find common [N+1 type problems](https://secure.phabricator.com/book/phabcontrib/article/n_plus_one/) that come from running SQL queries within a loop.

![](https://stackify.com/wp-content/uploads/2017/01/img_5877c7ff79773.png)

## How to Catch Bugs in QA Before They Get to Prod

So far, we have talked a lot about using tools that do transaction tracing to help find bugs and improve your code as you are writing and testing it on your workstation.

### **What Happens Once You Deploy Your App to QA?**

For most developers, understanding what their code is doing after it gets deployed is mostly a black box. If they are lucky they might be able to get access to some log files or remote access to the server.

**How Do You Get the Same Transaction Tracing Details on Your Servers?**

Some of the tools mentioned above can work on your servers to give you a trace, but they could cause huge a performance overhead.

To easily view transaction traces across every user, server, and app, you really need an APM solution. APM, or application performance management, typically runs as a lightweight profiler to collect the same sort of details as the tools mentioned above. APM solutions are designed to be have very low overhead and even run on high traffic production servers.

Examples of these types of tools are [Stackify Retrace or New Relic](http://stackify.com/retrace-vs-new-relic). Check out [our blog post about APM tools](http://stackify.com/application-performance-management-tools/) to get a full list of them.

![](https://stackify.com/wp-content/uploads/2017/01/img_5877c85844f16.png)

_Example transaction trace recorded by [Retrace](http://stackify.com/retrace) showing logging, Redis access, and SQL queries._

## Things to Look For and Validate in QA

APM solutions provide aggregate reporting across all of your apps and servers so you can really analyze and understand performance. Here are some things that you should be looking for:

  1. Identify slow web requests
  2. Look for all applications errors that are occurring
  3. Find high volume and slow SQL queries
  4. Understand the performance of application dependencies

### Identify Slow Web Requests

Sadly, "works on my machine" does not always translate to success when your code gets to QA. Generate some good traffic against your code changes to ensure it is performing well and working correctly.

Review how long requests are taking. Ensure that performance is in line with expectations and look for ways to improve it.

![](https://lh4.googleusercontent.com/q8Nla01IZqOVJkD1r-TZhKBpmllH9A_ItFF6tsEJFpPHWt6aDYbQMD_NruC25wGXhtwaefr0UqTyjhM8SJ4kk5w1CkXcm_jMwa0b4nFRFC_E_JiOdeaKJ5fPuopcgbSQbd7n7iQr)

> _Look for All Applications Errors That Are Occurring_

Application errors can happen for a lot of reasons. Sometimes they are just transient noise. But many times, they can be our first line of defense when it comes to identifying potential problems.

After every development, it is a really good idea to always look for new and regressed errors. In this example, we can quickly see that after a deployment we were missing a stored procedure that caused a ton of new exceptions.

![](https://lh3.googleusercontent.com/UzG30G8c2bSQsOY3ahZL1PDlhSGud8q03xEYOmpabE8GL54Ywc_47eypCSRfq66SCrvUD0A2HklevmU9S3ffTd5OLcluWzLQsmaq8GZR2ap_svtAkFtHqDcM-62rvU1-2XMmjphX)

> _Find High-Volume and Slow SQL Queries_

It is hard to really know how fast or how slow a SQL query is going to be until you test it against a large set of real data and a high enough volume concurrently to see how it performs.

![](https://stackify.com/wp-content/uploads/2017/01/img_5877c8b5d04bb.png)

> _Understand the Performance of Application Dependencies_

Today's applications are highly dependent on a lot of external services, beyond just a simple database. Apps typically do a lot of web service calls, caching, queuing, and much more.

It is important to understand how these dependencies perform and scale before getting to production. In this example, we can see a big spike in response times around 9:45 due to SQL database queries.

![](https://lh6.googleusercontent.com/PyFaMde5Ik-jzE32OOzwD9KCa4ucDErS__Y3L8T32SVHLvTegytobZWn_fsnTbBmJxzNb3RXd-aXGZHMPZpdIBDrqs-BNTZpV60LvkR5xaDI42PRMfnnbio_5lXI3c9A9on3bjbY)

> _Developer Tools for Constant Feedback_

Free and inexpensive developer tools can give you constant feedback and insight into your applications. Based on the examples shown in this post, I hope you that you see how valuable [APM tools](http://stackify.com/application-performance-management-tools/) like [Prefix](http://stackify.com/prefix) and [Retrace](http://stackify.com/retrace) can be.

By using them through every step of the lifecycle, you can improve your team's velocity, increase the quality of your production code, and dramatically reduce the risk of a bad release.

Ultimately, you can spend more time building valuable software and spend less time triaging bad code that could have been improved well before it was released into production.

The beauty of it all is that you can do it affordably and as a byproduct of work you're already doing!

[Is your APM strategy broken?](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) This [ebook](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) explores the latest in Gartner research to help you learn how to [close the end-user experience gap in APM](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE).
