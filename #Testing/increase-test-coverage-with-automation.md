# Increase Test Coverage With Automation

_Captured: 2018-08-24 at 16:45 from [dzone.com](https://dzone.com/articles/increase-test-coverage-with-automation?edition=385414&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-08-24)_

###  Test coverage is important, and increasing it offers many benefits. See how automation can help you achieve this. 

Read why times series is the [fastest growing database](https://dzone.com/go?i=283423&u=https%3A%2F%2Fwww.influxdata.com%2Ftime-series-database%2F) category.

Recently, I had the pleasure of presenting the concept of test coverage and its relationship with automation for a SmartBear featuring CrossBrowserTesting.

If you are someone who would rather read a blog post than watch a video, then this post is for you! As I did in the webinar, I'll explain the concept and limits of test coverage, present a very simple and useful strategy to increase it over time, and how you can employ automation with tools like CrossBrowserTesting.

## **Introduction to Test Coverage **

### **What Is Test Coverage? **

Many people say that test coverage is useful for measuring the quality of testing -- meaning, if the testing was good or bad. In my humble opinion, this way of seeing it creates some confusion. We should be careful with how we measure test coverage and how we interpret it.

I prefer to think of the concept of test coverage as a measure of how much we examine a system with our testing based on certain criteria.

And then, in a separate track, evaluate if it's good or not, and if it's enough or not, but not many people take the time to consider this.

![](https://abstracta.us/wp-content/uploads/2018/08/Screen-Shot-2018-08-10-at-4.55.14-PM.png)

Remember this tool called Disk Defragmenter? A system utility, this tool arranges something in the disk. It moves disk sectors in order to make the disk more efficient and faster. At least, this is what I can recall!

For me, this tool is showing coverage visually in a very clear way. You see a model of the disk, where it's clear what the total is, and how it was decomposed into smaller units. You can also see the percentage of progress, which is according to how many of those units have already been examined, and which ones still need to be examined. But, testers might never ask themselves, "How's the quality of the examination, how well are we examining it?"

So, back to testing. We need to model our system, and we need a criterion to decompose the system into different types of entities or elements, which will be the units that we are going to try to cover with our testing, and this is what we will be using as a measure of coverage: What is the percentage of units of our model that we test with respect to the total?

Here it is clear that this measure can be useful to determine what is the progress, to see what other things still need to be examined (to increase the test coverage based on the chosen criterion), but not directly to say how great our testing is.

Test coverage helps us know quantitatively the extent of our tests. It does not talk about testing quality nor system quality either!

It's a great measuring stick, but even with 100% test coverage, the application isn't guaranteed to be 100% bug free. Even if you only manage to achieve 20% coverage, it may not necessarily be a bad thing. The ideal amount of test coverage to aim for should be based on your priorities and risk analysis.

### **Test Coverage Is Like Sweeping **

This is another analogy I typically use to show what coverage means and its purpose.

If you told me that you swept your whole house, I would need to know what is your criteria for considering the house covered! If you only included sweeping the bedrooms for your sweep coverage criteria, would the whole house be clean if you swept 100% of the bedrooms? From my point of view, you should also sweep the dining room, living room, and more!

![](https://abstracta.us/wp-content/uploads/2018/08/Screen-Shot-2018-08-10-at-2.48.34-PM-min.png)

Therefore, we must always be careful with test coverage and the associated criteria. We have to decide which criteria are relevant to our context. Talking about criteria helps us to understand what we are covering, and what we are not, which is a very useful thing.

Also, how clean is the house if you have 100% coverage? Even if you did cover them, how clean are the bedrooms actually? It's like "requirement coverage" meaning that we covered all the requirements with our tests. But it doesn't tell us about how well we tested them. Right?

I could have different criteria over time: I sweep the kitchen and my bedroom every day, and once a week I sweep all the bedrooms, the bathroom, and the dining room, and maybe spend extra time sweeping those hard to reach spots, because certainly there's a higher probability (aka risk!) that dust has accumulated in those places. So, I have different strategies for my bedroom, depending on the day, the context and my needs.

This is something I can plan in order to have the best results with the optimal use of my energy and time. Can you see where I'm going with this analogy?

Replace the broom with tests and the house with code!

Not only is coverage useful to show progress, but it also gives ideas as to what other "parts of the house need to be swept" (thus expanding coverage). It also helps to know when to stop sweeping (according to the criteria, because I reached the goal defined in the plan).

### **Coverage Criteria **

As I've been mentioning since the beginning, the criteria is very important.

There are different criteria, from different perspectives, and also we can say that some of them are more exhaustive than others. So we need to understand them in order to understand how deeply something was tested. We can say that certain criteria subsume others when any test set covering the first criterion also covers the second, meaning that it's deeper.

For instance, taking into account the code perspective, covering all branches is deeper than covering all lines of code, because if we cover all branches we also cover all lines. So, the criteria named "branch coverage" subsumes the one known as "line coverage."

## **Types of Test Coverage **

### **Code Coverage **

![](https://abstracta.us/wp-content/uploads/2018/08/Screen-Shot-2018-08-10-at-4.48.43-PM-min.png)

Code coverage is the most popular metric for measuring test coverage for unit testing and there are different levels with different depths. For instance, the most popular one is "line coverage" which measures the number of lines covered by the test cases, reporting the total number of lines in the code and number of lines executed by tests. Essentially, it's the degree to which the source code of a program is executed when a test suite runs.

This measurement can also be broken down into different levels; not only lines of code covered, but there are also branches, decisions inside logic constructors, some others. The criteria should be selected according to the criticality of the unit tested, or according to how frequently it changes.

Remember that coverage gives us hints of what else could be tested. With code coverage tools integrated with IDEs, it's easy to see which lines are not covered (the ones colored in red in the image above).

Code coverage is very useful, following a white box approach, to add new unit tests to cover those lines or branches.

### **Data-Oriented Coverage **

With data-oriented coverage, we focus on the input and output parameters, each of them with their own domain (with a different spectrum of possible values that they can have).

Applicable to both white and black box approaches, some typical examples are equivalence partition and boundary values and combinatorial testing.

If we think about the values of different parameters, and we want to test all the possibilities, we will end up with a cartesian product, testing every possible combination.

On the other hand, we can test less and go with "each choice" coverage, which means that we choose each possible value at least once. There is also all-pairs or pair-wise combination, which is empirically said (according to some studies) to have the best cost-benefit relationship.

This is a great example to show that we need to plan the test coverage according to the risk levels and how much time we have for testing.

### **Others **

In addition to those previously mentioned, there are several more ways to cover the product that we are testing such as requirements coverage, different coverage when we model the logic or the behavior of a system with decision tables or decision trees, or with a state machine. In the latter, we can consider for instance, having tests to cover all the states, or all the transitions, or all combinations of input and output transitions for each state, or maybe more. There is always an error theory behind every test coverage criterion.

### **Don't Forget Platform-Related **

![](https://abstracta.us/wp-content/uploads/2018/08/Screen-Shot-2018-08-10-at-4.42.01-PM-min.png)

Additionally, there are other kinds of test coverage that are not related to lines of code or test data. One example is generated by mobile fragmentation, which concerns questions like: are we covering the main mobile devices, operating systems, and screen sizes?

This is not only for mobile, but also when it comes to web applications, we should plan the coverage across different browsers, not only thinking about how it will look, but also taking into consideration where the client side logic will run (mainly if developing with a Javascript framework).

## **Cross-Browser Testing **

Let's consider this first example of cross-browser testing:

![](https://abstracta.us/wp-content/uploads/2018/08/Screen-Shot-2018-08-10-at-4.41.47-PM-min.png)

We could apply combinatorial testing here, adding two new variables to our inputs and outputs, which is the OS and the browser. Imagine for example that we already have 4 test cases (covering the data or logic that we need).

Maybe we want to test the cartesian product, which would imply testing all the test cases in all the combinations of browsers and operating systems...in this example, that would mean a total of 36 combinations.

In some contexts we could apply only an each-choice combination, reducing the time invested in testing different platforms. This is the most lightweight option, where we would run only 4 combinations, each test case in one browser, in one OS.

Or we could have something in the middle, using a tool to design the pairwise combination, we would run 12 combinations in total, covering all possible pairs.

As you can see, testing has quite a lot of things to cover...and I have only mentioned some of the criteria to take into account!

How can we achieve the desired level of test coverage then? Remember this:

So, we need to plan and decide what we are testing, which means, we need to decide what to cover.

## **Laying Out a Plan to Optimize Test Coverage Over Time **

Here's a strategy that Abstracta has used that you could take into consideration in order to improve your approach for test coverage, since, as it happens in most teams, there is never enough time to reach the test coverage you need.

If this is the case, a good practice is to improve test coverage over multiple test cycles, in the long term.

Imagine we have different features to test on different browsers and have organized different test suites with the corresponding test cases, each suite with its own priority.

The proposal is to run the most critical test cases against all browsers everytime (this is the first row of the table, in green, the one named "priority"), but, we can decide to run the rest of the test suites on a single browser. A different browser for each suite, so, we are exercising the system in different browsers.

In the following test cycles, we can exchange the "test suite/browser" combinations. That way, in each test cycle we do not have perfect coverage, but after multiple test cycles we improve it.

Where it says "date 1", it could also say "sprint 1", "iteration 1", "day 1", or even "version 1."

The goal here is to distinguish which test cases we will run in each iteration in each environment.

![](https://abstracta.us/wp-content/uploads/2016/05/Graphs-01-1-1024x797.png)

> _When time is scarce, we have to use it wisely and do our best to reduce risk._

Here is another example applied to mobile testing in order to reduce risk related to device fragmentation. It's the same idea, but different test cycles are running each test case on a different device.

![](https://abstracta.us/wp-content/uploads/2016/05/Graphs-02-1-1024x379.png)

After the third execution, you'd have covered all combinations: each test case on each device.

![](https://abstracta.us/wp-content/uploads/2018/08/Screen-Shot-2018-08-10-at-4.40.27-PM-min.png)

It's a very simple strategy, that doesn't provide perfect coverage, but it's better than not doing any cross-browser or cross-device testing at all.

As I mentioned when discussing pairwise, I believe that this strategy has a better cost-benefit relationship.

## **Where Automation Comes Into Play **

Following the sweeping analogy, if we chose to use a Roomba (which we can consider to be a tool for "sweep automation"), we can use it to cover those high-risk spots for us, or those places that we want to sweep every day, allowing us to focus on cleaning new areas.

![](https://abstracta.us/wp-content/uploads/2018/08/roomba-puppy-A-min-1024x535.jpg)

To cover different devices or browsers or operating systems, I find it very useful to use tools like [CrossBrowserTesting](https://crossbrowsertesting.com/) because we can have quick access to different combinations of platforms and browsers. So, once we have our plan for covering different scenarios in different platforms, we can access them easily through our browser.

### **Watch a Demo **

Here you can watch the portion of the webinar in which I give a six-minute demo for using CrossBrowserTesting live. You'll see how the tool helped me uncover a problem with Abstracta's own website when someone accesses it using Windows 7 and Internet Explorer 8... whoops!

## **Careful With Test Coverage -- Automation Can Help! **

To bring it all home, the main takeaways from the webinar are that:

  * Test coverage is very useful, but it doesn't signify your software is bug-free when it's fully met.
  * There are different criteria and levels to take into consideration when defining the test plan.
  * You can use a simple strategy to increase coverage over time.
  * Automation with tools like CrossBrowserTesting can help improve test coverage by automating critical flows and providing access to the platforms we want to cover.

I really believe that by understanding testing coverage and considering these techniques and automation as part of a test strategy, testers can do a better job of mitigating risks.

Have you used strategies or a tool like this to boost test coverage?

Learn how to get 20x more performance than Elastic by [moving to a Time Series database](https://dzone.com/go?i=283422&u=https%3A%2F%2Fwww.influxdata.com%2Fresources%2Fbenchmarking-influxdb-vs-elasticsearch-for-time-series%2F%3Futm_campaign%3Ddbzone%26utm_medium%3Dpartner%26utm_source%3Ddzone%26utm_content%3D%26utm_term%3D).
