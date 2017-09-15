# Eight Of The Most Common Challenges Testers Face with Selenium

_Captured: 2017-08-19 at 18:17 from [dzone.com](https://dzone.com/articles/eight-of-the-most-common-challenges-testers-face-w?edition=317400&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-18)_

Speed up delivery cycles and improve software quality with [TestComplete.](https://dzone.com/go?i=228239&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad) Discover the most robust automated testing tool for end-to-end desktop, mobile, and web testing. [Try TestComplete Free.](https://dzone.com/go?i=228239&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad)

![Selenium Challenges](https://crossbrowsertesting.com/blog/wp-content/uploads/2017/07/080117_Selenium-Challenges.png)

Selenium automates the browser to mimic real user actions on the web. As the web gets more complex, using Selenium to test has become increasingly popular. Although it has made web testing far easier for many teams and organizations across the world, it still has its fair share of challenges due it's open source nature.

Most of the issues that testers experience have fairly straight forward solutions, which is why we outlined the most common Selenium challenges and how to fix them.

## Pop-Up Windows

When a simple, prompt, or confirmation alert pops-up, it can be difficult to automate it to either accept or close. Additionally, Windows-based alerts are beyond Selenium's capabilities since they're part of the operating system instead of the browser. However, since Selenium can operate in multiple windows, web-based alerts can usually be handled with the switchTo method to control the pop-up while keeping the browser in the background.

Learn more about handling pop-up windows with Selenium [here](https://crossbrowsertesting.com/blog/test-automation/automated-test-pop-ups-alerts/).

## Dynamic Content

A web page that has dynamically loaded content has elements that may not be at first visible when you visit the site. This can mean that the page is user specific and will display different content based on different users, new content appears on the page after a certain amount of time, or it appears after clicking something on the page. For when a locator cannot identify a new element present at that time, Selenium comes with an integrated Explicit Wait where you can specify an amount of time to wait before automating a command. This should help give the page enough time to load and identify the element to interact with.

Learn more about testing dynamic content with Selenium [here](http://elementalselenium.com/tips/23-dynamic-pages).

## Flakiness

Sometimes Selenium will give you flaky tests, which means they'll come back as positive or negative when they actually are the opposite. Eventually, too many flaky tests may mean testers might ignore the results, though this isn't a great option either. Oftentimes, unstable builds can be a product of one of many factors: poor test isolation, flaky external services, and timeouts. By examining the elements of your Selenium tests, it'll be easier to find out why your builds are unstable so you can approach the problem head-on.

Learn more about managing flaky tests [here](https://testing.googleblog.com/2009/06/my-selenium-tests-arent-stable.html).

## Can't Test Mobile Apps

While Selenium can test on any operating system and browser on desktops, it's limited when it comes to mobile testing in that it cannot run on native operating systems like iOS and Android. So, for example, the version of Facebook you pull up on Safari on your Mac can be tested with Selenium, but not the one on mobile Safari - on your iPhone 7. The Selenium family has a solution. It's cousin, Appium, is an open source test automation framework that drives iOS and Android native, mobile, and hybrid apps using the WebDriver protocol and can be used for this purpose for testing mobile apps instead of web applications. As users increasingly move to mobile devices, it's no surprise that developers and testers are taking advantage of the functionalities of Appium for this purpose.

Learn more about Appium [here](https://crossbrowsertesting.com/blog/appium/appium-native-web-hybrid-applications/).

## Limited Reporting and Documentation

While Selenium will exponentially increase your automated testing capabilities, as it's an open source tool, it is limited in its features and does not support much reporting on its own. For this purpose, Selenium is best complimented with a third-party tool like [CrossBrowserTesting](https://crossbrowsertesting.com/) that can capture screenshots and share reports through integrations like Slack and HipChat. However, you can also set up a framework to generate an output folder after a test with report information like errors, execution time, pass/fail count, etc., like TestNG.

Learn more about automated screenshot testing [here](https://crossbrowsertesting.com/automated-screenshots) and generating reports with Test NG [here](http://www.techbeamers.com/generate-reports-selenium-webdriver/).

## Multi-Tab Testing

Selenium has the ability to test in multiple tabs, but it might present as an obstacle if you don't know the correct commands. For example, if you want to open a new tab to perform a specific action without leaving the original tab, you'll still want to be able to control both tabs and go back to the parent tab if users are likely to perform these kinds of actions. The best method for this is to store the previous window handle in a variable and then continue in the new window and store that in a second variable. Then, you can use the switchTo method to go between both windows as needed.

Learn more about how to work with multiple windows [here](http://elementalselenium.com/tips/4-work-with-multiple-windows).

## No Manual Testing

Many testers will get excited about Selenium's capabilities and expect that they can automate everything when the reality is that this just isn't possible. In fact, a lot of automation relies on basic manual testing efforts. Rather, learning to [prioritize which tests to automate](https://crossbrowsertesting.com/blog/test-automation/prioritizing-test-automation/) will be beneficial to any tester. Additionally, as we mentioned, Selenium lacks capabilities for visual testing, which is important for testing beyond functionality to assess overall user experience. The most efficient way to do visual testing is by outsourcing to a third-party screenshot tool that integrates with Selenium.

Learn more about the need for manual testing [here](https://testlio.com/blog/manual-testing-matters/), prioritizing automated tests [here](https://crossbrowsertesting.com/blog/test-automation/prioritizing-test-automation/), and alternative visual testing with Selenium [here](http://testautomation.applitools.com/post/105435804567/how-to-do-visual-testing-with-selenium).

## Scalability

Again, while Selenium allows you to test on pretty much any browser or operating system, it's still limited in how many tests it can run at once and how fast it can run them based on how many hub/node configurations the tester has. And again, as your software scales, so must your testing. Without a Selenium grid, you can only test sequentially. However, with a Selenium grid and a device lab or a third party cloud tool like CrossBrowserTesting, you can test in parallel. This means multiples tests on different configurations can run at the same time, reducing the time it takes to run automated tests and increasing the configurations you can test on.

Learn more about parallel testing [here](https://crossbrowsertesting.com/blog/test-automation/what-is-parallel-testing/).

## Conclusion

One of the [best things about being a software tester](https://crossbrowsertesting.com/blog/test-automation/reasons-software-testing-career/) is that there's always something new to learn. As the industry shifted from manual to automation, testers were tasked with learning new skills such as programming.

Now, as they become more familiar with automation techniques and tools such as Selenium, it's admissible that they'll encounter more challenges as they explore and familiarize themselves with new testing trends. Fortunately, as software continues to evolve, experts can depend on insights and support from the rest of the testing community to make sure they're keeping up.

Release quality software faster with [TestComplete.](https://dzone.com/go?i=228240&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad) Discover how to decrease testing times and expand test coverage with the most robust automated UI testing tool. [Try free for 30 days.](https://dzone.com/go?i=228240&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad)
