# 5 TDD Antipatterns

_Captured: 2017-08-27 at 16:48 from [www.madetech.com](https://www.madetech.com/blog/5-tdd-antipatterns)_

The value of a test suite can easily go down when complexity goes up, and a lot of the time this complexity can be prevented. There is [a great discussion on SO](http://stackoverflow.com/questions/333682/unit-testing-anti-patterns-catalogue) about this.

There are many ways to complicate your tests, these are my 5 favourite and most encountered ones in the wild:

## 

The Liar

Perhaps the most devious of them all.

This test instills confidence that the system is correct even though the [SUT](https://en.wikipedia.org/wiki/System_under_test) is actually broken. Exposing this test for what it really is can be challenging to say the least. It's hard to accept the fact that tests have bugs too.

This is also closely related to the Mockery anti-pattern where boundaries are stubbed out with expected values. If you don't ensure that your boundaries are always correct in an ever changing codebase, you can start getting false positives.

## 

The Free Ride

Instead of writing a new test case for the feature, you add another assertion to an existing test case. This often results in additional setup to get both assertions to pass, a short term win as you have to write less code to make the assertion.

Instead of preserving cohesion, you are creating the equivalent of god objects in your tests. When they fail you cannot be sure which assertion to look at. Integration tests with a large amount of required setup usually fall victim to this.

## 

Excessive Setup

Every line of setup makes a test more difficult to understand, it also increases the possibility of introducing new bugs. This is usually a sign that you have too many dependencies, and that a feature cannot exist without the known world being in a very particular state. It becomes even worse when you start mixing in doubles and stubs etc.

Sometimes you will still be required to do some setup, and tools exist to help you with this such as FactoryGirl. You need to be able to make the distinction between required setup and setup due to unreasonable application code. For reasonable code, you need to master composing factories in a minimal way so that you preserve the understandability of your tests.

## 

The Happy Path

I see this happening most frequently in large integration tests. You will write your happy path test, which requires a fair amount of setup, then discover an edge case. You do not want to duplicate all the setup code (as this would be an anti-pattern itself "Second Class Citizen"), and you do not want to piggy-back off the happy path test as we saw above.

This discourages edge case testing, and only the happy path test gets written. Important edge cases may be missed such as boundary testing where data may be too large to fit in a database field. A solution to this would be to write the happy path test in a black box feature spec, and to test edge cases at a lower level.

## 

The Flickering Test

This anti pattern is usually caused by race conditions.

Ruby waiting for Javascript or vice versa is something that is very common in web apps these days. "_Meh it's just a flicker_" the developer said, and ran the suite again, but what this test has done is declare the entire test suite as unreliable.

These flickering tests need to be solved, and if that is not possible, need to be isolated from the healthy tests. I prefer to not enable javascript in my Rspec tests, and if a piece of javascript is complicated enough, it should be tested with a Javascript testing framework.

Keep your tests clean and reasonable or you will very quickly lose faith in them.

For teams of software engineers, it's important to be able to deliver great software reliably and quickly, whilst keeping pain points to an absolute minimum.

![](https://assets.convertflow.com/uploads/7a33067e-7f8a-4520-8653-6bf04aee33d5/twitter_card_book_1.jpg)
