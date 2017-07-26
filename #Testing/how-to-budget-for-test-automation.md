# How to Budget for Test Automation

_Captured: 2017-02-20 at 10:43 from [dzone.com](https://dzone.com/articles/how-to-budget-for-test-automation?utm_content=buffer3ad7d&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

According to this year's [World Quality Report 2016-17](http://www8.hp.com/us/en/software-solutions/capgemini-world-quality-report/), which is based on a global survey of 1,600 CIOs and IT leaders conducted by Capgemini, HP and Sogeti, 31 percent of all IT budgets is currently being spent on QA and testing. This amount is expected to grow to an eye-popping 40 percent by 2019. While participants recognized that [automation integration](https://www.getzephyr.com/resources/whitepapers/using-test-automation-frameworks-speed-your-devops-delivery) is a vital contributor to testing efficiency, the survey found that just 29% of testing activities are automated and that a high percentage of automation projects fail or don't result in the anticipated Return on Investment. One of the main reasons cited for this is the lack of long-term strategic planning when it comes to enterprise-wide automation of software testing activities.

## **Beyond the Test Automation Pyramid**

If your organization is building or has [DevOps Continuous Deployment](https://devops.com/i-want-to-do-continuous-deployment/) in place, then you're well on your way to strategically leveraging best practices in Agile testing, Continuous Integration, and test-driven development to accelerate your test QA processes and reduce cycle time. This includes automating as many tests as possible, including integration, GUI, API, component, and unit tests.

![](https://www.getzephyr.com/sites/default/files/agile%20pyramid.jpg)

> _Image Source: Cody Blog._

## **The Agile Test Automation Pyramid**

The testing pyramid is a popular strategy guide that QA teams use when in planning their testing efforts. As shown in the illustration above, the base or largest section of the pyramid is made up of Unit Tests -- which will be the case if developers in your organization are integrating code into a shared repository several times a day. This involves running unit tests, component tests (unit tests that touch the filesystem or database), and a variety of acceptance and integration tests on every check-in.

If your developers are practicing Test-Driven Development (TDD), they'll have already written unit tests to verify each unit of code does what it's supposed to do. Unit and component tests are the easiest tests to automate because they're usually run as part of an automated build since they're useful in providing developers with immediate feedback regarding potential issues in the latest release.

At the top or eye of the pyramid are the last tests that should be considered for automation, the manual exploratory tests, which are tests where the tester actively controls the design of the tests as those tests are performed and use information gained while testing to design new and better tests. Exploratory testing is done in a more freestyle fashion than scripted automated testing, where test cases are designed in advance. With a modern [application development process](https://www.getzephyr.com/resources/whitepapers/how-behavior-driven-development-can-fuel-your-software-testing-program) for software, however, it's possible to semi-automate these kinds of tests, which entails recording and playing back the test path taken by an exploratory tester during a testing session. This helps other agile team members recreate the defect and fix the bug.

The middle of the pyramid consists of Acceptance and GUI integration tests, which represent smaller pieces of the total number of automation test types that should be created.

Following the Test Automation Pyramid too literally can create problems in implementing -- and budgeting for -- an enterprise-wide software test automation project. The order of tests your company should attempt to automate should follow a standard business logic, meaning you may need to spend more time and money automating GUI tests if your software users expect a fast, rich and easy user interface experience. If you're developing an app for an Internet of Things (IoT) device that primarily talks to other IoT devices, automation of GUI testing is less of an issue.

## **Continuous Testing **

Building a successful Continuous Delivery pipeline with extensive test automation means creating a DevOps culture of collaboration among the various teams involved in software delivery (developers, operations, quality assurance, business analysts, management, etc.), as well as reducing the cost, time, and risk of delivering software changes by allowing for more incremental updates to applications in production. In practice, this means teams produce software in short cycles, ensuring that the software can be reliably released at any time.

As mentioned earlier, [test-driven development](https://dzone.com/articles/basics-test-driven-development) (TDD) requires developers, before they write any unit of code, to write an automated test for that code. Writing the automated tests is important because it forces the developer to take into account all possible inputs, errors, and outputs. TDD allows an agile team to make changes to a project codebase and then quickly and efficiently test the new changes by running the automated tests. The result of using TDD is that agile teams will accumulate a comprehensive suite of unit tests that can be run at any time to provide feedback that their software is still working. If the new code breaks something and causes a test to fail, TDD also makes it easier to pinpoint the problem and fix the bug.

![](https://www.getzephyr.com/sites/default/files/TDD.png)

> _Test-driven development. Image Source: Excirial._

![](https://www.getzephyr.com/sites/default/files/TDD%202.jpg)

_TDD 2.0: ATDD is an enhancement of TDD. Image Source: [Testdrivendeveloper.com](http://testdrivendeveloper.com/). _

## **Acceptance Test-Driven Development**

Acceptance test-driven development (ATDD) is an enhancement of test-driven development that promotes collaboration between business users, testers, and developers to define automated acceptance criteria before coding has begun. ATDD and TDD are complementary techniques: ATDD helps describe the high-level business objectives, while TDD helps developers implement them as requirements. ATDD helps ensure that all project members understand what is being implemented since failing ATDD tests provide quick feedback that requirements are not being met.

A key part of ATDD tests is that they are run automatically whenever a change is made to the source code. In addition to testing the application, automated acceptance tests are useful in measuring the progress your project team is making since, on an agile project, working software is considered to be the only objective measure of progress.

Another way to promote a collaborative DevOps culture is via behavior-driven development (BDD), an extension of test-driven development that encourages collaboration between developers, QA and non-technical or business participants on a software project.

## **Behavior-Driven Development (BDD)**

BDD extends TDD by writing test cases in a natural language that non-programmers and domain experts can read. BDD features are usually defined in a GIVEN WHEN and THEN (GWT) format, which is a semi-structured way of writing down test cases.

BDD features are written in the following format:

  * Describe who is the primary stakeholder of the feature.
  * What effect the stakeholder wants the feature to have.
  * What business value the stakeholder will derive from this effect.
  * Acceptance criteria or scenarios.

A brief example of a BDD feature in this format looks like this:

In TDD, the developers write the tests while in BDD the automated specifications are created by users or testers (with developers writing the underlying code that implements the test.)

In addition to promoting greater collaboration among developers, operations, testers, business analysts and management, TDD, ATDD, and BDD testing approaches improve traceability within your organization's software, from requirement to code to test case, which will reduce the cost of future changes and bug fixes.

## **Budgeting for Test Automation**

In a 2006 book, _[Global Software Test Automation: A Discussion of Software Testing for Executives_](https://www.amazon.com/Happy-About-Global-Software-Automation-ebook/dp/B0023RTC34/), authors Hung Nguyen, Michael Hackett, and Brent Whitlock said software development and software testing departments within a company need to have two separate budgets as they are two separate functions, "like sales and marketing." While Nguyen, Hackett and Whitlock offer useful and practical advice on test automation and the value of ranking test cases by order of importance -- "by impact on quality, by risk, by how often the feature tested is used, etc." -- their recommendation to allocate a separate budget for testing is not practical with the wide-spread adoption of the DevOps software deliver process in the past decade. An organization that practices DevOps is one in which the various teams involved in software delivery (developers, operations, quality assurance, management, etc.) collaborate on a continuous basis to make sure that software is released on time and runs without disruption.

DevOps also focuses on reducing the cost, time, and risk of delivering software changes by allowing for more incremental updates to applications in production. In practice, this means agile DevOps teams produce software in short cycles, ensuring that the software can be reliably released at any time. This is often done as part of a flow-based process known as a software release train that delivers software updates on a regular cadence in small batches. The advantage of using a DevOps cadence is that it lowers transaction costs and makes small batches of software more economically feasible.

## ** An Example of a Software Release Train**

A software release train is a release schedule in which multiple products are released at different times as part of an overall pre-planned schedule. This allows users to experiment with a newer product before adopting it for production, while continuing to use the previous "train's" point releases for their production systems. An example of a software release train in action is shown by this illustration from LibreOffice, a widely-used free and open source office suite that is an alternative to Microsoft Office.

![](https://www.getzephyr.com/sites/default/files/software%20release%20train.png)

> _Software release train for the LibreOffice project. Image source: LibreOffice._

LibreOffice developers and testers rely on a time-based cadence that does not wait for either features, or bug fixes --but is based (as much as possible) on time. This enforces discipline in introducing fixes, gives predictability, and allows more regular releasing. As a result, users get new major versions of LibreOffice every six months with a wide range of features, fixes, and enhancements. (They also get many pure bugfix micro releases.) The first version of a major release is intended for early adopters, while more conservative users are advised to wait for later bugfix releases.

## **Finding Resources for Test Automation**

DevOps is designed to remove the boundaries between the traditional silos of business, IT development, QA and IT operations, and to extend the agile and Lean principles from software development to the software release phase.

> "This process can only be successful if the Quality Assurance aspect is integrated and maximum automation is achieved in each step of the DevOps lifecycle," the World Quality Report states. 

Although test automation is a currently a major initiative in several large companies, many smaller organizations may lack the expertise and resources necessary for test automation. A good place to start developing that expertise is to adopt a test management tool and to become more familiar with the TDD, ATDD and BDD testing approaches outlined above.

A good way to find test automation resources may be to try a DevOps software release train similar to that used by LibreOffice in order to make the production of smaller batches of software more economically feasible. Focusing on smaller batches of software should make it easier to automate your testing process and increase how much agile testing is done, which, in turn, will improve the quality and time to release of your applications.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).

### Like This Article? Read More From DZone
