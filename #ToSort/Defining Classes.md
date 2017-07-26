# 5.3. Defining Classes

_Captured: 2016-02-21 at 01:59 from [www.diveintopython.net](http://www.diveintopython.net/object_oriented_framework/defining_classes.html)_

Python is fully object-oriented: you can define your own classes, inherit from your own or built-in classes, and instantiate the classes you've defined.

Defining a class in Python is simple. As with functions, there is no separate interface definition. Just define the class and start coding. A Python class starts with the reserved word class, followed by the class name. Technically, that's all that's required, since a class doesn't need to inherit from any other class.
    
    
    class Loaf: 
        pass     

Of course, realistically, most classes will be inherited from other classes, and they will define their own class methods and attributes. But as you've just seen, there is nothing that a class absolutely must have, other than a name. In particular, C++ programmers may find it odd that Python classes don't have explicit constructors and destructors. Python classes do have something similar to a constructor: the __init__ method.
    
    
    from UserDict import UserDict
    
    class FileInfo(UserDict): 

In Python, the ancestor of a class is simply listed in parentheses immediately after the class name. So the FileInfo class is inherited from the UserDict class (which was [imported from the UserDict module](http://www.diveintopython.net/object_oriented_framework/importing_modules.html)). UserDict is a class that acts like a dictionary, allowing you to essentially subclass the dictionary datatype and add your own behavior. (There are similar classes UserList and UserString which allow you to subclass lists and strings.) There is a bit of black magic behind this, which you will demystify later in this chapter when you explore the UserDict class in more depth. 

Python supports multiple inheritance. In the parentheses following the class name, you can list as many ancestor classes as you like, separated by commas.

This example shows the initialization of the FileInfo class using the __init__ method.
    
    
    class FileInfo(UserDict):
        "store file metadata"              
        def __init__(self, filename=None):   

__init__ is called immediately after an instance of the class is created. It would be tempting but incorrect to call this the constructor of the class. It's tempting, because it looks like a constructor (by convention, __init__ is the first method defined for the class), acts like one (it's the first piece of code executed in a newly created instance of the class), and even sounds like one ("init" certainly suggests a constructor-ish nature). Incorrect, because the object has already been constructed by the time __init__ is called, and you already have a valid reference to the new instance of the class. But __init__ is the closest thing you're going to get to a constructor in Python, and it fills much the same role. 

The first argument of every class method, including __init__, is always a reference to the current instance of the class. By convention, this argument is always named self. In the __init__ method, self refers to the newly created object; in other class methods, it refers to the instance whose method was called. Although you need to specify self explicitly when defining the method, you do _not_ specify it when calling the method; Python will add it for you automatically. 

__init__ methods can take any number of arguments, and just like functions, the arguments can be defined with default values, making them optional to the caller. In this case, filename has a default value of None, which is the Python null value. 

By convention, the first argument of any Python class method (the reference to the current instance) is called self. This argument fills the role of the reserved word this in C++ or Java, but self is not a reserved word in Python, merely a naming convention. Nonetheless, please don't call it anything but self; this is a very strong convention. 
    
    
    class FileInfo(UserDict):
        "store file metadata"
        def __init__(self, filename=None):
            UserDict.__init__(self)        
            self["name"] = filename        
                                           

When defining your class methods, you _must_ explicitly list self as the first argument for each method, including __init__. When you call a method of an ancestor class from within your class, you _must_ include the self argument. But when you call your class method from outside, you do not specify anything for the self argument; you skip it entirely, and Python automatically adds the instance reference for you. I am aware that this is confusing at first; it's not really inconsistent, but it may appear inconsistent because it relies on a distinction (between bound and unbound methods) that you don't know about yet.

Whew. I realize that's a lot to absorb, but you'll get the hang of it. All Python classes work the same way, so once you learn one, you've learned them all. If you forget everything else, remember this one thing, because I promise it will trip you up:

__init__ methods are optional, but when you define one, you must remember to explicitly call the ancestor's __init__ method (if it defines one). This is more generally true: whenever a descendant wants to extend the behavior of the ancestor, the descendant method must explicitly call the ancestor method at the proper time, with the proper arguments. 
