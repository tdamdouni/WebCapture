# How to Write Better Unit Tests For Embedded Software With TDD

_Captured: 2017-12-04 at 13:38 from [www.allaboutcircuits.com](https://www.allaboutcircuits.com/technical-articles/how-test-driven-development-can-help-you-write-better-unit-tests/)_

Want to try unit testing your embedded software? Here's why you should start with TDD.

Unit tests can help you write better embedded software. If you're interested in [the benefits of unit testing for yourself](https://www.allaboutcircuits.com/technical-articles/unit-tests-can-help-you-write-better-embedded-software...-heres-how/), you should start with test-driven development (TDD).

### What is TDD?

Test-driven development (TDD) is an iterative process for writing software, where the unit tests are developed just before the implementation. It's a tight feedback loop consisting of these steps:

  1. Write a unit test, watch it fail.
  2. Write just enough code to pass the test.
  3. Improve the code (without changing its behavior).

These steps are often referred to as "red, green, refactor," for the way in which the tests go from failing (red) to passing (green), with a final opportunity to improve the code and the tests (refactor). During development, this cycle is repeated over and over again hundreds or thousands of times.

![](https://www.allaboutcircuits.com/uploads/articles/red-green-refactor.png)

In this process, writing the tests is what _drives_ the development of the software. You think about what you want the code to do before you write it, and you save that idea in a unit test. Only then do you write the next bit of code. This forces you to be very clear about what you want the code to do.

With each passing test, you build a bit more confidence that your software is working correctly. And, since every bit of code is driven by a test, you end up with great _test coverage_ \-- the amount of your code that is tested with unit tests.

### Don't waste your time writing untestable code

One of the problems with unit tests -- especially when you're just getting started -- is that you might end up writing code that's difficult to test.

For example, maybe you've got some internal state that you need to access, but you don't want to expose it. Or maybe your unit under test has a lot of complicated dependencies that are difficult to mock.

Writing code that is testable requires experience, but how can you get that? Well, it turns out that _you don't need that experience if you start with TDD_. **When you write the tests first, you can't write untestable code.**

You'll be successful right from the start, and so you'll be more likely to actually adopt unit testing as a practice. Imagine two scenarios:

Scenario 1: You write a whole bunch of code, then you try to figure out how to test it. When you can't figure it out quickly, you give up because you've got software to ship! Maybe you learn something about how to make your code more testable for next time.

Scenario 2: You have an idea for some software module to create, but you're not sure how to test it. So, you spend a little time figuring out how to write the first test. Then you write some code to make it pass. Alright! You just wrote your first unit test. Nice work, you just learned something. Repeat until you have a fully unit-tested module. Congratulations... you just learned so much about unit testing.

TDD is an _experience amplifier_. You learn by doing. TDD encourages you to do the right things, so you learn more quickly. The more you learn, the better you'll get at writing unit tests.

### The test-driven mindset

When test-driving, you think about the code that you're writing a little differently. Instead of trying to keep track of _everything_ you want your software to do, you just worry about the _next thing_ that you want your software to do. Let's look at an example to illustrate.

One of my favorite examples for discussing TDD is a _command parser_, because it's used in so many embedded systems. Often, you want your system to be able to talk to the outside world so that it can actually do interesting things. This might be just a simple serial interface used for configuration, or it might be a connection to another device, or maybe the Internet.

In my experience, these sorts of interfaces can really benefit from unit testing. They are typically custom-built, and can quickly get complicated -- with many paths through the code and many error cases to handle. And, since this is an external interface to the system, you can't always expect the guy on the other end to behave nicely. With some unit tests though, you can make sure everything works as expected -- and all the error cases are handled.

Consider an embedded system with a simple command parser. It takes in a stream of characters from somewhere (maybe serial or USB for example, but our parser doesn't actually care) and does something when a particular sequence of characters is received. In this case, there's a speaker in the system that can be controlled.

![](https://www.allaboutcircuits.com/uploads/articles/command_processor_external.png)

The first instinct for most embedded software developers would be to start writing a whole bunch of code in command_parser.c. The test-driven approach is different.

The first step is:_ write a test, watch it fail_. In order to write a test, you need to figure out the first thing you want your command parser to do. If there's a protocol spec (ha, right!) you might take a look at that. If not, you can just decide right now what you need the code to do first. How about this?

_When an "m" character is received, then the speaker is muted._

Alright, that's a simple, small, and clearly-defined piece of functionality. Let's write a unit test that would pass if the code to do this were implemented.
    
    
                        #include "some_test_framework.h"
    #include "some_mock_framework.h"
    #include "command_parser.h"
    #include "mock_speaker.h" 
    
    // A test for the command_parser.
    void test_WhenAnMIsReceived_ThenTheSpeakerIsMuted(void)
    {
         // Receive an "m."
         command_parser_put_char('m');
    
         // Make sure the mute function is called.
         EXPECT_CALL(speaker_mute());
    }
                      

Whoa, this is just a single test but there are quite a few design decisions in here.

There's a new function defined for the command parser: `command_parser_put_char()`. This is how characters are fed into the command parser, and how the "m" is passed in for the test.

![](https://www.allaboutcircuits.com/uploads/articles/command_processor_internal.png)

There's also another new function that has been defined for the speaker module: `speaker_mute()`. This is what will do the actual muting of the speaker. You know that the test has passed when this function has been called.

Since this is a unit test, the command_parser will be tested in isolation and the real version of speaker_mute() will not be called. Instead, a mock function will be provided (possibly included in `mock_speaker.h`), and the `EXPECT_CALL` macro is a stand-in for whatever mocking mechanism is used. It will fail the test is the `speaker_mute()` function is not called.

Note that neither of these functions actually exist yet. But... you've just defined an exact behavior you want and you have an explicit way to test for it. If you were to run the test now it would certainly fail. In fact, it will fail to compile because the functions don't exist.

Now for step two: _write just enough code to pass the test_. It's finally time to write some code! Here is the simplest bit of code needed in `command_parser_put_char()` to make the test pass:
    
    
                        // Receive a character.
    void command_parser_put_char(char next_char)
    {
         speaker_mute();
    }
                      

_Note that you would also need to set up your mock for `speaker_mute()`. The details for this will depend on how you are using mocks in your project._

The test should pass now... but notice that we don't even check to see which character we received! This might seem kind of silly, but one of the goals of TDD is _maximizing the amount of work NOT done_.

Right now this is a trivial example. When the code gets more complicated, though, any code that you _don't_ actually write is going make your application simpler and easier to understand (ahem.. better). And when you're only doing exactly as much work as you need to, the people who care about the schedule and the budget are happier too.

The final step in the TDD cycle is to refactor, where you_ improve the code without changing its behavior_. The key to this step is that you already have unit tests that verify the behavior. So, you're free to experiment with changing the code because a failing test will tell you immediately if you changed the behavior. Since this is just the first test, though, there's not much to improve yet.

The rest of the command parser is implemented by repeating the TDD cycle. So, what do you want it your command parser to do next? How about:

_When an "u" character is received, then the speaker is unmuted._

Alright, this is another good one. Here's a test:
    
    
                        void test_WhenAUIsReceived_ThenTheSpeakerIsUnmuted(void)
    {
         // When
         command_parser_put_char('u');
    
         // Then
         EXPECT_CALL(speaker_unmute());
    }
                      

When you improve the command parser implementation to the pass the test, it might look something like this:
    
    
                        void command_parser_put_char(char next_char)
    {
         if (next_char == 'm')
         {    
              speaker_mute();
         }
         else
         {
              speaker_unmute();
         }
    }
                      

What about handling an error case now? What if an unexpected character is received?

_When an unexpected character is received, then the speaker mute state is unchanged._
    
    
                        void test_WhenAnUnexpectedCharIsReceived_ThenTheSpeakerMuteStateIsUnchanged(void)
    {
         // When
         command_parser_put_char('!');
    
         // Then
         DO_NOT_EXPECT_CALL(speaker_mute());
         DO_NOT_EXPECT_CALL(speaker_unmute());
    }
                      

And here is just enough code to make this test pass:
    
    
                        void command_parser_put_char(char next_char)
    {
         if (next_char == 'm')
         {    
              speaker_mute();
         }
         else if (next_char == 'u')
         {
              speaker_unmute();
         }
    }
                      

Is there anything that you want to refactor yet here? If you'd prefer a switch statement, you might go ahead and change it:
    
    
                        void command_parser_put_char(char next_char)
    {
         switch(next_char)
         {
         case 'm':
              speaker_mute();
              break;
         case 'u':
               speaker_unmute();
              break;
         default:
              break;
         }
    }
                      

Hmm, did this change break anything? No sweat, just run your tests to find out.

From here you just keep running the TDD cycle -- adding tests and functionality -- until the command parser does everything you need it to.

As an exercise, consider that there is another command that allows you to set the volume level. Maybe a "v" followed by a number. How would you write a test for that? This is going to introduce new error cases too. What if the number isn't a valid one? What if you get a "v" followed immediately by an "m?" You can see how this might quickly get complicated. But you can write a test for every one of these error cases! In each case you know exactly how the command parser is supposed to behave -- if it doesn't the unit tests will let you know.

### Reduce complex problems into simpler ones

Building a command parser (or any software module for that matter) is a complex task. If you're trying to envision the completed module before you've even started, it can be difficult. This is especially true if you're implementing something you've never done before, because you don't have the experience to apply any design patterns. Cramming all of this into your brain at once results in a _high cognitive load_.

But the test-driven approach can reduce your cognitive load, freeing up your brain to write some really great software. Look at what we just did in the command parser example. At each step we were only concerned with the _next bit of functionality to add_ \-- not _all the functionality_ we might add in the future. Deferring all those other concerns until later allows you to focus all of our attention on one thing at a time.

### The tools

So TDD is great, right? One problem tough is that the embedded software (that means C) test tools haven't been that great. When you're doing TDD, you're creating and running tests _all the time_. This means you need it to be really easy to add new tests and run them. If these things are difficult at all, you'll probably get frustrated and give up.

It's getting better though. Tools like Ceedling (with Unity and CMock) can get you up and running quickly. Ceedling provides automatic test discovery, mock generation and test execution to make your life easier. That's why I recommend it to anybody new to embedded unit testing, and I've written specifically about [how to use Ceedling to get started with TDD in C](http://www.electronvector.com/blog/try-embedded-test-driven-development-right-now-with-ceedling).

TDD isn't used widely in embedded software. If you start experimenting with TDD, you're going to be pushing the edge of embedded software development (and you can talk to your app and web developer friends about it!). There will still be plenty to learn, but you'll be on the path to improving yourself and your code. I think you'll like what you discover.
