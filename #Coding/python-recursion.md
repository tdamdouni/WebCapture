# Python Recursion

_Captured: 2017-08-15 at 19:49 from [dzone.com](https://dzone.com/articles/python-101-rescursion?edition=316416&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-15)_

Recursion is a topic in mathematics and computer science. In computer programming languages, the term recursion refers to a function that calls itself. Another way of putting it would be a function definition that includes the function itself in its definition. One of the first warnings I received when my computer science professor talked about recursion was that you can accidentally create an infinite loop that will make your application hang. This can happen because when you use recursion, your function may end up invoking itself infinitely. So, as with any other potential infinite loop, you need to make sure you have a way to break out of the loop. The idea in most recursive functions is to break up the procedure being done into smaller pieces that we can still process with the same function.

The favorite method of describing recursion is usually illustrated by creating a factorial function. A factorial normally looks something like this: **5!**. Note that there is an explanation mark after the number. That notation denotes that it is to be treated as a factorial. What this means is that **5! = 5*4*3*2*1** or 120.

Let's take a look at a simple example.
    
    
            return number * factorial(number-1)

In this code, we check the number that we pass in to see if it is equal to zero. If it is, we return the number one. Otherwise, we take the number and multiply it with the result of calling the same function but with the number minus one. We can modify this code a bit to get the number of times we have recursed:
    
    
    def factorial(number, recursed=0):
    
    
            return number * factorial(number-1, recursed)

Each time we call the factorial function _and_ the number is greater than zero, we print out the number of times we recursed. The last string you should see should be `"Recursed 2 time(s)"` because it should only need to call factorial twice with the number 3.

## Python's Recursion Limit

At the beginning of this article, I mentioned that you can create an infinite recursive loop. Well, you can in some languages, but Python actually has a recursion limit. You can check it yourself by doing the following:

If you feel that limit is too low for your program, you can also set the recursion limit via the sys module's `setrecursionlimit()` function. Let's try to create a recursive function that will exceed that limit to see what happens:

If you run this code, you should see the following exception thrown: `RuntimeError: maximum recursion depth exceeded`.

Python prevents you from creating a function that ends up in a never-ending recursive loop.

## Flattening Lists With Recursion

There are other things you can do with recursion besides factorials, though. A more practical example would be creating a function to flatten a nested list -- for example:

When you run this code, you should end up with a list of just integers instead of a list of integers and one list. Of course, there are many other valid ways to flatten a nested list, such as using Python's `itertools.chain()`. You might want to check out the code behind the `chain()` class, as it has a very different approach for flattening a list.

## Wrapping Up

Now, you should have a basic understanding of how recursion works and how you can use it in Python. I think it's neat that Python has a built-in limit for recursion to prevent developers from creating poorly constructed recursive functions. I also want to note that in my many years as a developer, I don't think I have ever really needed to use recursion to solve a problem. I am sure there are plenty of problems where the solution could be implemented in a recursive function, but Python has so many other ways to do the same thing that I've never felt the need to do so. One other note I want to bring up is that recursion can be difficult to debug since it is hard to tell what level of recursion that you have reached when the bug occurred.

Regardless, I hope you have found this article useful. Happy coding!

Leveraging big data is necessary for survival. The question is how, the hurdles--complexity, scalability, speed, cost, reliability, expertise--are many. The answer is [Qubole's Autonomous Data Platform](https://dzone.com/go?i=239225&u=https%3A%2F%2Fwww.qubole.com%2Fproducts%2Fautonomous-data-platform%2F).
