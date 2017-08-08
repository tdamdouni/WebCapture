# Model-Driven Software Development meets Test-Driven Development

_Captured: 2017-08-04 at 22:13 from [blogs.itemis.com](https://blogs.itemis.com/en/model-driven-software-development-meets-test-driven-development?utm_source=hs_email&utm_medium=email&utm_content=54879111&_hsenc=p2ANqtz--U4Wtf_MzIfAz4GuORBg87ZA9s8OMVLp9bsVaTcXtnMSA0GNAmjDDdUpICuiG_E-DvFMG6rzpSitZedCGzYvSjMMnLBw&_hsmi=54879210)_

In this blog post you will learn how Model Driven Software Development (MDSD) and Test-Driven Development (TDD) can work together and how you can develop software model driven and test driven.

In case you don't know exactly what TDD is I will first give you a brief introduction.

## What is Test-Driven Development?

[TDD is a software development process in which you develop your software driven by tests that were written beforehand (test-first approach)](https://blogs.itemis.com/de/testgetriebene-entwicklung-mehr-als-nur-qualit%C3%A4tssicherung).

TDD basically consists of [three steps](https://martinfowler.com/bliki/TestDrivenDevelopment.html) you do repeatedly:

  * Write a test for the next bit of functionality you want to add.
  * Write the functional code until the test passes.
  * Refactor both, new and old code, to make it well-structured.  
  

![TDD Gobal Lifecycle Illustration](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/1_test-first-development-1.png?t=1501858086893&width=2148&name=1_test-first-development-1.png)

> _Quelle: https://commons.wikimedia.org/wiki/File:TDD_Global_Lifecycle.png_

The illustration shows how these three steps form one TDD cycle. First, you write the test, which is supposed to fail, and then you make the test succeed with the least amount of effort and code. If your test succeeded you check whether all other tests that you may have written before are also still succeeding. If that's the case you look for code that can be refactored. If not all of your tests succeeded you have to correct the regressions until all of your tests succeed. Then do the refactoring.

When writing tests for your software, you focus on the functionality of the software and not its implementation details . Tests may also serve as a formal requirement specification for your software and help other developers (and also non-developers) to understand the purpose of your code.

Test Driven Development goes along with cleaner and more understandable code, because you refactor your code in every TDD cycle.

You also follow a more conceptual approach of developing your software, because in every cycle you focus on only one thing to make it work. Therefore your development process is usually more structured than a non test-first approach.

## **Test-Driven Development and Model-Driven Software Development **

In the context of model-driven software development, however, you are not focussing on testing the implementing code that is usually generated automatically from your model. We expect the code generator to work correctly and to be tested by its developers. (Of course you can still also test the generated code if you want and write appropriate tests for the implementation language.)

However, if your are not focussing on testing the code, what are you focussing on instead when developing your model test-driven?

In test-driven software modeling your focus is on testing the functionality of the model under test.

In case your model is for example a state machine you would probably focus on points like the following:

  * Does the model contain all transitions that are needed or are you missing transitions?
  * Do you have the right guards for your transitions?
  * Did you include all states that are needed?
  * Do all state changes work correctly?

There are definitely more things you might want to check when modeling and developing a state machine.

Applying TDD to model-driven software development means to incrementally develop your model by first writing a test and then extending your model to satisfy the test. In a following refactoring step you would usually try to simplify the model's complexity while still fulfilling all tests.

Tests are also serving as documentation for your state machine. If you have to change something you are guarded by your tests and can check anytime whether your state machine still works as expected.

## SCTUnit Framework

To show you how MDSD combined with TDD might look, I will give you an example for [YAKINDU Statechart Tools](https://www.itemis.com/en/yakindu/state-machine/) and its unit testing framework SCTUnit.

SCTUnit is a unit testing framework for statemachines and part of the [Standard Edition of YAKINDU Statechart Tools](https://blogs.itemis.com/en/introducing-yakindu-statechart-tools-standard-edition-3.0). It allows test-driven development of statechart models on their semantic level. It generates unit tests for various platforms like C, C++, or Java. The tests can also be executed in the simulator view.

In this example we will create a [simple light switch](https://www.itemis.com/en/yakindu/state-machine/documentation/examples/example/light_switch) that can be turned on and off.

We start by creating a SCTUnit file and an empty statechart model and write a test for an initial state:

![testclass with test for an initial state](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/2_testclass-light-switch.png?t=1501858086893&width=1920&name=2_testclass-light-switch.png)

> _testclass with test for an initial state_

As you can see the test contains errors, because there is no "Off" state defined and therefore the test is not executable. According to the TDD cycle, the next step is to make the test green with the least amount of effort, therefore we create an "Off" state in our statechart model:

![off state in statechart model](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/3_main-region.png?t=1501858086893&width=960&name=3_main-region.png)

> _off state in statechart model_

SCTUnit provides the opportunity to execute the SCTUnit tests like a JUnit test in order to check whether our test still fails or whether it passes:

![test execution and feedback if it fails or passes](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/4_light-switch-test.png?t=1501858086893&width=1920&name=4_light-switch-test.png)

> _test execution and feedback if it fails or passes_

Since model and test are very simple at the moment we can't refactor anything, so we start the second cycle.

We would now like to test that the state machine changes its active state from "Off" to "On" when we raise the "operate" event:

![Testing state change when operate event is raised](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/5_testclass-light-switch.png?t=1501858086893&width=1920&name=5_testclass-light-switch.png)

> _Testing state change when operate event is raised_

There are errors in the test, because we don't have an event "operate" or a state "On" defined in the statechart model yet. So let's add them to the model:

![on state and operate event is being added to the model](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/6_statechart-on-off.png?t=1501858086893&width=1920&name=6_statechart-on-off.png)

> _on state and operate event is being added to the model_

The next step is to check whether these changes made our tests green or not:

![another test execution and feedback if it fails or passes](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/7_light-switch-test.png?t=1501858086893&width=1920&name=7_light-switch-test.png)

> _another test execution and feedback if it fails or passes_

After modeling the state on and the transition from "Off" to "On" we would now like to model that the state "On" changes to "Off" if we raise the event "operate" again. So what do we do? Right, we first write a test:

![First write a test before modeling the state change from on to off](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/8_testclass-light-switch.png?t=1501858086893&width=1920&name=8_testclass-light-switch.png)

> _First write a test before modeling the state change from on to off_

As we can see, there are no errors in the SCTUnit file, so let's run the test and see if it is green:

![Third test execution and feedback if it fails or passes](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/9_light-swith-test-1.png?t=1501858086893&width=1920&name=9_light-swith-test-1.png)

> _Third test execution and feedback if it fails or passes_

No surprise: the test isn't green, because we haven't added a transition from "On" to "Off" which would be activated when raising the event "operate". So let's add that transition to the model:

![transition is being added to the statechart model](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/10_statechart-light-switch.png?t=1501858086893&width=1920&name=10_statechart-light-switch.png)

> _transition is being added to the statechart model_

Running the tests again, the result is green now:

![11_light-switch-test.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/11_light-switch-test.png?t=1501858086893&width=1920&name=11_light-switch-test.png)

Looking at the SCTUnit file again, we see that we can refactor the tests a little bit.

The code fragment

`raise operate  
`cycle

is redundant in every test so let's extract this fragment into an extra operation:

![12_testclass-light-switch.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/12_testclass-light-switch.png?t=1501858086893&width=1920&name=12_testclass-light-switch.png)

Now we have developed/modeled a light switch state machine in a fully test-driven manner.

Of couse, this was only a short overview of SCTUnit. The framework provides far more features we haven't covered here, like:

  * Grouping test classes into test suites
  * Mocking operation return values
  * Asserting how often operations were called
  * Using control structures like loops, if-else
  * Virtual time for instant testing of time triggers
  * And much more..

For more information please read our [documentation](https://www.itemis.com/en/yakindu/state-machine/documentation/user-guide/#sctunit_test-driven_statechart_development_with_sctunit). At the moment, the testing framework is in its beta phase which means that we are still heavily working on it and, as always, happy for every feedback we get. So, try it out and tell us what you think!
