# Test automation for iOS

_Captured: 2016-03-10 at 18:08 from [tech.blacklane.com](https://tech.blacklane.com/2015/12/13/test-automation-for-ios/)_

This is a long Christmas post: be sure to wrap yourself in your favourite blanket and have some amount of Gluhwein near you.

This is the summary of our testing practice that we have at Blacklane GmbH by the end of 2015.

To make it well-scoped we only describe the stable parts of our testing infrastructure and do not include material that is work-in-progress or is under experiment so this post could have been postfixed with "part 1" because we know we are not there yet with complete automation of our process.

Here we cover the kinds of tests that we have and the corresponding infrastructure behind them. Terminology we use is quite arbitrary, we do not stand on it to death: when people say "unit tests", "integration tests" or "functional tests", they often mean completely different things or just imply that they are the same thing. One example how we could even raise against our own terminology is that actually functional testing is just a subset of integration testing and should not stand as separate group: they share the same infrastructure, additional separation brings complexity to maintenance etc (we will describe both groups below thoroughly).

Still somehow we tried to come up with the most commonly used terms and so far it worked well for us. We appreciate any feedback about better terms or practices so let this summary be a good occasion for this sort of discussion.

## Introduction

On meetups or interviews it is very often that we ask devs who claim to have TDD badge among their skills or one their CVs or LinkedIn profiles:

> Do you write tests? What exactly do you (do you not) test? What kinds of tests do you have? How much of testing coverage do you have? Do you really do TDD?

It is unfortunate but here are the answers that we hear most often:

> We don't write any tests, our development plan is too tough for that (with expression of deep sadness a face).
> 
> We write unit tests, we only test "business logic" (whatever it means).
> 
> We have tried using Calabash or Frank but it didn't really work for us because their tests are hard to write and maintain.
> 
> …

Some devs are able to pass "bla-bla" part of this question but when it comes to pairing on some test-driven task we often feel like [Mickey Mouse Blood Tears Say Reactive One More Time](http://25.media.tumblr.com/tumblr_m3ed9jlCsh1qawa1bo1_400.jpg).

To be honest we also were there: we didn't know what to test, how to test, we couldn't explain to our stakeholders the benefits of test automation for iOS, so that every time we pronounced words "test" or "tests" we made them suspicious about what we were doing.

We still cannot always test everything but somehow our iOS community is maturizing, we have great books/blogs to read about test automation and test-driven development (we'll list a few at the end) and the most important we now understand that as soon as you are able to write one single test for particular piece of functionality all the subsequent tests of the same kind can be written very fast because you already have version 1 of your tool set for this particular kind of testing or group of features and most likely you will be able improve it a lot so no fear we have anymore about trying to put under test something that we previously didn't test at all.

Also we didn't meet a single person from non-tech staff who would have been willing to protect or patronize test automation upfront - we needed 67 meetings to argue about that additional time to actually write the very first set of integration or functional tests and only after a while it became clear to everyone including non-technical guys that we started spending less and less time on "[mouse-driven development"](http://stanislaw.github.io/2015/11/20/how-apple-could-improve-their-developer-tools.html) and improved quality of our product so that finally it contributed to the overall climate of our daily work: [I can sleep when the wind blows.](https://www.youtube.com/watch?v=aApmOZwdPqA)

## Heuristics for Test Automation

These are the heuristics we find useful in our practice, we call "heuristics" everything that helps us to write better code given we keep them in mind:

  * If you do not write tests you will never learn how to write them, it is better to write bad tests then not to write any.
  * Ability to do TDD is not about black and white: "can or can not", it is about having 1001 things in your toolbox: techniques, patterns, tricks and hacks - when you have enough of them you can test almost everything.
  * "Legacy code is a code without tests" ("Working effectively with Legacy Code" by Michael Feathers).
  * "If you can't measure it then it can't be called engineering" (taken from "Object-Oriented Software Engineering: A Use Case Driven Approach" by Ivar Jacobson). We of course also read "measure" as "test" which is another way of measurement.
  * Ideally we should be able to test everything: if something is hard to test, then we are just not there with quality of our code or corresponding tool set and infrastructure for testing but we will manage to find or improve them and get there.
  * If you don't know or not sure how to test something properly, try the ugliest version first: stub everything in an ugly way, stub network in an ugly way, assert what you want to assert and only then iterate on refactoring of both test and SUT (system-under-test).
  * "Encapsulate everything". Always encapsulate system-specific details behind classes: if it is localization put your `NSLocalizedString` behind Localization class and test it, if it is `[UIImage imageNamed:]` put your image construction behind Image Factory class and test it, if it is custom `User-Agent` or some build setting like `CFBundleVersion`, again put them behind corresponding classes and put those classes under test.

## 4 kinds of tests

All of the following is implicitly organized as a table so that every section follows the same structure: what makes particular testing activity specific, its infrastructure details, examples and some useful hacks:

  * Unit testing
  * Integration testing
  * Functional testing
  * Acceptance or end-to-end testing

### Unit testing

  * White box testing
  * The fastest group: it takes second or two to run hundreds of unit tests.
  * [Cedar](https://github.com/pivotal/cedar) is used.
  * In Xcode: Unit test target without application as test host.
  * Only classes are included to unit test target.
  * Testing is headless (no UI): we do not test UI, we do not look at it.
  * No Storyboards, Xibs, assets, localization and other non-code files are included.
  * Pure class level testing.
  * Extensive use of mocks and stubs.

What it includes:

Given the above restrictions for unit tests target it contains everything that whitebox- unit- testing usually implies, like:

  * Method of a class produces expected result given we invoke that method with particular parameters.
  * Method of a class, when invoked, calls other method of instance of some class with certain arguments.
  * Call a method and verify that a state of method's class is changed.

What it does not include:

  * It does not include any networking, even in a stubbed form.
  * It does not include any IO like file system: Xibs, Storyboards, NSUserDefaults.
  * No UI* classes are included as they are very often instantiated from Xibs/Storyboards which involves integration with file system (xibs/storyboards are files) that's why we prefer keeping them in Integration Tests group.
  * No asynchronicity, no workarounds for run loops.

Examples:

  * Test verifying that your Deserializer class produces correct object from JSON dictionary.
  * Test verifying that method of your Request builder produces correct NSURLRequest.
  * Test verifying that your service class for Push Notification does notify its delegate with new processed push notification.

Helpful tips:

  * One of the Cedar's feature that we use most often and that we are missing in XCTest framework is [Focused Specs feature](https://github.com/pivotal/cedar/wiki/Getting-started#focused-specs) \- we are able to run only one test or specific group of tests when we're working on them without a need to run hundreds of other tests that are not relevant to our immediate current progress.

### Integration testing

Integration testing is the intermediate group between unit testing and functional testing. It shares much of its approach with unit testing but here the accent on integration of our code with the rest of project is made: we test integration of our UIViewController classes with their xibs/storyboards, test localization keys, test the fact that invocation of buttonWasTapped: produces call to a delegate and so on.

  * Almost-white-box testing
  * The second fastest group after unit testing group: it takes longer then unit tests to run but still it is about few seconds.
  * In Xcode: Integration Tests target with application as test host
  * The whole application is compiled
  * XCTest is used

What it includes:

  * Unit-testing of UI* classes. Very good example of these tests can be found in excellent [Jon Reid - UIViewController TDD screencast](http://qualitycoding.org/uiviewcontroller-tdd/).
  * Tests for Factory classes that encapsulate everything iOS specific.
  * White- and black-box testing of storage-classes that have NSUserDefaults or keychain behind them.

What it does not include:

This kind of testing is best described by what we not include to this group: everything that goes to unit or functional tests.

Examples:

  * Instance of particular UIViewController instantiated from our view controller factory is not nil and is of correct class and has desired properties.
  * Instance of particular UIViewController instantiated from a storyboard has its IBOutlet property connected or its IBAction action connected.
  * Specific localization key for all languages is not nil (we have Localization class that encapsulates keys and NSLocalizedString stuff).
  * Our autolayout helper produces expected results when applied to some view that is being constrained to its superview.
  * Our storage for non-sensitive temporary information backed by NSUserDefaults works as expected.

### Functional testing

Functional testing is rather recent group that we introduced: previously those tests were part of integration testing suite and we even continue to think about those tests as a subset of integration testing but still we now find it practically meaningful to differentiate them into a separate group. The rational behind having this separate group is our observation that integration testing actually consists of two different groups of tests: unit-testing of some code that involves integration with the rest of the system (non-code files) and testing of, let's call it this way, view controllers or groups of view controllers in isolation.

It was a pivotal point for us when we had the first test written and that test case had been testing specific view controller in isolation: we stopped doing mouse-driven and started doing keyboard-driven development in this important area of iOS development. The idea was very simple: if we have screen that is 67 user taps or other gestures away from initial screen why do we ever need to every time go to it manually or wait while Xcode 7 UI test will make those steps for us, we could have just put our controller on "empty stage" i.e.:

…and then given we would have all of its dependencies satisfied: stub models, network calls, reproduce original view hierarchy for our controller to be displayed correctly - we could exercise our assertions on that screen without a need to get to it via numerous actions like taps, fill-in-textfield etc that are normally required to get to that screen in real application (or acceptance test case).

Later we realized that this group of tests also was different from the first group i.e. unit-testing of integration in a sense that it often involved multiple view controllers or services to communicate to each other so that it had more of practical sense to organize them not according to their view controller class names but according to the use cases that those actors were to execute.

  * Semi-blackbox testing: since functional test operates on large components or groups of large components we only care about putting correct dependencies needed for test to work, internal details of components-under-tests are not touched.
  * It is slower group than integration tests but faster than acceptance tests.
  * Allows "UI Testing" of particular pieces of application which are hard to test using acceptance tests without exhaustive duplication of tests and very long waiting time.
  * [KIF](https://github.com/kif-framework/KIF) ("keep it functional") is the main tool for this group of tests
  * In Xcode Integration Tests target with application as test host (the same as integration tests)
  * The whole application is compiled (the same as integration tests)
  * Animations are disabled for faster speed of test execution and to lower the KIF waiting timeouts to 0 (the same as acceptance testing, see helpful tips).
  * Separate `.bundle` for `.json` fixtures and Fixtures class in that bundle that encapsulates reading from them.
  * Extensive use of [OHHTTPStubs](https://github.com/AliSoftware/OHHTTPStubs) \- we create fixtures using VCRURLConnection's cassettes and Charles proxy and stub those fixtures with OHHTTPStubs. Also using it we stub 400, 401, 503 and other responses to test alternative courses of our use cases.
  * Extensive use of [ VCRURLConnection](https://github.com/dstnbrkr/VCRURLConnection). We do not use it to replay requests but only to record them when we're crafting our test fixtures and setting up our tests.

Helpful tips:

  * At the very start of application you need to put specific hack to set empty view controller instead of running your real application's initial screen because you don't need it your application to run in your functional tests, we do it like:
  * Animations should be disabled. This is example in the beginning of AppDelegate (of course there is better place for it):
  * KIF's `tester` has very useful lower-level method `waitForAccessibilityElement:view:withElementMatchingPredicate:tappable:` which allows you match everything custom that you might need.

Example 1: Push Notifications

Test case: make sure that your app opens correct target screen when user jumps into your application from a push notification alert.

You put your real initial view controller on stage, call `application:didReceiveRemoteNotification:fetchCompletionHandler:` on your AppDelegate and write KIF assertions to ensure that your app ends on expected target screen corresponding to push notification payload. Of course you can also test all alternative courses along the way.

Example 2: You need to implement feature: your specific screen must have certain behavior when server returns 503.

Test case:

(Even before the following steps it is better to implement functional test for your screen when it works green against all 200 responses)

  * Before implementing the feature use OHHTTPStubs to stub every request with 503.
  * Put your view controller "on empty stage"
  * Write KIF queries/actions/assertions that correspond to this 503 feature
  * Modify code for your screen
  * Run test again and see if it now passes

Example 3: Working with legacy code

Test case: one of your screens which is 67 taps from initial screen and you need to verify that is contains different labels depending on the input it receives after tap #66.

For that screen you have full-blown functional-reactive-declarative-massive view controller with ReactiveCocoa in it and with view models with ReactiveCocoa in them without any test coverage, everything is magically dependency-injected and you don't have a clue how to test it. Here are steps how we do it:

  * Do nothing upfront, just instantiate that view controller and put it "on empty stage" using `-[UIApplication sharedApplication].rootViewController = ...`
  * It will either present nothing on UI or will fail on some assertions about missing dependencies: for example for this exercise you might need your real API key to be put somewhere: `-[APIManager setAPIKey:]` or something like that, or some view model might be missing: create a one and inject it before putting system-under-test on stage.
  * Also you might need to stub some networking in case if your controller is directly depends on networking. Use your real API key, Charles or VCRURLConnection, write real server responses to fixtures and enable them via OHHTTPStubs. I remember how we were to stub around 10 networking requests including calls to some third-party services like Google Maps but that turned out to be worth it.
  * Repeat all steps until your view controller will show you expected results from stage that he is on.
  * Having all of the above in place you'll be able to iterate on your specific development task.

### Acceptance testing

  * Complete black-box testing
  * The slowest group of tests
  * Xcode 7 UI Tests written in Swift
  * Written by our [QA Engineer](https://twitter.com/anasofiavistas) with some help from developers
  * Animations are disabled to improve speed of execution (the same as in functional tests)

What it includes:

  * Testing of complete use cases against real server. It is about what real user does with your application.

What it does not include:

  * It does not include any hacks on application host that are usual for other groups of tests, application is treated as opaque as possible.

Helpful tips:

  * Disable animations

The following works together with above hack to disable animations (see functional tests)
    
    
    1
    2
    3
    4
    5
    
    
    
    override func launch() {
        launchEnvironment = [ "ACCEPTANCE_TESTS": "YES" ]
        super.launch()
    }
    

  * User agents

User agent is just a class that encapsulates user credentials and other for test agent. We have three agents in our test suite:

  1. Test agent that has predefined email/password credentials - we use it to execute tests that real registered user is supposed to execute.
  2. Test agent that contains unique email/password pairs - we use it to test Registration use case.
  3. Static user (QA call it "static dude") - is a test agent for tests where we execute some static content on specific pages (like on past bookings page we assert existence of bookings of specific kind). This kind of tests is hard to achieve with test agent #1 because his content always changes because of new stuff created on every run.

## Tip helpful for all groups of tests

  * Use [IDEBuildOperationMaxNumberOfConcurrentCompileTasks](https://twitter.com/1101_debian/status/675305084855668738) to improve your build time when you xcodebuild from command-line:

> Xcode users, add "IDEBuildOperationMaxNumberOfConcurrentCompileTasks=`sysctl -n hw.ncpu`" to your xcodebuild commands and enjoy.`

We didn't test Xcode itself thoroughly but looks like it builds concurrently under the hood, so only command-line builds can have this speedup.

## Recommended reading on Test Automation

"Omnis qui quaerit invenit", here we are just listing the reading which is the most outstanding for us.

  * [Growing Object-Oriented Software guided by Tests](http://www.growing-object-oriented-software.com/)

It's implementation context is Java but still it is the best book we have read so far on testing. It can be especially useful if you want to improve your integration and functional test practices. This book is MUST to be read.

  * [Test-Driven Development By Example](http://www.amazon.com/Test-Driven-Development-By-Example/dp/0321146530)

No comments, everyone must read this classics.

**Update:** Recently I have published my notes on this book: [Notes on "Test-Driven Development by Example" by Kent Beck](https://stanislaw.github.io/2016/01/25/notes-on-test-driven-development-by-example-by-kent-beck.html).

  * [Jon Reid's Quality Coding](http://qualitycoding.org/)

This is another MUST. If you are new to it follow Jon's recommendation on where to start first on his [About page](http://qualitycoding.org/about/).

  * [Object Oriented Software Engineering: A Use Case Driven Approach](https://www.ivarjacobson.com/publications/books/object-oriented-software-engineering-1992)

This is not strictly related to TDD but is more about good industrial OOP in general. While everyone is excited about functional/reactive/Swift/etc we are filling the gaps in our understanding of what good-old-OOP is (and is not).

**Updated later**: see also similar post [Offline UI Testing on iOS With Stubs](http://albertodebortoli.github.io/blog/2015/11/23/offline-ui-testing-on-ios-with-stubs/) by [@albertodebo](https://twitter.com/albertodebo).

## Conclusion

We have covered enough for one post. Here are the topics that are left behind the scope:

  * Snapshot view testing with [ios-snapshot-test-case](https://github.com/facebook/ios-snapshot-test-case). According to our framework this kind of testing is part of integration testing group.
  * Continuous Integration
  * Property-based testing
  * Mutation testing
  * Use-case driven approach to writing functional tests

Some of those topics are still work-in-progress or even undiscovered at all (like mutation testing) but we're going to come through all of that and probably publish part 2 of this post but that will be another story for new 2016 year.

Merry Christmas and Happy New Year!
