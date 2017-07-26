# How can I capture complex logic in an App?

_Captured: 2017-04-06 at 20:10 from [blogs.itemis.com](https://blogs.itemis.com/en/how-can-i-capture-complex-logic-in-an-app?utm_source=hs_email&utm_medium=email&utm_content=50066132&_hsenc=p2ANqtz-_056uKhWN4_IxCb6f9Mweceg_PXJGvfL7P4yknB90QvmUCkxbIWlKj7PM7DgPXHvAtF0JpbRWpvdsgEOfEm5pM8vWWxnda9DznmOC24vupuzdkNwI&_hsmi=50065691)_

Several customers of ours need Apps that represent internal logic that cannot be externalized to backend services.

The complexity reaches from registration and login scenarios, where the current user's state needs to be tracked, to control the internal states of an external device. The latter scenario often occurs in IoT scenarios.

They need to capture the system's state within the Apps logic, so that it can act asynchronous or completely independent from a backend server or cloud service.

Additionally we often have the requirement of developing fully native code for the Apps to grant direct access to the mobile OS's functions or create the best achievable User Experience.

![how-can-i-capture-complex-logic-app.jpg](https://blogs.itemis.com/hubfs/Blog/Mobile/how-can-i-capture-complex-logic-app.jpg?t=1491488351797)

## Preparing for complexity

Being confronted with these requirements, we have three possibilities (basically talking about Android and iOS):

  1. Implement the logic by hand for every platform in the target language.
  2. Create a C/C++ library that can be used almost cross-platform for iOS as well as Android (i.e. using the NDK).
  3. Use cross-platform tools to develop the logic only once and later generate the platform specific code.

Using the first option, you will have a - hopefully - stable version of the logic. The effort for implementing is almost the factor of platforms you need to support. Adjusting the business logic for later versions requires the developers to implement the changes for every single platform.

The second option has several limitations:

First of all the low level development for iOS and Android has several pitfalls and calls for very experienced experts for porting and integrating those developed libraries in the Apps.

Additionally C/C++ developers aren't usually used to mobile development - and mobile developers aren't usually very firm in C/C++ development.

For the third option you need the knowledge of an additional tool or workbench to generate your logic from. But it can ease your effort, since you only have "think through" your algorithm once.

Let's dive into that third option a bit deeper:

## Capturing the complexity

Usually you will have requirements defined for a specific workflow, a certain business logic and the like in textual or graphical form. This logic needs to be explained to the developer and transferred to code by them. Then challenged and refactored to display the technical possibilities and cover side tracks that might have been forgotten in the first idealistic definition of the flow. And in reality, you'll repeat that last sentence again and again...

Having those tasks done directly within code leads to massive effort and need for refactoring. Wouldn't it be wise, to have a model of what the stakeholders meant before transferring it to code? That's what e.g. UML is for. Wouldn't it be nice to also execute that model to see and test the flow setup in that model, so that you can track possible problems upfront - before implementing code? That's what tools like [YAKINDU Statechart Tools](https://www.itemis.com/en/yakindu/statechart-tools/) can help you with. You need tools, that can help you with modeling the logic platform independent. The logic itself is target platform agnostic, so it is easy to swap a platform or generate for multiple platforms, even if you start of with just one like Android.

Basically you need to think the process through, before putting any code to paper.

## Coding the complexity

Having modelled your way through the logic, you'll have a validated, verified specification of the algorithms you need to cover. Now you could implement these documented functions using on of the approaches mentioned above being either code in Swift, Java, C or C++ by hand, always being concerned that your implementation really matches the requirements.

Or you could press a button and generate code for your required platforms.

Here again YAKINDU Statechart Tools enters the game.

You'll get standardized code, that by design is independent to your UI following standard patterns.

It helps you with clean separation of application and business logic. It's even easier to exchange your ViewControllers or Fragments since the logic is completely encapsulated and independent from additional libraries.

Also by using tools like YAKINDU Statechart Tools you'll benefit from shorter development cycles. Especially in mobile development the turnaround cycles can be long and tedious, when waiting for Android Studio to build and run, to have a quick test of your implemented logic.

Either way - having it hand-written or generated - at some point you're done with coding. Time to test and maintain, right?

## Maintaining the complexity

Obviously when developing, you need to test. The higher the complexity of your logic, the higher the effort for creating UnitTests and performing manual tests.

Let the system grow and age and you'll be confronted with the everyday problem of mature software systems: they are hard to maintain.

From our experience, it is required that automatic tests are either created up-front or setup after the first development steps. Otherwise regression tests will be hard to accomplish.

With tool support you can test and verify your modelled logic up front. It can be tested on the semantic level of the state machine and you don't have to worry about the generated code - it just works.

Nevertheless, test cases can also be generated from models. You might need that for later verification or if you choose to add additional platform specific logic to the generated code - keeping in mind that abstraction would be the better choice here.

## Wrapping it up

I myself am not convinced by platform independent development with tools like PhoneGap or Titanium. Especially not in the projects we are involved with. I tend to promote the way of native development because it is the most powerful, better in User Experience, more mature.

On the other hand I'm lazy and I encourage my team to be the same.

I don't want to code the logic of several different states of a [steam cabine](https://www.grohe.com/cy/25551/shower/private-spa/f-digital-deluxe/) in Swift and Java, then test it myself, then have the customer test it, to adjust it, to test it myself, then have the customer test it, ….. and then with version 2 having the whole stuff changed again.

I want to discuss the control on a different level and then just press a button.

For Android that already works like a charm with YAKINDU Statechart Tools. For iOS we're currently working on it.
