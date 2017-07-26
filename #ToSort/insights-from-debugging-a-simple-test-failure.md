# Insights From Debugging a ''Simple'' Test Failure

_Captured: 2017-03-02 at 18:22 from [dzone.com](https://dzone.com/articles/insights-from-debugging-a-quotsimplequot-test-fail?oid=twitter&utm_content=bufferfd45e&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Discover 50 of the latest mobile performance statistics with the [Ultimate Guide to Digital Experience Monitoring](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE).

Brian and I were pairing on a new client's project recently. We were working towards expanding the functionality of an existing method. We figured out a new method that would be best, added it to the class, threw it in the appropriate controllers and views, and did some manual testing on a locally run version of the app. Everything looked good, so I mentioned we should add some specs for our new method. (I know, I know, shame on us for forgetting TDD.)

We add some specs, run the test suite, and get hit with an error. No problem. Let's see what the new specs are complaining about. Upon closer inspection, though, we notice the failing spec is not one of our new ones, but a previously existing one. So, we jump into breaking down the failing spec and method. First, here's the method.

There's a Player class that has a Date of Birth attribute. There is then an age method for a Player that returns how old that player is in years from today's date. Here is the age method:
    
    
    now.year - birthday.year - ((now.month > birthday.month || (now.month == birthday.month && now.day >= birthday.day)) ? 0 : 1)

The method gets the difference between the current year and the year the Player was born. Then, it checks to see if today's month and day are greater than the Player's birth day and month. If it is, it subtracts one year from the original difference since that Player has not had their birthday yet. Seems fairly straightforward, and you can find similar (if not copy+paste exact) versions from StackOverflow and Rails forums.

So, now we are looking at a failing spec that the age method "should be able to handle players born on a leap year." The actual output was off by one year of the expected output. I immediately shift into my debugging mode and start rattling off every potential problem I can think of.

Had we missed something? Was our new method overriding or somehow altering the age method? Did we miss edge cases where the age method would get messed up due to leap years?

I immediately started whiteboarding potential conflicting issues.

What happens if we check someone's age on February 29 of leap year? If we pretend it's February 28 and check someone born on February 29? Pretend it's March 1 and check someone born in Feb 29? Have we checked to see if there are errors when someone attempts to enter February 29 as a birthday on a non-leap year?

Luckily, Brian brought me back down from orbit by asking a rather simple question: What is the spec asking? I was so concerned with dissecting the method that failed a test that I had scarcely glanced at the test itself. Here was the test:
    
    
        expected_age = (Date.today.year - 1992) + ((Date.today.month < 2 && Date.today.day < 26) ? 1 : 0)
    
    
    player = Factory(: player, : birthday => Date.new(1992, 2, 26))

So, my initial burst of debugging energy should have been directed at the spec instead of the method it was testing. After analyzing the test for awhile, I realized it had three key issues:

  1. It repeats code it's testing without calling the actual method.
  2. It's not comprehensive.
  3. It doesn't properly test what it says it's testing.

Let's dive into these three issues and uncover possible solutions to each one.

## 1\. It Repeats Code Without Calling the Actual Method

To me, this was the biggest red flag on the test. In the spec, the line creating the variable `expected_age` is essentially a repeat of the age method. We are definitely unit testing the Player class here, so we should not be relying on logic we are in the middle of testing to create our expected answer. Otherwise, we'd need a test to see if our test logic was working properly. We could have a very large test suite if we adopted that kind of testing strategy. It's unit tests all the way down!

A better solution here is to remove the dynamic variable of today's date from the equation. We achieve this by spoofing a constant date as today's date to get a consistent answer from the age method. Then we test the age method against several already known ages based on that consistent date. There are several ways to do this, including using the [ActiveSupport TimeHelpers](http://api.rubyonrails.org/classes/ActiveSupport/Testing/TimeHelpers.html) or the [TimeCop Gem](https://github.com/travisjeffery/timecop).

## 2\. It's Not Comprehensive

This test seems a little too narrow in scope for the issue it is attempting to test. Just picking and testing a random date in a leap year is far from exhaustive and leaves plenty of room for edge cases to creep in. For something discussing leap years, not even using February 29 anywhere in the test should be a warning that you might not have everything covered. Testing dates can be tricky so we should not just rely on one instance of test being enough to satisfy a wide berth of potential problems.

A quick, if inelegant, solution would be to [prove this by exhaustion](https://en.wikipedia.org/wiki/Proof_by_exhaustion). This would involve creating three players to test: one born on a February 28, one on February 29, and one on March 1, then testing each of their ages based on three spoofed dates: February 28, February 29, and March 1. I'm sure there are more elegant ways to test this method but brute forcing it was the most time-efficient approach for us.

## 3\. It Doesn't Properly Test What It Says It's Testing

While this issue is essentially taken care of by following the above recommendations, it's still worth exploring. Let's compare the main logic of the age method with the spec's first line:

Main logic:
    
    
    now.year - birthday.year - ((now.month > birthday.month || (now.month == birthday.month && now.day >= birthday.day)) ? 0 : 1)

Spec:
    
    
    expected_age = (Date.today.year - 1992) + ((Date.today.month < 2 &&         Date.today.day < 26) ? 1 : 0)

The areas `now.month > birthday.month` and `Date.today.month` are where I notice a major flaw in logic. Since the spec flips the logic around to add a year in an affirmative case, the logic is also flipped around. But changing from the greater-than comparator to a less-than comparator, in this case, is incorrect. To maintain a similar effect with the flip in the action, you need to use the less-than-or-equal to comparator.

Again, this code shouldn't really even be necessary in the spec once we approach the problem from the correct angle, but it's always good to remind yourself of how to use comparators properly.

## Diving Into a New Test Suite

So, when you are diving into a new codebase and test suite, be skeptical of how methods and tests arrive at their conclusions. Just because there is an existing, working test suite doesn't mean you're totally covered. Especially when you are inheriting existing code, it never hurts to analyze the source code with a bit of healthy distrust. Not only could you solve some potential problems, but it will definitely help you get more comfortable and familiar with the new project!

Also, take time to look at the context of tests and see if the code actually matches with its stated purpose. This can be more difficult than it sounds, especially because this task is more qualitative than quantitative. It isn't something that can be automated (as far as I know...just give the AI guys some time I suppose). It requires an understanding of what the program should do, what the test says it's looking for, and what the spec is actually testing.

All of these things require a bit of expertise and, more importantly, time. It's important to budget time towards getting familiar with an app so you can feel confident in its test suite before you start deploying.

Lastly, pairing can give you great perspectives on code, especially when you are looking at it for the first time. Had I run into this issue while working on the code alone, I guarantee I would have spent far more time looking directly at the age method, trying to break down where it could be going wrong when I needed to be directing my attention to the test itself.

[Is your APM strategy broken?](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) This [ebook](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) explores the latest in Gartner research to help you learn how to [close the end-user experience gap in APM](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE).
