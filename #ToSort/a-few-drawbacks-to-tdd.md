# A Few "Drawbacks to TDD"

_Captured: 2017-03-08 at 09:24 from [blog.jbrains.ca](http://blog.jbrains.ca/permalink/a-few-drawbacks-to-tdd?utm_content=buffer992d0&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

I teach test-driven development (TDD) quite frequently, and so naturally people ask me when _not_ to practise TDD. Here I describe a few situations in which practising TDD might hurt more than it helps. Although the original questioner asked for "drawbacks to TDD", I don't think in terms of "good or bad practices", nor "what or whom to blame", but rather how the situation and the practice interact with each other.

## Not A Significant Problem

I use TDD to gain feedback about my design, so that I can improve it, and lower the cost of adding features in the future. If you have more urgent, more costly problems than this, then TDD might help you solve a problem that doesn't make your situation any better. For example: maybe you have a big problem with bugs, so the refactoring part of TDD will not help you as much as the testing part will. In this situation, writing the tests first or last becomes a question of discipline and style for most people. (Read about Theory of Constraints and learn about bottleneck theory and throughput accounting. The book _[The Goal_](http://link.jbrains.ca/1dmhLhC) could help.)

## Not How They Measure You

If someone important in management measures your performance by how quickly you "get something done", but ignores how long it takes to fix bugs, then practising TDD will make you look slower than the people around you, even though you might actually be finishing work sooner than they do. For example: your organization has a separate testing budget and some important manager somewhere actively wants to push work into the testing organization (and onto _their_ budget). In this situation, when you practise TDD you take on a responsibility that makes that manager look worse, not better, even if it improves the overall situation. Not testing _at all_--letting the testers do it--might provide a better strategy as long as this situation exists. (Learn about dealing with people, and how "you get what you measure". The book _[The Three Signs of a Miserable Job_](http://link.jbrains.ca/10YFc8J) might help.)

## Just Plain Too Hard to Do

If you work in a domain or environment where you don't know the expected outcome in advance, or you can't easily describe the expected outcome in advance, then you will find it difficult to write tests first. You might be doing original research. You might be producing bitmapped image files that don't need to match 100% to the "expected result". If you can't describe in advance the result you want, then you can't write the test first. If you can't describe the result you want _except_ to look at it, and multiple acceptable results are possible, and you don't know how to describe what they all have in common, then you might not be able to automate the test _at all_. (Learn more about general testing theory do understand what you _could_ test. The book _[Lessons Learned in Software Testing_](http://link.jbrains.ca/R0XsSo) might help.)
