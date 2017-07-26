# 7 Mobile Test Automation Tips

_Captured: 2017-01-30 at 23:02 from [dzone.com](https://dzone.com/articles/7-mobile-test-automation-tips?edition=266885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-30)_

Developing a mobile test automation scenario isn't really that complicated. Developers and testers use a variety of commercial test automation frameworks or open-source tools such as Selenium and Appium to do automation. However, when trying to execute these tests on real devices or integrate them into an Agile or CI workflow, things can get a little complicated.

## The Major Challenges Around Mobile Test Automation

The essence of developing test automation is to be able to use and re-use scripts many times across platforms and environments. Test automation should be as maintainable as possible, especially as new platforms and product features are released. Many organizations that develop test automation for their mobile apps face the following challenges:

  1. Executing the tests against a variety of real mobile devices.
  2. Executing these tests in parallel.
  3. Leveraging existing test code (re-usability) for new tests.
  4. Including real end-user environments and conditions (i.e., changing network conditions, low battery) in the tests.
  5. Overcoming unexpected interruptions (i.e., incoming calls, apps running in the background).
  6. Running these tests unattended overnight as part of a Jenkins CI job.

These are just a few of the challenges organizations we confront when trying to progress from older SDLC processes and meet faster releases and enhanced Dev > Build >Deploy > Test >Deploy cycles.

## 7 Mobile Test Automation Tips 

Overcoming these challenges starts with few changes in the overall mobile app development and test processes.

Consider these seven recommendations for building sustainable unattended automation.

![Test automation](https://i1.wp.com/blog.perfectomobile.com/wp-content/uploads/2016/05/7Keys-1024x357.jpg)

The key to mobile test automation is to start with a small number of test cases, automate those test cases, and assure that they are robust enough and can be executed both in parallel and unattended. Only then should you invest more and grow the test suite.

An important question to ask at the start is: What should I be automating? Organizations often do not choose the right tests to automate, resulting in lost development time, weak ROI, and an over-reliance on manual testing.
