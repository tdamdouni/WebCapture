# How I Use Python Debugger to Fix Code

_Captured: 2018-06-22 at 07:48 from [dzone.com](https://dzone.com/articles/how-i-use-python-debugger-to-fix-code?edition=383240&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-21)_

Maintain Application Performance with real-time monitoring and instrumentation for any application. [Learn More!](https://dzone.com/go?i=281422&u=https%3A%2F%2Fwww.nastel.com%2Fapplication-performance-monitoring%2F%3Futm_source%3DDZone%26utm_medium%3DPrePostRoll%26utm_campaign%3DDZone2018%2520for%2520all%2520pre%2Fpost-roll%2520text%2520ads%3A)

Debugging is actually a fun thing to do, especially if you discover more and more efficient ways to do it. I'm going to show you how you can pimp your debugging skills.

To me, debugging is like playing Pac-Man -- you go line by line, looking to identify and remove errors -- Pac-Dots -- from whatever software you're working with. You get them all -- you're done with a level.

## Working With Python Debugger

Speaking generally, a debugger is a tool that allows you to open up the insides of an application to find out what needs fixing. You look at your variables, call stack, set conditional breakpoints, step through the source code line by line, do what you need to do. This is how you identify the defects of a program.

I prefer working with Python, which gives me some additional possibilities when it comes to debugging. Not only I can look through the code in the process, but also run the code written in the debugger command line or even affect the process by changing the variables' value.

Python's secret weapon is its very own built-in debugger called `pdb`. Its simple command line interface basically does the job for you. It's a simple utility that has all the basic debugger features you may need. However, whenever I'm looking for something more complex, I extend it by using [ipdb](https://pypi.org/project/ipdb/), which provides my debugger with some extra features from [IPython](https://ipython.org/).

The easiest way to use `pdb` is to call it in the code you're working on.

You run the interpreter, and as soon as it reaches this line, you get a command prompt on the terminal of the program you're using. It's basically a general Python prompt, but it features some new commands.

### list(l)

I use the _list(l)_ command to see the code line the Python interpreter is currently on. I use this command to check a different area of the code as well -- it has arguments for the first and the last lines to show. But if I provide only the number of the first line, I'll get to see only the code around this particular line.

### up(p) and down(d)

_Up(p) and down(d)_ are the commands I use to navigate through the call stack. I use these two to see who is calling the current function, for example, or why the interpreter is going this way.

### step(s) and next(n)

Another important pair of commands are _step(s)_ and _next(n)_. With their help, I continue the execution of the application line by line. The only difference between them is that _next(n) _will only go to the next line of the current function, even if it has a call for another function, but _step(s)_ will go deeper in a case like this.

If I need to set up new breakpoints without changing the code, I use the _break(b) _command. It requires a bit more explaining, so I'll go into detail below.

But before that, let me give you a quick overview of all the other `pdb` commands:

![](https://cdn-images-1.medium.com/max/800/0*6TPWwai_v4-rxdQG.png)_[ Source](https://djangostars.com/blog/debugging-python-applications-with-pdb/)._

Previously, I had to change the code to print something or set a breakpoint, but sometimes I had to set the breakpoint inside a third-party package. Yes, I could open the source code of a library anytime from my virtual environment and add a call for "pdb."

What do we have now? Now, I can run the application from the debugger and set the breakpoints I need with no source code changes whatsoever. I would just use the command _ `python -m pdb <python script>` _to execute the application with the debugger, and that's it.

To show you an example, I will use this simple application that I use to track my working time. Inside of this application, I use the `requests` library to make HTTP requests, and what I'm going to do is break on a post request. It goes like this: I run the application with the debugger and set a breakpoint inside the said library.

The easy part is, I don't have to enter the full source file path. I just put a relative path from any folder in `sys.path`, the same way I'd make an import into my code.

This is why it's now easier to set the breakpoint. I don't have to put it somewhere in my code, go step-by-step to the function I need like I'm poking in the dark, or to find the library source file and change it.

One more thing. As it happens, the application may run a lot of calls, but sometimes I just need one particular call. What do I do then? In this case, I can specify a breakpoint condition, and the debugger will break the application only if this condition will be considered True.

In this example, the application will break only if `json` has a `time_entry` key.

I'm using the Django web framework, and here, if `DEBUG` is set to `True` in the settings, then on any exception I get a special page with the following information: exception type and message, traceback, local variables, etc.

This is a little enhancement I made my installing django-extensions and using the `runserver_plus` command to start my Django server for development. When I need to set up the debugger pin, here's how I do it:

`WERKZEUG_DEBUG_PIN=1234 ./manage.py runserver_plus`

By using [django-extensions](https://github.com/django-extensions/django-extensions) instead of this default page, I get a traceback page where I can see the code for every single line and an open debugger.

The debugging process is then carried out with the help of the [Werkzeug](https://pypi.org/project/ipython/)project, which is a WSGI library for Python.

This is it for now, I hope my little tricks will help you with your debugging. By using a debugger smartly, you will save yourself and your company a lot of time and energy, and also add to your good reputation among your clients by making your product better faster. Good luck and have fun debugging!

Collect, analyze, and visualize performance data from mobile to mainframe with AutoPilot APM. [Learn More!](https://dzone.com/go?i=281423&u=https%3A%2F%2Fwww.nastel.com%2Fapplication-performance-monitoring%2F%3Futm_source%3DDZone%26utm_medium%3DPrePostRoll%26utm_campaign%3DDZone2018%252520for%252520all%252520pre%2Fpost-roll%252520text%252520ads%3A)
