# Python 3: An Intro to Enumerations

_Captured: 2018-03-25 at 22:30 from [dzone.com](https://dzone.com/articles/python-3-an-intro-to-enumerations?edition=367220&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-25)_

Python added the **enum** module to the standard library in version 3.4. The Python [documentation](https://docs.python.org/3.6/library/enum.html) describes an enum like this:

> An enumeration is a set of symbolic names (members) bound to unique, constant values. Within an enumeration, the members can be compared by identity, and the enumeration itself can be iterated over.

Let's look at how you might create an Enum object:

Here we create an Enumeration class called **AnimalEnum**. Inside the class, we create class attributes called _enumeration members_, which are constants. When you try to print out an enum member, you will just get back the same string. But if you print out the _repr_ of the enum member, you will get the enum member and its value.

If you try to modify an enum member, Python will raise an **AttributeError**:

Enum members have some properties you can use to get their name and value:

Enumerations also support iteration. So you can do something fun like this:

Python's enumerations do not allow you to create enum members with the same name:

As you can see, when you try to reuse an enum member name, it will raise a **TypeError**.

You can also create an Enum like this:

Personally, I think that is really neat!

### Enum Member Access

Interestingly enough, there are multiple ways to access enum members. For example, if you don't know which enum is which, you can just call the enum directly and pass it a value:

If you happen to pass in an invalid value, then Python raises a **ValueError**

You may also access an enumeration by name:

### Enum Niceties

The enum module also has a couple of other fun things you can import. For example, you can create automatic values for your enumerations:

You can also import a handy enum decorator to make sure that your enumeration members are unique:

Here we create an enumeration that has two members trying to map to the same value. Because we added the **@unique** decorator, a `ValueError` is raised if there are any duplicate values in the enum members. If you do not have the **@unique **decorator applied, then you can have enum members with the same value.

### Wrapping Up

While I don't think the enum module is really necessary for Python, it is a neat tool to have available. The documentation has a lot more examples and demonstrates other types of enums, so it is definitely worth a read.

### Further Reading
