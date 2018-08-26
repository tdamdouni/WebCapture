# Getting Started With Test Automation: How to Structure Your Team

_Captured: 2018-06-29 at 17:23 from [dzone.com](https://dzone.com/articles/getting-started-with-test-automation-how-to-struct?edition=383278&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-06-29)_

[Discover How Software Testing Kills DevOps](https://dzone.com/go?i=296431&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fhow-software-testing-kills-devops%2F%3Futm_source%3DDZone_Resources%26utm_medium%3DWhitepaper%26utm_campaign%3DDZoneDevOps%26utm_content%3DST-DevOps) and how software testing is still dominated by yesterday's tools and outdated processes. Brought to you in partnership with [Tricentis](https://dzone.com/go?i=296431&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fhow-software-testing-kills-devops%2F%3Futm_source%3DDZone_Resources%26utm_medium%3DWhitepaper%26utm_campaign%3DDZoneDevOps%26utm_content%3DST-DevOps).

Test automation has always been important for increasing the speed, accuracy, and repeatability of testing-but Agile and DevOps had made automation an imperative. Nevertheless, test automation rates remain dismally low: well under 20%. One way to boost your likelihood of success is to start off with an effective structure for automation. The following article, by Tricentis' Max Bauer, presents several field-tested models for structuring teams for test automation.

I'd like to share some proven practices for a few different test automation adoption scenarios that have helped numerous organizations enjoy long-term success...

![](https://www.stickyminds.com/sites/default/files/shared/2018-04-16%20MaximilianBauer%20For%20Sustainable%20Test%20Automation%2C%20Look%20beyond%20the%20Surface%20image1.png)

## Automation Team Rolling Out Test Automation Project by Project

The best piece of advice I can give is to start with the small things, then go big. The proven first practice is to start by creating an automation team.

This team will iterate through the different projects and start automating the most important test cases. This lets you demonstrate progress on the initiative and gives you some insight into how application changes impact key application functionality.

I recommend starting with the most impactful test cases: the ones that cover your top business risks. This creates the foundation for a powerful regression portfolio that can provide fast feedback on whether application changes broke previously working functionality.

The automation team should include at least one test design specialist, who starts by reviewing the requirements and using test case design approaches to map out the test cases that should be automated. Then, the test design specialist or one of the two or three automation specialists can evaluate if test data management (TDM) is needed, and they can collaborate on defining the test cases. Meanwhile, the test design specialist will take care of the next project.

Depending on the software you want to test and how much you have customized it, an automation engineer could be required. They will ensure that custom controls are created and later maintained.

The size of the team will increase over time, depending on the number of test cases and projects the team has to handle. These suggestions are only for the initial rollout. As soon as the rollout starts progressing, you'll want to start recruiting more people as soon as possible.

Once the test cases are automated, they can run on test virtual machines overnight, then report execution results on a daily basis. The most important thing for getting test automation up and running is to actually run test cases! If you're not running your tests, you're not receiving any value from them, no matter how well-designed your test suite is and how well it covers your top business risks.

Depending on your company structure (agile or not, testing teams or independent testers), the automation team may take the lead on educating everyone about the overall automation best practices to apply and the project variations they should consider as they start their own test automation.

Before testers start applying test automation, a decision must be made: Who is responsible for the test cases? This is critical. If the automation team (or maybe later the regression team) is responsible, then they have to communicate much more with the testers and the business side. If it's the testers' responsibility, they need enough time to ensure all test cases are running and meet business expectations. Each organization needs to decide what's best for them, depending on their structure and working style.

Regardless of which direction you take, be sure to save enough time for communication. On one hand, new test cases need to be reviewed by the regression team and then set up for execution. On the other hand, the regression test results (especially failed test cases) need to be shared so that responsible team members or testers can review them and update the tests if needed. At a minimum, ensure that testers independently check regression results and make the appropriate adjustments so that the regression team can pull new test cases from a shared folder and review them on their own.

![](https://www.stickyminds.com/sites/default/files/shared/2018-04-16%20MaximilianBauer%20For%20Sustainable%20Test%20Automation%2C%20Look%20beyond%20the%20Surface%20image2.png)

## Regression Team Leading and Mentoring Testers on Each Project

The most effective setup I've seen is to establish an initial automation team that evolves into a regression team once the test automation foundation is established and others are prepared to drive it forward.

The regression team remains responsible for creating test cases in initial projects, maintaining existing test cases, running test cases, guarding the testing infrastructure, and overseeing the broader test automation setup and project. You could call this team the test center of excellence.

With this setup, it's possible to have projects and bigger changes steered through test design specialists, who will take care of the right format and provide an overview of what it should look like. They are like software architects (or, in our case, test architects).

The regression team is the "go-to group" if you have questions regarding problems or you want to drive new innovations. The ownership and responsibility should be the regression team's because they have the best overview of the test portfolio.

From a resource view, you need highly skilled people in the regression team, but you could get away with less experienced team members as testers. If the testers need more knowledge than the trainings provide, they can always ask the regression team, who can then help by sharing the knowledge they have built up.

## Adaptations for Agile Environments

For agile environments, test automation is driven by an agile tester within the team. This person should be more advanced than an automation specialist-they need to understand test case design, requirements, test case creation and execution, and core testing best practices, and they need a good understanding of what to test and how to test it effectively.

I recommend a continuous setup for development and testing from sprint to sprint:

![](https://www.stickyminds.com/sites/default/files/shared/2018-04-16%20MaximilianBauer%20For%20Sustainable%20Test%20Automation%2C%20Look%20beyond%20the%20Surface%20image3.png)

When development finishes with the feature of Sprint n-1, testing starts. Meanwhile, development can continue with feature 2 (Sprint n), and so on. Just be sure to reserve time for fixing bugs and further improvements.

[Get a reality check on the Best (and Worst) Use Cases of Testing in AI](https://dzone.com/go?i=296432&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fhow-software-testing-kills-devops%2F%3Futm_source%3DDZone_Resources%26utm_medium%3DWhitepaper%26utm_campaign%3DDZoneDevOps%26utm_content%3DST-DevOps) and how AI will soon become part of our day-to-day quality engineering process. Brought to you in partnership with [Tricentis](https://dzone.com/go?i=296432&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fhow-software-testing-kills-devops%2F%3Futm_source%3DDZone_Resources%26utm_medium%3DWhitepaper%26utm_campaign%3DDZoneDevOps%26utm_content%3DST-DevOps).
