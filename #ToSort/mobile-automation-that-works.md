# Mobile Automation That Works

_Captured: 2018-03-08 at 15:06 from [dzone.com](https://dzone.com/articles/mobile-automation-that-works?edition=366220&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=mobile%202018-03-08)_

At Lucid, we automated half of our manual regression testing for our Lucidchart Android app--knocking the regression cycle down from six to three hours. As Lucid moves toward a continuous release cycle, we are working to reduce manual QA testing for server and native releases to only one hour of user-centric exploratory testing. Automation is making that possible.

The initial difficulty of this task was wading through oceans of information and thousands of opinions about mobile test automation. No matter what we chose to do with automation, there was always a better way of doing it. Yet we had to start somewhere and produce something of value that could be improved over time. Here are some automation choices we made and what we learned along the way.

![Logos of tools we chose to use for our test automation.](https://d2slcw3kip6qmk.cloudfront.net/marketing/techblog/mobile-automation-that-works/AutomationTools.png)

> _Tools we used to build our automation includes AndroidSDK, NodeJS, Appium, SBT, and Java._

## Appium

After doing our research, we decided to go with the open source [Appium node server](https://github.com/appium/appium) because of its continuity with our existing Selenium framework, its cross-platform capability for Android and iOS, its popularity, and its ease of use in multiple languages including Java and Scala.

## TestNG

We use TestNG as our test framework to run tests in parallel, utilize test group tags, and create custom test suites from command line arguments. Optional parameters are used to activate visual comparison tools, select devices for parallel testing, specify the apk and server environment, and set activity intent overrides. TestNG groups indicate test-specific supported devices, environments, priority level, and content areas covered. The following is an example of how we use our TestNG groups.
    
    
    @Parameters({"eyesActivated", "device", "app", "environment", "intents"})

Creating a custom TestNG XML allows full flexibility to generate tests from command line arguments:
    
    
    suite.setName(testName + ": " + timestamp);
    
    
    Map<String, String> params = new HashMap<>();
    
    
    Map<Android, XmlTest> xmlTests = new HashMap<>();
    
    
       xmlTests.put(android, new XmlTest(suite));
    
    
       params.put("device", android.model);
    
    
       xmlTests.get(android).setParameters(params);
    
    
       xmlTests.get(android).setName(android.name());
    
    
       List<XmlClass> xmlClasses = new ArrayList<>(testContainer.get(android).size());
    
    
       for (Class<? extends AndroidNativeDriver> focus : testContainer.get(android)) {
    
    
       xmlTests.get(android).setClasses(xmlClasses);
    
    
    List<XmlSuite> suites = new ArrayList<>();

## Run Tests Dynamically From the Command Line

Every test is assigned a priority level to allow control of the balance between testing time and coverage. This encourages use of automated tests to get both early feedback during development and complete coverage during regression testing.

![Pie Graph showing test priority categories](https://d2slcw3kip6qmk.cloudfront.net/marketing/techblog/mobile-automation-that-works/TestPriorityLevelsLowRes.png)

> _Tests are assigned priority level categories to enable full control of testing time vs. coverage._

Immediate feedback during development is available by running high/critical tests against the development branch already installed on the device:

The environment variable $ANDROIDTEST points to the executable jar. We can also run tests in a specific area of the app to get quick results:

Our server-side regression includes all medium and critical/high test cases against the pre-production environment using the Play store app. To run, we simply attach all devices to a usb hub and begin the test:

For a complete automated suite using a native APK from the master branch:

When using in-house devices for automated tests like we do, quick yet comprehensive results come from randomly assigning test cases to single devices on a first pass. If a test fails, we'll repeat the test on every device to get solid evidence of its performance.

## UI Visual Comparison

We use [Applitools](https://applitools.com/) to capture and compare visual UI elements during automated tests. It integrates seamlessly with Selenium and Appium. Below is an example of a test case for Lucidchart's document list :

Of course, a view can be in a large variety of states at any point in time, making UI tests flaky and unreliable. Applitools helps by providing options to exclude areas from comparison, check specific elements or regions, check dynamically positioned elements, and ignore insignificant differences.

Applitools uses image comparison to determine if a test succeeds or fails. Image comparison failure causes the automated test to fail with a link to visually inspect the differences. Baseline images can be updated, if necessary, with a single click. This makes it easy to update your tests if the app's UI changes.

![Applitools provides side by side visual comparison of UI snapshots during testing.](https://d2slcw3kip6qmk.cloudfront.net/marketing/techblog/mobile-automation-that-works/ApplitoolsImageComparison.png)

> _Applitools provides visual UI testing tools._

## Page Object Model

We chose to use the page object model to get page element identifiers organized by app activities. The page object model helps test scripts to read like English:

A single repository of page objects also saves significant time in identifying and testing valid selectors. We chose _not_ to use @FindBy to assign page objects because of the difficulty of debugging annotations. Instead, we added logging inside our page object methods to immediately identify objects not found during a test.

How do we keep track of all these pages objects? We document them in [Lucidchart](https://www.lucidchart.com/), making it simple to assign good names for the activity and write test scripts using the page objects.

![Lucidchart makes it easy to document the page object model.](https://d2slcw3kip6qmk.cloudfront.net/marketing/techblog/mobile-automation-that-works/PageObjects.png)

> _Use Lucidchart to easily document your page objects._

## Mobile Touch Actions

Touch interactions are a vital part of mobile automated testing. To make using touch interactions simple when writing tests, we wrapped the basic Appium TouchAction method in our own abstraction, allowing easy interactions with specific areas of the screen or elements.
    
    
       log.action(LogType.TAP, String.format("Tapping on %s (%d,%d).", place.toString(), point.x, point.y));
    
    
       new TouchAction(driver).tap(point.x, point.y).perform();
    
    
    … (Intermediate overloaded methods handle assigning full-screen or specific element locations.) …
    
    
    protected Point getPoint(Point elementLocation, int elementWidth, int elementHeight, Place placeInElement) {
    
    
       int x = elementLocation.x , y = elementLocation.y;
    
    
        … (Assigns a point for each area of the page or element) …

Here is an example of our touch interactions. In the app, we have a left side panel which must close in two ways: (1) tap outside the left panel (2) drag the panel closed with a left swipe (a swipe moving from the _right of the panel_ to the _center left of the screen)_.

![Touch commands can be applied to any position within an element.](https://d2slcw3kip6qmk.cloudfront.net/marketing/techblog/mobile-automation-that-works/TouchInteractions.png)

> _An abstraction to make touch interactions intuitive and user-centric._
    
    
    swipe(getPoint(docsList.leftPanel(),Place.CENTER_RIGHT), getPoint(Place.CENTER_LEFT));

## Writing Reliable Tests

Automated tests can return flaky results because of timing and external issues. Here are a few practical examples of how we have increased reliability.

Use explicit waits to control timing of execution when specific conditions are required. For simplicity, we include explicit waits in tap() and other interactive methods.

As a result, test scripts are simplified.

We found that the WebDriver sometimes doesn't initiate correctly and, at other times, automated tapping of elements does not work. When test failures occurred for reasons beyond the test script or app under test, we found a high rate of success in automatically repeating the step for a limited number of attempts.

## Automation ROI

Automated tests take a lot of effort to set up and require constant updates as the product changes. Failing tests can take significant time to triage. Flaky tests send false alarms and can waste a lot of time. With continued focus on quality, however, these downsides can be greatly minimized.

Automation provides the ability to thoroughly test cases in ways not practical with manual testing alone. For example, automated tests can check ALL our shape libraries and ALL of our document templates. When we only used manual testing for shape libraries and document templates, QA ended up only checking a few of each since testing all of them would be a very time-consuming task. Automated tests can save time by doing the mindless, tedious work for you. Plus they automatically set up the complicated scenarios that are necessary for some tests.

When checklist features pass automated tests, manual testers have time to use the product like an actual person in exploratory testing. This exploratory testing becomes a sanity check of the automated tests and should cover the most-used features in a user-centric approach.

It's also important to note that, periodically, all automated tests should still be done manually. Software is designed for people. There is no adequate substitute for a creative, living person using the product to verify customers are seeing and experiencing what you expect.

## Tips for Making Mobile Test Automation Successful

  1. Keep tests short and sweet.Have fun with it! This backwards compatibility test logs in a user with the following documents in their document list:
![User documents are created to spell 'you are logged it' in the document list.](https://d2slcw3kip6qmk.cloudfront.net/marketing/techblog/mobile-automation-that-works/HaveFunWithIt.png)

> _Do small creative things to make the testing enjoyable!_

  1. Make code organized and clean so that it is pleasant to work with.
  2. Talk with the people who use your automated tests. Find out what works for them. Make it easy for developers to test their own branches, run a targeted subset of the tests, run post-release tests, and run functional/regression suites. Make it easy to get feedback fast.
  3. Overcome every challenge. We overcame literally thousands of obstacles. But with every obstacle we overcame, our confidence increased that we could handle the next one. Keep going until tests work reliably. Document tests you have completed and remove them from the manual regression. Don't be afraid to move forward because it's not perfect. Just keep at it, keep improving, keep learning, and you'll get there!
  4. Establish a threshold for bugs you are attempting to prevent. Focus on reasonable priorities.
  5. Always remember you are representing a person (not usually a computer) using the software. You want it to be a great experience for them and help them out in their life. If you remember that, you'll actually test things that matter.

## Sincere Thanks

Wrapping up, I'd like to thank Lucid for the opportunity to work on automating our Android regression. It's incredible to work for a company who cares as much about their employees as they do about their product. Thank you, as well, to the countless people throughout the world who have helped make this automation project work for us.

Hopefully, this post has taught you something new and provided a little help and encouragement if you're still in the process of making your mobile test automation great!
