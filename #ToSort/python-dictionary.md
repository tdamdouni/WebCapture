# Python Dictionary

_Captured: 2018-08-07 at 08:03 from [dzone.com](https://dzone.com/articles/python-dictionary?edition=388196&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-06)_

A Python dictionary is a sequence of key/value or item pairs separated by commas.

A Python dictionary is created by using curly braces (`{}`).

The syntax to create an empty dictionary is:

**< variable-name > = {}**

OR

**< variable-name > = dict()**

The syntax to create a Python dictionary with items is:

**<variable-name> = { key : value , key : value }**

The pair of key and value is called an item, and key and value are separated by a colon (`:`). Each item is separated by comma `,`), and the whole thing is enclosed in curly braces (`{}`).

## Features of a Python Dictionary

  1. The key of a Python dictionary cannot be changed.
  2. The value of a key can be changed.
  3. The ordering is not significant. The order in which you have entered the items in the dictionary, may not be the same order in which the items are returned. 

### Features of a Python Dictionary: Key

Keys are unique to the Python dictionary they are used in. We cannot assign the same key twice.

Let's look at an example.

In the above example, we used the same key, `Mohit`, two times, although the program is not giving any errors. But, y can see the most recent key replaced the old one.

`int`, `float`, and `string` can be used as a key. The tuple which does not contain any lists can be used as a key. Let us see the example.

Traceback (most recent call last):

In the example, it is very clear that if a tuple with a list is used then the interpreter will throw an error.

### Features of a Python Dictionary: Value

The value can be repeated.

You can store anything in the value.

Y can add and update the value from the dictionary.

Let's create an empty dictionary and add some items.
    
    
    >>> AV[ ‘IRON-MAN’ ] = “Tony Stark”

You have seen we can update the value by using the dictionary's key.

### Accessing the Values of Python Dictionary

Like Python lists, indexing does not exist in Python dictionaries. The values can only be accessed by its key.

Let us take the example of computer network ports.

Traceback (most recent call last):

You can see if a key does not exist then the interpreter shows an error. In order to tackle this problem, the `get()` method is used. See the example below.

Instead of an error, a customized message gets printed.

### Different Ways to Check for the Existence of a Key

In this section, we'll see how to check whether a particular key exists or not.

You have already seen the `get()` method.

The `has_key()` method returns `True` and `False` statements.

### By Using in Operator

### Delete Elements of a Python Dictionary

Example

Traceback (most recent call last):

You can see the error because dictionary named port does exist after command del port1.

### Iterating the Python Dictionary Using a for Loop

In order to iterate over the Python dictionary, we used the `items()` or `iteritems()` method. The `items()` method returns a list of tuple pairs. The `iteritems()` method is the iterator which saves the memory.

In Python 3, the `iteritems()` method has been removed and the `items()` method works just like the `iteritems()` method.

**Output :**

![output](https://www.learntek.org/blog/wp-content/uploads/2018/07/python-dictionay.jpg)

Consider you want to update the dictionary with another dictionary

See the example below.

**Output:**

So far you have learned about Python dictionary creation, deleting an item, adding an item, and updating items. Let's create a copy of an existing dictionary. In order to make a copy of a dictionary, we will use the `copy()` method.

In the above example, a new dictionary, `port2` , which is a copy of `port1`, has been created.

The memory addresses of both the dictionaries are different.

## Practical Example

Let us create a dictionary using two lists.

**Output :**

The same result can be achieved in one line. See the example below.

**Output:**

{1: 'a', 2: 'b', 3: 'c', 4: 'd'}
