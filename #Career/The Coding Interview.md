# The Coding Interview

_Captured: 2016-05-23 at 13:38 from [www.palantir.com](https://www.palantir.com/2011/10/the-coding-interview/)_

![](https://www.palantir.com/wp-assets/wp-content/static/techblog/2011/09/einstein_coding_interview.jpg)

> _Note: this part is part two of our series on doing your best in interviews. Part one:_

"[How to Ace an Algorithms Interview"](https://www.palantir.com/2011/09/how-to-ace-an-algorithms-interview/)

Here at Palantir algorithms are important, but code is our lifeblood. We live and die by the quality of the code we ship. It's no surprise, then, that coding ability is what we stress the most in our interview process. A candidate can get by with mediocre algorithm skills (depending on the role), but no one can skimp on coding.

Suppose you're confident in your ability to write great software. Your task in a coding interview (of which there will be several) is to show the interviewers that you in fact do have the programming chops--that you're an experienced coder who knows how to write solid, production-quality code.

This is easier said than done. After all, coding in your [favorite IDE](http://eclipse.org/) from the comfort of `$familiar_place` is very different from coding on a whiteboard (on a problem you're totally unfamiliar with) in a pressure-filled 45-minute interview. We realize that the interview environment is not the real world, and we adjust our expectations accordingly. Nonetheless, there are a number of things you can do to put your best foot forward during the interview.

First, though, we'd like to give you a sense for what we look for during a coding interview. Most important is the ability to write clean **and** correct code--it's not enough just to be correct. A lot of people will be interacting with your code once you're on the job, so it should be readable, maintainable, and extensible where appropriate. If your solution is clean and correct, and you produced it in a reasonable amount of time without a lot of help, you're in good shape. But even if you stumble a bit, there are other ways to demonstrate your ability. As you work, we also watch for debugging ability, problem-solving and analytical skills, creativity, and an understanding of the ecosystem that surrounds production code.

With our evaluation criteria in mind, here are some suggestions we hope will help you perform at your very best.

## Before you start coding

  * **Make sure you understand the problem**. Don't hesitate to ask questions. Specifically, if any of the problem requirements seem loosely defined or otherwise unclear, ask your interviewer to make things more concrete. There is no penalty for asking for clarifications, and you don't want to miss a key requirement or proceed on unfounded assumptions.
  * **Work through simple examples**. This can be useful both before you begin and after you've finished coding. Working through simple examples before coding can give you additional clarity on the nature of the problem--it may help you notice additional cases or patterns in the problem that you would otherwise have missed had you been thinking more abstractly.
  * **Make a plan**. Be wary of jumping into code without thinking about your program's high-level structure. You don't have to work out every last detail (this can be difficult for more meaty problems), but you should give the matter sufficient thought. Without proper planning, you may be forced to waste your limited time reworking significant parts of your program.
  * **Choose a language**. At Palantir, we don't care what languages you know as long as you have a firm grasp on the fundamentals (decomposition, object-oriented design, etc.). That said, you need to be able to communicate with your interviewer, so choose something that both of you can understand. In general, it's easier for us if you use Java or C++, but we'll try to accommodate other languages. If all else fails, [devise your own pseudo-code](http://lolcode.org/). Just make sure it's precise (i.e. not hand-wavy) and internally consistent, and explain your choices as you go.

## While you're coding

  * **Think out loud**. Explain your thought process to your interviewer as you code. This helps you more fully communicate your solution, and gives your interviewer an opportunity to correct misconceptions or otherwise provide high-level guidance.
  * **Break the problem down and define abstractions**. One crucial skill we look for is the ability to handle complexity by breaking problems into manageable sub-problems. For anything non-trivial, you'll want to avoid writing one giant, monolithic function. Feel free to define helper functions, helper classes, and other abstractions to reach a working solution. You can leverage design patterns or other programming idioms as well. Ideally, your solution will be well-factored and as a result easy to read, understand, and prove correct.
  * **Delay the implementation of your helper functions**. (This serves a corollary to the previous point) Write out the signature, and make sure you understand the contract your helper will enforce, but don't implement it right away. This serves a number of purposes: (1) it shows that you're familiar with abstractions (by treating the method as an API); (2) it allows you to maintain momentum towards the overall solution; (3) it results in fewer context-switches for your brain (you can reason about each level of the call stack separately); and (4) your interviewer may grant you the implementation for free, if he or she considers it trivial.
  * **Don't get caught up in trivialities**. At Palantir we are much more interested in your general problem solving and coding abilities than your recall of library function names or obscure language syntax. If you can't remember exactly how to do something in your chosen language, make something up and just explain to your interviewer that you would look up the specifics in the documentation. Likewise, if you utilize an abstraction or programming idiom which admits a trivial implementation, don't be afraid to just write out the interface and omit the implementation so you can concentrate on more important aspects of the problem (e.g., "I'm going to use a circular buffer here with the following interface without writing out the full implementation").

## Once you have a solution

  * **Think about edge cases**. Naturally, you should strive for a solution that's correct in all observable aspects. Sometimes there will be a flaw in the core logic of your solution, but more often your only bugs will be in how you handle edge cases. (This is true of real-world engineering as well.) Make sure your solution works on all edge cases you can think of. One way you can search for edge-case bugs is to…
  * **Step through your code**. One of the best ways to check your work is to simulate how your code executes against a sample input. Take one of your earlier examples and make sure your code produces the right result. Huge caveat here: when mentally simulating how your code behaves, your brain will be tempted to project what it wants to happen rather than what actually says happen. Fight this tendency by being as literal as possible. For example, if you're calculating a string index with code like `str.length()-suffix.length()`, don't just assume you know where that index will land; actually do the math and make sure the value is what you were hoping for.
  * **Explain the shortcuts you took**. If you skipped things for reasons of expedience that you would otherwise do in a "real world" scenario, please let us know what you did and why. For example, "If I were writing this for production use, I would check an invariant here." Since whiteboard coding is an artificial environment, this gives us a sense for how you'll treat code once you're actually on the job.

As an addendum, here are a few suggestions for books we like about the art of software construction:

* _[Design Patterns: Elements of Reusable Object-Oriented Software](https://secure.wikimedia.org/wikipedia/en/wiki/Design_Patterns)_ \- Erich Gamma, et al.
  
* Clean Code: A Handbook of Agile Software Craftsmanship - Robert C. Martin

* Code Complete: A Practical Handbook of Software Construction - Steve McConnell

* The Practice of Programming - Brian Kernighan, Rob Pike

* Effective Java - Joshua Bloch
