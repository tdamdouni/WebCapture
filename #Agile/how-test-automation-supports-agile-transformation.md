# How Test Automation Supports Agile Transformation

_Captured: 2018-07-11 at 07:45 from [dzone.com](https://dzone.com/articles/how-test-automation-supports-agile-transformation?edition=385216&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202018-07-10)_

**The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=275424&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dfooter). Learn how DevOps and SAFe® can be used either separately or in unison as a way to make your organization more efficient, more effective, and more successful in our [SAFe® vs DevOps eBook](https://dzone.com/go?i=275424&u=http%3A%2F%2Fpages.aspeinc.com%2FSAFe-vs-DevOps.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Dsafe_vs_devops%26utm_content%3Debook).**

## Agility in IT Processes

In a world where new business models are disrupting established revenue streams and expectations of the customer experience are constantly increasing, businesses everywhere are struggling to stay relevant. To stay competitive requires efficiency: fast market adaptation, well-organized change management, and the ability to secure emerging opportunities. One of the ways to get there is through Agile transformation.

In short, the aim of Agile transformation is for businesses to reach a state of change readiness that let them embrace the unknown. Internally, this means establishing a smooth and predictive path for converting ideas into practice. The actual implementation of Agile principles is usually done by introducing new ways of managing projects and development processes in a company, i.e. Scrum and/or SAFe (Scaled Agile Framework). Although Agile transformation is relevant for every business, companies whose value chain is largely based on IT processes tend to be the first to embrace the concept of agility. Not surprisingly, Scrum, SAFe, etc. are first and foremost applied to the IT processes in enterprises, especially in software development.

Before the introduction of Agile development, projects were often managed using the "waterfall model." With this approach, each discipline had a dedicated focus and place in the project timeline. A project would begin with an outlining of all requirements for the software to be developed. Then developers would begin building the software - this could take months or even years - and then testers would take over the final product and begin testing it. Not surprisingly, the waterfall model has proven to be too rigid an approach for modern software development.

## Agile Development

In an Agile project model, there is no dedicated, focused time for each discipline. Instead, the project timeline is broken into iterations, called sprints, that involve all disciplines: scoping, development, testing, and more. Typically, the duration of a sprint is two to four weeks depending on the number of people involved, the maturity of the department, etc.

> **Working in short, focused iterations combined with the lack of a dedicated testing phase presents a challenge to testers: how and when to verify the quality of the software in its entirety.**

As shown in the figure below, the number of features in a software will accumulate as sprints are completed. Assuming that the project is not supplied with additional test resources along the way, the accumulation of features means that during each sprint, testers will only have time to test the recently developed features and will not be able to do regression testing, i.e. testing how the new features affect existing features.

![The regression issue](https://dzone.com/storage/temp/9531962-graphic-the-regression-issue.jpg)

> _The regression issue_

_**FIGURE 1 - The regression issue:** As features to be tested accumulate,  
and with a fixed amount of testing resources available, testers are forced make to compromises._

The regression testing issue is a well-known problem in software development. Agile development has just accentuated the problem; with iterative sprints, it has become increasingly difficult to answer questions such as "How is the quality?" and "When can we do a release?".

## Automated Regression Testing

Of course, one way to solve the regression testing problem would be to hire more testers. However, this would increase project costs significantly and is not a scalable solution. Another approach could be to go back to doing end-to-end testing from time to time, but this would defeat the purpose of agility. This leaves us with just one option: automation.

With test automation - in this case, automated functional UI testing - robots are instructed to execute the repetitive, predictable test scripts allowing testers to focus on testing the new features of the latest sprint. The figure below illustrates how test automation supplements the testing efforts during sprints.

![Automated regression testing](https://dzone.com/storage/temp/9531971-graphic-automated-regression-testing.jpg)

> _Automated regression testing_

_**FIGURE 2 - Automated regression testing: **Robots take care of regression testing,   
while testers continue to focus on testing new features._

With test automation implemented, it would still be the testers themselves designing test cases and monitoring the results, but the main regression efforts are carried out by robots. To sum up, automation reduces risk by ensuring that any uncertainties are limited to the recently developed features.

## An Agile Automation Strategy

[LEAPWORK](http://www.leapwork.com)'s approach to test automation is that all testers on a team should have ownership of the automation effort; each tester should be enabled to build automated test cases and to monitor and analyze the results. If an entire team can take part in utilizing automation, then each team member will also reap the benefits, and have time freed up for testing new features.

In other words, for test automation to truly support the objective of being Agile, the underlying automation strategy should not be dependent on only a few technical specialists. Instead, the strategy should be based on making automation a natural part of each tester's profession. This will make test automation much more efficient and scalable.

## Key Takeaways

  * Agile transformation is an attempt of reaching a state of readiness, including fast market adaptation, well-organized change management, and the ability to secure emerging opportunities.
  * Applying the Agile approach to software development presents a challenge to testers: how and when to verify the quality of the software in its entirety.
  * With iterative sprints it has become increasingly difficult to answer questions such as "How is the quality?" and "When can we do a release?"
  * Test automation reduces risk by ensuring that any uncertainties are limited to the recently developed features.
  * All testers should be empowered to utilize automation in their daily work, and a test automation strategy should not be dependent on only a few technical specialists.
![Test Automation - LEAPWORK Guide](https://dzone.com/storage/temp/9531985-cluster-banner-test-automation.png)

> _Test Automation - LEAPWORK Guide_

**Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F). **

Topics:

test automation ,testing ,software testing ,agile testing ,agile development ,devops ,automation ,agile
