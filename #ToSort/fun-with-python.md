# Fun With Python

_Captured: 2018-06-20 at 19:40 from [dzone.com](https://dzone.com/articles/fun-with-python?edition=383232&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-20)_

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278435&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278435&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))

> _"My favorite language for maintainability is Python. It has simple, clean syntax, object encapsulation, good library support, and optional named parameters." \- [Bram Cohen](https://www.brainyquote.com/quotes/bram_cohen_219754)_

The company I'm working for started a project as a start-up last year. In the beginning, there was a discussion on what programming language to choose so that we could easily have an MVP (Minimum Valuable Product) in the shortest time possible, but also to learn something new while working on this project. The most common programming language used in the company is Java, thus we had to answer a question: _do we want to continue with Java or try something else?_ We chose the second option. But what exactly does this "_something else_" mean?

First of all, the project is a web application, therefore we had to look first for a web framework and after that for a language that would be compatible with that framework. It didn't take us too much time to find out the best option, so we opted for the [Django web framework](https://www.djangoproject.com/). As you might know, Django is a web framework written in [Python](https://www.python.org/), so the choice of the programming language was obvious - it's Python. That's how my journey with Python started.

I've been developing software using Python for almost one year. When I first started to write code in Python, I had a feeling that I made the wrong choice, but very soon I understood how powerful it is and how easy is to have something working in a short amount of time.

In this article, I would like to share with you why I find Python an interesting programming language and how easy it is to work with it, compared to Java or any other language.

## **Basic Example**

Let's start with something trivial - Hello World.

Java:

Python:

So, how do you like Python,? Easy-peasy right? You don't need a class, you don't need a method; you can do exactly what you need to do, print the text without any additional work. There is not that much syntax in this example, but you could already see that Python syntax is relatively simple, and the ease of making a highly readable program that "does the right thing" is a huge advantage.

## **Indentation**

The next thing I like about Python is that it compels you to correctly indent every line of the code, this being part of syntax checking. This makes it so only one way possible to do anything and makes it a very readable language. Here is an example:

![Indentation in Python](https://dzone.com/storage/temp/9480413-python-indentation.png)

> _Fig. 1 Indentation in Python_

## **Variables and Methods**

Another thing I was surprised about is that in Python you don't and can't specify a type for a variable. This makes Python a strong and dynamic typed language. It is strong because the type of the variable doesn't suddenly change, and dynamic because the program has the responsibility to use built-in functions like `isinstance()` and`issubclass()`to test variable types and correct usage at runtime. Someone may say that this way it's easy to introduce bugs into your programs, but I find that to not be the case. Try to write the correct code. Here is an example:

![Python vs JS variable types](https://dzone.com/storage/temp/9480415-python-vs-js-types.png)

> _Fig. 2 Python vs JS variable types_

As you can see in the image above, the variables don't have any type, so they can be anything - integer, string, list, object, etc. In Python, the variable itself is not bound to a type, however, the value is. It won't ever happen that a string could be added to an integer, like in JavaScript.

It is very easy to change the value of the variable, for instance, if it has a string assigned to it, but later, if you want to change it to an integer, you can just do it. In a statically typed language, the variable has a type, so if you have a variable that's an integer, thus you won't be able to assign any other type of value to it later.

You have probably noticed that the method also doesn't have a return type, again, it can be anything. However, it is possible to bind the returned value to a type, but if you do so, you cannot return anything else except something that belongs to that specific type:

![Bound vs unbound methods in Python](https://dzone.com/storage/temp/9480416-method-return-type.png)

> _Fig. 3 Bound vs unbound methods in Python_

## **Method Overloading**

Though I needed to overload a method only once, I was a bit disappointed when I found out that I won't be able to do so because Python doesn't support it; at least there is no standard way of overloading a method like I'm used to doing in Java.

![Method overloading is not supported in Python](https://dzone.com/storage/temp/9480418-method-overloading-no.png)

> _Fig. 4 Method overloading is not supported in Python_

Even if it is not supported, it is possible; no one stops you from writing methods with the same name, thus it is valid. But each time you write another function with the same name, the Python interpreter completely forgets about the prior functions with that name. Doesn't really help, right?

But this is not the end. With some perseverance, you could get the desired result using the [multimethods pattern](http://www.artima.com/weblogs/viewpost.jsp?thread=101605) or, even better, use default argument values. I find the second option a greater choice because this creates a function that can be called with fewer arguments than it is defined to allow:

![Using default argument values as a way of overloading a method](https://dzone.com/storage/temp/9480419-method-overloading-yes.png)

> _Using default argument values as a way of overloading a method_

_Fig. 5 Using default argument values as a way of overloading a method_

This is just a very small part of what I've learned while working with Python. Every time I need to build a specific functionality into the system, I'm astonished by the simplicity and ease of coding Python provides. To be honest, I'm very excited and I look forward to discovering new capabilities of this language, so stay tuned and don't miss the next article.

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278436&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278436&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))

Opinions expressed by DZone contributors are their own.
