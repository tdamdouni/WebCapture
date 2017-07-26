# Stop sweeping your failing tests under the RUG

_Captured: 2017-06-06 at 10:34 from [www.ontestautomation.com](http://www.ontestautomation.com/stop-sweeping-your-failing-tests-under-the-rug/)_

Hello and welcome to this week's rant on bad practices in test automation! Today's serving of automation bitterness is inspired by a question I saw (and could not NOT reply to) on LinkedIn. It went something like this:

> My tests are sometimes failing for no apparent reason. How can I implement a mechanism that automatically retries running the failing tests to get them to pass?

It's questions like this that make the hairs in my neck stand on end. Instead of sweeping your test results under the RUG (Retry Until Green), how about diving into your tests and fixing the root cause of the failure?

First of all, there is ALWAYS a reason your test fails. It might be the application under test (your test did its work, congratulations!), but it might just as well be your test itself that's causing the failure. The fact that the reason for the failure is not apparent does not mean you can simply ignore it and try running your test a second time to see if it passes then. No, it means there's work for you to do. It might not be fun work: dealing with and catching with all kinds of exceptions that can be thrown by a Selenium test can be very tricky. The task also might not be suitable for you: maybe you're inexperienced and therefore think 'forget debugging, I'll just retry the test, that's way easier'. That's OK, we've all been inexperienced at some point in our career. In a lot of ways, most of us still are. And I myself have not exactly been innocent of this behavior in the past either.

But at some point in time, it's time to get over complaining about flaky tests and doing something about it. That means diving deep into your tests, how they interact with your application under test, getting to the root cause of the error or exception being thrown and fixing it, for once and for all. Here's a real world example from a project I'm currently working on.

In my tests, I need to fill out a form to create a new savings account. Because the application needs to be sure that all information entered is valid, there's a lot of front-end input validation going on (zip code needs to exist, email address should be formatted correctly, etc.). Whenever the application is busy validating or processing input, a modal appears that indicates to the end user that the site is busy processing input, and that therefore you should wait a little before proceeding. Sounds like a good idea, right? However, when you want your tests to fill in these forms automatically, you'll sometimes run into the issue that you're trying to click a button or complete a text field while it is being blocked by the modal. Cue WebDriverException ("other object would receive the click") and failing test.

Now, there are two ways to deal with this:

  1. Sweep the test result under the RUG and retry until that pesky modal does not block your script from completing, or
  2. Catch the WebDriverException, wait until the modal is no longer there and do your _click_ or _sendKeys_ again. [Writing wrappers around the Selenium API calls](http://www.ontestautomation.com/using-wrapper-methods-for-better-error-handling-in-selenium/) is a great way of achieving this, by the way.

Option 1. is the easy way. Option 2. is the right way. You choose. Just know that every failing test is trying to tell you something. Most of the time, it's telling you to write a better test.

One more argument in favour of NOT sweeping your flaky tests under the RUG, but preventing them from happening in the future: some day, your organization might start, you know, actually relying on these test results. For example as part of a go / no go decision for deployment into production. If I were to call the shots, I'd make sure that all my tests that I rely on for making that decision were:

  * Returning reliable test results, all the time
  * Checking the right thing (but that's [a different post altogether](http://www.ontestautomation.com/do-you-check-your-automated-checks/))

Really, it's time to quit tolerating flaky tests. Repair them or throw them away, because what's the added value of an unreliable test?. Just don't sweep your failing tests under the RUG.
