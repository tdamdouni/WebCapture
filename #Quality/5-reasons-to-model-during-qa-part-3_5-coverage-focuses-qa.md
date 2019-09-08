# 5 Reasons to Model During QA, Part 3/5: Coverage Focuses QA - DZone DevOps

_Captured: 2019-09-06 at 21:52 from [dzone.com](https://dzone.com/articles/5-reasons-to-model-during-qa-part-35-coverage-focu?edition=521312&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202019-09-06)_

Welcome to part 3/5 of 5 _Reasons to Model During QA_!

This five-part blog series considers the benefits of introducing Model-Based Techniques to QA. It considers five reasons for adopting modeling, [the theme of an upcoming Curiosity webinar of the same name](https://zoom.us/webinar/register/WN_t0qHtPWuTDKNwVLO2d2fEQ). 

[Part one](https://dzone.com/articles/5-reasons-to-model-during-qa-part-15-shift-left-qa) of this series discussed how modeling enables “shift-left” QA, eradicating potentially costly defects as they arise during the design phase.

[Part two](https://dzone.com/articles/5-reasons-to-model-during-qa-part-25-automated-tes Test Generation) then shifted focus “right,” to testing code built from the requirements. It considered the significant time gains achieved by generating test cases, test scripts, and test data automatically.

Model-based testing thereby makes it possible to test complex applications sufficiently, even within short iterations. Today’s article continues this theme, focusing in particular on the test coverage gains that accompany the increased testing efficiency.

## Manual Test Creation Leaves Systems Exposed to Costly Defects

Manual test creation is not only slow and repetitive, but leads to the undesirable combination of over-testing and under-testing. Overall test coverage remains low, while certain logic is wastefully tested repeatedly. QA, in turn, does not mitigate the risk of damaging defects sufficiently, leaving a system exposed to costly bugs.

The sheer complexity of modern applications means that creating test cases manually and unsystematically cannot reach the coverage required for true quality assurance. Multi-tiered systems have a multitude of interrelated components, as demonstrated in the following dependency map:

![Test Coverage](https://curiositysoftware.ie/wp-content/uploads/2019/07/Test-Coverage.png) _A dependency map created from around 100,000 lines of C# code. This map only shows the relationships between the components in the system. The picture becomes vastly more complex once the intertwined logic contained in each component is factored in._   


The above dependency map reflects an application with around 100,000 lines of code, and modern applications will typically contain millions of possible paths through their logic. This is more than any one person could comprehend in their head, and 2018 research suggests that 66% of organizations struggle “merely deciding what to test.” [[1]](https://curiositysoftware.ie/2019/07/5-reasons-to-model-during-qa-part-3-5-coverage-focuses-qa/#_ftn1)

Manual test creation typically, therefore, undertests complex systems severely. The tests tend to pick off the most obvious, “happy” path scenarios first, testing these expected behaviors repeatedly. Negative scenarios and unexpected results go untested, when it is these outliers that can cause the most severe defects in production.

The result is resource-intensive, wasteful over-testing that nonetheless leaves systems exposed to bugs. Low test coverage persists even with test execution automation, as executing tests automatically does nothing to improve the quality of the test suite itself. Instead, a measurable and systematic approach to identifying what to test is needed, along with an efficient and systematic method for creating those tests.

## Model-Based Test Generation: Systematic and Measurable

Model-Based testing enables such a systematic and measurable approach to test case design. It harnesses the power of computer processing and the reliability of mathematics to identify all the tests contained in massively complex systems. This is possible even when the logic is greater than any human mind could comprehend.

[Part two](https://dzone.com/articles/5-reasons-to-model-during-qa-part-25-automated-tes) of this series set out how mathematically precise flowcharts enables the automated identification of every path through the models. Each logical journey is equivalent to a test case, and [automated algorithms](https://curiositysoftware.ie/automated-test-case-design/) can, therefore, identify every test in the flowchart. Using [The VIP Test Modeller](https://curiositysoftware.ie/vip-test-modeller/), subflows can additionally be used to embed lower-level components within master models, rapidly creating comprehensive test cases for complex systems:

![](https://curiositysoftware.ie/wp-content/uploads/2019/07/Test-Coverage-with-Subflows.png) _Subflows integrate lower level functionality into master flowcharts, enabling rapid and reliable test case generation for complex systems._ __

Generating tests from models introduces measurability to test design. Test coverage is proportional to the logic contained in model, and tests can be generated touch all the logic contained in the model at least once.

Multiple algorithms might be used, for instance, to test every logical step (node) in the model, or cover every connecting “edge” (arrow) between the blocks at least once.

These techniques generate the smallest number of tests needed to cover the model, reducing testing time while still covering every positive and negative scenario. Testing, in turn, avoids wasteful over-testing, while still testing every distinct combination of logic and data once.

Generating tests from logical models further maximizes observability, reducing the likelihood of false positives and of bugs masking bugs. Testers can instead know that their tests got the right result, for the right reason, providing true assurance of the quality of a system.

## Targeted Testing: Reliable, Risk-Based Testing

It is rarely feasible to execute every test case associated with a complex system in a single iteration, and exhaustive testing should instead be reserved for the most high-risk, high visibility functionality. Fortunately, Model-Based testing also enables reliable risk-based testing, focusing test creation on critical functionality.

The VIP Test Modeller makes reliable, risk-based test design possible. Several coverage profiles can be created for a given model, setting requisite coverage levels for tagged features. Automated test generation will then create the smallest set of tests needed to satisfy the coverage levels by feature, while testing the untagged logic in a model to a specified coverage level:

![Test Coverage Profiles](https://curiositysoftware.ie/wp-content/uploads/2019/07/Test-Coverage-Profiles.png) _A coverage profile created for a login screen focuses on testing negative scenarios. The generated test cases will target scenarios where invalid data is entered into the screen. “Happy path” scenarios will be ignored, while logic contained in the surrounding model will be tested to a medium level of coverage._

This granular approach to test coverage enables QA teams to focus testing on high-risk functionality. Testing might focus on the negative paths that can cause the most severe defects in production. Coverage profiles might also be created for targeted regression, focusing on features that failed in the last test run, or on features that have been recently updated.

Model-Based Testing provides the flexibility to dynamically explode test coverage, focusing in detail on given parts of the system. Combined with the improved efficiency of automated test creation, QA can test more functionality in short iterations while also mitigating against the negative risk of defects as much as possible.

This is particularly true after a change has been made to a complex and vast system, the subject of the next article in this series.

If you would like to find out more about Model-Based Testing, please [sign up to join Curiosity Software Ireland and Lemontree for the September 5 Webinar: “Five Reasons to Model During QA”](https://zoom.us/webinar/register/WN_t0qHtPWuTDKNwVLO2d2fEQ)

_[[1]](https://curiositysoftware.ie/2019/07/5-reasons-to-model-during-qa-part-3-5-coverage-focuses-qa/#_ftnref1) Vanson Bourne and Panaya (2018), survey of over 300 IT decision makers in the UK and US. Cited from Islam Soliman (2018), “AI & automation vs humans: the future of software testing?”, DevOpsOnline (16-11-18). Retrieved from <http://www.devopsonline.co.uk/14159-2-ai-and-automation-vs-human-testers/>on 05-12-18._
