# Six Python Tips for Beginners - DZone Web Dev

_Captured: 2019-08-27 at 19:48 from [dzone.com](https://dzone.com/articles/5-python-tips-for-beginners?edition=520328&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202019-08-26)_

****

Python is one of the easiest programming languages to learn. The syntax is close to English. Beginners generally encounter only a few surprises, such as forced indentation and the use of  `self` in methods. 

At some point, everyone starts reading, copying, and editing other people’s code. That’s where the confusion starts. 

I'll explain five Python concepts that will help beginners to modify code written by other authors. These tips were compiled by observing problems novice Python developers encountered in workshop-style training as well as analyzing online discussions that took place in a free and open [development community](https://community.theta360.guide/) focused on the usage of APIs, image processing, and metadata (text) processing for the RICOH THETA camera. The typical person has intermediate programming experience with Java, C, JavaScript, or bash, but is still a Python novice. 

They can write their own Python code to get a job done, but have problems reading the code contributed by other people. 

Here are five things that helped some of these people better understand Python.

## 1\. *args and **kwargs Are Function Arguments

If you look at Python modules or even documentation for the module, you’re likely to see `*args` and `**kwargs`. They look and act vaguely like a pointer in C. They are not. `*args` is simply a list of arguments sent to a function.

`**kwargs` is a dictionary of keyword arguments.

**`*args` example:**

**Output: **

**`**kwargs` example:**

**Output:**

## 2\. List Comprehensions Are For Loop Shortcuts

list compressions are a short way to return a list. In the snippet, the for loop is `for number in args`.

The expression that is normally inside the loop is `num **2` , which returns the square of the arguments.

**Output:**

You can tack on a filter to the end of the list comprehension to filter out inputs. For example, to only square the even numbers, filter it with this:

**Output:**

The list comprehension does not add any special feature over the `for` loop. People use list comprehensions because they are shorter and can make code easier to read once you get accustomed to the syntax. Some people may overuse list comprehensions and make code more difficult to read. Be careful of this, as convoluted a list comprehension with multiple nesting is not best practice. 

If you're just getting started with Python and see a `for` loop all in one line, you can search on the Internet for list comprehension and review the syntax of the three components:

  1. Expression.
  2. For loop.
  3. Filter.

## 3\. F Strings Can Replace .format()

Python is wonderful for string manipulation. You'll probably see at least three techniques to insert variables into strings. Two are clunky. One is cool.

### String Concatenation

Long ago, you may have inserted variables into a string with code similar to this:

**Output:**

This is difficult to read and easy to make errors. Even with syntax highlighting, it's easy to miss a space.

### String Format

A better method is to use `.format()` and make strings like this:

Although `.format` is a big improvement over string concatenation, it is still a bit clunky.

## F String

First, upgrade to Python 3.6 or 3.7. Now, you can use f strings.

## 4. Lambda Functions Are Anonymous

Python lambda functions are shortcuts. Although they can be assigned to a variable, similar to a normal function, they are commonly used as an anonymous function using the syntax below.

**Output:**

Like most of these Python shortcuts, the lambda function doesn't usually add new functionality. Though, it can reduce the code complexity once you get used to the syntax.

## 5\. Decorator Functions Extend Python Functions

You'll likely see a decorator function used with an `@decorator_name` above a function.

The name of the decorator can be anything. For example, it would work with `@panda` . You don't have to understand how to create your own decorator in order to use it. For example, let's look at the [Django documentation for http decorators](https://docs.djangoproject.com/en/2.2/topics/http/decorators/).

The `import ` line allows you to use pre-built decorators. In this case, you just need to understand that the `@require_http_methods`  adds additional features to the function you created called, `my_view()` .

## Additional Tips

As I primarily discuss Python programming with a group of people focused on a specific class of problems, I would love to get additional tips suitable for novice programmers that can help them interact with a wider developer community. 
