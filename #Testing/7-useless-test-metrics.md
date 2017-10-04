# 7 Useless Test Metrics

_Captured: 2017-09-21 at 11:08 from [dzone.com](https://dzone.com/articles/7-useless-test-metrics?edition=326502&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-20)_

[Transform incident management with machine learning and analytics](https://dzone.com/go?i=239227&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fanalytics-machine-learning-incident-management-ebook.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Five_Strategies_Dzone_eBook-AB-03-f-08162017%26cc%3Dpt%26elqcid%3D4046%26sfcid%3D7011O0000027vq2) to help you maintain optimal performance and availability while keeping pace with the growing demands of digital business with this [eBook](https://dzone.com/go?i=239227&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fanalytics-machine-learning-incident-management-ebook.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Five_Strategies_Dzone_eBook-AB-03-f-08162017%26cc%3Dpt%26elqcid%3D4046%26sfcid%3D7011O0000027vq2), brought to you in partnership with BMC.

Software test metrics take a quantitative approach to software development by measuring the quality and effectiveness of the software testing process. Dev teams use test metrics to keep track of software quality at all stages of the development process. Test metrics are also useful at the executive level by allowing stakeholders to assess the efficiency of software development teams.

Test metrics should always be meaningful and actionable. The problem is that some test metrics do not achieve this goal. Many metrics are misleading, some are little more than vanity measurements, while others are simply meaningless.

![Image title](https://dzone.com/storage/temp/6589071-dzone-test-metrics-featured.jpg)

The following examples of useless test metrics can help you better understand whether your test metrics are providing the type of insight you need.

## 1\. Number of Test Cases Executed

This is a poor metric for the simple reason that it doesn't tell you what the test cases are testing.

The original idea behind this metric was that the more test cases we have developed, the more comprehensive our testing is. In reality, many test cases do not contribute to test coverage at all. Many test suites contain deprecated tests that are no longer relevant in new versions of the software. Test cases can be inefficiently designed so that they overlap and essentially test the same functionality.

In these and many other cases, having more test cases is not a good thing, and might be an indication of a bloated and overly complex test suite.

## 2\. Number of Bugs Found Per Tester

One reason that this is a poor metric is that measuring anything per tester is not a good practice--it encourages excessive competition and discourages cooperative teamwork, which is strongly encouraged in Agile organizations.

Some companies go as far as basing employee compensation on how many bugs found per software tester, which is especially detrimental to the goals of the team because it tends to inhibit the sharing of information and promote an "every man for himself" attitude.

Furthermore, one employee might be testing a stable software feature, while another tests a buggy, unstable feature. The latter would be regarded as performing better under this metric because he finds more bugs, which is [plain silly](https://thedailywtf.com/articles/The-Defect-Black-Market).

## 3\. Percentage Pass Rate

Using percentage pass rate as a metric is a bad idea because it is easy to manipulate this measurement with behavior that you don't want to encourage in your software development team.

For example, the testing team might focus on executing easier tests that are more likely to pass, thus improving the pass rate. Alternatively, the team could break up one long test into many smaller ones, artificially boosting the percentage pass rate. In other words, this metric is fickle and prone to manipulation.

## 4\. Unit Test Code Coverage

Code coverage is another commonly used metric that is often used incorrectly. Code coverage is the percentage of lines of code which are covered by unit tests. Code coverage can give you a completely false picture of actual test coverage, for two reasons.

First, unit tests are not a comprehensive test of your software. They merely test that a specific micro-component within your code is functioning as expected. Even if all the components in your car are tested and working perfectly, there is no guarantee the car will start.

Second, this metric says nothing about unit test quality. A unit test can consist of elegantly designed code that tests all relevant inputs and outputs of a method or function. Or it can be a sloppy mess that tests only some of that functionality, or other irrelevant or deprecated functionality. Covering code with more and more sloppy unit tests will not do anyone any good.

## 5\. Percentage of Automation

The percentage of automated test cases is, in many cases, a vanity metric. Automating more and more of your tests is not meaningful if the automated tests don't test functionality as well as the old manual tests. Or if the software changes so quickly that automated tests quickly break and need to be completely refactored.

Another aspect hidden by this metric is test duration. Adding more and more Selenium tests to automate UI testing is a great idea. But running those tests can increase build times from minutes to hours. In today's reality of very frequent releases, such tests will be meticulously built, only to be skipped in the build process by teams in a rush to deliver.

## 6\. Cost Per Defect

This is possibly the oldest metric for software quality, which was used within IBM as early as the 1960s. The metric attempts to place a price tag on a bug--how much it costs to identify a bug, fix it, and verify it. The common conception is that fixing bugs very early in the development cycle is [much cheaper](https://www.jrothman.com/articles/2000/10/what-does-it-cost-you-to-fix-a-defect-and-why-should-you-care/) while fixing them in late stages of testing, or in production, is extremely expensive.

Measuring cost per defect in different stages of the development cycle is a great idea. However, some teams measure cost per defect in an attempt to make software maintenance more efficient.

The main problem with this is that defects can have different implications on the quality of the software and the user experience. Some bugs are "cosmetic" and hardly impact a software's users. Other bugs, such as security issues, can cause catastrophic problems if not addressed. A software team might, for example, focus on cosmetic bugs and dramatically decrease the cost per defect, but at a detriment to software quality.

## 7\. Defect Density

Defect density is the number of confirmed defects detected in software. It is common to assume that a lower defect density equates to lower software quality, but this isn't really true.

One problem with defect density is that the quantity of bugs depends on how testing is structured and reported, and on the skill of software testers. A software problem could be reported as one bug, as 15 bugs capturing different aspects of the problem, or not reported at all because testers didn't find it. So defect density can vary dramatically for the very same software.

## Conclusion: Three Testing Challenges

There are three challenges in today's testing world which are closely related to [test metrics](https://www.sealights.io/resources/test-metrics):

  1. Finding a way to simultaneously increase testing quality and speed. Continuous testing is a practice that helps to increase software quality while keeping pace with fast iterations. Metrics are crucial in a continuous testing environment, to ensure that software quality really increases, instead of being eroded, between iterations.

  2. Preventing untested code changes from making it into production. No software has true 100% test coverage (even if it has 100% code coverage, which as mentioned above, is not the same). Traditional pass/fail metrics don't tell you whether a recent code change has been tested. If it's not tested, metrics won't reveal the risk inherent in releasing that part of the software.

  3. Collecting quality metrics for analysis in a single place. There are numerous testing tools that provide QA dashboards. But these are typically focused on measuring the progress or work done by a testing team. Some of them show metrics which, like the above, are fickle or misleading. Today's dashboards do not provide enough meaningful measurements to reveal the real trend of software quality.

Real metrics that actually provide useful information and help you to understand the quality of your software are hard to come by.

New platforms, such as [SeaLights](https://www.sealights.io/), a platform for measuring true test coverage in an Agile environment, are changing the testing landscape by providing test metrics that are more useful and more representative of software quality. Specifically, a holistic measure of test coverage across all types of automated and manual tests; a "holy grail" metric which reveals the risk inherent in every Agile release.

Software development has grown up with the advent of Agile, and so has testing, but metrics are far behind. It is paramount to identify, measure, and practice the real metrics that can help Agile teams make software better.

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=227260&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).
