# Understanding Tracebacks in Python

_Captured: 2018-07-27 at 07:35 from [dzone.com](https://dzone.com/articles/understanding-tracebacks-in-python?edition=385293&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-26)_

Sensu is an open source monitoring event pipeline. [Try it today](https://dzone.com/go?i=299442&u=https%3A%2F%2Fsensu.io%2F%3Futm_source%3DDZone).

When you are first starting out learning how to program, one of the first things you will want to learn is what an error message means. In Python, error messages are usually called **tracebacks**. Here are some common traceback errors:

  * SyntaxError
  * ImportError or ModuleNotFoundError
  * AttributeError
  * NameError

When you get an error, it is usually recommended that you trace through it backwards (i.e. traceback). So start at the bottom of the traceback and read it backwards.

Let's take a look at a few simple examples of tracebacks in Python.

## Syntax Error

A very common error (or exception) is the SyntaxError. A syntax error happens when the programmer makes a mistake when writing the code out. They might forget to close an open parentheses, or use a mix of quotes around a string on accident, for instance. Let's take a look at an example I ran in IDLE:

Here we attempt to print out a string and we receive a SyntaxError. It tells us that the error has something to do with it not finding the End of Line (EOL). In this case, we didn't finish the string by ending the string with a single quote.

Let's look at another example that will raise a SyntaxError:

When you run this code from the command line, you will receive the following message:

Here the SyntaxError says that we used "invalid syntax". Then Python helpfully uses an arrow (^) to point out exactly where we messed up the syntax. Finally we learn that the line of code we need to look at is on "line 1." Using all of these facts, we can quickly see that we forgot to add a semi-colon to the end of our function definition.

## Import Errors

Another common error that I see even with experienced developers is the **ImportError**. You will see this error whenever Python cannot find the module that you are trying to import. Here is an example:

Here we learn that Python could not find the "some" module. Note that in Python 3, you might get a **ModuleNotFoundError** error instead of ImportError. ModuleNotFoundError is just a subclass of ImportError and means virtually the same thing. Regardless of which exception you end up seeing, the reason you see this error is because Python couldn't find the module or package. What this means in practice is that the module is either incorrectly installed or not installed at all. Most of the time, you just need to figure out what package that module is a part of and install it using pip or conda.

## AttributeError

The **AttributeError** is really easy to accidentally hit, especially if you don't have code completion in your IDE. You will get this error when you try to call an attribute that does not exist:

Here I tried to use a non-existent string method called "up" when I should have called "upper." Basically the solution to this problem is to read the manual or check the data type and make sure you are calling the correct attributes on the object at hand.

## NameError

The **NameError** occurs when the local or global name is not found. If you are new to programming that explanation seems vague. What does it mean? Well in this case it means that you are trying to interact with a variable or object that hasn't been defined. Let's pretend that you open up a Python interpreter and type the following:

Here you find out that **'var' is not defined**. This is easy to fix in that all we need to do is set "var" to something. Let's take a look:

See how easy that was?

## Wrapping Up

There are lots of errors that you will see in Python and knowing how to diagnose the cause of those errors is really useful when it comes to debugging. Soon it will become second nature to you and you will be able to just glance at the traceback and know exactly what happened. There are many other built-in exceptions in Python that are documented on their [website](https://docs.python.org/3/library/exceptions.html) and I encourage you to become familiar with them so you know what they mean. Most of the time, it should be really obvious though.

From bare metal to Kubernetes, Sensu gives you complete visibility across every system and protocol. [Get started today.](https://dzone.com/go?i=299443&u=https%3A%2F%2Fsensu.io%2F%3Futm_source%3DDZone)

Topics:

python ,errors ,exceptions ,debugging ,open source ,web dev ,code
