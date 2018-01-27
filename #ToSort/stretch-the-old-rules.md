# Stretch the Old Rules, Please

_Captured: 2017-12-26 at 09:59 from [dzone.com](https://dzone.com/articles/stretch-the-old-rules-please?edition=347122&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-25)_

Get the Edge with a Professional Java IDE. [30-day free trial](https://dzone.com/go?i=255333&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-preroll%26utm_campaign%3Didea).

In my programming career, I heard plenty discussions about single vs. multiple return statements in methods. In the past, I was sure that single exit was the only valid way, which led me to one return per method. Now, I still think that a single exit point is good, but the meaning of it is completely different for me.

In the original definition, which is "A function should have one point of entry and one point of exit," we have two hidden rules. In modern OOP languages like Java, it is hard to imagine that you can start your method from the middle, so the first rule is quite outdated (in older languages, you can use "goto" or something like "jump"), so we should cut this rule into "A function should have one point of exit."

Ok, so what is this "single point of exit?" Most programmers think that rule is saying that there is only one return statement, and I was in this group. We can easily point some advantages of this approach:

  * multiple returns are harder to read

  * fewer returns means less complexity

  * you can put a debugger breakpoint on one return at end of the method

  * some languages require a single point of exit (e.g. Pascal)

While the last argument is quite weak for me (as I mainly think in Java), the rest are very convincing. So from code like this:

I started refactoring my code to this:

Single exit, so we can be happy now.

**BUT**

Is it really better now? Is it easier to read? Is it less complex? These were my questions after each refactoring. But I was so blind about sticking to the rule that I silenced my inside voices without really thinking about it. Then after a few months, when I got more experience in coding, I started to be more elastic in my coding standards.

Of course, the first code will be always clearer and less complex, even if there are three or four returns. The biggest problem with readability is not the number of return statements, but the lines of code (LOC) in the method. Imagine, a 200 LOC method with three return statements, first in line 10, second in line 130, and the last in line 200.

Is that a problem with the three return statements? Or is it with the complexity of the method? Then imagine a small method (for me, a good method has max 10 LOC) with the same number of return statements. The smaller method is more readable and, even with multiple returns, it will be still easier to test and maintain. Everyone can look at it and know what is going on.

But returning to rule -- finally, I discovered that even for one return value, this rule can be not valid:

What do you think about this code (besides the poor complexity of my use case)? How many return statements and exit points does it have? From an API view, we should expect that person will be not updated, but copied into a new instance and returned, but in this situation, it will not occur. We have TWO points of exit -- one by return statement and second by the parameter. In this situation, to put it into the single exit point rule, we should write:

OR

Again, as you can see, the problem here is not the number of return statements, but what an exit point is from a user view of the object's API.

Multiple return statements are not evil at all. You can use them in a situation when they will be more readable (check the first code block in this post). In my opinion, they are not breaking the rule of single exit points.

In my understanding, the single point of exit nowadays in Java is applied to "returning" by return statement or by parameters, not by the number of return statements itself. So one exit point should be rewritten to one exit point type, which can be "return" statements (one or multiple) or by modification of entry parameters.

The biggest issue with that is that programmers write unnecessarily long code, do not divide big methods into smaller ones, and create trouble-making, complicated contracts in their APIs. In the present world of OOP languages with Garbage Collection and without ugly "gotos" or explicit "jumps", we should rewrite some old programming rules.

[Get the Java IDE](https://dzone.com/go?i=255334&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-postroll%26utm_campaign%3Didea) that understands code & makes developing enjoyable. Level up your code with IntelliJ IDEA. [Download the free trial](https://dzone.com/go?i=255334&u=https%3A%2F%2Fwww.jetbrains.com%2Fidea%2Fspecials%2Fidea%2Fidea.html%3Futm_source%3Ddzone%26utm_medium%3Dcpc-postroll%26utm_campaign%3Didea).
