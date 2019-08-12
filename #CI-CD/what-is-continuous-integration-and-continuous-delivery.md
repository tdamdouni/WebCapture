# What is Continuous Integration and Continuous Delivery?

_Captured: 2018-12-31 at 19:14 from [dzone.com](https://dzone.com/articles/what-is-continuous-integration-andontinuous-delive)_

Continuous integration and Continuous Delivery are the processes in which your development team involves frequent code changes that are pushed in the main branch while ensuring that it does not impact any changes made by developers working parallelly. The aim of it is to reduce the chance of defects and conflicts during the integration of the complete project. Let's take a deep dive and learn more about the fundamentals of Continuous Integration and Continuous Delivery.

## What Is Continuous Integration?

Continuous Integration is a development methodology that involves frequent integration of code into a shared repository. The integration may occur several times a day, verified by automated [test cases](https://www.lambdatest.com/blog/17-lessons-i-learned-for-writing-effective-test-cases/) and a build sequence. It should be kept in mind that [automated testing](https://www.lambdatest.com/blog/automated-cross-browser-testing/) is not mandatory for CI. It is only practiced typically for ensuring a bug-free code.

### Benefits of Continuous Integration

Here are few benefits that have made continuous integration essential to any application development lifecycle.

  * **Early Bug Detection**: If there is an error in the local version of the code that has not been checked previously, a build failure occurs at an early stage. Before proceeding further, the developer will be required to fix the error. This also benefits the QA team since they will mostly work on builds that are stable and error-free.
  * **Reduces Bug Count:** In any application development lifecycle, bugs are likely to occur. However, with Continuous Integration and Continuous Delivery being used, the number of bugs is reduced a lot. Although it depends on the effectiveness of the automated testing scripts. Overall, the risk is reduced a lot since bugs are now easier to detect and fix early.
  * **Automating the Process**: The Manual effort is reduced a lot since CI automates build, sanity, and a few other tests. This makes sure that the path is clear for a successful continuous delivery process.
  * **The Process Becomes Transparent**: A great level of transparency is brought in the overall quality analysis and development process. The team gets a clear idea when a test fails, what is causing the failure and whether there are any significant defects. This enables the team to make a real-time decision on where and how the efficiency can be improved.
  * **Cost-Effective Process**: Since the bug count is low, manual testing time is greatly reduced and the clarity increases on the overall system, it optimizes the budget of the project.

## What is Continuous Delivery?

Continuous delivery is the process of getting all kinds of changes to production. Changes may include configuration changes, new features, error fixes etc. They are delivered to the user in a safe, quick and sustainable manner.

The goal of Continuous Delivery is to make deployment predictable and scheduled in a routine manger. It is achieved by ensuring that the code always remains in a state where it can be deployed whenever demanded, even when an entire team of developers is constantly making changes to it. Unlike continuous integration, testing and integrating phases are eliminated and the traditional process of code freeze is followed.

### Benefits of Continuous Delivery

If the best practices are followed, continuous delivery can help your application development in quite a few ways.

  * **Reducing the Risk**: The main goal of Continuous Delivery is to make deployment easier and faster. Patterns like blue-green deployment make it possible to deploy the code at very low risk and almost no downtime, making deployment totally undetectable to the users.
  * **High-Quality Application**: Most of the process is automated, testers now have a lot of time to focus on important testing phases like exploratory, usability, security and performance testing. These activities can now be continuously performed during the delivery process, ensuring a higher quality application.
  * **Reduced Cost**: When an investment is made on testing, build and deployment, the product evolves quite a lot throughout its lifetime. The cost of frequent bug fixes and enhancements are reduced since certain fixed costs that are associated with the release is eliminated because of continuous delivery.
  * **Happier Team and Better Product**: Since the aim of Continuous Delivery is to make a product release painless, the team can work in a relaxing manner. Because of frequent release, the team works closely with users and learn what ideas work and what new can be implemented to delight the users. Continuous user feedback and new testing methodologies also increase the product's quality.

Not only that, with the development and testing team working together in automating the deployment and build, developers can incorporate regression testing and integration in their daily tasks and reduce the amount of rework required in the traditional application development lifecycle.

## How Is Continuous Delivery Different From Continuous Deployment?

Continuous integration is usually the process when code changes made by different developers are integrated into the main code branch as soon as possible. It is usually done several times a day. The process ensures that code changes committed by individual developers do not divert or impact the main code branch. When combined with automated testing, it ensures that your code is dependable and can be moved into the next phase, i.e. testing or production.

Continuous deployment is somewhat similar to continuous integration. It is the process where your application can be deployed at any time to production or test environment if the current version passes all the automated unit test cases.

Continuous delivery is the methodology where your codebase can be deployed at any time. Apart from ensuring that your application has successfully passed all automated test cases, it also saved the configuration required to deploy the code in production, resulting in a faster application development lifecycle.

## How To Perform Continuous Delivery

Let's discuss the process flow:

  * The developer builds their code on the local system that has all the new changes or new requirements.
  * Once coding is completed, the developer needs to write automated unit testing scripts that will test the code. This process is optional, however, and can be done by the testing team as well.
  * A local build is executed which ensures that no breakage is occurring in the application because of the code.
  * After a successful build, the developer checks if any of his team members or peers have checked-in anything new.
  * If there are any incoming changes, they should be accepted by the developer to make sure that the copy he is uploading is the most recent one.
  * Because of the newly merged copies, syncing the code with the main branch may cause certain conflicts.
  * In case there is any conflict, they should be fixed to make sure the changes made are in sync with the main branch.
  * The changes are now ready to be checked in. This process is known as a "code commit."
  * After the code is committed, another build of the source code is run on the integration system.
  * The new and updated code is finally ready for the next stage, i.e. testing or deployment. In the next section, we shall discuss some basic checklist for continuous delivery.

## Continuous Delivery Checklist

The following checklist should be followed before you submit your code in order to create a smooth delivery process.

  * Before any changes are submitted, ensure that the current build is successful. If there are some issues, fix the build before any new code is submitted.
  * If the build is in the successful state, rebase your workspace to the configuration in which the build was successful.
  * In your local system, build and test the code to check if any functionality is impacted because of the changes you made.
  * If everything goes well, check in the code.
  * Allow competition of continuous integration with the new code changes.
  * If somehow the build fails, stop and go back to the 3rd step in the checklist.
  * If the build is successful, work on your next code.

## Tools Of Trade For Continuous Integration & Continuous Delivery

Although there are many tools used for continuous integration, we shall discuss a few top-rated tools that are used by well-known organizations and software professionals worldwide.

  * **[Jenkins](https://jenkins.io/):** An open-source Java-based CI tool that is platform independent. The best part is, it can be configured both using a console or a graphical user interface.
  * **[Team City](https://www.jetbrains.com/teamcity/):** This is a cloud-based CI server, developed by JetBrains. Although the enterprise edition is paid, there is a free version as well that allowed 3 build agents and a maximum of 100 builds.
  * **[Travis CI](https://travis-ci.org/):** One of the oldest Continuous Integration and Continuous Delivery solution, the tool is free for all projects that are open source. It is hosted on GitHub and based on your usage, you can choose the appropriate package from several options.
  * **[Gitlab](https://about.gitlab.com/):** The CI developed by GitLab is cloud-based, hosted on their official website. It is supported on multiple platforms and has both free and paid versions.
  * **[Circle CI](https://circleci.com/):** A cloud-based CI tool, it supports GitHub and languages like Node.js, Java, Ruby, Python, Scala, Haskell, and PHP. It allows the parallel building of your code.
  * **[Codeship](https://codeship.com/):** This is also another hosted tool that comes with basic as well as enterprise editions. The basic version comes with several packages and with expensive enterprise edition, it brings you more options to run parallel builds.

## Best Practices of Continuous Integration and Continuous Delivery

Let's discuss some best practices for Continuous Integration and Continuous Delivery that should be followed by all software professionals as well as organizations.

  * **Keep a Central Repository**: A large project involves multiple developers constantly pulling and pushing codes that are organized together to build the application. A revision control system should be kept that will help the team to get the latest clean code from the repository at any point of time during the development cycle.
  * **Automated Deployment and Build**: Automated build ensures that the team only gets the latest source code available in the repository and it is compiled every time before the final product is built. Automated Build cycle also allows the developers to push the code into different environments quickly, saving a lot of time.
  * **Include Automated Unit Testing**: This will help the team to detect bugs before the code is pushed in the repository. Unit testing, as well as interface testing, have greater clarity on the product's state before it is released. Testing phase becomes easier and issues can be fixed rapidly.
  * **Test in the Production's Clone**: Often an application that has passed all testing scenarios fails when it is deployed in production because of the environment is different. To prevent this, testing should be executed in an environment that is exactly the same as the production environment. This will allow testers and developers to understand how the application behaves before it is deployed into production.
  * **Commit the Code Everyday**: To prevent any conflicts, developers should make it a mandatory practice to commit the code every day in the repository. It provides very little scope to look for errors occurring due to conflicts. It also improves the communication between the team members and allows developers to divide their work into small sections and track the progress of their code.
  * **Build Faster**: Continuous integration fundamental purpose is to get feedback instantly after a build. A quick and perfect build keeps the development team ahead and prevents any bottleneck that may occur during unit testing.
  * **Everyone Can See What Others are Doing**: Continuous Integration and Continuous Delivery essential goal is to make the communication between team members smooth and effective. Everyone should have a clear idea regarding the state of the application and the latest changes that are made on it. Builds that have failed should be reported immediately to the stakeholders who can then make the relevant changes. IMs, Emails and other monitoring tools are used by various organizations to monitor the state of the builds.

Although the continuous integration and continuous delivery fundamentals discussed above may look simple, they are a bit complicated to implement. You will need to start a bit slower and buy in some extra time from the stakeholders to ensure that the team gets sufficient time to complete all the required procedures and deploy a quality product that has passed all the required test cases.
