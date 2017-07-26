# The Essence of Mobile DevOps Is to Destroy Silos

_Captured: 2017-02-28 at 11:28 from [dzone.com](https://dzone.com/articles/the-essence-of-mobile-devops-is-to-destroy-silos?edition=271921&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-27)_

[Mobile DevOps](http://bitbar.com/deep-dive-on-devops-in-mobile-app-testing/) is a practice of bringing the different disciplines involved in developing, testing, releasing, and operating software into being functional inside organizations or by a team that works closely together. By bringing together developers (Dev) and operations (Ops), the team is able to continuously deliver their product based on continuous feedback and iteration. And as always, there are different practices, habits and different flavors of adopted company cultures that set the behavior for an actual process and daily doing.

In this blog, we'll take a look at the most common and widely accepted Mobile DevOps 'process' with its steps and what those mean. In addition, the focus is to provide insights on how enterprises can get rid of 'siloes' inside their organizations for dynamic development, testing, deployment, and monitoring.

The Mobile DevOps adoption by enterprises has been done different ways depending on various factors. Adopted tools, processes, company culture and [industry for which mobile app is produced](http://bitbar.com/who-should-include-mobile-monitoring-in-their-devops-process/) make their own flavors in the adoption of mobile DevOps practices.

Used tools required to build and test against a production-like environment, deployment done with a repeatable and trustworthy process, and monitoring and constant verification of the process flow are those principles that vary depending on organization's scope and the [level of Mobile DevOps adoption](http://bitbar.com/7-process-steps-with-mobile-devops-tools/).

As there are plenty of Mobile DevOps practices and all tools that are used have different use cases. Sometimes, those tools and processes involved in mobile app creation can overlap each other in the overall Mobile DevOps process. In this blog, we'll also take a look at different phases of the process and how mobile DevOps can help you to get rid of siloed thinking.

## Typical Delivery Pipeline for Android and iOS Apps

Today's mobile app developers and organizations behind those apps are increasingly investing in mobile monitoring systems that can capture a bunch of metrics from production and development, all in real time. The growing trend of using [synthetic mobile monitoring](http://bitbar.com/synthetic-monitoring-and-real-user-monitoring-whats-the-best-approach/) for apps makes following up of app behavior, performance and even user experience in production with real-life conditions easier, effortless and the most importantly, provides with those details that mobile app can be optimized and improved for end-users.

But mobile monitoring is just one part of the entire development life cycle. If that's not well-aligned with [build, test, and deployment part of the flow](http://bitbar.com/the-basics-of-mobile-continuous-integration-workflow/), you might not get the best outcome out of your development.

The following picture illustrates the typical delivery pipeline for mobile apps today:

![Delivery Pipeline for Android and iOS Apps](http://bitbar.com/wp-content/uploads/2017/02/Screen-Shot-2017-02-20-at-12.17.40-PM.png)

Today, any aspect of app development is tightly coupled with continuous integration. The agile methodology and agile practices have made continuous integration highly popular as it has enhanced the way developers work, collaborate and integrate their work together.

## Continuous Integration Is the Heart of the Mobile DevOps

The continuous integration with regular daily routines produce lots of data about the mobile application, regressions, and compatibility of each developer's contribute, and discovering issues early exposes integration flaws, even incompatibility of developer's doings, and makes better time consumption and schedule estimating easier and more accurate.

![CI is Vital for Mobile DevOps](http://bitbar.com/wp-content/uploads/2017/02/Screen-Shot-2017-02-22-at-12.15.10-PM.png)

Building an application is an everyday job for mobile app developer organizations. In Mobile DevOps, organizations use a variety of version control systems, source code management (SCM) setups, different practices for merging code and notifying everyone about the build status.

## Test Automation Is a Vital Part of Mobile DevOps

Testing - and especially the use of test automation - has been one of those functions that had the "[shift-left](http://bitbar.com/synthetic-mobile-monitoring-in-devops-process/)" due to DevOps adoption. Testing is also one of those key areas that define the quality aspects of the software; despite no error, bug or issue is fixed by QA, all or at least majority of those should be discovered during this phase of the mobile DevOps flow. As [continuous integration and deployment have several goals for testing](http://bitbar.com/the-basics-of-mobile-continuous-integration-workflow/), the testing steps should be always automated to ensure seamless flow, rich and detailed results, and adequate verification of mobile application.

[Continuous quality and testing](http://bitbar.com/deconstructing-continuous-quality-process/) basically mean testing each regression, build, and continuously practice this throughout the development lifecycle. Early testing, early validation, and frequent testing ensure thatquality is built into the application can be verified and issues to be tackled early. When Mobile DevOps is concerned of a production-like or real environment, the mobile app testing should always go on with real mobile devices.

In addition, there are a bunch of good reasons why Mobile DevOps process [should not consider using emulators/simulators](http://bitbar.com/rely-only-on-real-emulators-vs-devices/) in this stage.

## Deployment Is About Packaging and Releasing Product to End-Users

Looking from the technical point, packaging an app includes tools for package repositories and other storage mechanisms for the binaries created in the build step. Repositories, also known as artifact or asset repositories - contain all assets required and associated with binaries to facilitate deployments such as scripts, configuration files and additional infrastructural files for deployment.

The [continuous deployment](http://bitbar.com/using-fastlane-for-continuous-delivery-of-ios-apps/) adoption may not be ideal for every company (and developers), but the practice that enables releasing and deploying can also enable a seamless of a delivery pipeline and flow for Mobile DevOps. This kind of flow facilitates continuous deployment of applications to testing and then all way to production, in automated and efficient manner. The package step clearly supports the goal of continuous deployment to package and release new versions of applications, with new features, to end-users.

However, release management and deployment planning with every release require collaboration across stakeholders. Release management tools allow organizations to plan and execute releases, provide a single collaboration portal for all stakeholders in a release, and provide traceability for a release and its components across all stages of the build and delivery pipeline.

## The Essence of Mobile DevOps Is to Get Rid of Silos

The model presented above indicates that there are "silos" with this sort of process. Regardless of if the process includes tools and technology to seamlessly move application through all these steps, it still includes barriers on each and every step that are not necessarily well streamlined.

![The Real Scope of Mobile DevOps](http://bitbar.com/wp-content/uploads/2017/02/Screen-Shot-2017-02-20-at-12.23.13-PM.png)

The scope of mobile DevOps is to get rid of silos and streamline the process between the build and the production (including testing and deployment) phases. In fact, there should not be even phases when thinking about how mobile app development is done and adopted by development organizations.

The adoption of mobile DevOps starts from the source code building that includes the use of continuous integration. Each and every release should be pushed for real device testing. This testing setup should include a large number of real mobile devices used by the target audience. This type of use of automation produces enormous amounts of data (logs, videos, screenshots, performance statistics etc.) that should be then absorbed by DevOps and issues fixed by developers.

## The Importance of Mobile Monitoring in App Development Process

The modern way to monitor mobile apps in the production environment is a synthetic mobile monitoring. By the industry, it has been called with different names but I like to call it 'user experience monitoring' as it describes the used methodology, target, and environment the best.

The [user experience monitoring](http://bitbar.com/the-value-of-user-experience-monitoring-for-mobile-apps/) is a modern monitoring practice using synthetic and proactive monitoring methods that replicate the real user interactions for mobile apps, [games](http://bitbar.com/how-will-devops-boost-mobile-game-quality/), and mobile websites. The results from mobile monitoring can guide developers, IT and mobile DevOps to improve their apps and significantly [enhance the end-user experience of the application](http://bitbar.com/the-importance-of-agile-and-devops-for-end-user-experience/).

There is also an important aspect of making sure organization gets (only) valid data about the process, results in each step, and the outcome. Continuous monitoring provides that sort of data and metrics to the organization to evaluate all different functions of the process: development, operations, testing/QA, personnel and other individuals involved in the process. It's important to remember that these metrics should not be measured only in production but during the process itself. When done properly as part of the process, enhancing and changing the daily doings is easier and will have an impact for all steps
