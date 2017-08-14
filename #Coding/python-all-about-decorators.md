# Python: All About Decorators

_Captured: 2017-08-08 at 20:11 from [dzone.com](https://dzone.com/articles/python-all-about-decorators?edition=310396&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-24)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

Decorators can be a bit mind-bending when first encountered and they can also be a bit tricky to debug. But they are a neat way to add functionality to functions and classes. Decorators are also known as a "higher-order function." What this means is that they can take one or more functions as arguments and return a function as its result. In other words, decorators will take the function they are decorating and extend its behavior while not actually modifying what the function itself does.

There have been two decorators in Python since version 2.2, namely **classmethod()** and **staticmethod()**. Then [PEP 318](https://www.python.org/dev/peps/pep-0318/) was put together and the decorator syntax was added to make decorating functions and methods possible in Python 2.4. Class decorators were proposed in [PEP 3129](https://www.python.org/dev/peps/pep-3129/) to be included in Python 2.6. They appear to work in Python 2.7, but the PEP indicates that they weren't accepted until Python 3, so I'm not sure what happened there.

Let's start off by talking about functions, in general, to get a foundation to work from.

### The Humble Function

A function in Python and in many other programming languages is just a collection of reusable code. Some programmers will take an almost bash-like approach and just write all their code out in a file with no functions at all. The code just runs from top to bottom. This can lead to a lot of copy-and-paste spaghetti code. When ever you see two pieces of code that are doing the same thing, they can almost always be put into a function. This will make updating your code easier since you'll only have one place to update them.

Here's a basic function:

This function accepts one argument, number. Then it multiplies it by 2 and returns the result. You can call the function like this:

As you can see, the result will be 10.

### Function Are Objects Too

In Python, a lot of authors will describe a function as a "first-class object." When they say this, they mean that a function can be passed around and used as arguments to other functions just as you would with a normal data type such as an integer or string. Let's look at a few examples so we can get used to the idea:
    
    
    ['__call__', '__class__', '__closure__', '__code__', '__defaults__', '__delattr__', '__dict__', '__doc__', '__format__', '__get__', '__getattribute__', '__globals__', '__hash__', '__init__', '__module__', '__name__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'func_closure', 'func_code', 'func_defaults', 'func_dict', 'func_doc', 'func_globals', 'func_name']

As you can see, you can create a function and then pass it to Python's **print()** function or any other function. You will also note that once a function is defined, it automatically has attributes that we can access. For example, in the example above, we accessed **func_doc **which was empty at first. This attribute holds the contents of the function's docstring. Since we didn't have a docstring, it returned None. So we redefined the function to add a docstring and accessed func_doc again to see the docstring. We can also get the function's name via the **func_name** attributes. Feel free to check out some of the other attributes that are shown in the last example above.

### Our First Decorator

Creating a decorator is actually quite easy. As mentioned earlier, all you need to do to create a decorator is to create a function that accepts another function as its argument. Let's take a look:
    
    
                print('Function name: ' + func.__name__)
    
    
                print('Function docstring: ' + str(func.__doc__))
    
    
    >>> my_decorator = info(doubler)
    
    
    >>> print(my_decorator(2))

You will note that our decorator function, **info()**, has a function nested inside of it, called **wrapper()**. You can call the nested function whatever you like. The wrapper function accepts the arguments (and optionally the keyword arguments) of the function you are wrapping with your decorator. In this example, we print out the wrapped function's name and docstring, if it exists. Then we return the function, calling it with its arguments. Lastly, we return the wrapper function.

To use the decorator, we create a decorator object:

Then to call the decorator, we call it just like we would a normal function: **my_decorator(2)**.

However, this is not the usual method of calling a decorator. Python has a special syntax just for that!

### Using Decorator Syntax

Python allows you to call a decorator by using the following syntax: **@info**. Let's update our previous example to use proper decorator syntax:
    
    
            print('Function name: ' + func.__name__)
    
    
            print('Function docstring: ' + str(func.__doc__))

Now you can call **doubler()** itself instead of calling the decorator object. The **@info** above the function definition tells Python to automatically wrap (or decorate) the function and call the decorator when the function is called.

### Stacked Decorators

You can also stack or chain decorators. What this means is that you can use more than one decorator on a function at the same time! Let's take a look at a silly example:
    
    
            return "<b>" + func() + "</b>"
    
    
            return "<i>" + func() + "</i>"

The **bold()** decorator will wrap the text with your standard bold HTML tags, while the _italic()_ decorator does the same thing but with italic HTML tags. You should try reversing the order of the decorators to see what kind of effect it has. Give it a try before continuing.

Now that you've done that, you will have noticed that your Python appears to run the decorator closest to the function first and go up the chain. So in the version of the code above, the text will get wrapped in italics first and then that text will get wrapped in bold tags. If you swap them, then the reverse will occur.

### Adding Arguments to Decorators

Adding arguments to decorators is a bit different than you might think it is. You can't just do something like **@my_decorator(3, 'Python')** as the decorator expects to take the function itself as its argument…or can you?
    
    
        print('Decorator arg1 = ' + str(arg1))
    
    
        print('Decorator arg2 = ' + str(arg2))
    
    
            def wrapper(*args, **kwargs):
    
    
                    function.__name__, str(args), str(kwargs)))
    
    
                return function(*args, **kwargs)

As you can see, we have a function nested in a function nested in a function! How does this work? The **function** argument doesn't even seem to be defined anywhere. Let's remove the decorator and do what we did before when we created the decorator object:
    
    
            def wrapper(*args, **kwargs):
    
    
                    function.__name__, str(args), str(kwargs)))
    
    
                return function(*args, **kwargs)
    
    
    decorator = info(3, 'Python')(doubler)

This code is the equivalent of the previous code. When you call **info(3, 'Python')**, it returns the actual decorator function, which we then call by passing it the function, **doubler**. This gives us the decorator object itself, which we can then call with the original function's arguments. We can break this down further though:
    
    
            def wrapper(*args, **kwargs):
    
    
                    function.__name__, str(args), str(kwargs)))
    
    
                return function(*args, **kwargs)
    
    
    decorator_function = info(3, 'Python')

Here we show that we get the decorator function object first. Then we get the decorator object which is the first nested function in **info()**, namely **the_real_decorator()**. This is where you want to pass the function that is being decorated. Now we have the decorated function, so the last line is to call the decorated function.

I also found a [neat trick](https://stackoverflow.com/a/25827070/393194) you can do with Python's `functools` module that will make creating decorators with arguments a bit shorter:
    
    
    def info(func, arg1, arg2):
    
    
        def wrapper(*args, **kwargs):
    
    
                function.__name__, str(args), str(kwargs)))
    
    
            return function(*args, **kwargs)
    
    
    decorator_with_arguments = partial(info, arg1=3, arg2='Py')

In this case, you can create a **partial** function that takes the arguments you are going to pass to your decorator for you. This allows you to pass the function to be decorated AND the arguments to the decorator to the same function. This is actually quite similar to how you can use **functools.partial** for passing extra arguments to event handlers in wxPython or Tkinter.

### Class Decorators

When you look up the term "class decorator," you will find a mix of articles. Some talk about creating decorators using a class. Others talk about decorating a class with a function. Let's start with creating a class that we can use as a decorator:
    
    
        def __init__(self, arg1, arg2):
    
    
        def __call__(self, f):
    
    
            def wrapped(*args, **kwargs):

Here we have a simple class that accepts two arguments. We override the **__call__()**method which allows us to pass the function we are decorating to the class. Then in our __call__() method, we just print out that where we're at in the code and return the function. This works in much the same way as the examples in the previous section. I personally like this method because we don't have functions nested 2 levels inside another function, although some could argue that the partial example also fixed that issue.

Anyway, the other use case that you will commonly find for a class decorator is a type of meta-programming. So let's say we have the following class:

That's pretty simple, right? Now let's say we want to add special functionality to our class without modifying what it already does. For example, this might be code that we can't change for backward compatibility reasons or some other business requirement. Instead, we can decorate it to extend its functionality. Here's how we can add a new method, for example:
    
    
            def doubler(self, value):
    
    
        def quad(self, value):

Here we created a decorator function that has a class inside of it. This class will use the class that is passed to it as its parent. In other words, we are creating a subclass. This allows us to add new methods. In this case, we add our doubler() method. Now when you create an instance of the decorated **MyActualClass()** class, you will actually end up with the **Wrapper()** subclass version. You can actually see this if you print the **obj** variable.

### Wrapping Up

Python has a lot of decorator functionality built-in to the language itself. There are @property, @classproperty, and @staticmethod that you can use directly. Then there is the **functools** and **contextlib** modules which provide a lot of handy decorators. For example, you can fix decorator obfuscation using **functools.wraps** or make any function a context manager via **contextlib.contextmanager**.

A lot of developers use decorators to enhance their code by creating logging decorators, catching exceptions, adding security, and so much more. They are worth the time to learn as they can make your code more extensible and even more readable. Decorators also promote code reuse. Give them a try sometime soon!

Also include class decorators, functools.wrap, @contextlib, decorators with arguments.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
