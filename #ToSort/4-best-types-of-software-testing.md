# 4 Best Types of Software Testing

_Captured: 2018-05-18 at 14:43 from [dzone.com](https://dzone.com/articles/4-best-types-of-software-testing?edition=376324&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-05-18)_

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309721590%3B137110683%3Bb), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309721590%3B137110683%3Bb).

There's a wealth of great content on the internet when it comes to software testing. As a DevOps consultant, though, I still regularly get asked about testing best practices. So, I thought I'd collate the information into one place as part of a short series on Software Testing.

When it comes to making code changes, there are a variety of tests you can perform to ensure everything is working correctly. Testing is fundamental to building quality into software. By making sure you gain fast feedback on code to make impactful changes sooner rather than later. The rate at which you can ship or merge code depends entirely on the speed with which you can test it!

The top four types of testing produce very different outcomes, and there are certain benefits and downsides to each of them. Which testing method is most beneficial? This article covers the differences in the four primary types of tests and determines which is the most valuable to your development pipeline.

## Unit Testing

Unit tests refer to the different methodologies and functions used to test the individual parts, components, and modules that make up the whole of your software. The tests are usually low level, and also relatively inexpensive to automate. Build an abundant number of Unit tests into your pipeline early. Split these into two categories; locally-run rapid sub 10-second tests and those that take more time. Move longer tests to your Continuous Integration pipeline to minimize the negative impact slower tests can have on dev productivity.

Unfortunately, Unit testing is often frequently overlooked or considered to be unimportant in favor of Integration tests. And in order to shorten development time and save financial resources, Unit testing is sometimes the first thing to be cut from projects by customers.

One of the great things about Unit tests, though, is that you can verify separate modules and functionalities prior to merging them together to be tested as a whole later. Unit testing should occur throughout the process and prior to Integration testing or System testing. This is recommended for a variety of reasons. These include bug prevention, to document trial and error throughout the code, clarify specifications with the Product Owner, and perhaps most importantly, save time and money.

Although problems can arise throughout any project, it is always simpler to fix the earlier you identify a problem. Unit tests prevent and eliminate potential issues before they even have the chance to become a problem. Even though Unit tests will not identify and solve all of the problems you may run into, they can still help prevent deadlines being pushed back.

## Smoke Testing

Another popular test is the Smoke test. In terms of time frame, these should be sub 15-minute tests. as their aim is to spot leaks quickly. Commonly referred to as "Build Verification Testing," this method verifies that critical elements and functions of the software are working properly. Therefore, create tests that identify common faults. Now, this method of software testing is not going to provide you with in-depth details about each function. However, the results will indicate as to whether or not you should proceed with further testing. If the software fails a Smoke test, it is best to go back and do a rebuild with the required fixes in place. Otherwise, you will lose time and effort running further detailed testing.

Like Unit tests, Smoke tests are most helpful in exposing issues early, and you can coordinate the two together. Smoke tests can also confirm if previously made changes are negatively affecting major areas of the program or not. Smoke tests can also be expanded as needed as well. This will allow you to automate testing throughout the application. Overall, use Smoke tests early and often. But they are not truly independent tests, as they work well with other test types.

## Integration Testing

Once you have completed multiple components of your software--including Unit tests on each individual element--you may want to run an Integration test. This type of test will allow you to verify that the varying components of your software will work well together. A downside to Integration tests is that they are more expensive to run than Unit tests. This is partly because they require multiple parts of the software application to be operational. The benefit of Integration tests is that interactions between components that do have errors will be brought to light by the test. Making their expense worthwhile. If you have not run Unit tests on each component, you may run into additional work and time fixing individual components in order to integrate them.

There are a few different ways to approach Integration testing. You can wait to implement Integration testing once the whole software is available. However, this may allow errors to continue throughout other stages of development until that point. Alternatively, some individuals prefer to use the Top Down or Bottom Up methods. Either the top-level or bottom-level units are tested first and then each level is tested step-by-step until completed. These two methods can be combined in an approach known as the Sandwich or Hybrid. Whichever method you use, verify that Unit tests are complete on each component. And try to complete Integration testing prior to System testing.

## Acceptance Testing

After you have spent time running Unit tests and Integration tests, you may want to run an Acceptance test. Use these tests to verify the software meets the client's or business' needs. Again, this type of testing is more expensive to run than Unit tests. On top of that, the entire software must be available and operational in order to perform Acceptance testing. Acceptance tests focus more on replicating user behavior than the other three test types, but they offer a measurable performance of the software. They also provide a way for the client/product owner to reject different changes you have made if they do not meet certain needs.

Companies tend to start out with manual acceptance tests, often in the form of peer code review. As development pipelines become more sophisticated the trend is to automate these tests and even outsource them. Execute Acceptance testing via different methods.

  * Canary Deployment: Run acceptance tests through canary deployment to make sure there are no misconfigurations with the production environment.
  * Alpha Testing: Which is usually completed by members of the business who are not directly involved in other aspects of development or testing, i.e., product management or customer support.
  * External Acceptance testing: Which is run by individuals who are not associated with the group who has developed the software. Sometimes customers of the client or end users perform Acceptance testing, depending on the needs of the organization.

Each test type has its time and place in your development pipeline, but Unit testing can address the most crucial needs of the process and highlight many errors sooner than the others, saving time in the pipeline. Which is why Unit testing should be the foundation you start with as part of your development process. This practice is vital to DevOps implementation to prevent errors being carried further downstream and having an impact on other team members within the pipeline. Fast feedback and problem-swarming in this manner ensure quality assurance rather than quality control.

Use Unit testing in conjunction with other types of testing or independently. As such tests can be run with all--or only parts--of the software operating. It can be automated or maintained manually as well. Though DevOps best practices encourage automating as much of your testing as possible. Another major advantage of Unit tests is that the practice helps ensure minimal testing time, preventing lost time and effort. With clients putting more and more focus on wanting to constantly update and provide changes to their end users, Unit tests will ensure that customers are regularly kept up to date with the latest software innovations.

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309721589%3B137110681%3Bh) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309721589%3B137110681%3Bh).

Topics:

software testing ,unit testing ,smoke testing ,acceptance testing ,integration testing ,devops
