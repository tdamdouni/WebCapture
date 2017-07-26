# Resource Acquisition is Initialization (RAII)

_Captured: 2015-10-20 at 17:24 from [davidcorne.com](http://davidcorne.com/2013/04/18/resource-acquisition-is-initialization-raii/#more-827)_

The idea behind this pattern is to correctly dispose of all the resources that you acquire. This pattern was first written about by [Bjarne Stroustrup](http://en.wikipedia.org/wiki/Bjarne_Stroustrup), the creator of C++. The most common examples of this pattern are in opening and closing files and web sockets. It is also important in controlling mutexes so you can write tread safe code.

## The Pattern

This pattern concerns a single class, and as such I will only describe it's implementation I won't give a UML diagram.

I know this is a post about python, but as this pattern originated in C++ I am going to start talking about it there.

In a C++ class, like most object oriented languages, you have a constructor and destructor. So in C++ you would implement RAII in the following way.

`//=============================================================================``class` `RAII {``public``:``RAII();``// Constructor, acquire resources here``~RAII();``// Destructor, release resources here``};``//=============================================================================``RAII::RAII()``{``// acquire resource i.e. open file``}``//=============================================================================``RAII::~RAII()``{``// release resource i.e. close file``}`

In C++ whenever a class instance goes out of scope the destructor will be called. This is a deterministic process managed by the compiler and that means that you are guaranteed to release the resources. Leading on from this you might imagine you can implement RAII in the following way in python.

`#==============================================================================``class` `RAII(``object``):``__init__(``self``):``# acquire resource``__del__(``self``):``# release resource`

This is however wrong! As python does not use deterministic garbage collection __del__ will not necessarily ever get called. [Here](http://docs.python.org/2/reference/datamodel.html#object.__del__) there is more information about when/how/if __del__ is called. As a side not python is even not guaranteed to be garbage collected, this is an implementation detail for each specific interpreter, see [here](http://docs.python.org/2/reference/datamodel.html).

So how do we implement this pattern in python? We can use the context manager language feature. Context managers were introduced to python in version 2.5 and are called using the [with statement](http://docs.python.org/2/whatsnew/2.5.html#pep-343-the-with-statement). So the old code

`text_file ``=` `open``(``"file.txt"``, ``"r"``)``# do some reading``text_file.close()`

Should instead be written as.

`with ``open``(``"file.txt"``, ``"r"``) as text_file:``# do some reading`

That is the calling code, In the next section I will go over how you can create custom classes to do RAII.

## Implementation of a Context Manager

Making a context manager needs two [magic methods](http://www.rafekettler.com/magicmethods.html) __enter__ and __exit__.

__enter__ is called from the with statement, it takes no argument and it should return the context manager. In most examples you will find that the class it's is the context manager, but it doesn't have to be.

__exit__ is called when the with block is exited, either naturally or through and exception. This function takes three arguments; the type of exception, e.g. TypeException, the instance of the exception, and a traceback object which can be read with the [traceback module](http://docs.python.org/2/library/traceback.html). If there was no exception raised, all three of these will have None value. If you want to ignore the exception (or one wasn't raised) __exit__ should return True, otherwise it should return False.

So a context manager will look like this.

`#==============================================================================``class` `ContextManager(``object``):``def` `__enter__(``self``):``return` `self``def` `__exit__(``self``, exception_type, exception, traceback):``# return if there was an exception``return` `all``(``arg ``is` `None` `for` `arg ``in` `[exception_type, exception, traceback]``)`

## An Example Usage

My example usage for this is a Box. After you open a box you always need to close it.

The file for this example can be found [here](https://github.com/davidcorne/Design-Patterns-In-Python/blob/master/Creational/ResourceAcquisitionIsInitialization.py).

891011121314151617181920212223242526
`#==============================================================================``class` `Box(``object``):``def` `__init__(``self``, name):``self``.name ``=` `name``def` `__enter__(``self``):``print``(``"Box "` `+` `self``.name ``+` `" Opened"``)``return` `self``def` `__exit__(``self``, exception_type, exception, traceback):``all_none ``=` `all``(``arg ``is` `None` `for` `arg ``in` `[exception_type, exception, traceback]``)``if` `(``not` `all_none):``print``(``"Exception: \"%s\" raised."` `%``(``str``(exception)))``print``(``"Box Closed"``)``print``("")``return` `all_none`

This is then called with the following code.

28293031323334
`#==============================================================================``if` `(__name__ ``=``=` `"__main__"``):``with Box(``"tupperware"``) as simple_box:``print``(``"Nothing in "` `+` `simple_box.name)``with Box(``"Pandora's"``) as pandoras_box:``raise` `Exception(``"All the evils in the world"``)``print``(``"end"``)`

Which outputs.

`Box tupperware Opened``Nothing ``in` `tupperware``Box Closed``Box Pandora's Opened``Exception: ``"All the evils in the world"` `raised.``Box Closed``Traceback (most recent call last):``File` `"./Creational/ResourceAcquisitionIsInitialization.py"``, line ``33``, ``in` `<module>``raise` `Exception(``"All the evils in the world"``)``Exception: ``All` `the evils ``in` `the world`

Note that although the exception was raised and the program exited the box was still closed.

All of the code for the design patterns can be found [here](https://github.com/davidcorne/Design-Patterns-In-Python).

Thanks for reading.
