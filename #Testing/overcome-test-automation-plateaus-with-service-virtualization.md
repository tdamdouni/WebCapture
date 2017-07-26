# Overcome Test Automation Plateaus with Service Virtualization

_Captured: 2017-06-06 at 10:11 from [www.stickyminds.com](https://www.stickyminds.com/article/overcome-test-automation-plateaus-service-virtualization?page=0%2C2)_

Basic service virtualization scenario:

![Basic service virtualization scenario](https://www.stickyminds.com/sites/default/files/shared/2017-04-10%20AlexanderMohr%20Overcome%20Test%20Automation%20Plateaus%20with%20Service%20Virtualization%20image2.png)

> _Advanced service virtualization scenario:_

![Advanced service virtualization scenario](https://www.stickyminds.com/sites/default/files/shared/2017-04-10%20AlexanderMohr%20Overcome%20Test%20Automation%20Plateaus%20with%20Service%20Virtualization%20image3.png)

> _Advanced service virtualization scenario_

Orchestrated service virtualization is sometimes called _t__est-__d__riven __s__ervice __v__irtualization_ because it focuses on simulation from the perspective of the test and places the tester at the center of service virtualization asset creation and management.

Service virtualization also provides a simple way to test how your AUT behaves against edge cases and error conditions that would be difficult to configure in a staged test environment. For example, assume that your account management system interacts with multiple dependent systems (a CRM, location system, and order processing system), and you want to automate tests that validate how your AUT reacts when different combinations of dependent systems are down, delayed, or behaving incorrectly. Or, assume that you want to automate a test that validates how your AUT reacts when its expected messages are sent or received in an incorrect order. Service virtualization helps you simulate these conditions so that you can automate the broad range of tests required to effectively cover your risks.

### Applying Service Virtualization to Boost Test Automation

For an idea of how these strategies are applied by testers in the field, consider the following example from one of the largest European communications providers.

Testers in this organization already had the challenging task of testing a rather complex sales-to-activation process. This process started with various touch points (e.g., a mobile application as well as a web interface) and processed the order through the full end-to-end system chain, which included back-end order processing systems, a CRM, and various billing and provision systems. These transactions involved more than two hundred dependencies communicating via HTTP and SOAP, with both ESB-driven and batch transactions. Further complicating testing, the process involved a huge number of variations, including private, small-business, and enterprise segments with distinctly different product characteristics.

  


As you can imagine, this was always a difficult system to test, even with four- to eight-week testing windows. However, once the team adopted two-week agile sprints and expected continuous testing, they realized they needed a new approach: a way to dramatically accelerate testing speed without compromising their high quality standards.

They knew that increasing test automation was essential for achieving this goal. However, their test automation efforts were limited due to test environment instability that caused false positives and interrupted test execution. To move past this barrier, they needed a reliable and cost-effective way to ensure that required dependencies were all available for testing--with the proper test data--every time an automated test executed.

Their first step in tackling this challenge was adopting service virtualization. They initially used service virtualization to simulate behavior associated with unstable systems in their test environment. They created service virtualization scenarios for their test case portfolio by recording the service requests--essentially, learning from the existing systems with minimal effort.

Committed to advancing automation, the team proceeded to apply a more advanced level of service virtualization. This time, they began by focusing their service virtualization efforts on all the dependent system behavior required to test. Starting with their two most important systems of engagement, they simulated all required dependency behavior based on their existing test case portfolio and service virtualization recordings.

By doing this, they fully decoupled each system, enabling a full integration test as part of their continuous integration and continuous deployment process. As a result, they could deploy rigorously tested systems to their staging environment for the final end-to-end tests.

![Service virtualization for integration testing and end-to-end testing](https://www.stickyminds.com/sites/default/files/shared/2017-04-10%20AlexanderMohr%20Overcome%20Test%20Automation%20Plateaus%20with%20Service%20Virtualization%20image4.png)

> _Service virtualization for integration testing and end-to-end testing_

Building upon the success of their initial efforts, they soon expanded the approach from the original two systems to forty-two systems. This enabled them to transition from their original four- to eight-week testing windows and complete testing within two-week agile iterations.

### Ensuring Fast, Quality Test Feedback

If you can guarantee that all the dependent systems associated with your end-to-end tests will always be available, operating correctly, and configured with appropriate test data every time your automated tests execute, you might not need service virtualization. But for everyone else, it's vital for achieving the sustainable, scalable test automation required for continuous testing, agile, and DevOps.

Providing the team with fast, quality feedback is one of the top goals of test automation. The goal of service virtualization is to ensure that test environment issues don't impact the speed, accuracy, or completeness of that feedback, so you can satisfy business expectations for quality at speed.
