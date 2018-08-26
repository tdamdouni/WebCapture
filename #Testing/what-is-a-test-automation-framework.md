# What Is a Test Automation Framework?

_Captured: 2018-08-10 at 19:26 from [dzone.com](https://dzone.com/articles/what-is-a-test-automation-framework-1?edition=385359&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-08-10)_

The DevOps Zone is brought to you in partnership with xMatters. xMatters delivers integration-driven collaboration that relays data between systems, while engaging the right people to proactively resolve issues. [Read this best practices guide and learn 4 steps that are critical to DevSecOps success](https://dzone.com/go?i=273425&u=https%3A%2F%2Fwww.xmatters.com%2Fresources%2Freports%2Fdevsecops-best-practices-guide%3Futm_campaign%3D70138000001F6XsAAK%26utm_source%3Ddzon%26utm_medium%3Dbanner%26utm_content%3Ddevsecops-best-practices-guide).

In the [Design & Architecture Series](https://www.automatetheplanet.com/category/series/designarchitecture/), we usually discuss themes how you can make your test automation framework better. However, I realized that many people have a wrong conception about what really is a test automation framework. So, in the next few articles, I will discuss what the test automation frameworks are, how they help us, what are the different types and so on. In the first article of these mini-series, I will try to define what exactly a test automation framework is.

## Terms Explained

Here I will try to explain a few terms that a vital to understand fully what a test automation framework is.

### Application

An application is computer software designed to perform a group of coordinated functions, tasks, or activities for the benefit of the user. In information technology, an application is a computer program designed to help people perform an activity.

The first conclusion we can make after this definition is that our automated tests are applications. So, as I continuously state in my articles, the people working on these types of tests should be good programmers following the best coding practices in mind. Whoever tells you that you can create "good" test automation without this is just lying to you. Sorry, the unicorns don't exist neither does the magical "codeless"/AI test automation tools.

### API

An API or application programming interface is a set of functions and procedures that allow the creation of applications which access the features or data of an operating system, application, or other service. A good API makes it easier to develop a computer program by providing all the building blocks, which are then put together by the programmer.

A software library (or just library) generally consists of pre-written code, classes, procedures, scripts, configuration data and more. All of the available functions within a software library can just be called/used within the program body without defining them explicitly.

A software framework (or just framework) is an abstraction in which common code providing generic functionality can be selectively overridden or specialized by user code providing specific functionality. Frameworks are a special case of software libraries in that they are reusable abstractions of code wrapped in a well-defined API, yet they contain some key distinguishing features that separate them from normal libraries.

**Software frameworks** have these distinguishing features that separate them from libraries:

  * **Inversion of control** -- In a framework, unlike in libraries or normal user applications, the overall program's flow of control is not dictated by the caller, but by the framework.
  * **Default behavior** -- A framework has a default behavior. This default behavior must actually be some useful behavior and not a series of no-ops.
  * **Extensibility** -- A framework can be extended by the user usually by selective overriding or specialized by user code providing specific functionality.
  * **Non-modifiable framework code** -- The framework code, in general, is not allowed to be modified. Users can extend the framework, but not modify its code.

A sub-type of frameworks providing generic code for testing different aspects of our applications- UI, API, security, performance and many other.

Many people confuse unit testing frameworks with test automation frameworks.

Unit testing frameworks are code libraries, modules and set of tools that help developers unit test their code.

Doing tests and regression testing completely manually, repeating the same actions again and again like a monkey, is error-prone and time-consuming, and people seem to hate doing that as much as anything can be hated in software development. These problems are alleviated by tooling. Unit testing frameworks help developers write tests more quickly with a set of known APIs, execute those tests automatically, and review the results of those tests easily. Unit tests are written as code, using libraries from the unit testing framework. Then the tests are run from a separate unit testing tool or inside the IDE, and the results are reviewed.

Programs, that can be combined together to accomplish a task.

Many people refer to [Selenium WebDriver](https://www.seleniumhq.org/) as a test automation framework but cannot be more wrong. Here is the official definition on their website.

"__Selenium automates browsers_. That's it! What you do with that power is entirely up to you. Primarily, it is for automating web applications for testing purposes, but is certainly not limited to just that. Boring web-based administration tasks can (and should!) be automated as well._"

So, Selenium WebDriver is mostly known as the standard for web automation testing but is actually a tool for controlling browsers that we later use in our software libraries and frameworks to write automated tests.

## Library and API

An API is usually related to a software library. The API describes and prescribes the expected behavior (a specification) while the library is an actual implementation of this set of rules. A single API can have multiple implementations (or none, being abstract) in the form of different libraries that share the same programming interface. For example, because C# and VB.NET compile to compatible MSIL, .NET developers can take advantage of any .NET API. Scala and Java compile to compatible bytecode, Scala developers can take advantage of any Java API.

## Framework and API

A framework can be based on several libraries implementing several APIs, but unlike the normal use of an API, the access to the behavior built into the framework is mediated by extending its content with new classes plugged into the framework itself. Moreover, the overall program flow of control can be out of the control of the caller and in the hands of the framework by inversion of control or a similar mechanism.

## Test Automation Framework Definition

Various guidelines, coding standards, concepts, processes, practices, project hierarchies, modularity, etc. to support automated testing. The user can follow these guidelines while automating application to take advantages of various productive results.

All things that we said about software frameworks are valid for test automation frameworks as well.

## Summary

In the next articles of these mini-series, we will talk about different types of test automation frameworks, what are the benefits of having one, what is the cost of building one yourself.

[4 Steps to an Effective DevSecOps Infrastructure](https://dzone.com/go?i=273426&u=https%3A%2F%2Fwww.xmatters.com%2Fresources%2Freports%2Fdevsecops-best-practices-guide%3Futm_campaign%3D70138000001F6XsAAK%26utm_source%3Ddzon%26utm_medium%3Dbanner%26utm_content%3Ddevsecops-best-practices-guide). Check out [xMatters](https://dzone.com/go?i=273426&u=https%3A%2F%2Fwww.xmatters.com%2Fsolutions%2Fdevops%2F%3Futm_campaign%3D70138000000quUrAAI%26utm_source%3Ddzon%26utm_medium%3Dbanner%26utm_content%3Dxmatters-website).
