# Is Continuous Deployment right for your business?

_Captured: 2017-04-08 at 19:32 from [blogs.starcio.com](http://blogs.starcio.com/2017/04/continuous-deployment-right-for-your-business.html?utm_campaign=Content&utm_content=52296661&utm_medium=social&utm_source=twitter&m=1)_

![](https://2.bp.blogspot.com/-rL7HM2dLvYI/WOD-5Gpi_ZI/AAAAAAAAcFo/XPKRvYtVyBgc1UE1f-c3j5m229Fm0VYCACEw/s280/Continuous%2BIntegration-Delivery-Deployment.JPG)

It's easy for technologists to target a challenging architecture or development practice, after all, they love solving technical challenges. So as automation has become a key capability of software development, and organizations have begun to adopt [DevOps practices](http://blogs.starcio.com/2015/01/the-what-why-and-how-of-devops.html) many development teams are striving for the "holy grail" of continuous deployment.

Some product owners also love the notion of continuous deployment. Ask for a feature today, build tomorrow and deploy the same day. Seems too good to be true.

My question to you is, do you have all the technical capabilities to truly enable continuous deployments? Is your business ready to establish a competitive advantage with this capability and has the right mindset and culture to support experimentation? Are the application users ready to embrace rapid changes to the user experience and workflows? Does your organization have the size and scale of application development that warrants the investment in continuous deployment?

##  Continuous Integration vs. Delivery vs. Deployment

To answer these questions, let's start with the basics by reviewing the three practices of continuous integration, continuous delivery, and continuous deployment.

Most experts agree that continuous integration, the automation of integrating code, building software packages and executing automated test cases is an important baseline for development teams. Even for the smallest teams, the ability to click a button or run a command to see that the changes implemented have successfully been incorporated into the application and tested is an important efficiency. To receive immediate feedback that the code you just checked in failed to build or pass a regression test enables the developer to make fixes before he or she moves on to the next agile story. If the time to run continuous integration scripts is fast, developers are more likely to check in code frequently leading to better quality.

![](https://1.bp.blogspot.com/-vBHM57tNEMs/WOI5vXf75mI/AAAAAAAAcGA/sB3ioeplad4uJDKF5VwJknUYrcdHXOcOQCLcB/s280/Continous_Delivery_by_Jez_Humble_and_David_Farley%2B%25281%2529.jpg)

Organizations that support many applications and development teams can also benefit from continuous delivery. This automation picks up where continuous integration ends and automates the steps to push software builds to a destination environments. It can be a development environment, testing, staging, UAT, demo, or a production environment.

Automating delivery not only saves time and effort, it's made advantage is quality. Manual deployments, especially ones that require multiple steps that differ by environment or type of deployment are highly error prone. For those of us that survived the days of manual deployments, we'll recall nights spent chasing configuration differences between test and production environments that caused a code push to production to fail. If you're a developer, you probably have bad dreams of resolving issues when a system admin skipped a critical step in a delivery. If you're that system admin, you likely have pent up frustration from the complexity and frequency of development changes. Continuous delivery not only addresses these issues, it potentially improves the culture as there is less blame from the human errors associated with manual deployments.

The next stage is continuous deployment whereby new code is built, tested, delivered to environments, and fully deployed to production frequently. Some organizations translate continuous deployment to a production push on a frequent schedule like daily or hourly while others will deploy with every build. The first time I saw it in action I was both amazed and frightened on the level of automation achieved and the frequency of changes being deployed to the application's customers.

##  Is Continuous Deployment Appropriate for All Businesses?

Like I said, it's easy for development teams to want continuous delivery, but that doesn't mean it makes businesses sense. First let's consider why some businesses may want continuous delivery -

  * They are in a hyper-competitive industry where they need to deploy frequent changes to improve customer experience or test new capabilities. Many larger B2C companies fit this profile.
  * Business leaders promote a culture of experimentation and "failing fast" paving the way for development teams to try new things, promote the ones that succeed and rollback the ones that were misses.
  * They have also developed sophisticated ways to test changes using A/B tests, user experience metrics, and surveys to know that their deployment achieved the desired business outcome.
  * The have also matured code branching practices so small features changes can go out with the nightly deployment but new features requiring longer development periods can be integrated when ready.
  * Their automated testing not only runs through regression tests but also trigger performance, load, and security testing. 
  * They have a large enough development pipeline warranting the investment in advanced testing, automation, and SDLC practices.

You can see that there is technical investment and a level of process maturity to enable continuous deployment. In addition, the business strategy and culture has to warrant this process and be able to take advantage of it.

##  Why continuous deployment may not be right for your business

Here are some reasons why continuous delivery may not be right for your business

  * Your applications are used within business-important (critical?) workflows. 
  * Software deployments often require training users on new or changed capabilities.
  * Your application enables customers to customize the application and your testing isn't sophisticated enough to validate a sufficient number of use cases.
  * Your organization doesn't have the sophistication to take business advantage over this capability. 
  * There's no process to validate the impact or recognize changes that have less desirable outcomes.
  * Your organization doesn't subscribe to experimentation and will view any deployment that had a negative outcome as a failure. 
  * Your business stakeholders are less willing to release capabilities to customers without going through UAT (user acceptance testing).
  * Your testing practices aren't mature. Testing coverage isn't sufficient and you haven't automated testing for performance, security, and other testing needs.
  * You have a history of unstable releases that required patching or rollbacks because of technical reasons. 
  * You have few development resources, and the investment to enable continuous deployment competes with the effort required to develop new innovations or improve applications.

The figure below summarizes when continuous deployment might make sense -

![](https://2.bp.blogspot.com/-WOWCpTbD7zc/WOKXyDsmvTI/AAAAAAAAcGU/v7W8UlQDgjoSbZoxeQTCeF-S1x7ANNUCACLcB/s280/Continuous%2Bdeployment%2Bby%2Bstarcio.JPG)

##  Who's driving your DevOps strategy?

Continuous integration, delivery, and deployment should be part of the overall DevOps strategy and as I said in one of my earlier posts, the [CIO has to set the DevOps strategy and priorities](http://blogs.starcio.com/2015/02/Key-Successful-DevOps-Transformation.html). Targeting continuous deployment shouldn't be left to developers that want a seamless, frictionless process with Ops at the potential cost of customer experience and quality. It also shouldn't be driven by a controlling product owner that wants to drive quick changes without planning for their impacts or investing in the technical practices required to perform continuous deployment.

If you're interested, [contact me](http://www.starcio.com/) if you want to develop a decision matrix on whether to invest in continuous development.
