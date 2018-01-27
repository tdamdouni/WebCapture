# Top 15 UI Test Automation Best Practices You Should Follow

_Captured: 2017-12-15 at 20:24 from [dzone.com](https://dzone.com/articles/top-15-ui-test-automation-best-practices-you-shoul-1?edition=345096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-15)_

In the past several years, I have heard many engineers from various projects complain about the stability and the reliability of UI automation tests. But are they really so unstable and unreliable? Believe me, they are not! It's true that UI automation testing is a hard and treacherous road that can be full of different holes. However, it's in your hands to make your UI automation framework a high-speed track instead of an old and an unstable country road.

In my experience, I have found that it is very difficult to come up with the exact rules you need to follow to create a well designed and maintainable automation framework with very stable tests. This is because there are always many exceptions from each rule. But despite that fact, there are principles that you should and should not follow in each particular case.

In this article, I will aggregate and define the 15 top best practices for creating a solid and maintainable UI testing automation framework. We will also go over some handy examples for each of these principles. In addition, I have prepared a fully working UI automation framework that was created following these mentioned principles below. You can use it as a starting point for your framework as well.

The example UI test automation framework and all the code snippets are based on the Java programming language. In addition, I have used Serenity test automation framework as a base framework for my solution, which worked great for me in a couple of past projects. But don't worry if Java language or Serenity are not the tools you plan on using for your framework creation. All the principles are still the same and you can easily apply the same rules on your situation as soon as you understand the main concept.

The example test project can be found through [this link.](http://%3Ca%20data-sumome-listbuilder-id%3D%22c296c051-4a25-4fc9-81f8-f91036cb7778%22%3Eclick%20here%20to%20subscribe%20to%20our%20newsletter.%3C/a%3E) Please, feel free to use, fork, improve and share your thoughts!

Before we dive into each principle, here is a summary of the best practices that I am going to talk about, for your convenience:

So, **the top 15 best practices for creating a UI test automation framework:**

  1. Do not rely **only** on UI test automation.
  2. Consider using a BDD framework.
  3. Always always ALWAYS use test design patterns and principles.
  4. **Never** use Thread.sleep() unless there are specific test requirements.
  5. Do not run ALL tests across ALL target browsers.
  6. Separate your tests from your test automation framework.
  7. Make your test automation framework portable.
  8. Name your tests wisely.
  9. Use soft assertions if you need to make a list of related checks on the same web page.
  10. Take screenshots for failure investigation.
  11. Make tests simpler instead of adding comments.
  12. Follow the "green tests run" policy.
  13. Use data-driven instead of repeated tests.
  14. All tests should be independent.
  15. Setup detailed automation tests reporting.

## 1\. Do Not Rely ONLY on UI Test Automation

One of the main best practices you should consider at first - do not rely on UI test automation alone. Ideally, you should be confident that if you remove your whole UI automation suite from the test cycle, you will be able to catch up to 90% of existing bugs in your release. You always need to remember that high-level tests should be only the third defense shield, for catching all the remaining issues that were not caught on the first two levels.

Which levels am I talking about?

![ui automation testing best practices](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/uiauto1.png)

This is a representation of the agile test pyramid initially designed by [Mike Cohn](https://www.linkedin.com/in/mikewcohn/), one of the most successful and wise Agile and Scrum instructors. It shows the recommended proportion of tests to be implemented on each test level, if you want to have a solid test automation pipeline.

Let's try to think why the pyramid was constructed this way. First, low-level tests are much faster by nature. Unit tests are faster than API tests while API tests are much faster than UI tests. Why is this important? Mainly, because faster tests give you faster feedback. Faster feedback from tests execution allows you to catch issues early on, saving you huge amounts of costs.

Second, low-level tests are executed much earlier in the [QA automation pipeline](https://www.blazemeter.com/blog/qa-automation-pipeline-learn-how-to-build-your-own?utm_source=blog&utm_medium=BM_blog&utm_campaign=top-15-ui-test-automation-best-practices-you-should-follow). Usually, unit tests are run before each commit in your repository. If this is true for your project, then you can even say that you do not only catch but you prevent bugs and do not let them get into the project repository. Of course, this also saves you a lot of costs.

Third, low-level tests are much more stable than high-level ones. When somebody asks me why I prefer more low-level tests in my test automation frameworks, I like to show them this picture. It nicely represents the stability of low-level tests (black) and high-level tests (white). That's why, in the automation process, I take the dark side first...

![ui automation testing guide](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/uiauto2.png)

This whole Agile test automation pyramid mentioned in the beginning of the paragraph was applied with great success in many famous companies across the world. That's why we have chosen to include it at the top of our best practices chart.

Don't understand me incorrectly. Of course, you should always run all of these test types! But you always need to think twice if you have some high-level tests that can be completely replaced by low-level, and having them in the UI suite is just redundant.

## 2\. Consider Using a BDD Framework

What is BDD? [BDD](https://www.blazemeter.com/blog/api-testing-with-cucumber-bdd-configuration-tips?utm_source=blog&utm_medium=BM_blog&utm_campaign=top-15-ui-test-automation-best-practices-you-should-follow) is a software development methodology in which software is implemented in the way its behavior is described. You can start from this [wiki page](https://en.wikipedia.org/wiki/Behavior-driven_development) if you have never heard about this methodology. BDD can be applied for any type of testing including unit tests, component, integration as well as for many other types. UI testing is one of the main areas where BDD can be applied with a great success. BDD is recommended for UI Automation, for many reasons.

First of all, BDD is a methodology that helps teams understand each other, creating strong outside and inside team collaboration. By writing your tests with BDD you also create specifications that can help your team understand tests and requirements much better. This means that along with writing your tests, you are creating a clear tests documentation. This ensures you don't waste other team members' time (who might work on your tests later), as well as your own time, because you don't need to explain and help with such tests if they are unclear.

Second, BDD helps the Business side (e.g.Test and Project managers) understand these tests. This brings additional value to testing because they can make recommendations based on business benefits.

Third, BDD usually forces you to follow a strict code organization pattern, which helps avoid code duplication. This is done by having separate components called steps or actions that will be the building blocks for your tests.

Now let's look at a simple example. Assume we want to write a very small test that verifies a basic workflow on the blazedemo.com website. Try to go over the test scenario and understand what it does:

That was easy, right? But let's imagine that you are the manager - how easy would it be for you to read such tests? Or let's assume that you are a new team member and you have to go over existing tests to understand what they do. Would you like to go over such tests or maybe you would be happier to see the same tests, written like this:

The second example is the same test written in BDD style using [Gherkin line-oriented languag](https://github.com/cucumber/cucumber/wiki/Gherkin)e in one of the most famous BDD frameworks - [Cucumber](https://cucumber.io/).

Even if you do not prefer to write tests in human-readable text files, there are plenty of options for applying the BDD model to your tests, no matter which programming language they are written in. For example, you can even put BDD style comments in your code yourself:

## 3\. Always Always ALWAYS Use Test Design Patterns and Principles

A design pattern is a reusable solution for a common problem in software design. We can say that each pattern is a particular example of a specific solution for a specific problem, regardless of the programming language or paradigm. Complementing design patterns, we have design principles. Design principles provide you with guidelines or rules that you need to follow for constructing well built and maintainable software. While patterns apply for specific issues, design principles apply regardless of context.

How is this relevant to UI Automation testing? As discussed before, UI testing is a hard and treacherous road full of different holes. But I have good news for you. You are not the first driver to travel this road. That's why there are almost no holes no one has ever passed through. You can think of design patterns and principles as powerful navigators. One tells you how to drive safely in general (design principle), while another gives clear instructions about how to handle each specific hole if it got in your way (design pattern).

In this section, I want to talk about two patterns: the **[Page Objects ](https://github.com/SeleniumHQ/selenium/wiki/PageObjects)**pattern, which has become the most popular web UI automation pattern among test automation engineers, and the **[Screenplay](http://blog.caplin.com/2017/01/04/screenplay-pattern-a-solid-alternative-pattern-to-page-objects/) **pattern, which organizes the **Page Objects** pattern and improves it.

The concept of the **PageObjects** pattern was introduced almost 10 years ago. Its purpose was to make UI automation tests consistent, to avoid code duplication, to improve readability and to organize code for web pages interaction. During web tests creation you always need to interact with web pages and web elements that are presented on these pages (buttons, input elements, images, etc.). The **PageObjects** pattern takes this requirement and applies [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming) principles on top of this, enforcing you to interact with all pages and elements as with objects.

For example, if you need to click on a button, you don't need to care about how to retrieve this button in the test, as it will already be handled in page objects. You should have the object of the page you are looking for and it should already contain the object of the button you are looking for inside it. All you need is to use a reference to this button object and apply the "click" action on it. You can think about all pages and web elements like this:

![automating your ui tests - here's how](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/uiauto3.png)

For each page and element, you need to interact with, you should create a separate object that will be a reference to this web element in your test. This is an example of the test written without the Page Objects pattern:

If we apply the **PageObjects** pattern and refactor the same test, we see an absolutely different picture:

You can find the working example of such a test in the [test project ](https://github.com/BushnevYuri/web-ui-automation-best-practices)under the_**"/src/test/java/ui/pageobject/FindFlightsSimplePageObjectExampleTest.java**_" location. Just go ahead and try it yourself.

To sum up, the **PageObjects** brings you these benefits:

  * Makes your tests much clearer and easy to read by providing an interaction with pages and application page elements.
  * Organises code structure.
  * Helps to avoid duplications (we should **never** specify the same page locator twice).
  * Saves a lot of time on tests maintenance and makes the UI automation pipeline faster => reduces costs.

If you want to you make this test even cleaner and more maintainable, you can introduce one more level of abstraction - steps or keywords. In different frameworks, you might see different names of these modules but the principles are the same. Steps (keywords) form modules of actions that you can reuse in any test. Once these steps (keywords) modules are written, all you need is to make a reference to the module in your test and you can use all the functionalities provided by these specific modules.

For example, if we create a module that aggregates all functionalities related to flights search on our website, then the test would look like this:

We have a handy example for this case as well, which you can find by _**"/src/test/java/ui/pageobject/FindFlightsPageObjectWithStepsExampleTest.java"**_ in the [test project.](https://github.com/BushnevYuri/web-ui-automation-best-practices)

But even if you use the **PageObjects** pattern, you might sooner or later run into a contradiction that will get you stuck with a framework that is very heavy to support. Why? Because in addition to design patterns, you need to take care of design principles.

For example, it's a common case when **PageObjects** pattern becomes the reason of an anti-pattern called "Large Class". This happens when you have too many elements on some of the pages, so the number of functions on an object that represents the page might become really huge (this is called "**LargeClass**" pattern). This goes against one of the most important design principles in object-oriented programming called **SOLID**:

  * **S**ingle Responsibility Principle
  * **O**pen Closed Principle
  * **L**iskov Substitution Principle
  * **I**nterface Substitution Principle
  * **D**ependency Inversion Principle

The main contradiction it goes against is the [Single Responsibility Principle](https://en.wikipedia.org/wiki/Single_responsibility_principle), which says that each class should have a single functionality. [Robert C. Martin](https://en.wikipedia.org/wiki/Robert_C._Martin) (one of the well-known software engineers and collaborators in **SOLID**) described this principle with these words: "A class should have only one reason to change." That's why **PageObjects** might contradict this principle, because page classes can contain hundreds of functions which do many different actions.

No worries, we are not going to cover the meaning of each principle in detail. You can go over many articles across the web to get an idea (e.g., you can start from wiki). But all you need to know for know that in order to follow **SOLID** principles with the **PageObjects **pattern, we should always care how we separate actions across pages and web elements and make additional [code refactoring](https://en.wikipedia.org/wiki/Code_refactoring) once in awhile to keep our framework maintainable.

Cue the **ScreenplayPattern**, which is designed to follow the **SOLID**principles from scratch. Briefly, **Screenplay** is the design pattern for acceptance tests (including UI tests) that allows you to easily follow **SOLID** principles. I recommend checking out [this article](https://dzone.com/articles/page-objects-refactored-solid-steps-to-the-screenp), which will give you an outstanding explanation of the **Screenplay** pattern and its usage in UI automation testing. But even without going into details, you can go over the same test we had before, but written with the usage of the **Screenplay** pattern, and feel the difference yourself:

The test looks awesome, right? You can find a fully working example in our [test project](https://github.com/BushnevYuri/web-ui-automation-best-practices), which has been implemented following these practices. It is located at _**"/src/test/java/ui/screenplay/FindFlightsScreenPlayExampleTest.java".**_

## 4\. NEVER Use Thread.sleep() Unless There Are Specific Test Requirements

This is a golden rule that you need to follow regardless of the complexity of your web application. Sleep or exact timeout (better known as Thread.sleep() function and analogs) block your test thread for an exact specified number of seconds. In other words, it gives you the ability to [pause](https://www.blazemeter.com/blog/how-pause-and-resume-load-tests?utm_source=blog&utm_medium=BM_blog&utm_campaign=top-15-ui-test-automation-best-practices-you-should-follow) your tests. When would you need such a capability?

The behavior of web applications depends on many factors like network speed, your machine capabilities or the current [load](https://www.blazemeter.com/load-testing?utm_source=blog&utm_medium=BM_blog&utm_campaign=top-15-ui-test-automation-best-practices-you-should-follow) on application servers. Because of all these factors, you cannot always predict how much time it will take to load a specific page or web element. That's why sometimes you might want to add a timeout and pause script check execution for at least a certain amount of time.

If you do not know how to deal with this in the right way, you will never see stability in your UI automation.

Let's assume that in our test we are going to open the home page and verify the heading of the main page. Extremely simple. You just need to implement two functions. One that opens the page and the second that verifies if the heading element is presented and has the right value. But what if we knew that our application can take up to 7-8 seconds to start?

Selenium, a web browser automation tool, works pretty fast and honestly saying, even faster than you. It can open the page in milliseconds and will try to get the text of heading element while the application itself is still starting. In this situation…. please, **NEVER **write a code like this:

This is the strongest killer of UI automation tests stability. Why? We lose time because you know that in 95% of cases, the application should be up and running in 7-8 seconds. Therefore, each time we lose about 2-3 seconds of execution time.

Do you think this is nothing? I have seen many projects that have about 3000 UI tests. Each time you need to open the application and wait until it is up and running. Maybe you even want to run it on 3 different browsers? 3000 (tests) * 3 (browsers) * 2.5 (lost seconds in average) = 22500 (seconds) = 375 (minutes) = **6.25 HOURS!** To sum up, in this situation we lose around 6 hours just because we do not want to create it properly.

What happens if application load takes 10.5 seconds one day? Just because of some network slowness. We will get failed tests. But when you try to run it locally on the next day, it works perfectly fine. This is one more example of the troubles you might get into by using this way of waiting in your tests.

I guess you see that it is bad, right? Then how should such a situation be managed? You can find the answer in the main [Selenium ](http://www.seleniumhq.org/)documentation - implicit and explicit waits! Exactly in this order. An implicit wait tells the browser to wait for a specified time for all elements. If a certain element is not found at this time, report this as a failure. If the element is found faster than the specified time, move on and do not wait the full time. For example, if the implicit wait specified 5 seconds but the element appeared after 2 seconds, then our script will not wait the rest of the 3 seconds. This is a huge time saver for your UI automation tests.

This is how you can specify the implicit wait in Java by using [Selenium](https://www.blazemeter.com/blog/how-automate-testing-using-selenium-webdriver-jenkins-and-allure?utm_source=blog&utm_medium=BM_blog&utm_campaign=top-15-ui-test-automation-best-practices-you-should-follow):

What is the explicit wait then? The explicit wait is designed for needs when a certain web element or action takes a much longer time to load than the rest. What if your application works in a way that it takes a long time to start (7-8 seconds) but after that, it works very fast? There is no sense to specify the implicit wait as 10 or even 15 seconds only because you have a slow application loading. For this, you can use the explicit wait, which waits for a certain condition for a specified amount of time.

Here is how we can rewrite our previous example by using the idea of the explicit wait:

In this case, we also do not waste any time and the script execution will continue immediately after the expected element will be found.

Looks clear, right? Not so clear as you might think… the official Selenium website displays this very important note: _"Do not mix implicit and explicit waits. Doing so can cause unpredictable wait times. For example, setting an implicit wait of 10 seconds and an explicit wait of 15 seconds, could cause a timeout to occur after 20 seconds."_

You can use [this](https://sqa.stackexchange.com/questions/12583/is-it-a-bad-practice-to-use-implicit-wait-in-selenium-webdriver-should-one-use) article as well as [this one](http://elementalselenium.com/tips/47-waiting) to learn why it is better and enough to use ONLY explicit waits.

## 5\. Do Not Run ALL Tests Across ALL Target Browsers

The main idea of this rule is that running all tests against all target browsers is redundant and unnecessary. We need to clearly understand what we are going to achieve by running our tests across different browsers. The main goal of this action is to perform browser-compatibility, to verify that application works correctly on all supported browsers.

But should we really run all tests on all browsers to verify that? Of course not. Browser-compatibility testing can be performed by a limited test suite, which has tests that interact with all web elements and perform all the main workflows at least once.

Now let's go over an example that will definitely help you to get the main idea. Let's assume that we need to verify search functionality for three browsers that we need to support (Firefox, IE, Chrome), as well as different search terms combinations (let's say we have 100 terms).

What would you do in this case? Are you going to run all 100 combinations for each browser? No, that doesn't sound wise... Let's start with the browser compatibility. All we need is to ensure that the search input, search button, and search result list elements all work fine for all 3 browsers. Should we run the search 100 times to verify that? Of course not! Just one time would be more than enough to verify the elements' behavior under the different target browsers.

All the other 99 combinations are required just to verify the relevancy of the search. They are not related to browser compatibility testing itself and therefore can be done by using even one browser. 99 tests in 1 browser instead of 3 browsers? Well… we **saved almost one hour of overall test suite execution. **Well done!

## 6\. Separate Your Tests From Your Test Automation Framework

To make your framework maintainable, you need to care about its structure. By structure, I mean the way you organize your code. The basic principles are simple - you should clearly separate your tests from your test automation framework functionality. In other words, each class in the tests section should represent a test site, while each function of such classes should be a test.

Let's assume that we have one project and all UI automation tests are supposed to test one web application. Then you might want to follow this separation approach:

![how to automate ui testing, tips and best practices](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/uiauto4.png)

You might have another situation when your system consists of several UI applications that are interconnected with each other. In this case, it is always better to create a separate module with your test automation framework that will be shared across separate test modules (for each application accordingly).

## 7\. Make Your Test Automation Framework Portable

I have seen many automation frameworks that require huge efforts to run them on another machine, unlike the one which was used for framework creation. This is a very bad practice because it doesn't allow new engineers or other team members to run tests, without struggling with setup troubles. And what if you need to run your tests on the CI server? It would be a very tricky task if your UI test automation framework is not portable. That's why we have a few tips that can help you avoid such issues.

First, do not store test automation files on your local machine! If you have test automation files that are required for tests execution, they should be attached to the framework. If they are relatively small, you can store them under the control version along with the framework itself. If they are big, then you can use external storage like [Amazon S3](https://aws.amazon.com/ru/s3/?sc_channel=PS&sc_campaign=acquisition_ND&sc_publisher=google&sc_medium=s3_b&sc_content=s3_e&sc_detail=amazon%20s3&sc_category=s3&sc_segment=192066474462&sc_matchtype=e&sc_country=ND&s_kwcid=AL!4422!3!192066474462!e!!g!!amazon%20s3&ef_id=WCYWkAAABbNpRQ3d:20171105230951:s) or any other cloud storage. Then, implement a mechanism that downloads these files to the right locations during the first test executions, if the files are not there yet.

The same principle goes for the web driver. For some reason, from project to project, I still see a lot of cases when web drivers are required to be installed in order to run tests. Moreover, sometimes you need a specific web driver version and if documentation is not so great you can spend many hours trying to see the first green tests. How should this be dealt with?

There is an excellent helper tool called [WebDriverManger](https://github.com/bonigarcia/webdrivermanager). It takes care of the whole driver download and configuration workflows. All you need to do is to configure one more additional java dependency in your framework, and all the web drivers will be downloaded and configured automatically! It's a miracle that doesn't require human interaction once you've decided to run your tests on another machine that doesn't have any web drivers installed.

The installation of the WebDriverManager is very simple and is covered in a few easy steps on [this page](https://github.com/bonigarcia/webdrivermanager). However, I found it not so straightforward when I did it for the first time for the Serenity framework.

Serenity has its own workflow of web driver configuration. I couldn't find a proper solution across the web so this section might be useful if you also decided to use the Serenity framework. The main idea of the solution is that Serenity has the mechanism of a custom web driver. All you need is to create a separate class that extends the DriverSource class of the Serenity framework and create the required driver by using the WebDriverManager:

After that, you just need to specify a few lines in your serenity.conf file settings file:

By using this configuration, you don't need to care about web drivers configuration anymore. Everything will be installed automatically and you will save a lot of time for the other engineers who work on the same project.

## 8\. Name Your Tests Wisely

Test names should be very clear and provide a self-descriptive idea about which exact functionality is being tested by using this test. Why? First, you need to immediately understand what each test verifies even a year after you wrote the test. In addition to that, you should always help your team members and make all your tests clear for them. Moreover, if some of the tests failed during tests execution run, you should understand which functionality was broken just by having a quick look at the test name. You should not waste time on verifying what the test actually does.

This is an example of a bad test name:

It is bad because it doesn't tell any details about the test scenario. This is an example of a well-named test:

This test name is much better because in the case of a failed test, you immediately understand which functionality failed and you don't need to go inside the test and verify which it actually does. It's just a matter of taste, but many engineers prefer to use the "_" separation approach instead of the CamelCase:

But again, this is just a matter of taste.

## 9\. Use Soft Assertions If You Need to Make List of Related Checks on the Same Page

Assertions are designed in a way that makes the test fail if the assertion fails. Initially, assertions were designed for unit tests. This is good practice since each unit test should make only one specific assertion.

But in UI automation you might want to verify several things in a row. Let's assume that you have several UI elements that you are going to verify and two of them have some unexpected values. With classic assertions, after test execution, you would notice only one error, after which the test would fail. This means that your test did a great job! It caught a bug! But…what about the second issue? How will you be able to catch this other issue? Right, only after the first issue is fixed. This might take days, sometimes weeks. That's why it's in our interest to catch all the issues right away! Here you can reap huge benefits by using the mechanism of soft assertions.

That's why it is useful to remember soft assertions. This type of assertions is used when you need to assert a condition but to let the test continue. By using soft assertions, your test execution flow will continue even if one of your assertions failed. At the end, it will sum up the list of failed assertions and let you know of all the found issues.

There are many ways to implement soft assertions. I prefer to use soft assertions via a powerful assertions framework called **[AssertJ**](http://joel-costigliola.github.io/assertj/assertj-core-features-highlight.html). If you've never heard about it, you should definitely go over my [other article](https://www.blazemeter.com/blog/hamcrest-vs-assertj-assertion-frameworks-which-one-should-you-choose?utm_source=blog&utm_medium=BM_blog&utm_campaign=top-15-ui-test-automation-best-practices-you-should-follow) that shows benefits that you can get from using 3rd party assertion frameworks.

Here is an example of soft assertions based on our test:

As always, you can find the fully working example in our [test project ](https://github.com/BushnevYuri/web-ui-automation-best-practices)at the _**"/src/main/java/pageobject/steps/BaseSteps.java" **_path.

## 10\. Take Screenshots for Failure Investigation

This best practice will help you save a lot of time when investigating the reasons for a test failure. You can implement a mechanism that will make a browser screenshot in case a test failed. If you don't have this mechanism yet or you have just started the creation of your UI test automation framework, please, keep in mind this important tip.

Depending on which tool you use or don't use, the implementation of screenshot creation for failed steps might vary. As for me, I prefer to use the awesome Serenity framework which has an in-built mechanism for screenshots creation. Moreover, it allows you to save the screenshots of all test steps for free because it is inbuilt framework functionality so you don't even need to care about it's implementation.

This is a small part of the report provided by Serenity, when you use this framework to handle your tests execution:

![Testing the User Interface with Automated UI Tests](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/uiauto5.png)

For each step accordingly, you can see the related screenshot, which shows the state of the web application during the test step. Extremely handy and useful.

## 11\. Make Tests Simpler Instead of Adding Comments

Tests should always be clear and simple to read. If you have a feeling you need to leave a comment to understand what is done in this line, then you need to take a step back and think again about what are you doing wrong. Let's assume that in this test we need to wait until the main page is fully loaded. We can do it this way:

Does it work? Yes! Is it clear? Well… we left a comment… so no! Please, never do this in your tests. Instead, you can just create a function, put this code inside and give this function a reasonable name. After that, in the test we can just replace this line with:

No comments are needed anymore. Try to simplify all your tests without any comments nearby.

## 12\. Follow the "Green Tests Run" Policy

On the one hand, this is one of the simplest principles. But on the other, most engineers ignore this rule. By the "green tests run" policy, we mean that if some tests failed and are red, then 100% you have an issue in your application under test.

Sometimes, there are situations when the application already has a list of bugs that are prioritized lower, and the team is not going to fix these issues in the foreseeable future. In this case, most of the test automation engineers just ignore these tests. They leave them inside the run and finish up with many red tests at the end of the test execution. Once the test execution is finished, they just go over the failed tests and verify all the red tests are those that are expected to fail due to these existing bugs, or whether there some new issues.

No and again no! This is not the way, based on best practices. First, each time when execution is finished you have no idea if you have some unexpected issues or not. If the result was red and it is still red, the execution run status tells you nothing. Second, to understand if you really had some unexpected errors or if all of these errors were expected, you need to spend some time. If it were only once, that would be fine. But tests results validation is a repeated process that you probably do on daily basis. You are losing a huge amount of time and effort by conducting the same unnecessary checks again and again.

Instead, if you have failed tests in your run that are expected to fail, the best thing you can do is to separate them to a separate run and ignore them in the main test execution. This will save you a lot of time when investigating failed builds. When you separate all the expected failures from the build, you know that if test execution results in at least one red failed test, then it is a real and new issue. In any other case, they should all be green.

## 13\. Use Data-Driven Instead of Repeated Tests

Data-driven tests are extremely useful when you need to test the same workflow by using different data. Let's assume that you want to verify a flights search between different cities. This is how tests would look like without the data-driven approach:

But what if you need to test 10 or 100 combinations? Our test file will grow very fast and become unhandy to use and unmaintainable. Mainly, because if we need to make a small change in the workflow itself, we need to apply the same change to all the tests! That's where data-driven tests can give you a huge benefit. By using data-driven tests, you can use only one test and one array of data, which we are going to use in order to run all the different data combinations:

Looks clean right? Now you have just one that you need to maintain. If you want to write one more test with an additional combination, all you need is to add the additional combination to the test data array.

You can find a great example of data-driven tests in [our project](https://github.com/BushnevYuri/web-ui-automation-best-practices) by the _**"/src/test/java/ui/pageobject/DataDrivenExampleTest.java" **_path.

## 14\. All Tests Should Be Independent

You might disagree, but I strongly believe that **ALL** tests should **ALWAYS** be independent. Dependencies will make your tests hard to read and maintain. You will definitely get into trouble during parallel automation runs because during parallel testing you cannot guarantee the order of your tests in the run. If you need to implement a precondition that is valid for many tests, just use the "[Before](http://junit.sourceforge.net/javadoc/org/junit/Before.html)" method and configure it in the way that it will run only once during tests execution.

## 15\. Setup Detailed Automation Tests Reporting

Test automation reporting is extremely important to optimize your work as a QA automation engineer. Ideally, you should not spend more than 10-20 percent of your time on the verification of test results from different test executions.

There are plenty of options about how you can proceed with this step. You can set up reporting by using basic test execution tools like TestNG (covered[ in this article](http://www.baeldung.com/testng-custom-reporting)). You can make an integration with tests management tools, like Zephyr, X-Ray or TestRail. Or, you can use a high-level framework that provides you with such abilities.

In my automation frameworks, I like to use Serenity frameworks, which give you outstanding live test reporting that shows all your tests grouped according to execution results, types, tags, functionality and so on. In addition to that, it has very detailed step notes for each test, which are extremely useful during results analysis. I highly recommend checking out our [test automation framework](https://github.com/BushnevYuri/web-ui-automation-best-practices), which was developed by using the Serenity framework. Now, try this reporting yourself. All you need to do is to execute all tests by running the specified command in the command line of the project root:

After that, the result report file will be located through this path: _**"/target/site/serenity/index.html".**_

![Automated GUI testing](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/uiauto6.png)

## Conclusion

UI test automation is not unstable. The stability of your UI test automation framework is only up to you. True, stable and reliable UI automation is hard work, but it's also fun. You have a choice at the beginning of your framework creation: are you going to use a tool that will help you reach your goal and solve your issues, or will you create software that you will fight with over and over on daily basis? To me, the answer is clear.
