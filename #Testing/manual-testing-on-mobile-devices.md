# Manual Testing on Mobile Devices

_Captured: 2017-05-05 at 23:55 from [dzone.com](https://dzone.com/articles/manual-testing-on-mobile-devices?edition=297993&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-05)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190139&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190139&u=https%3A%2F%2Fwww.wakanda.io%2F).

In the DevOps age, "manual" may sound like a bad word. But manual tests still have an important role to play, even for organizations that successfully automate most of their tasks.

Nowhere is the importance of manual testing clearer than in the context of writing software for mobile devices. Below, I'll discuss the importance of manual tests for mobile, and how to perform them.

## Why Do Manual Tests on Mobile?

While automated tests can streamline most of the testing required to release software, manual testing is used by QA teams to fill in the gaps and ensure that the final product really works as intended by seeing how end users actually use an application.

In the context of mobile, manual tests often answer questions like:

  * Are all elements of the design arranged in a comfortable way?
  * Is it easy to get to elements with one finger?
  * Is it still easy if the user is using only one hand?

By performing manual tests with real users, you can measure their reactions as they test the functions of the app. You will also be able to take note of any challenges in performing tasks on the device.

## How to Perform Manual Mobile Tests Effectively

To perform manual tests, you have to organize and standardize the tests. By taking these steps, you can repeat them in any device without any changes in the flow, and you will be able to reproduce an error again if it is necessary.

Without organizing, you are just going around in circles and hoping to find something wrong. Organizing tests will save time, and it will be easier to reproduce errors. There are a few steps to follow to create our manual tests.

### Plan the Test

Most things start with a good plan, and testing is no exception. Your first step when preparing a test is to plan out the steps that will comprise the test, and your route for executing them.

### Test

With the test planned, run it. Test everything you have planned, note the route you used and how each point was addressed to avoid confusion when the test is run again.

When an error appears, try to reproduce all the steps the same way you did the first time. Determine what caused the error. (Was it just human error?)

### Note the Errors

Registering errors is necessary to make them easier to reproduce. Show your test to the developers to help find out what is causing the errors. After solving each of the problems, perform all tests to verify that nothing was broken. Use an appropriate tool to share your test results with QA and the development team, and keep a history of your tests and issues.

### Repeat

We have to repeat all the steps again after performing any kind of code change, reproducing the tests exactly as from the start, and remembering to note any changes, thus reducing the test error rate of our manual tests.

### Select Devices

Select different devices to perform tests. Try distinct device brands, platforms, and operational systems. Differentiate whenever possible the hardware and software, check the version of the auxiliary software, and take note if there are differences between updates. Because there are often differences between screens and resolution, checking if the app is responsive is mandatory (Sometimes, we only can see this with manual testing).

While mobile device testing is often automated, it's always wise to use manual testing to encourage greater dedication and higher quality. Even if we can perform most tests in an automated way, we still lack the technology to fully automate some types of tests, such as those for accessibility and usability. Manual testing also allows us to monitor user reactions, see where problems may lie, and what features users like more.

To get started, simply follow the short list of steps above to perform manual tests on mobile devices. To become a good manual tester for mobile devices, you need to stay focused on testing the devices that best meet the needs of your target audience, and maintain consistent standards for mobile testing.

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190140&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190140&u=https%3A%2F%2Fwww.wakanda.io%2F).
