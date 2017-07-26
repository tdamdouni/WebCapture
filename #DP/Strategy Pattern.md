# Strategy Pattern

_Captured: 2015-10-20 at 23:08 from [davidcorne.com](http://davidcorne.com/2013/01/21/strategy-pattern/#more-635)_

##  The Purpose 

The idea behind the strategy pattern is to encapsulate the implementation details of an algorithm and make them interchangeable. This gives more flexibility in how an object can be used and enables each algorithm to be tested independently of the calling object.

##  The Pattern 

Here is a UML diagram of a typical use of the strategy pattern.

![](http://yuml.me/ffab35c4.png)

This shows an interface (an unimplemented class denoted by <<>>) called IAlgorithm. The caller class will contain an instance of an object which implements this interface using [aggregation](http://en.wikipedia.org/wiki/Object_composition#Aggregation). This means that the lifetime of the algorithms is not necessarily tied to the caller. The implemented algorithm classes derive from the interface.

##  An Example Usage

I will give two implementations of this pattern; one which is more standard and will closely match the above UML and one which I believe is more pythonic.

###  First Example 

My example will be using two different algorithms to calculate prime numbers.

Here is the caller class PrimeFinder.

678910111213141516171819202122232425262728
`#==============================================================================``class` `PrimeFinder(``object``):``def` `__init__(``self``, algorithm):``""" ``Constructor, takes a lass called algorithm. ``algorithm should have a function called calculate which will take a ``limit argument and return an iterable of prime numbers below that ``limit.``"""``self``.algorithm ``=` `algorithm``self``.primes ``=` `[]``def` `calculate(``self``, limit):``""" Will calculate all the primes below limit. """``self``.primes ``=` `self``.algorithm.calculate(limit)``def` `out(``self``):``""" Prints the list of primes prefixed with which algorithm made it """``print``(``self``.algorithm.name)``for` `prime ``in` `self``.primes:``print``(prime)``print``("")`

This will be given an algorithm on construction, the contract for the algorithm is that it must have a function called calculate which takes a limit. This is explained in the docstring for __init__ but in a statically typed language such as c++ the constructor would look something like this.

`PrimeFinder(``const` `IAlgorithm& algorithm);`

We can not (and should not) enforce what is passed into the constructor in python. However we can pass in objects derived from an abstract base class so that our algorithms will definitely work. The functionality of abstract base classes is importable in python from the module abc. So we need this at the top of the file.

4
`import` `abc`

Here is the base class I will be using in this example.

30313233343536
`#==============================================================================``class` `Algorithm(``object``):``__metaclass__ ``=` `abc.ABCMeta``@abc``.abstractmethod``def` `calculate(``self``, limit):``raise`

This defines an abstract base class Algorithm. The __metaclass__ line changes the way this class is constructed. If you derive from it and you have not implemented the functions decorated with @abc.abstractmethod the following error will be raised.

This enforces the contract that any class deriving from Algorithm will be able to be used in PrimeFinder. So now we can derive our algorithms from this with the following two classes.

383940414243444546474849505152535455565758596061626364656667686970717273747576777879
`#==============================================================================``class` `HardCoded(Algorithm):``""" ``Has hardcoded values for all the primes under 50, returns a list of those``which are less than the given limit.``"""``def` `__init__(``self``):``self``.name ``=` `"hard_coded_algorithm"``def` `calculate(``self``, limit):``hardcoded_primes ``=` `[``2``,``3``,``5``,``7``,``11``,``13``,``17``,``19``,``23``,``29``,``31``,``37``,``41``,``43``,``47``]``primes ``=` `[]``for` `prime ``in` `hardcoded_primes:``if` `(prime < limit):``primes.append(prime)``return` `primes``#==============================================================================``class` `Standard(Algorithm):``""" ``Not a great algorithm either, but it's the normal one to use.``It puts 2 in a list, then for all the odd numbers less than the limit if ``none of the primes are a factor then add it to the list.``"""``def` `__init__(``self``):``self``.name ``=` `"standard_algorithm"``def` `calculate(``self``, limit):``primes ``=` `[``2``]``# check only odd numbers.``for` `number ``in` `range``(``3``, limit, ``2``):``is_prime ``=` `True``# divide it by all our known primes, could limit by sqrt(number)``for` `prime ``in` `primes:``if` `(number ``%` `prime ``=``=` `0``):``is_prime ``=` `False``break``if` `(is_prime):``primes.append(number)``return` `primes`

I am not going to go through all the details of these two classes as that is not what this post is about, I'll just give an overview.

The first has a hard-coded list and returns all the primes it knows about below the limit you give.

The second makes a list of primes then iterates over all the odd numbers less than the limit and if none of the primes on the list divide the number it adds it to the list of primes.

The following is the calling code included at the bottom of this file

8182838485868788899091
`#==============================================================================``if` `(__name__ ``=``=` `"__main__"``):``hard_coded_algorithm ``=` `HardCoded()``hardcoded_primes ``=` `PrimeFinder(hard_coded_algorithm)``hardcoded_primes.calculate(``50``)``hardcoded_primes.out()``standard_algorithm ``=` `Standard()``standard_primes ``=` `PrimeFinder(standard_algorithm)``standard_primes.calculate(``50``)``standard_primes.out()`

So you instantiate an algorithm, pass it to the prime finder then call the methods on it and the algorithm you gave it will be used. This code does not show that, as these algorithms give the same results on a limit of 50. The code afterwards shows that they are different.

93949596979899100101102103104105
`print``(``"Do the two algorithms get the same result on 50 primes? %s"``%``(``str``(hardcoded_primes.primes ``=``=` `standard_primes.primes))``)``# the hardcoded algorithm only works on numbers under 50``hardcoded_primes.calculate(``100``)``standard_primes.calculate(``100``)``print``(``"Do the two algorithms get the same result on 100 primes? %s"``%``(``str``(hardcoded_primes.primes ``=``=` `standard_primes.primes))``)`

Which prints the following

Here is the specific UML diagram for these.

![](http://yuml.me/9dfd5ea2)

> _Specific Strategy Pattern_

The code for this implementation is found in [this file](https://github.com/davidcorne/Design-Patterns-In-Python/blob/master/Behavioural/Strategy_old.py).

###  Second Example 

The previous example is more how you would implement this pattern in a statically typed language such as C++ or C#. This is a more pythonic approach which will take some advise I heard in a talk; classes with only a __init__ function and one other function are functions in disguise. As functions are first class objects in python there is a lot we can do with them and I believe this gives a more pythonic variant of the strategy pattern.

Here is the calling class.

45678910111213141516171819202122232425
`#==============================================================================``class` `PrimeFinder(``object``):``def` `__init__(``self``, algorithm):``""" ``Constructor, takes a callable object called algorithm. ``algorithm should take a limit argument and return an iterable of prime ``numbers below that limit.``"""``self``.algorithm ``=` `algorithm``self``.primes ``=` `[]``def` `calculate(``self``, limit):``""" Will calculate all the primes below limit. """``self``.primes ``=` `self``.algorithm(limit)``def` `out(``self``):``""" Prints the list of primes prefixed with which algorithm made it """``print``(``self``.algorithm.__name__)``for` `prime ``in` `self``.primes:``print``(prime)``print``("")`

There are a few differences between this and the class PrimeFinder in the previous example. This one asks for a callable object rather than an object with a calculate method, this is reflected in the implementation of calculate where it calls the passed in object. The other difference is that it does not need a property name it uses the python built in __name__.

This means we can pass functions into the class. Here are two functions which correspond to the previous classes.

2728293031323334353637383940414243444546474849505152535455565758
`#==============================================================================``def` `hard_coded_algorithm(limit):``""" ``Has hardcoded values for all the primes under 50, returns a list of those``which are less than the given limit.``"""``hardcoded_primes ``=` `[``2``,``3``,``5``,``7``,``11``,``13``,``17``,``19``,``23``,``29``,``31``,``37``,``41``,``43``,``47``]``primes ``=` `[]``for` `prime ``in` `hardcoded_primes:``if` `(prime < limit):``primes.append(prime)``return` `primes``#==============================================================================``def` `standard_algorithm(limit):``""" ``Not a great algorithm either, but it's the normal one to use.``It puts 2 in a list, then for all the odd numbers less than the limit if ``none of the primes are a factor then add it to the list.``"""``primes ``=` `[``2``]``# check only odd numbers.``for` `number ``in` `range``(``3``, limit, ``2``):``is_prime ``=` `True``# divide it by all our known primes, could limit by sqrt(number)``for` `prime ``in` `primes:``if` `(number ``%` `prime ``=``=` `0``):``is_prime ``=` `False``break``if` `(is_prime):``primes.append(number)``return` `primes`

These are called in almost the same way as using the classes.

737475767778798081
`#==============================================================================``if` `(__name__ ``=``=` `"__main__"``):``hardcoded_primes ``=` `PrimeFinder(hard_coded_algorithm)``hardcoded_primes.calculate(``50``)``hardcoded_primes.out()``standard_primes ``=` `PrimeFinder(standard_algorithm)``standard_primes.calculate(``50``)``standard_primes.out()`

As this can take any callable object this can also be a class. A class in python is also a callable object. When a class is called an object is made so the function in PrimeFinder

will set self.primes to an instance of the class. As out() needs only that the object self.primes is iterable we can use the python magic method __iter__ to make that so.

Here is the implementation of a class which can be passed in to PrimeFinder.

6061626364656667686970717273747576777879
`#==============================================================================``class` `HardCodedClass(``object``):``def` `__init__(``self``, limit):``hardcoded_primes ``=` `[``2``,``3``,``5``,``7``,``11``,``13``,``17``,``19``,``23``,``29``,``31``,``37``,``41``,``43``,``47``]``self``.primes ``=` `[]``for` `prime ``in` `hardcoded_primes:``if` `(prime < limit):``self``.primes.append(prime)``def` `__iter__(``self``):``return` `iter``(``self``.primes)``1``This ``is` `called ``in` `the following way.``1``class_primes ``=` `PrimeFinder(HardCodedClass)``class_primes.calculate(``50``)``class_primes.out()`

Note that HardCodedClass has no brackets after it, this is because the class is being passed in as an object not an instance of the class.

Another thing to note is that although I have used different instances of PrimeFinder in my calling code I could have just set the property algorithm in the following way.

73747576777879808182838485
`#==============================================================================``if` `(__name__ ``=``=` `"__main__"``):``prime_finder ``=` `PrimeFinder(hard_coded_algorithm)``prime_finder.calculate(``50``)``prime_finder.out()``prime_finder.algorithm ``=` `standard_algorithm``prime_finder.calculate(``50``)``prime_finder.out()``prime_finder.algorithm ``=` `HardCodedClass``prime_finder.calculate(``50``)``prime_finder.out()`

The code for this specific file can be found [here](https://github.com/davidcorne/Design-Patterns-In-Python/blob/master/Behavioural/Strategy.py). All of the code for the design patterns can be found [here](https://github.com/davidcorne/Design-Patterns-In-Python).

Thanks for reading.
