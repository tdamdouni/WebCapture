# catherinedevlin/python_learners_glossary

_Captured: 2015-09-11 at 18:12 from [github.com](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)_

## python_learners_glossary

Definitions of Python jargon to help Python beginners understand Pythonista gobbletigook. The idea is to help a Python beginner's understanding even before they've learned to write the code.

## CONTRIBUTING

Please submit [issues](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) and [pull requests](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)!

  1. Clarity
  2. Conciseness
  3. Accuracy

... are all desirable - _in that order_. Don't get pedantic or hung up on [`corner cases`_](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).

Terms to define are not strictly Python terms, but any terms likely to be frequently heard at a Python conference.

To reduce cognitive load, let's use examples around a consistent, familiar theme: cats.

## Glossary

### General

Execute
    Go. Run. Do that thing you do. Nothing to do with beheading anybody.

Code
    Collection of computer instructions in a human-readable computer/programming language.

Comment
    To clarify something in the middle of a piece of [code](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst). If used properly can make understanding your [code](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) much easier than if they weren't present.

### Numeral systems

Decimal
    

A numeral system of base 10, which means it has 10 digits to represent numbers. As long as you only have ten digits, your system can be called decimal, but it is conventional to use from 0 to 9.

It is the standard today.

Example: 20 [octal](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) is 16 [decimal](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)

Binary
    

A numeral system of base 2, which means it has 2 digits to represent numbers. As long as you only have two digits, your system can be called binary, but it is conventional to use 0 and 1.

Example: 12 [octal](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) is 1010 [binary](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)

Octal
    

A numeral system of base 8, which means it has 8 digits to represent numbers. As long as you only have eight digits, your system can be called octal, but it is conventional to use from 0 to 7.

Example: 80 [decimal](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) is 120 [octal](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)

Hexadecimal (or Hex)
    

A numeral system of base 16, which means it has 16 digits to represent numbers. As long as you only have sixteen digits, your system can be called hexadecimal, but it is conventional to use from 0 to 9 and A to F.

Example: 123 [decimal](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) is 7B [hex](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)

### Data

Value
    A single piece of data, like `3` or `'Fluffy'`

Literal
    

A representation of a value _as the value itself_, as opposed to the result of a [function](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) or [expression](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).
    
    
    "Whiskers"  # a string literal
    'Whiskers'  # a string literal
    1  # an integer literal
    1.5  # a float literal
    ["Whiskers", 10]  # a list literal
    

String
    A piece of text data, like `'hello'`. Enclosing it in quotation marks tells Python that it's a string and not something like a [variable](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) name.

Float
    Short for _floating-point number_, a number with a decimal point.

Variable
    

A piece of data that has a name.
    
    
    cat_name = 'Fluffy'
    

Now `cat_name` is a _variable_ with the [value](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) 'Fluffy'.

Assign
    Give a name to a [value](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst), making a [variable](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).

Expression
    

A description of a value that contains calculations and/or other executable code; the code must be executed to determine the expression's actual value. Typically, these fit on one line, but not necessarily.

Examples:
    
    
    'lazy ' + 'cat'  # Evaluates to 'lazy cat'
    2 * 2 > 100  # Evaluates to ``False``
    

Boolean
    `True` or `False`.

List
    

A series of values. Python will remember what order they come in.
    
    
    ['Mouser', 17, 'Whiskers']
    

Tuple
    

A series of values. Python will remember what order they come in.

Hey, is that the same as a [list](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)? It's very similar, but after a tuple is set up, you're not allowed to change it.
    
    
    ('Mouser', 17, 'Whiskers')
    

Set
    Just like in mathematics - a group of values. Python will _not_ necessarily remember what order they came in, and each [value](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) can only appear in the set once.

### Functions

Function
    

A named series of instructions. Its definition begins with the def keyword.
    
    
    def feed_cat(kg_of_food, kg_of_cat):
        kg_of_food = kg_of_food - 0.1
        kg_of_cat = kg_of_cat + 0.1
    

Call
    

Tell a [function](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) to [execute](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst). To call a function, give its name followed by parenthesis containing its [arguments](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) (if any).
    
    
    feed_cat(8.0, 3.0)
    

Argument
    A piece of data that you "pass" (give) to a [function](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) as you [call](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) it. In our `feed_cat` [function](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst), `kg_of_food` and `kg_of_cat` are the function's arguments.

Parameter
    Synonym for [argument](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).
Return
    Stop running a [function](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) and return to the place where the function was [called](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) from. Send a [value](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) back - the "return value".

### Object-oriented

Object
    A logical grouping of functions (called "[methods](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)" in this context) and variables (called "[attributes_](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)" in this context).

Method
    

A function that _belongs to_ an object and "knows" about the object it belongs to. For instance, if my_cat is an object that has a speak method, then we can [call](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) it:
    
    
    my_cat.speak()
    'meow'
    

... and my_cat.speak doesn't need to be told what kind of animal should speak, because it already knows that it belongs to my_cat.

Attribute
    

A piece of data that belongs to an object. This object, `my_cat`, has a `name` attribute with the value `'Agamemnon'`.``
    
    
    my_cat.name
    'Agamemnon'
    

Class
    A code template, used for creating and initializing an [object](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) with pre-defined data, and for providing code to operate on that object's data.

Instance
    An [object](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) of a given [class](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst). my_cat is an _instance_ of the class Cat.

Instantiate
    Create a new instance of a given class. When my_cat has kittens, she is instantiating several new instances of the class Cat. (Please spay our neuter your pets!)

[Object-oriented programming](http://docs.python-guide.org/en/latest/writing/structure/#object-oriented-programming)
    Programming that makes use of [classes](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) and [objects](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).

Dunder
    The two underscores before and after a method name to indicate that it is "magic", i.e. __init__, __new__, etc. (Short for "Double-underscore")

Magic Method
    Methods that can be used to change the normal behavior of an object. HINT : in Python, everything is an object.

### Program Structure

[`Module`_](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)
    A single file of Python commands. Calling it a module implies we plan to "import" it, not just call it on its own.

[`Package`_](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)
    A directory full of modules that can all together be referred to by the package's name.

Import
    Make the contents of a [module_](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) or [package_](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) available in your current program, even though it comes outside your current program's file.

### Tools

Editor
    A program to create or change files. We usually mean _text editor_, since a Python program is a kind of text file. Notepad is an example of an editor (but don't use Notepad to edit Python, it can introduce mistakes into your Python programs; [Notepad++](https://notepad-plus-plus.org/) is a good alternative).

[IDE](http://docs.python-guide.org/en/latest/dev/env/#ides)
    Abbreviation for Integrated Development Environment. A kind of text [editor](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) with programming-related superpowers; a program that lets you build more programs. Examples include Eclipse, Sublime, Wingware, and IDLE

[Database](http://docs.python-guide.org/en/latest/scenarios/db/)
    A place to store data outside the program, possibly in memory ("in-memory databases") but generally on disk. A file on disk could be considered a _very simple_ database, but we usually mean much more advanced programs.

Relational database
    A very common kind of database that's good at retrieving data that have relationships to one another. For instance, a question like "How expensive is the cat food brand that most of my cats prefer?" is usually easier to answer in a relational database than in other types of database.

RDBMS
    Relational database management system - basically a synonym for relational database.

SQL
    The specialized language usually used to get and manipulate data in a [relational database](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).

SQL database
    More or less a synonym for [relational database](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).

REPL
    An interactive programming language interpreter that allows a user to type in statements which are immediately evaluated. The term REPL is an acronym for _Read-Evaluate-Print-Loop_.

### Techniques

Bug
    A mistake in software that makes it crash or behave badly.

Debug
    Find and fix [bugs](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) in [code](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)

Refactor
    Change a program so that the functionality seems the same from the user's point of view, but the code itself is better - easier to read, understand, maintain, etc.

Agile Development
    

A systematic approach to software development that emphasizes short, concentrated periods of work on specific features or enhancements, where such features are delivered independently of the project at large

Contrast with the [Waterfall Model](https://en.wikipedia.org/wiki/Waterfall_model).

### Version Control

Version Control
    Tools and techniques for keeping track of the changes in files in a reversible way. More importantly, it helps people cooperate on changes to a file without ruining each others' work.

Issue
    Request for a specific change to software, either to fix a [bug](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) or provide new features ("enhancement"). Issues are usually filed in a project's [`bug tracker`_](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).

Bug report
    A category of [issue](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) for notifying the programmers of a [bug](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst)

Repository
    A record on disk of the [version control](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) history for a directory (and its subdirectories). Usually we mean someplace on line, usually at a service like [github_](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).

Repo
    Abbreviation for [repository](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).

Branch
    A parallel version of a repository, generally used for making and testing changes to a code base in a safe, non-destructive way.

Fork
    To copy over source code from a project and start independent work on it, usually because of different perspectives on how the program should be developed. A project that started this way, by basing itself over another project's source, is called a fork. (i. e. Pale Moon is a fork of Mozilla Firefox)

Pull Request
    After you have fork_ed a [repository](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) and made changes, you may ask the original repository owner to incorporate ("pull") your changes into the original repository.

Git
    The most popular program for version control.

Mercurial
    Another version control program

Github
    The most popular commercial service that hosts version control [repositories](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) online.

Bitbucket
    Another commercial service for hosting version control [repositories](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).

### Testing

Testing
    To programmers, them means scripts that verify that a program works as desired automatically. We rarely talk about non-automated, direct human testing, because it's soul-sucking and can't keep up with our speed of generating [bugs](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).

Regression test
    Tests to make sure that one part of a program doesn't get worse - _regress_ \- as improvements aren't made to a different part. All of our tests could generally be considered regression tests.

Unit Test
    A fine-scale test that works directly on one small piece of a program, at a scale finer than the end-user will directly see. Contrast [functional test](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).

Functional test
    A test that makes sure a program is working from the user's point of view. Contrast [unit test](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst).

Test-Driven Development
    A style of development where you first write the tests saying what you want the program to do - even before the program exists. Then you write the code until the tests no longer fail.

Corner Case
    A situation that's likely to show [bugs](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) in code because it's so unusual that the developers were unlikely to account for it. For instance, if you are classifying cats by their eye color, a cat with two different-color eyes may be a corner case that disrupts your classification scheme.

### Packaging

PyPI
    [PyPI](https://pypi.python.org/pypi), pronounced "Pie-Pee-Eye" and also known as _The Cheeseshop_, is the "Python Packaging Index". It is where you can publish and download open source Python packages.

pip
    [pip](https://pip.pypa.io/en/latest/index.html) is the recommended tool for installing Python packages and is preferred over [easy_install](https://pypi.python.org/pypi/setuptools).

### Architecture

API
    

Shorthand for "application programmer interface". This is the way that other programs can make use of this program. Web services can have APIs that let them accept messages from other programs and send messages back in response.

Examples include POSIX (the unix/Linux API), Win32, Cocoa, Amazon AWS, and Android. However, many other services have APIs to add things like (for instance) Dropbox and Facebook to your app.

TODO: generalize this more

### Operations

Operations
    Activities related to deploy_ing software and keeping it running on its destination servers.

DevOps
    Philosophy and tools for [operations](https://github.com/catherinedevlin/python_learners_glossary/blob/master/README.rst) that try to make the process as automatic and failsafe as possible by imitating software developers' tools and techniques.

Deploy
    To deliver a completed program so that other people can use it. Ususually different than just programming it so that it works. Sometimes, a program needs to be installed in a package, or through an App Store, or maybe it just needs to be on the web. That last step to make it so that other people can reach it is called "deployment"

Build
    TODO

Build Server
    TODO

[Continuous Integration](http://docs.python-guide.org/en/latest/scenarios/ci/)
    TODO

### Web

HTML
    Markup language used by default by most of the Web. Has tags for various kinds of elements, graphical or not. Stands for Hyper Text Markup Language
CSS
    Descriptive language to style markup elements. Usually used with HTML to style its various tags. Stands for Cascading Style Sheet

### More words to define

GIL
    TODO
PEP
    TODO
PEP 8
    TODO
program
    TODO
script
    TODO
scripting language
    TODO
regex
    TODO
pickle
    TODO
socket
    TODO
thread
    TODO
virtualenv
    TODO
kit
    TODO
hash
    TODO
commit
    TODO
branch
    TODO
polymorphism
    TODO
inheritance
    TODO
bytecode
    TODO
serialize
    TODO
JSON
    TODO
YAML
    TODO
XML
    TODO
dependency injection
    TODO
repr
    TODO
queue
    TODO
event
    TODO
message
    TODO
GUI
    TODO
command line
    TODO
loop
    TODO
list comprehension
    TODO
lambda
    TODO
closure
    TODO
generator
    TODO
coroutine
    TODO
blocking
    TODO
lock
    TODO
mutex
    TODO
semaphore
    TODO
signal
    TODO
bit
    TODO
callable
    TODO
namespace
    TODO
file object
    TODO
query
    TODO
cron
    TODO
constant
    TODO
C API
    TODO
utf-8
    TODO
ascii
    TODO
encoding
    TODO
code point
    TODO
source
    TODO
NLTK
    TODO
MVC
    TODO
file extension
    TODO
functional programming
    TODO
higher-order function
    TODO
first-class value
    TODO
indentation
    TODO
SQL injection
    TODO
decorator
    TODO
code object
    TODO
frame
    TODO
traceback
    TODO
statement
    TODO
standard library
    TODO
IDLE
    TODO
twisted
    TODO
django
    TODO
flask
    TODO
requests
    TODO
scipy
    TODO
numpy
    TODO
pandas
    TODO
matplotlib
    TODO
ipython
    TODO
jupyter
    TODO
setup.py
    TODO
mutable
    TODO
immutable
    TODO
unicode
    TODO
byte
    TODO
byte string
    TODO
array
    TODO
CPython
    TODO
PyPy
    TODO
Jython
    TODO
Cython
    TODO
ctypes
    TODO
cffi
    TODO
compile
    TODO
interpret
    TODO
syntax
    TODO
integration test
    TODO
load test
    TODO
performance test
    TODO
acceptance test
    TODO
mock
    TODO
stub
    TODO
fake
    TODO
test double
    TODO
coverage
    TODO
alpha
    TODO
beta
    TODO
release candidate
    TODO
semantic versioning
    TODO
sphinx
    TODO
ReST
    TODO
rst
    TODO
documentation
    TODO
docstring
    TODO
doctest
    TODO
concatenation
    TODO
slice
    TODO
index
    TODO
item
    TODO
property
    TODO
descriptor
    TODO
metaclass
    TODO
emacs
    TODO
vim
    TODO
pycharm
    TODO
sublime
    TODO
exception
    TODO
catch
    TODO
raise
    TODO
error
    TODO
CSV
    TODO
server
    TODO
client
    TODO
protocol
    TODO
network
    TODO
import
    TODO
synchronous
    TODO
asynchronous
    TODO
type
    TODO
type checking
    TODO
duck typing
    TODO
DSL
    TODO
subclass
    TODO
superclass
    TODO
mixin
    TODO
multiple inheritance
    TODO
interface
    TODO
abstract class
    TODO
static method
    TODO
operating system
    TODO
Windows
    TODO
Linux
    TODO
Ubuntu
    TODO
pastebin
    TODO
IRC
    TODO
operator
    TODO
operation
    TODO
object-oriented
    TODO
use case
    TODO
requirements
    TODO
recursion
    TODO
iteration
    TODO
garbage collection
    TODO
memory management
    TODO
reference
    TODO
c extension
    TODO
factory
    TODO
portable
    TODO
pythonic
    TODO
singleton
    TODO
