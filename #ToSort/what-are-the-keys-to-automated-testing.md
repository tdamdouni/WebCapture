# What Are the Keys To Automated Testing?

_Captured: 2017-07-08 at 09:28 from [dzone.com](https://dzone.com/articles/strategic-automation-key-to-automated-testing?oid=twitter&utm_content=buffer24ec8&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

To gather insights on the state of automated testing today, we spoke with twenty executives who are familiar with automated testing and asked, "What are the keys to using automated testing to improve speed and quality?"

Answers were around two themes: strategic automation, and use of testing and data.

## Strategic Automation

  * **Don't believe people when they say they cannot automate manual tests**. Gary Gruver at HP automated testing for printers and fax machines.
  * Have a good process around testing. **Link automation into the CI/CD/DevOps process**. You cannot achieve speed and agility without it.
  * **Nirvana happens without engineers coding in testing.** Automate the entire CI/CD process. Develop unit tests and regression testing with Artifactory and other common workflow automation tools. 1) Developers integrate the proper unit tests. 2) Automatically run a nightly build test. 3) Regression testing.
  * There's front end/UI testing and backend/API testing. The focus is now more on the back end with mobile and more API connections. The key for both the front end and the back end is to **reduce the amount of manual testing**. Run test overnight as part of the continuous integration process. Parallelize your tests since the shift to automation can take six to eight hours and become a point of friction. Start running tests in parallel, especially in DevOps.
  * **Better integration into DevOps for continuous testing**. Make the test team independent from the IT and operation team. This is critical for speed and quality.
  * **Application and orchestration automation built in extensive APIs** so it will scale. Multiple customers in the enterprise and the cloud. Get an in-view portal. Enterprise needs to see protection and throughput. Can make part of VM onboarding. Ongoing reporting and visibility.
  * **Increase speed and quality at every step. **Build the pipeline and set-up for automated tests to run in. Branch only when passing the test. Regression testing before release of the framework. Ensure confidence in the framework. Speed leverage browser renders to increase the number of VM's = 50, 40,000 tests in multiple versions, 420,0000 test cases in 20 to 60 minutes. Concurrency multi-threaded tests. Must run in parallel since IE 10 and 11 runs slower than Chrome.
  * Both aspects have the same answer for the most part. **Automation stops the need for repeating the same tests repeatedly.** Instead, they are afforded the time and freedom to explore the more exotic test cases. In modern development, everyone is very aware of the common areas to test, along with developers writing more and more unit level tests. This means that we are less likely to find the usual bugs as before; instead, we need to be more creative with our testing - automation allows us to pursue that given better coverage and quality.
  * You first must **have a stable test infrastructure** in place, where you are catching regressions and able to notify developers appropriately. At that point, you need clear policies for what is done when regressions are detected: who is assigned to fix them, how fast must they be resolved vs completing other tasks, what happens to ambiguous regressions (is the code wrong or is the test wrong), etc. We've seen a recurring type of dysfunction in several organizations: they've built an automated test system, but the noise from broken tests is drowning out the signal from the working tests, so everyone ignores the test system. That's worse than having no automated test infrastructure at all. You must actively maintain both the tests and the people processes around them, or you end up with this dysfunction.
  * **Rapid development and execution are core components of delivering quality software on a schedule**. Repetitive, automated coverage allows us to focus on the current product changes while the regression content - content that has either already been delivered into the field or has already been checked in previously - is adequately covered for any integration level defects. With most automation, less human interaction is desirable. This applies to the actual test, but also to things like setting up the test harness, triaging results, finding out historical details about the test and providing a general stability metric for the content that has already been shipped or delivered.
  * **Architecture agility is key to support multiple vendors.** It requires more agility and good quality automated testing - integration testing and endurance testing 24x7 on specific test scenarios to detect memory leaks. We start with manual tests until we get it automated. We must address the gap when developing a new feature. The automated testing team writes automation pieces. We are moving to Test-Driven Development (TDD) but we're not all the way there yet. You need a platform that enables you to consistently leverage and use automated test development on a consistent basis and understand how to write automated test cases.
  * For web testing, use Selenium or Appium to test cross-browser and cross-platform. You can write tests without having to learn a test scripting language. **Write tests that automate repeatable core functionality.** Developers should learn how to write tests and QA people should learn a little bit of code. You need the teams to work cross-functionally to be able to scale. Run tests in parallel to scale. It cuts testing down to just minutes. Once test automation is up and running, start thinking about CI/CD (continuous integration and delivery).
  * **If you just constrain your efforts to the pure automation of tests, you very likely will fail**. That's because the maintenance of the test cases will be a huge burden. To succeed with test automation, you will need to solve for the stability of infrastructure for the systems you're acting on. Plus, you need to assure that the test data that needs to be present so that test cases can run smoothly is here in the desired state and quantity. Only if you solve for the core automation, and in addition, the test data management issue, and service virtualization to make sure that the systems are stable and available, will you succeed with automation.

## Using Testing and Data

  * We track 140,000 events per second with the goal of optimizing the UX. 1) Start with analytics and see where people are getting stuck. 2) Optimize the UX. 3) Campaign messaging, conversations, A/B tests, layer, language, timing, content, and location. 4) **Data and event automation with marketing systems of record.**

  * 1) The main key that we've discovered is to **maintain and sharpen our test scope**. This starts with always determining the best level for tests - Should we be testing this in the UI, or is it more effective on a unit level? Next, we must ensure that our test strategy isn't allowed to experience scope creep, especially with UI tests, which can be expensive to create and maintain. To do this, we focus on prioritizing our use cases and subsequent tests and seek to automate in priority order. This will allow us to produce sanity checks quickly that span critical end to end scenarios. Keeping our scope focused greatly impacts both speed and quality of our efforts. 2) Another key is to heavily leverage a data-driven approach. This helps our teams write tests that are deterministic and only fail when real application changes are made, cutting down on maintenance time for flaky tests. Solutions for this can depend on context, but mainly leverage tools like Chance.js to generate randomized data, and use Factory and Data Builder patterns to allow tests to set up and clean up data effectively.

  * Identifying and aligning to true business value is critical with respect to improving speed and quality. It is important to be able to measure and clearly demonstrate the value to the organization in terms of quicker speed to market with new products, fewer customer impacting incidents and an overall reduction in overhead and expense. This understanding helps with **creating the business case for continued investment in test automation.**

## Developer Adoption

  * Developers need to take accountability for their work. **Testing is not someone else's job**. Quality from a functional and non-functional point-of-view. Inspect quality in.

What do you think are the keys to automated testing from your perspective?

Here's who we talked to:

  * Murali Palanisamy, EVP and Chief Product Officer, [AppViewX](http://www.appviewx.com)
  * Eric Montagne, Technology PM, [Barclaycard](http://www.barclaycard.com)
  * Greg Luciano, Director of Services and Amit Pal, QA Manager, [Built.io](http://www.built.io)
  * Donovan Greeff, Head of QA, [Currencycloud](http://www.currencycloud.com)
  * Shahin Pirooz, CTO, [DataEndure](http://www.dataendure.com)
  * Luke Gordon, Senior Solutions Engineer and Daniel Slatton, QA Manager, [Dialexa](http://www.dialexa.com)
  * Anders Wallgren, CTO, [ElectricCloud](http://www.electriccloud.com)
  * Charles Kendrick, CTO, [Isomorphic](http://www.isomorphicsw.com)
  * Bryan Walsh, Principal Engineer, [NetApp](http://www.netapp.com)
  * Derek Choy, V.P. of Engineering, [Rainforest QA](http://www.rainforestqa.com)
  * Subu Baskaran, Senior Product Manager, [Sencha](http://www.sencha.com)
  * Ryan Lloyd, V.P. Products, Testing and Development and Greg Lord, Director of Product Marketing, [SmartBear](http://www.smartbear.com)
  * Christopher Dean, CEO, [Swrve](https://www.swrve.com/)
  * Harry Smith, Technology Evangelist, [Zerto](http://www.zerto.com)
