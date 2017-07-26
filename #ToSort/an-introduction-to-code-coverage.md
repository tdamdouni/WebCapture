# An Introduction to Code Coverage

_Captured: 2017-05-25 at 10:20 from [dzone.com](https://dzone.com/articles/an-introduction-to-code-coverage?edition=300092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-24)_

Code coverage is a metric that can help you understand how much of your source is tested. It's a very useful metric that can help you assess the quality of your test suite, and we will see here how you can [get started with your projects. ](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=introduction-to-code-coverage&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content)

## How Is Code Coverage Calculated?

Code coverage tools will use one or more criteria to determine how your code was exercised or not during the execution of your test suite. The common metrics that you might see mentioned in your coverage reports include:

  * **Function coverage:** how many of the functions defined have been called.
  * **Statement coverage: **how many of the statements in the program have been executed.
  * **Branches coverage**: how many of the branches of the control structures (if statements for instance) have been executed.
  * **Condition coverage:** how many of the boolean sub-expressions have been tested for a true and a false value.
  * **Line coverage: **how many of lines of source code have been tested.

These metrics are usually represented as the number of items actually tested, the items found in your code, and a coverage percentage (items tested / items found).

These metrics are related, but distinct. In the trivial script below, we have a Javascript function checking whether or not an argument is a multiple of 10. We'll use that_ function_ later to check whether or not 100 is a multiple of 10. It'll help understand the difference between the function coverage and branch coverage.

**coverage-tutorial.js:**

We can use the coverage tool istanbul to see how much of our code is executed when we run this script. After running the coverage tool we get a coverage report showing our coverage metrics. We can see that while our _Function Coverage_ is 100%, our _Branch Coverage_ is only 50%. We can also see that the isntanbul code coverage tool isn't calculating a _Condition Coverage_ metric.

![Image title](https://dzone.com/storage/temp/5344575-cdmicro-600x338-retina2x-a-22-21-16.png)

> _Getting a Coverage Report in the Command Line_

This is because when we run our script, the else statement has not been executed. If we wanted to get 100% coverage, we could simply add another line, essentially another test, to make sure that all branches of the if statement is used.

**coverage-tutorial.js:**

A second run of our coverage tool will now show that 100% of the source is covered thanks to our two console.log() statements at the bottom.

![Image title](https://dzone.com/storage/temp/5344589-cdmicro-600x338-retina2x-a-22-31-46.png)

### Getting to 100% Coverage in All Criteria

In this example, we were just logging results in the terminal but the same principal applies when you run your test suite. Your code coverage tool will monitor the execution of your test suite and tell you how much of the statements, branches, functions and lines were run as part of your tests.

![Image title](https://dzone.com/storage/temp/5344590-cdmicro-600x338-retina2x-a-11-58-7.png)

> _istanbul for Javascript can show you a detailed report of coverage for each path_

## Getting Started With Code Coverage

### Find the Right Tool for Your Project

You might find several options to create coverage reports depending on the language(s) you use. Some of the popular tools are listed below:

  * Javascript: istanbul, Blanket.js
  * PHP: PHPUnit
  * Python: Coverage.py
  * Ruby: SimpleCov

Some tools like istanbul will output the results straight into your terminal while others can generate a full HTML report that lets you explore which part of the code are lacking coverage.

### What Percentage of Coverage Should You Aim For?

There's no silver bullet in code coverage, and a high percentage of coverage could still be problematic if critical parts of the application are not being tested, or if the existing tests are not robust enough to properly capture failures upfront. With that being said it is generally accepted that 80% coverage is a good goal to aim for. Trying to reach a higher coverage might turn out to be costly, while not necessary producing enough benefit.

The first time you run your coverage tool you might find that you have a fairly low percentage of coverage. If you're just getting started with testing it's a normal situation to be in and you shouldn't feel the pressure to reach 80% coverage right away. The reason is that rushing into a coverage goal might push your team to write tests that are hitting every line of the code instead of writing tests that are based on the business requirements of your application.

For instance, in the example above we reached 100% coverage by testing if 100 and 34 were multiples of 10. But what if we called our function with a letter instead of a number? Should we get a true/false result? Or should we get an exception? It is important that you give time to your team to think about testing from a user perspective and not just by looking at lines of code. Code coverage will not tell you if you're missing things in your source.

### Focus on Unit Testing First

Unit tests consist in making sure that the individual methods of the classes and components used by your application are working. They're generally cheap to implement and fast to run and give you an overall assurance that the basis of the platform is solid. A simple way to increase quickly your code coverage is to start by adding unit tests as, by definition, they should help you make sure that your test suite is reaching all lines of code.

### Use Coverage Reports to Identify Critical Misses in Testing

Soon you'll have so many tests in your code that it will be impossible for you to know what part of the application is checked during the execution of your test suite. You'll know what breaks when you get a red build, but it'll be hard for you to understand what components have passed the tests.

This is where the coverage reports can provide actionable guidance for your team. Most tools will allow you to dig into the coverage reports to see the actual items that weren't covered by tests and then use that to identify critical parts of your application that still need to be tested.

![Image title](https://dzone.com/storage/temp/5344592-cdmicro-600x338-retina2x-a-10-49-26.png)

> _SimpleCov for Ruby can show you which methods have not been tested_

### Make Code Coverage Part of Your Continuous Integration Flow When You're Ready

When you've established your [continuous integration (CI) workflow](https://bitbucket.org/product?utm_source=dzone&utm_medium=paid-content&utm_content=introduction-to-code-coverage&utm_campaign=bitbucket_adexp-bbtofu_dzone-syn-content) you can start failing the tests if you don't reach a high enough percentage of coverage. Of course, as we said it earlier, it would be unreasonable to set the failure threshold too high, and 90% coverage is likely to cause your build to fail a lot. If your goal is 80% coverage, you might consider setting a failure threshold at 70% as a safety net for your CI culture.

Once again, be careful to avoid sending the wrong message as pressuring your team to reach good coverage might lead to bad testing practices.

### Good Coverage Does Not Equal Good Tests

Getting a great testing culture starts by getting your team to understand how the application is supposed to behave when someone uses it properly, but also when someone tries to break it. Code coverage tools can help you understand where you should focus your attention next, but they won't tell you if your existing tests are robust enough for unexpected behaviors.

Achieving great coverage is an excellent goal, but it should be paired with having a robust test suite that can ensure that individual classes are not broken as well as verify the integrity of the system.

## Are You Using Bitbucket to Accomplish Your Company's Mission?

[Share your company's mission with #Forthecode](http://ow.ly/MR9m30bQrbT) for a chance to be featured on our homepage, our social media channels, or [win a free t-shirt! ](http://ow.ly/MR9m30bQrbT)

[Bitbucket's mission](http://ow.ly/FyfF30bQr2Y) is to help teams solve real-world problems. Our customers select Bitbucket because it supports professional teams building things with a purpose. We want to share what you're doing with the rest of the world.
