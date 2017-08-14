# Yet Another Python Problem List

_Captured: 2017-08-08 at 20:04 from [dzone.com](https://dzone.com/articles/yet-another-python-problem-list)_

This was a cool thing to see in my Twitter feed:

More problems with Python. Here's the short list.

1\. Encapsulation (Inheritance, really).

2\. With Statement.

3\. Decorators.

4\. Duck Typing (and Documentation).

5\. Types.

I like these kinds of posts because they surface problems that are way, way out at the fringes of Python. What's important to me is that most of the language is fine, but the syntaxes for a few things are sometimes irksome. Also important to me is that it's almost never the deeper semantics; it seems to be entirely a matter of syntax.

The really big problem is people who take the presence of a list like this as a reason dismiss Python in its entirety because they found a few blog posts identifying specific enhancements. That "Python must be bad because people are proposing improvements" is maddening. And dismayingly common.

Even in a Python-heavy workplace, there are Java and Node.js people who have opinions shaped by little lists like these. The "semantic whitespace" argument coming from JavaScript people is ludicrous, but there they are: JavaScript has a murky relationship with semicolons and they're complaining about whitespace. Minifying isn't a virtue. It's a hack. Really.

My point, in general, is not to say this list is **wrong**. It's to say that these points are minor. In many cases, I don't disagree that these can be seen as problems. But I don't think they're toweringly important.

1\. The body of the first point seems to be more about inheritance and accidentally overriding something that shouldn't have been overridden. Java (and C++) folks like to use **private** for this. Python lets you read the source. I vote for reading the source.

2\. Yep. There are other ways to do this. Clever approach. I still prefer **with** statements.

3\. I'm not sold on the syntax change being super helpful.

4\. People write bad documentation about their duck types. Good point. People need to be more clear.

5\. Agree. A lot of projects need to implement type hints to make it more useful.
