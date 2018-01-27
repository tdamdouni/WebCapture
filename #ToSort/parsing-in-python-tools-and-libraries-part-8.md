# Parsing in Python: Tools and Libraries (Part 8)

_Captured: 2018-01-18 at 19:33 from [dzone.com](https://dzone.com/articles/parsing-in-python-tools-and-libraries-part-8?edition=355096&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202018-01-18)_

Check out [Part 7 here](https://dzone.com/articles/parsing-in-python-tools-and-libraries-part-7)!

## Python Libraries Related to Parsing

Python offers also some other libraries or tools related to parsing.

### Parsing Python Inside Python

There is one special case that could be managed in a more specific way: you want to parse Python code in Python. When it comes to Python, the best choice is to rely on your own Python interpreter.

The standard reference implementation of Python, known as CPython, include a few modules to access its internals for parsing: [tokenize](https://docs.python.org/release/3.6.1/library/tokenize.html), [parser](https://docs.python.org/release/3.6.1/library/parser.html), and [ast](https://docs.python.org/release/3.6.1/library/ast.html). You may also be able to use the [parser in the PyPy interpreter](http://doc.pypy.org/en/latest/parser.html).

### Parsing With Regular Expressions and the Like

Usually, you resort to parsing libraries and tools when regular expressions are not enough. However, there is a good library for Python that can extend the life and usefulness of regular expressions or use elements of similar complexity.

> Regular Expression-based parsers for extracting data from natural languages [..] This library basically just gives you a way to combine Regular Expressions together and hook them up to some callback functions in Python. 

Nonetheless, [Reparse](http://reparse.readthedocs.io/en/latest/) is a simple tool that can be quite useful in certain scenarios. The author himself says that it is much simpler and with fewer features than PyParsing or Parboiled.

The basic idea is that you define regular expressions, the patterns they can use to combine and the functions that are called when an expression or pattern is found. You must define functions in Python, but expressions and pattern can be defined in YAML, JSON, or Python.

In this example from the documentation, expressions and patterns are defined in YAML:
    
    
            Expression: ([0-9]|[1][0-2]) \s? (am|pm)

Fields like `Matches` are there for humans, but can be used for testing by Reparse.

An example function in Python for the pattern:
    
    
        Color, Hour, Period = Color[0], int(Time[0]), Time[1]

The file that puts everything together:

### Parsing Binary Data: Construct

> Instead of writing _imperative code_ to parse a piece of data, you declaratively define a _data structure_ that describes your data. As this data structure is not code, you can use it in one direction to _parse_ data into Pythonic objects, and in the other direction, to _build_ objects into binary data. 

And that is it: [Construct](https://construct.readthedocs.io/en/latest/). You could parse binary data even with some parser generators (i.e. ANTLR), but Constuct makes it much easier. It is a sort of DSL combined with a parser combinator to parse binary formats. It gives you a bunch of fields to manage binary data. Apart from the obvious ones (i.e. float, string, bytes etc.), there are a few specialized to manage sequences of fields (sequence), groups of them (struct), and a few conditional statements.

It also makes available functions to adapt or validate (test) the data and debug any problem you find.

As you can see in the following example, it is quite easy to use:

There is a nice amount of documentation and even many [example grammars for different kinds of format](https://github.com/construct/construct/tree/master/construct/examples/formats), such as filesystems or graphics files.

## Summary

Any programming language has a different community with its own peculiarities. This difference remains even when we compare the same interests across languages. For instance, when we compare parser tools, we can see how Java and Python developers live in a different world.

The parsing tools and libraries for Python, for the most part, use very readable grammars and are simple to use. But the most interesting thing is that they cover a very wide spectrum of competence and use cases. There seems to be an uninterrupted line of tools available from regular expressions, passing through Reparse to end with TatSu and ANTLR.

Sometimes, this means that it can be confusing if you are a parsing expert coming from a different language. Few parser generators actually generate parsers, but they mostly interpret them at runtime. On the other hand, with Python, you can find the perfect library or tools for your needs. And to help you with that, we hope that this comparison has been useful for you.
