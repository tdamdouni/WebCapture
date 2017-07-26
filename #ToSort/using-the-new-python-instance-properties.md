# Using the New Python Instance Properties

_Captured: 2017-06-16 at 02:11 from [dzone.com](https://dzone.com/articles/using-the-new-python-instance-properties?edition=305097&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-15)_

Effortlessly power IoT, predictive analytics, and machine learning applications with an [elastic, resilient data infrastructure](https://dzone.com/go?i=207144&u=https%3A%2F%2Fmesosphere.com%2Fsolutions%2Fdata%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_term%3Dpre-article%26utm_content%3D101). Learn how with [Mesosphere DC/OS](https://dzone.com/go?i=207144&u=https%3A%2F%2Fmesosphere.com%2Fproduct%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_term%3Dpre-article%26utm_content%3D101).

Last week, [I showed you my new implementation for instance-level properties in Python](https://dzone.com/articles/another-look-at-instance-level-properties-in-pytho). This week, we'll take another look at it by implementing a few Delegated Properties and helpers to make using them just a hair nicer.

## Recreating Kotlin's Built-In Delegates

For inspiration of what Delegated Properties to create, we'll start by recreating the ones built into Kotlin, starting with `Lazy`.

### Lazy

The `Lazy` Delegated Property allows you to initialize it with a function that takes no parameters and returns an object -- preferably one that is relatively expensive to create. Then, the first time the property is retrieved, the object is created as a store, which subsequent lookups will use.

To start us off, let's create an object that we can use as a flag to represent that the value isn't initialized yet (we could use `None`, but it's possible that the function could return `None`, and we'd start having some difficulties).

Using that, here's `Lazy`:
    
    
        def __init__(self, initializer, *, readonly=False):
    
    
    def get(self, instance, name):
    
    
                self.value = self.initialize()
    
    
    def set(self, value, instance, name):

Note the optional read-only with the convenient `readonly()` class method. I'm not sure what else to say about it. If you have any trouble understanding any of these, ask me about it in the comments.

### Lateinit

Next up is `lateinit`. This isn't quite as handy in Python as it is in Kotlin since it is largely provided to allow for non-null properties in a class that implements the bean protocol. The problem is that the bean protocol requires a constructor that takes no arguments, where all the fields on the class are initialized to null. In Kotlin, you have null safety, and people like to mark their fields as non-nullable. So, in order to make the bean field non-nullable and yet have them start of null, Kotlin includes `lateinit`, which represents an uninitialized non-nullable field. If the field is accessed before it is ever set to something, then it triggers an exception. Technically, this isn't a Delegated Property in Kotlin; it's a language modifier, but it could be implemented as a Delegated Property.

What use does it have in Python? Well, it's possible you might want to create a class where some or all of the attributes aren't initialized right away, - rather they're set later - but the class requires some or all of those attributes for certain actions. This way, instead of writing verifiers at the beginning of those actions to be certain that they were set, you simply access the attribute, and if it wasn't set, it'll raise an exception on its own.

Here's what such a Delegated Property looks like:
    
    
        def __init__(self, value=no_value, *, readonly=False):
    
    
        def readonly(cls, value=no_value):
    
    
    def get(self, instance, name):
    
    
    def set(self, value, instance, name):
    
    
            if self._readonly and self.value is not no_value:  # the second part allows you to use set to initialize the value later, even if it's read-only

The constructor and `readonly()` class method include the ability to initialize the property immediately, even though that's not the typical case, but I like the idea of making it a little more flexible that way.

### Bymap

Sometimes, you just want to take in a dictionary in the constructor and have attributes refer to that dictionary for their values. That's what this Delegated Property does for you. So, it would be used like this:
    
    
    def __init__(self, dict_of_values):
    
    
            self.a.initialize(dict_of_values)
    
    
            self.b.initialize(dict_of_values)

And here, `a` and `b` will read from and write to the provided dictionary instead of to the instance's `__dict__`.
    
    
        def __init__(self, mapping, *, readonly=False):
    
    
    def get(self, instance, name):
    
    
    def set(self, value, instance, name):
    
    
                self.mapping[name] = value

Here is where passing in `name` to `get()` and `set()` methods really comes in handy. Without the automatic calculating and passing of names, this would be more tedious to implement and use. The name would have to be taken in through the constructor, which means the user would have to provide it with initialize call. And that means that it would have to be updated by hand if they ever decide to change the name in a refactoring.

### Observable

Kotlin also has the `Observable` Delegated Property, which I don't see as being all that useful, so I won't bother showing you that one.

## Custom Delegated Property: validate

One of the biggest reasons we ever need properties is to ensure that what is provided is a valid value to be given. While using the built-in Python `property` isn't bad for this use case, it does still require the user to have to think about where to _actually_ store the value, and it requires the verbosity of creating a method. But the biggest shortfall is when you need to reuse the logic of that property elsewhere. You could implement a full-blown descriptor for it, but that's also excessive. With `Validate`, all you really need to implement is the validation function and possibly a helper function for creating the specific validator.
    
    
    return isinstance(num, int) and num > 0

See how you could just write a simple validator function and use that with `InstanceProperty(Validate.using(<function>))`? Pretty nice, right? Let's see what `Validate` looks like, shall we?
    
    
        def __init__(self, validator, value,  *, readonly=False):
    
    
        def using(cls, validator, *, readonly=False):
    
    
            return lambda value: cls(validator, value, readonly=readonly)
    
    
            return cls.using(validator, readonly=True)
    
    
        def get(self, *args):
    
    
    def set(self, value, instance, name):

We had to unfortunately use lambda to implement the class methods. It could have been done by returning an inner function as well, but the lack of need for a name makes that excessive.

It also kind of sucks that we can't do a proper error message in `__init__()` because we don't have access to the name and instance. To get around this, I'm passing those arguments in as named arguments in `initialize` in the final version on [GitHub](https://github.com/sad2project/descriptor-tools) (I wrote `Validate` for the first time after last week's article and didn't want to present any changes to last week's code here). The Delegated Properties that don't use them can just add `**kwargs` into their `__init__()` signature and ignore it.

## Helpers

### Shortening instanceproperty

Always instantiating an `InstanceProperty` using that full name is tedious, and could potentially be enough to keep people from using it in the first place. So let's make a shorter-named function that delegates to it:

I chose "by" as the name since it reflects the keyword used in Kotlin. You can use whatever name you want.

Why don't I just rename `InstanceProperty` to something shorter? Because anything shorter would likely lose meaning, and we always want our names to have meaning.

### Read Only Wrappers

I have a couple ideas for this, both of which aren't compatible with 100% of Delegated Properties. Both of these make it so we don't need to have a class method named "readonly", and otherwise make implementing Delegated Properties easier.

The first is just a convenience function:

Which can then be used like this:

Seeing that Delegated Properties aren't required to have the `readonly` parameter, this isn't 100% compatible. The respective properties should document whether or not they work with this function or not. This applies to the next one as well.
    
    
            return lambda *args, **kwargs: cls(delegate(*args, **kwargs))
    
    
    def get(self, instance, name):
    
    
            return self.delegate.get(instance, name)

`Readonly` is used in the following way:

It's annoying that we had to return a function within a function again, but when `InstanceProperty`needs a function for instantiating a Delegated Property, there's not a whole lot of choice.

## Outro

So that's everything. Again, this is all in a [GitHub repo](https://github.com/sad2project/descriptor-tools), which turns out to be the same repo (descriptor-tools) I made for my book. The new code is added, but not all the tests and documentation are written for it yet. When that's done, I'll submit the rest to PyPI so you can easily install it with pip.

Thanks for reading, and I'll see you next week with an article about the MVP pattern.

Learn to design and build better data-rich applications with this [free eBook from O'Reilly](https://dzone.com/go?i=207145&u=https%3A%2F%2Fmesosphere.com%2Fresources%2Fdesigning-data-intensive-applications%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_campaign%3Doreilly-data-apps-ebook%26utm_term%3Dpost-article%26utm_content%3D202). Brought to you by [Mesosphere DC/OS](https://dzone.com/go?i=207145&u=https%3A%2F%2Fmesosphere.com%2Fproduct%2F%3Futm_source%3Ddzone%26utm_medium%3Dbig-data%26utm_campaign%3Doreilly-data-apps-ebook%26utm_term%3Dpost-article%26utm_content%3D202).
