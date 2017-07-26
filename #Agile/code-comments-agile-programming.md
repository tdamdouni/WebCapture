# Code Comments & Agile Programming

_Captured: 2017-06-03 at 01:16 from [blog.dmbcllc.com](https://blog.dmbcllc.com/code-comments/)_

![PEOP0067](https://blog.dmbcllc.com/wp-content/uploads/2015/05/PEOP0067.png)

A long time ago, in a galaxy far far away, we were forced to name variables and methods with very short names. When I started my career, I was programming Clipper and C. Clipper was a dBase compiler, so it only had 10 characters available for variable names. You could write longer variable names if you wanted, but only the first 10 mattered. I think at the time, C gave us 32 characters. But now, we aren't so limited. And so the argument goes, if you use long variable names, you shouldn't need to comment your code. I've argued as much.

Of course every time you bring this subject up, you will inevitably find someone who will say, "But don't we need comments to at least explain what the code was supposed to do? After all, code is generally hard to read." Well, yes I guess it is if you are new to the language. But should every foreign movie have subtitles? Would you want native language movies to have subtitles because other people in the room might not understand it? Must we dumb everything down to the lowest common denominator? If so, where will it stop?

## Sometimes Comments Are Needed

And yet, I would argue that there are times when comments make sense. Not so much for what you did, but for explaining why you decided to do it the way you did. Again, you don't always have to do this. But there are times when I write my code that I look at it and think, "If I come back to this three months from now, I'm going to wonder what I was thinking. I'd better add a comment to make this a bit more clear as to why this statement is here."

You see, it is the WHY that we comment. Not the what. The what would be described in the code itself.

## A Perfect World

But this all assumes a perfect world. And judging from the comments and blog post I've seen on the subject, I believe this is where the real arguments for and against code comments, have their origin.

First, let's assume for a second that you are of the persuasion that you need to comment code to tell the reader what it is you are trying to accomplish. Where else could we put that information?

## Requirements in lieu of Comments

Well, in a perfect world, there would be some kind of requirements document that would state that this feature was needed. The problem is, of course, it is hard to associate the design document with the code you are writing because most design documents are really long. Even for the most trivial of programs. But in an Agile world, there would be some sort of back log. A list of requirements that are broken down into small enough task that each one can be implemented as a discreet unit. Even in an environment that is more Scrumerfall than truly Scrum, you could implement this by breaking the requirements down so they all ended up in a task list of some sort.

But we still lack the ability to associate the code with the feature.

Well, there are several systems available that allow you to associate task in your backlog with code you've checked in. You just associate the code you are checking in with the backlog item it is associated with and the system established a two way link between the code that was changed and the backlog item that it is associated with.

## Tests as Comments

The next place you might associate changes with what it is you are trying to do is by creating Unit Test for the code you are writing. The way I write my Unit Test, I have one Unit Test class per method and Given/Arrange I am testing. Within that class I have a different test for each When/Then or Act/Assert the Given or Arrange I am trying to test. This allows me to write my test in such a way that I know what class and method is being tested and what the test.

So if I have a Class named Math that has an Add function:
    
    
    namespace Math
    {
        public class Math
        {
            public int Add(int a, int b)
            {
                return a + b;
            }
        }
    }

I might have a test class that looks like:
    
    
    namespace Math.Math.Add
    {
       [TestFixture]
        public class GivenTwoPositiveNumberAsParameters
        {
            private _math;
            [SetUp]
            public void Setup()
            {
                _math = new Math();
            }
            
            [Test]
            [TestCase(1,1)]
            [TestCase(5,7)]
            public void ThenTheResultShouldBePositive(int a, int b)
            {
               Assert.That(_math.Add(a,b), Is.GreaterThan(0));
            }
        }
    }

Yes, I know the test itself is a weak test. The point is the structure of the test. I can find the tests for any one class because the test that are associated with the class are structured in such a way as to find out what the original requirement was for the test. And so, even if I don't have any documentation from a backlog or even from a design document. Because of the structure of the test, it would be relatively simple to write a tool that would let you view your code and the associated test in a hyperlinked fashion so that you could easily identify the tests associated with your code and the code associated with your tests.

## TDD as Comments - A Story

Right after the dotCom crash, I ended up working for a company that had a system that they had lost the documentation for. That is, there was no requirements document and they didn't want to admit to the client we were working for that they had lost the document. So, my job eventually became one of perpetual bug fixing. And of course, since I had no idea what the system was supposed to do, I'm sure every time I fixed a bug, I introduced three more. This was 15 years ago and I had not yet gotten TDD religion. But looking back on it now, I see that what I could have been doing from day one is that I could have been writing unit test for each bug that came in. Eventually, my test suite would be my documentation and there wouldn't be any more bugs.

Unlike code comments, if you are running your tests as part of a continuous integration system, you will be forced to keep your test up to date as the code changes. Obviously, you should be updating the test, or creating new tests before you make changes, but even if you don't, if you make a change that breaks the test, you will be forced to either fix the code so that the test succeeds or fix the test to match the new requirement.

But this doesn't really address the broader code quality issue. At times we still need comments and they can't be addressed by writing unit tests. But this is why we need at least occasional paired programming and systematic code reviews.

## Code Reviews

Several questions should be raised during code reviews:

  * Is this code too complex?
  * Have we named things appropriately?
  * Are there any dependencies that need to be removed?
  * Are there any comments that we could add that would help a future developer maintain this code without possibly confusing him when the code changes?

I've talked about a lot of these issues before so I'm not going to go into a lot of detail here other than to say that you should notice that I've placed the issue of code comments LAST on the list of things to consider. This is because if you take care of the code quality, you will find that most of the time when you get to the issue of comments, no one will have anything to add.

## Conclusion

If you are working at an organization where you have no tests, you routinely deal with 1000 line methods, names of things seem arbitrary, you have no real backlog, and your code is not loosely coupled, I can see why you might think you need comments in your code. But the problem isn't the lack of comments. The problem is, you are dealing with bad code.

## Other Resources

This page contains copyright material from [//blog.dmbcllc.com](https://blog.dmbcllc.com) and you have no rights to copy and paste the full text into your own blog even if you have written permission to the contrary. Violations will be reported.

**Other post in Programming Best Practice**

  * [Treat Warnings As Errors](https://blog.dmbcllc.com/treat-warnings-as-errors/) \- May 15th, 2014
  * [DRY Programming](https://blog.dmbcllc.com/dry-programming/) \- May 29th, 2014
  * [Avoiding Code Complexity](https://blog.dmbcllc.com/avoiding-code-complexity/) \- June 19th, 2014
  * [Defining &ldquo;Done&rdquo;](https://blog.dmbcllc.com/defining-done/) \- July 10th, 2014
  * [JavaScript Performance Tweaks](https://blog.dmbcllc.com/javascript-performance-tweaks/) \- August 21st, 2014
  * [Technical Debt Is Inevitable](https://blog.dmbcllc.com/technical-debt-is-inevitable/) \- October 16th, 2014
  * [Raking Leaves and Writing Code](https://blog.dmbcllc.com/raking-leaves-and-writing-code/) \- November 20th, 2014
  * [Magic Strings and Magic Numbers](https://blog.dmbcllc.com/magic-strings-and-numbers/) \- December 18th, 2014
  * [Limiting Beliefs of Programmers](https://blog.dmbcllc.com/limiting-beliefs-of-programmers/) \- April 9th, 2015
  * [Code Comments &amp; Agile Programming](https://blog.dmbcllc.com/code-comments/) \- May 14th, 2015
  * [Debugging Software](https://blog.dmbcllc.com/debugging-software/) \- June 25th, 2015
  * [How to Sabotage Estimates](https://blog.dmbcllc.com/how-to-sabotage-estimates/) \- August 23rd, 2016
  * [The Myth of Sloppy Code](https://blog.dmbcllc.com/the-myth-of-sloppy-code/) \- October 18th, 2016
