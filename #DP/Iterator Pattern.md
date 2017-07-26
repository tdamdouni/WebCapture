# Iterator Pattern

_Captured: 2015-10-20 at 17:25 from [davidcorne.com](http://davidcorne.com/2013/02/22/iterator-pattern/#more-720)_

## The Purpose

The idea behind this pattern is to have an object which you can loop over without needing to know the internal representation of the data. While in python nothing is private so you can find out the internals of the class, the iterator pattern gives you a standard interface.

I think the best example of an iterator in python is using a list. As I'm sure you know this is how you would iterate over a list in python.

`list` `=` `[``"one"``, ``"two"``, ``"three"``]``for` `number ``in` `list``:``print``(number)`

Which gives the following output.

`one``two``three`

The goal of this pattern in python is to be able to do that with a user defined class.

## The Pattern

This is quite a small pattern so I will focus more on the implementation detail than the design.

But in the interest of consistency here is the UML diagram.

![](https://raw.github.com/davidcorne/Design-Patterns-In-Python/master/Images/UML/Iterator_general.png)

So the iterator holds a container by aggregation, so it doesn't own/delete the container, it just has a reference to it.

You can see from this that we are talking about a general collection/data structure here so it is not specific to a list or dictionary for example. The methods on these classes are standard for defining a collection/iterator interface in python and I will go through these in more detail next.

## Python Protocols

Protocols are the name given in python, for the interface you need to make a certain kind of object. These are not a formal requirement like an interface, but more of a guide.

They focus on pythons magic methods, which are those with double underscores surrounding the name.

I'm going to briefly talk about the protocols for mutable and immutable containers, and iterators.

### Immutable Containers

An immutable container is one where you cannot change the individual items. For this you only need to be able to get the length of it and access individual items.

The python magic methods for an immutable container are.

`def` `__len__(``self``):``""" Returns the length of the container. Called like len(class) """``def` `__getitem__(``self``, key):``""" ``Returns the keyth item in the container. ``Should raise TypeError if the type of the key is wrong.``Should raise KeyError if there is no item for the key. ``Called like class[key]``"""`

Again the exceptions mentioned in __getitem__ are convention, but it's important for writing idiomatic python.

### Mutable Containers

As you might expect a mutable container has the same methods for accessing items as an immutable container, but adds ways of setting or adding them.

Here are the magic methods.

`def` `__len__(``self``):``""" ``Returns the length of the container. ``Called like len(class) ``"""``def` `__getitem__(``self``, key):``""" ``Returns the keyth item in the container. ``Should raise TypeError if the type of the key is wrong.``Should raise KeyError if there is no item for the key. ``Called like class[key]``"""``def` `__setitem__(``self``, key, value):``""" ``Sets the keyth item in the container. ``Should raise TypeError if the type of the key is wrong.``Should raise KeyError if there is no item for the key. ``Called like class[key] = value``"""``def` `__delitem__(``self``, key):``""" ``Deletes an item from the collection.  ``Should raise TypeError if the type of the key is wrong.``Should raise KeyError if there is no item for the key. ``Called like del class[key]``"""`

For an immutable container you probably want to have some way of adding elements too. For a list/array style container this might be in the form of a function append(self, key) or for a dictionary/table type container it might be using the __setitem__(self, key, value) function.

There are other functions you can add such as __reversed__(self) and __contains__(self, item) but they are not needed for core functionality. They are very well described [here](http://www.rafekettler.com/magicmethods.html#sequence).

### Iterators

The protocol for an iterator is very simple.

`def` `__iter__(``self``):``"""``Returns an iterator for the collection.``Called like iter(class) or for item in class:``"""``def` `next``(``self``):``"""``Returns the next item in the collection.``Called in a for loop, or manually.``Should raise StopIteration on the last item.``"""`

The __iter__ function will typically return another iterator object or return itself. Note in python 3 next() is renamed __next__().

## An Example Usage

Here is an example of how you might implement a simple iterator. My iterator will loop over a collection in reverse.

45678910111213141516171819202122232425
`#==============================================================================``class` `ReverseIterator(``object``):``""" ``Iterates the object given to it in reverse so it shows the difference. ``"""``def` `__init__(``self``, iterable_object):``self``.``list` `=` `iterable_object``# start at the end of the iterable_object``self``.index ``=` `len``(iterable_object)``def` `__iter__(``self``):``# return an iterator``return` `self``def` `next``(``self``):``""" Return the list backwards so it's noticeably different."""``if` `(``self``.index ``=``=` `0``):``# the list is over, raise a stop index exception``raise` `StopIteration``self``.index ``=` `self``.index ``-` `1``return` `self``.``list``[``self``.index]`

Note this only has the two functions needed for the iterator protocol, as these are all that are needed.

Hopefully it is fairly obvious what these functions do. The constructor takes some iterable and caches it's length as an index. The __iter__ returns the ReverseIterator as it has a next() function. The next function decrements the index and returns that item, unless there is no item to return at which point it raise StopIteration.

In my example the ReverseIterator is used by a Days class, given here.

27282930313233343536373839404142
`#==============================================================================``class` `Days(``object``):``def` `__init__(``self``):``self``.days ``=` `[``"Monday"``,``"Tuesday"``, ``"Wednesday"``, ``"Thursday"``,``"Friday"``, ``"Saturday"``, ``"Sunday"``]``def` `reverse_iter(``self``):``return` `ReverseIterator(``self``.days)`

This is just a wrapper for a list of the days of the week, which has a function to return an iterator.

This is how these classes are used.

`#==============================================================================``if` `(__name__ ``=``=` `"__main__"``):``days ``=` `Days()``for` `day ``in` `days.reverse_iter():``print``(day)`

Note I could have used a __iter__() function in Days instead of reverse_iter(). This would then have been used like this.

`#==============================================================================``if` `(__name__ ``=``=` `"__main__"``):``days ``=` `Days()``for` `day ``in` `days:``print``(day)`

My reason for not doing this is that this does not make it clear that you are reversing it.

The output from either of these is.

`Sunday``Saturday``Friday``Thursday``Wednesday``Tuesday``Monday`

This code for this can be found in [this file](https://github.com/davidcorne/Design-Patterns-In-Python/blob/master/Behavioural/Iterator.py).

Here is the specific UML for these classes.

![](https://raw.github.com/davidcorne/Design-Patterns-In-Python/master/Images/UML/Iterator_specific.png)

> _Specific Iterator Pattern_

All of the code for the design patterns can be found [here](https://github.com/davidcorne/Design-Patterns-In-Python).

Thanks for reading.
