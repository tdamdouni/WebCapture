# When to Use Yield Instead of Return in Python

_Captured: 2017-08-08 at 20:21 from [dzone.com](https://dzone.com/articles/when-to-use-yield-instead-of-return-in-python?edition=310395&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-23)_

Effortlessly power IoT, predictive analytics, and machine learning applications with an [elastic, resilient data infrastructure](https://dzone.com/go?i=207144&u=https%3A%2F%2Fmesosphere.com%2Fsolutions%2Fdata%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_term%3Dpre-article%26utm_content%3D101). Learn how with [Mesosphere DC/OS](https://dzone.com/go?i=207144&u=https%3A%2F%2Fmesosphere.com%2Fproduct%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_term%3Dpre-article%26utm_content%3D101).

Lately, I've seen so many projects that are using `yield` keyword in the structure, whether or not it was needed.

So I've decided to look into this a bit and wanted to share some information about it with you guys.

First things first.

The yield statement is only used when defining a generator function and is only used in the body of the generator function.

Using a yield statement in a function definition is sufficient to cause that definition to create a generator function instead of a normal function.

The yield statement suspends the function's execution and sends a value back to the caller, but retains enough state to enable the function to resume where it is left off. When resumed, the function continues the execution immediately after the last yield run. This allows its code to produce a series of values over time rather them computing them all at once and sending them back like a list.

Let's see this with an example:

The output of this code will be:

When a yield statement is executed, the state of the generator is frozen and the value of `[expression_list](https://docs.python.org/2.4/ref/exprlists.html#tok-expression_list)` is returned to `next()`'s caller. By "frozen," we mean that all local state is retained, including the current bindings of local variables, the instruction pointer, and the internal evaluation stack. Enough information is saved so that the next time `next()` is invoked, the function can proceed exactly as if the `yield` statement were just another external call.

![yield-vs-return-in-python](http://orcunyilmaz.com/wp-content/uploads/2017/06/yield-vs-return-in-python-300x300.gif)

The `yield` statement is not allowed in the`try` clause of a `try ... finally` construct. The difficulty is that there's no guarantee the generator will ever be resumed, hence no guarantee that the `finally` block will ever get executed.

`return` sends a specified value back to its caller, whereas `yield` can produce a sequence of values.

We should use `yield` when we want to iterate over a sequence but don't want to store the entire sequence in memory.

`yield` is used in Python generators. A generator function is defined like a normal function, but whenever it needs to generate a value, it does so with the `yield` keyword rather than return. If the body of a `def` contains `yield`, the function automatically becomes a generator function.

The output of this code will be:

And that's it!

Learn to design and build better data-rich applications with this [free eBook from O'Reilly](https://dzone.com/go?i=207145&u=https%3A%2F%2Fmesosphere.com%2Fresources%2Fdesigning-data-intensive-applications%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_campaign%3Doreilly-data-apps-ebook%26utm_term%3Dpost-article%26utm_content%3D202). Brought to you by [Mesosphere DC/OS](https://dzone.com/go?i=207145&u=https%3A%2F%2Fmesosphere.com%2Fproduct%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_campaign%3Doreilly-data-apps-ebook%26utm_term%3Dpost-article%26utm_content%3D202).
