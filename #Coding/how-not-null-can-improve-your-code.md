# How not_null Can Improve Your Code

_Captured: 2017-10-30 at 20:13 from [dzone.com](https://dzone.com/articles/how-not-null-can-improve-your-code?edition=334817&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-30)_

![not_null examples](https://1.bp.blogspot.com/-x8ZG7XOykSk/WeNZ8kqeJmI/AAAAAAAADGU/aVlO5lPGn4kpV2NxDXxAkSFEbgu9Uj4ZgCLcBGAs/s1600/not_null.png)

One of the key points of modern C++, as I've observed, is to be expressive and use proper types. For example, regarding null pointers, rather than just writing a comment:

I should actually use `not_null<int *> pInt`.

The code looks great now, doesn't it? Let's investigate what `not_null` (from the Core Guidelines/Guideline Support Library) can do for us.

## Intro

In your application, there are probably lots of places where you have to check if a pointer is not null before you process it. How many times do you write similar code:

or:

or

What are the problems with the code?

  * It's error-prone: you might forget about if statements and then you might end up with AV (Memory Access Violation), or some other strange errors.
  * Code duplication.
  * Error handling might be on the wrong level. Some functions must accept the null object, but some should depend on the caller to do the checks.
  * Performance hit. One additional check might not be a huge deal, but in some projects, I see hundreds or more of such tests.

What if we could forget about most of those safety checks and just be sure the pointer is always valid? How can we enforce such a contract?

As you know, writing a simple comment, like `"this argument cannot be null"` won't do the job.

There's a simple solution suggested in the Core Guidelines:

> [I.12](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-nullptr): Declare a pointer that must not be null as `not_null`.

So what's that `not_null` type? How can it help us?

The article was inspired mostly by Kate Gregory's original article: [Using the not_null Template for Pointers That Must Never Be Null](https://visualstudiomagazine.com/articles/2016/06/01/using-the-not_null-template.aspx). Moreover, Kate's done a great course about core guidelines, where she also experimented with `not_null`. Check it here: [First Look: C++ Core Guidelines and the Guideline Support Library @Pluralsight](http://www.shareasale.com/m-pr.cfm?merchantID=53701&userID=1600409&productID=687369677).

## The Basics

`not_null` is a class that can wrap a pointer (or a smart pointer) and guarantees that it will hold only not null values.

The helper class can be found in the Guideline Support Library (GSL, not GLS)

We can use Microsoft's implementation:

(Strangely the class itself is located not in a separate header, but in the core header for GSL, so you cannot include only that class without including all the other stuff. There's a reported issue that might solve that problem: [#issue 502](https://github.com/Microsoft/GSL/issues/502)).

The basic idea is that you can write:

And you'll get a compile-time error as it's not possible to assign `nullptr` to the pointer. When you have such pointer, you can be sure it's valid and can be accessed.

For a function:

Inside `Foo` you are guaranteed to have a valid pointer, and the additional checks might be removed.

That's some basic theory, and now let's consider a few more examples.

I divided examples into two sections: compile time and runtime. While it would be cool to handle `nullptr` at compile time only, we won't get away with issues happening at runtime.

## Compile Time

The wrapper class won't allow us to construct a `not_null` object from `nullptr`, nor does it allow us to assign null. That's useful in several situations:

  * When you have a not null pointer and want to clear it:

In the above case you'll get:

I really advise that you do not use raw new/delete (my code is only for a demonstration!). Still, `not_null` gives a strong hint here: "don't mess with the pointer!" Such a use case is also a topic of the ownership of such a pointer. Since we have only a raw pointer (just wrapped with `not_null`), we can only observe it and not change the pointer itself. Of course, the code will compile when you only delete the pointer and don't clear it. But the consequences of such an approach might be dangerous.

  * When you want to pass null to a function requiring a not null input parameter.

Violation of a contract!

You'd get the following:

In other words, you cannot invoke such function, as there's no option to create such a param from `nullptr`. By marking input arguments with `not_null`, you get a stronger guarantee. Much better than just a comment.

  * Another reason to initialize when declaring that a pointer is variable.

While you can always initialize a pointer variable to `nullptr`, maybe it's better just to init it properly (with some real address/value/object)?

Sometimes it will force you to rethink the code and move the variable to be declared later in the code.

Write:

You can play with the code below. Uncomment the code and see what errors you'll get...

Compile time is relatively easy. The compiler will reject the code, and we have just to redesign/fix it. But what about runtime?

## Runtime

Unfortunately, the compiler cannot predict when a pointer becomes null. It might happen for various reasons. So how can we get away with the `if (pPtr) { }` checks?

For example:

By default, we'll get (Under VS 2017, Windows):

![Error](https://4.bp.blogspot.com/-fEhU4j8tGBQ/WeRY0P3rmOI/AAAAAAAADGk/WcWy-5-13B0Wy3OPEEQlf5HxvsDZPZIywCLcBGAs/s1600/not_null_abort_called.png)

> _Under that condition the wrapper class can do the following:_

  1. Terminate the app.
  2. Throw an exception.
  3. Do nothing.

You can control the behavior using a proper `#define`.

See gsl_assert file: [github.com/Microsoft/GSL/include/gsl/gsl_assert](https://github.com/Microsoft/GSL/blob/master/include/gsl/gsl_assert).

I probably prefer to use `GSL_THROW_ON_CONTRACT_VIOLATION` and that way we can use exceptions to check the null state.

Let's look at the following example. When we have only a single pointer param it's simple anyway, but what if we have more:

So this (2 params):

can become:

But now, all of the checks need to go to the caller:

Is this better?

  * Might be, as we can handle the `nullptr` pointer in only one place, shared for several 'child' functions.
  * We can move the checks up and up in the code, and in theory, have only one test for null pointers.

You can play with the code below:

## Issues

  * Smart pointers? The type is prepared to be used with smart pointers, but when I tried to use it, it looked strange. For now, I am not convinced. Although, the 'ownership' of a pointer and null state seems to be orthogonal. 
  * Any difference between `[reference_wrapper`](http://en.cppreference.com/w/cpp/utility/functional/reference_wrapper)? In C++, we have references that were designed not to hold null values, there's also a reference_wrapper class that is copyable and assignable. So can't we just use ref wrapper instead of `not_null`? 

## Summary

Should we immediately use `not_null` everywhere in our code? The answer is not that obvious.

For sure, I am waiting to see such a class in the Standard Library, not just in GSL. When it's included in STL, it would be perceived as a solid standardized helper to our code. I haven't seen any papers on that, however… maybe you know something about it?

Still, I believe it can help in many places. It won't do the magic on its own, but at least it forces us to rethink the design. Functions might become smaller (as they won't have to check for nulls), but on the other hand, the caller might require an update.

It's definitely worth a try, so I plan to write more code with `not_null`.

  * Play with `not_null` for some time. Share your feedback.
