# The Deadly Sins of Unit Testing — Part 1

_Captured: 2018-07-06 at 19:31 from [dzone.com](https://dzone.com/articles/the-deadly-sins-of-unit-testing-part-1)_

![](https://www.typemock.com/wp-content/uploads/2018/06/part1.jpg)

What makes for [bad unit tests](https://www.typemock.com/why-do-programmers-fail-to-write-good-unit-tests/)? What are the signs that your test suite needs a little more care? That's what this post is about. But I thought that just listing a bunch of items could make for a boring read.

So, in an attempt to make things a little bit more playful, I've come up with a metaphor. Today I proudly (oops, that's a sin, isn't it?) present to you the seven deadly sins of unit testing.

## Unit Testing Greed

The first sin we'll cover is greed. "How on earth can a unit test be greedy?" you might be asking to yourself. Or maybe not, since people have been using [this metaphor in computer science](https://en.wikipedia.org/wiki/Greedy_algorithm) for quite a while.

What makes for a greedy unit test? Well, even though I'm sure you know what the word means, maybe it'd make sense for us to start out by defining greed itself. It's often illuminating. So, let's see what [the online version of the Cambridge Dictionary has to say](https://dictionary.cambridge.org/dictionary/english/greed):

> "A very strong wish to continuously get more of something, especially food or money."

So, a greedy person is a person who _wants always more_. They're never satisfied. In the same way, think of a greedy test as a test that always needs more. More assertions, more complex scenarios to in which to instantiate the [SUT](https://en.wikipedia.org/wiki/System_under_test), and so on.

Some people take the position that only one assert should be allowed per test method. I think that's a little bit too extreme, but maybe it's wise to err to the side of less. No matter which side you take on this matter, always remember to think of a test case as a single example of the SUT's behavior.

Let's see a quick example, using the C# language. Suppose we're test driving the creation of a stack class (for a code kata session, for example) and we wrote the following test:
    
    
        Assert.Throws<EmptyStackException>(() => sut.Pop());

Is this test greedy? As I've mentioned earlier, having more than one assert isn't automatically a problem (even though having way too many is definitely a red flag). But more important than the quantity of asserts is their quality-their semantics. The test name promises that it tests for just a single scenario: trying to pop from an empty stack, which should throw an exception. But the test goes way beyond that and tests other behaviors, each one deserving of its own focused and well-named test case.

Verdict: definitely greedy.

## Unit Testing Pride

Have you ever met a snob? It doesn't matter the area of their expertise-be it coffee, cinema, music, or anything, really-they're always ready to bury us mere mortals in tons of unsolicited advice and contempt. "Do you seriously listen to music on this Spotify thing? That's pure garbage! Vinyl is the only true way, you heretic!"

That's the persona my mind conjures when I try to think of what a proud unit test would be. Well, to be honest, I'm more thinking of proud code in general. It's the code that seems to pride itself in the fact that it's hard to understand. Can you picture code like this? I bet you can.

Let's extrapolate to unit tests, then. Similar to proud code, proud tests are tests that are too fancy for their own good.

What causes unit testing pride? A variety of reasons, most likely. Maybe the developer had just learned a new language feature -- or at least, new to _them -- _and wanted to use it everywhere_. _Or maybe it was the other way around: the developer didn't know a language feature that would greatly reduce the complexity of the code.

The developer might have even decided that, for whatever reason, it was ugly to hardcode the expected values of an assertion. So they decided to use some logic to generate. Double mistake: besides adding more complexity to the test, they probably ended up duplicating the production implementation in the test code, which can lead to nasty, hard-to-find bugs.

Quick example: a test for the famous [String Calculator Kata](http://osherove.com/tdd-kata-1/) in which the developer got impatient and duplicated the implementation in the test:

Of course, the code above is nothing more than a toy example. Consider it a proxy for more complex code. But I believe that, even in its simplicity, it drives the point home. The second line in the method is a perfect mirror of the implementation code. What if they're both wrong? In this case, the test will pass, but the implementation would be wrong. That's a nightmarish situation to be in.
