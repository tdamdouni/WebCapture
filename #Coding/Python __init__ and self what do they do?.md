# Python __init__ and self what do they do?

up vote 267 down vote favorite

**124**

I'm learning the Python programming language, and I've come across certain things I don't fully understand. I'm coming from a C background, but I never went far with that either.

What I'm trying to figure out is:

In a method:

    
    
    def method(self, blah):
        def __init__(?):
            ....
        ....
    

What does self do? what is it meant to be? and is it mandatory?

What does the `__init__` method do? why is it necessary? etc

I think they might be oop constructs, but I don't know very much..

[python](/questions/tagged/python) [oop](/questions/tagged/oop)

[share](/q/625083)|[improve this question](/posts/625083/edit)

[edited Jul 2 '14 at 0:54](/posts/625083/revisions)

![](https://i.stack.imgur.com/xEJu4.jpg?s=32&g=1)

[alex](/users/31671/alex)

244k111609767

asked Mar 9 '09 at 5:09

GUIDED BOMB 

1

 

This may help: [itmaybeahack.com/homepage/books/nonprog/html/p12_objects/…](http://www.itmaybeahack.com/homepage/books/nonprog/html/p12_objects/p12_c02_classdef.html#class-use-making-new-objects) (previously [homepage.mac.com/s_lott/books/nonprog/htmlchunks/ch42.html](http://homepage.mac.com/s_lott/books/nonprog/htmlchunks/ch42.html)). - [S.Lott](/users/10661/s-lott) Mar 9 '09 at 10:37

4

 

Your sample code looks all messed up. Luckily many answers contain proper Python class examples, hopefully setting you straight. :) - [unwind](/users/28169/unwind) Mar 9 '09 at 10:48

  
 

[diveintopython.net/object_oriented_framework/…](http://www.diveintopython.net/object_oriented_framework/defining_classes.html) see here on the function of the `__init__` method. Especially 5.3.1 example 5.5 - [franklin](/users/778694/franklin) Jul 6 '13 at 18:18

  
 

possible duplicate of [What is the purpose of self in Python?](http://stackoverflow.com/questions/2709821/what-is-the-purpose-of-self-in-python) - [Antti Haapala](/users/918959/antti-haapala) Feb 20 '15 at 11:11

  
 

possible duplicate of [Why do we use __init__ in python classes?](http://stackoverflow.com/questions/8609153/why-do-we-use-init-in-python-classes) - [PM 2Ring](/users/4014959/pm-2ring) Feb 20 '15 at 11:32

add a comment | 

##  16 Answers 16

[ active](/questions/625083/python-init-and-self-what-do-they-do?answertab=active#tab-top) [ oldest](/questions/625083/python-init-and-self-what-do-they-do?answertab=oldest#tab-top) [ votes](/questions/625083/python-init-and-self-what-do-they-do?answertab=votes#tab-top)

up vote 273 down vote

In this code:

    
    
    class A(object):
        def __init__(self):
            self.x = 'Hello'
    
        def method_a(self, foo):
            print self.x + ' ' + foo
    

... the `self` variable represents the instance of the object itself. Most object-oriented languages pass this as a hidden parameter to the methods defined on an object; Python does not. You have to declare it explicitly. When you create an instance of the `A` class and call its methods, it will be passed automatically, as in ...

    
    
    a = A()               # We do not pass any argument to the __init__ method
    a.method_a('Sailor!') # We only pass a single argument
    

The `__init__` method is roughly what represents a constructor in Python. When you call `A()` Python creates an object for you, and passes it as the first parameter to the `__init__` method. Any additional parameters (e.g., `A(24, 'Hello')`) will also get passed as arguments--in this case causing an exception to be raised, since the constructor isn't expecting them.

[share](/a/625098)|[improve this answer](/posts/625098/edit)

answered Mar 9 '09 at 5:18

![](https://www.gravatar.com/avatar/f7a299bf5d76571cdaa91d2d1ff3805e?s=32&d=identicon&r=PG)

[Chris B.](/users/9161/chris-b)

23.4k96196

2

 

what if you put `x = 'Hello'` outside **init** but inside the class? is it like java where it's the same, or does it become like a static variable which is only initialised once? - [Jayen](/users/192798/jayen) Apr 9 '12 at 0:41

5

 

It's like a static variable. It's only initialized once, and it's available through `A.x` or `a.x`. Note that overriding it on a specific class will not affect the base, so `A.x = 'foo'; a.x = 'bar'; print a.x; print A.x` will print `bar` then `foo` - [Chris B.](/users/9161/chris-b) Apr 9 '12 at 15:46

90

 

It's worth pointing out that the first argument need not necessarily be called `self`, it just is by convention. - [Henry Gomersall](/users/709852/henry-gomersall) Jun 24 '12 at 19:37

add a comment | 

up vote 75 down vote

Yep, you are right, these are oop constructs.

init is the constructor for a class. The self parameter refers to the instance of the object (like **this** in C++).

    
    
    class Point:
        def __init__(self, x, y):
            self._x = x
            self._y = y
    

The init method gets called when memory for the object is allocated:

    
    
    x = Point(1,2)
    

It is important to use the self parameter inside an object's method if you want to persist the value with the object. If, for instance, you implement the init method like this:

    
    
    class Point:
        def __init__(self, x, y):
            _x = x
            _y = y
    

Your x and y parameters would be stored in variables on the stack and would be discarded when the init method goes out of scope. Setting those variables as self._x sets those variables as members of the Point object (accessible for the lifetime of the object).

[share](/a/625097)|[improve this answer](/posts/625097/edit)

[edited Mar 9 '09 at 11:56](/posts/625097/revisions)

answered Mar 9 '09 at 5:18

![](https://www.gravatar.com/avatar/7c81112d42daebf4e08981a6641f9713?s=32&d=identicon&r=PG)

[RedBlueThing](/users/73488/redbluething)

25.6k1372103

  
 

So, that means if we do not wish to initialize any class variables, we can just forget __init__(self): Am I correct? - [Tharindu Rusira](/users/998377/tharindu-rusira) Jul 16 '13 at 8:34

  
 

@TharinduRusira Yep - [RedBlueThing](/users/73488/redbluething) Jul 16 '13 at 8:57

2

 

why you have used underscores? - [avi](/users/1382297/avi) Nov 21 '13 at 9:27

15

 

Underscores are used to indicate those class members are "private". Client code should not depend on them. They may change in the future. It's just a convention. - [Wei Qiu](/users/1854834/wei-qiu) Nov 22 '13 at 12:53

1

 

@TharinduRusira no. They are instance variables, not class variables - [Antti Haapala](/users/918959/antti-haapala) Feb 19 '15 at 10:15

 |  show **1** more comment

up vote 52 down vote

# A brief illustrative example

In the hope it might help a little, here's a simple example I used to understand the difference between a variable declared inside a class, and a variable declared inside an `__init__` function:

    
    
    class MyClass(object):
         i = 123
         def __init__(self):
             self.i = 345
    
    a = MyClass()
    print a.i
    345
    print MyClass.i
    123
    

[share](/a/17260649)|[improve this answer](/posts/17260649/edit)

[edited Mar 7 '15 at 9:17](/posts/17260649/revisions)

answered Jun 23 '13 at 12:15

![](https://www.gravatar.com/avatar/c94743fafb1114f9742bf7a16a2e11d7?s=32&d=identicon&r=PG)

[Dave Everitt](/users/123033/dave-everitt)

5,51012452

3

 

Interesting observation but I think you are on the wrong track. With print MyClass.i it looks more like you are calling a 'static' variablie i. Where as with a.i you are calling a member variable, i. It seems to me that _init_ is just a constructor that is first executed when you create an object of the class. - [captainspi](/users/812206/captainspi) Jun 23 '13 at 17:38

4

 

That's what I was trying to 'explain to myself' with this example - that the variable set by `__init__` is what gets passed to _instances_ of the class, not the 'static' variable of the class itself that has the same name... - [Dave Everitt](/users/123033/dave-everitt) Jun 25 '13 at 8:34

add a comment | 

up vote 19 down vote

They are OOP constructs. If you are a beginner in OOP, it's going to be hard to explain them in a few sentences.

Here's a tutorial that introduces OOP in Python. It also provides some answers to your questions:

<http://www.voidspace.org.uk/python/articles/OOP.shtml>

[share](/a/625094)|[improve this answer](/posts/625094/edit)

[edited Mar 9 '09 at 5:22](/posts/625094/revisions)

answered Mar 9 '09 at 5:16

![](https://i.stack.imgur.com/pFb1E.jpg?s=32&g=1)

[maxyfc](/users/72990/maxyfc)

4,56332440

4

 

While this link may answer the question, it is better to include the essential parts of the answer here and provide the link for reference. Link-only answers can become invalid if the linked page changes. - [timo.rieber](/users/3246440/timo-rieber) Feb 19 '15 at 11:54

5

 

This answer basically says "I am not attempting to answer this question but have a link", unbelievable that it got the number of upvotes it got. - [Antti Haapala](/users/918959/antti-haapala) Feb 19 '15 at 13:06

  
 

Surprised it hasn't been flagged for removal. - [Matt O'Brien](/users/2822004/matt-obrien) Nov 2 '15 at 7:33

add a comment | 

up vote 18 down vote

In short:

  1. `self` as it suggests, refers to _itself_\- the object which has called the method. That is, if you have N objects calling the method, then `self.a` will refer to a separate instance of the variable for each of the N objects. Imagine N copies of the variable `a` for each object
  2. `__init__` is what is called as a constructor in other OOP languages such as C++/Java. The basic idea is that it is a _special_ method which is automatically called when an object of that Class is created

HTH, Amit

[share](/a/625133)|[improve this answer](/posts/625133/edit)

[edited Mar 9 '09 at 12:57](/posts/625133/revisions)

![](https://www.gravatar.com/avatar/e6488132d206883770017ba97d0f521f?s=32&d=identicon&r=PG)

[SilentGhost](/users/12855/silentghost)

112k30207231

answered Mar 9 '09 at 5:41

![](https://www.gravatar.com/avatar/e649984086cb48e24a6dfd040a86fe96?s=32&d=identicon&r=PG)

[Amit](/users/59634/amit)

6,89183758

add a comment | 

up vote 12 down vote

`__init__` does act like a constructor. You'll need to pass "self" to any class functions as the first argument if you want them to behave as non-static methods. "self" are instance variables for your class.

[share](/a/625096)|[improve this answer](/posts/625096/edit)

[edited Mar 9 '09 at 12:57](/posts/625096/revisions)

![](https://www.gravatar.com/avatar/e6488132d206883770017ba97d0f521f?s=32&d=identicon&r=PG)

[SilentGhost](/users/12855/silentghost)

112k30207231

answered Mar 9 '09 at 5:18

![](https://www.gravatar.com/avatar/32312c5237714957e3ff867e6a68b49b?s=32&d=identicon&r=PG)

[ewalk](/users/75479/ewalk)

945613

add a comment | 

up vote 10 down vote

note that `self` could actually be any valid python identifier. For example, we could just as easily write, from Chris B's example:

    
    
    class A(object):
        def __init__(foo):
            foo.x = 'Hello'
    
        def method_a(bar, foo):
            print bar.x + ' ' + foo
    

and it would work exactly the same. It is however recommended to use self because other pythoners will recognize it more easily.

[share](/a/626081)|[improve this answer](/posts/626081/edit)

answered Mar 9 '09 at 12:50

![](https://www.gravatar.com/avatar/d8da959b2a586b4a147604e6f534a9fe?s=32&d=identicon&r=PG)

[SingleNegationElimination](/users/65696/singlenegationelimination)

76.8k9133200

add a comment | 

up vote 10 down vote

Basically, you need to use the 'self' keyword when using a variable in multiple functions within the same class. As for **init**, it's used to setup default values incase no other functions from within that class are called.

[share](/a/12552203)|[improve this answer](/posts/12552203/edit)

[edited Jul 2 '14 at 19:27](/posts/12552203/revisions)

![](https://i.stack.imgur.com/z7Qy0.gif?s=32&g=1)

[paintedcones](/users/2548192/paintedcones)

141110

answered Sep 23 '12 at 12:02

![](https://www.gravatar.com/avatar/d1ac2cee2a3b758a463bf5f37e120d6b?s=32&d=identicon&r=PG)

[user1675111](/users/1675111/user1675111)

660179

2

 

There is no 'self' keyword in Python. Calling the first parameter 'self' is simply a convention. - [David Anderson](/users/90476/david-anderson) Nov 13 '14 at 22:21

add a comment | 

up vote 9 down vote

Had trouble undestanding this myself. Even after reading the answers here. 

To properly understand the `__init__` method you need to understand self. 

**The self Parameter**

The arguments accepted by the `__init__` method are :

    
    
    def __init__(self, arg1, arg2):
    

But we only actually pass it two arguments :

    
    
    instance = OurClass('arg1', 'arg2')
    

Where has the extra argument come from ?

When we access attributes of an object we do it by name (or by reference). Here instance is a reference to our new object. We access the printargs method of the instance object using instance.printargs.

In order to access object attributes from within the `__init__` method we need a reference to the object.

_**Whenever a method is called, a reference to the main object is passed as the first argument._** By convention you always call this first argument to your methods self.

This means in the `__init__` method we can do :

    
    
    self.arg1 = arg1
    self.arg2 = arg2
    

_**Here we are setting attributes on the object._** You can verify this by doing the following :

    
    
    instance = OurClass('arg1', 'arg2')
    print instance.arg1
    arg1
    

values like this are known as object attributes. **_Here the `__init__` method sets the arg1 and arg2 attributes of the instance._**

source: <http://www.voidspace.org.uk/python/articles/OOP.shtml#the-init-method>

[share](/a/21032703)|[improve this answer](/posts/21032703/edit)

[edited Jan 21 '14 at 8:29](/posts/21032703/revisions)

answered Jan 9 '14 at 22:39

![](https://www.gravatar.com/avatar/b8ae1a67fbe4b611bc0e74ef4788c9b7?s=32&d=identicon&r=PG)

[eee](/users/1751625/eee)

1,359154

add a comment | 

up vote 9 down vote

Try out this code. Hope it helps many C programmers like me to Learn Py.

    
    
    #! /usr/bin/python
    
    class Person:
    
        '''Doc - Inside Class '''
    
        def __init__(self, name):
            '''Doc - __init__ Constructor'''
            self.n_name = name        
    
        def show(self, n1, n2):
            '''Doc - Inside Show'''
            print self.n_name
            print 'Sum = ', (n1 + n2)
    
        def __del__(self):
            print 'Destructor Deleting object - ', self.n_name
    
    p=Person('Jay')
    p.show(2, 3)
    print p.__doc__
    print p.__init__.__doc__
    print p.show.__doc__
    

Output:

`Jay`

`Sum = 5`

`Doc - Inside Class`

`Doc - __init__ Constructor`

`Doc - Inside Show`

`Destructor Deleting object - Jay`

`

[share](/a/16474519)|[improve this answer](/posts/16474519/edit)

[edited May 16 '15 at 16:46](/posts/16474519/revisions)

answered May 10 '13 at 3:03

![](https://i.stack.imgur.com/knczE.jpg?s=32&g=1)

[Jayzcode](/users/2148870/jayzcode)

711710

add a comment | 

up vote 8 down vote

The 'self' is a reference to the class instance

    
    
    class foo:
        def bar(self):
                print "hi"
    

Now we can create an instance of foo and call the method on it, the self parameter is added by Python in this case:

    
    
    f = foo()
    f.bar()
    

But it can be passed in as well if the method call isn't in the context of an instance of the class, the code below does the same thing

    
    
    f = foo()
    foo.bar(f)
    

Interestingly the variable name 'self' is just a convention. The below definition will work exactly the same.. Having said that it is **very strong convention** which should be followed **always**, but it does say something about flexible nature of the language

    
    
    class foo:
        def bar(s):
                print "hi"
    

[share](/a/625174)|[improve this answer](/posts/625174/edit)

answered Mar 9 '09 at 6:09

![](https://www.gravatar.com/avatar/b0b17217693f577c0d297b93edc2cc3c?s=32&d=identicon&r=PG)

[tarn](/users/75276/tarn)

1,6821011

  
 

Why does that say anything about the flexible nature of the language? It just says you can give variables any legal name you choose. How is that different from any other programming language? - [Daniel](/users/864027/daniel) Sep 11 '14 at 21:44

  
 

As I wrote in my answer "bar" is just a function where a class instance is provided as the first parameter. So while "bar" is defined as a method bound to "foo" it could also be called with an instance of some other class. This is not how methods and "this" work in Java for example, although I imagine you see that these are the same concept, functions and some instance context (the instance context being the first parameter in Python and "this" in Java"). Perhaps you can now see the flexibility of the language I was referring to? - [tarn](/users/75276/tarn) Oct 16 '14 at 13:59

  
 

Yeah that does show the flexibility of the language. The way you phrased your answer, it seemed like you were saying that the fact that you could call the "self" variable something else (like `s`) was showing the flexibility of python. - [Daniel](/users/864027/daniel) Oct 19 '14 at 1:30

add a comment | 

up vote 5 down vote

You would be correct, they are object-oriented constructs. Basically `self` is a reference (kind of like a pointer, but `self` is a special reference which you can't assign to) to an object, and `__init__` is a function which is called to initialize the object - that is, set the values of variables etc. - just after memory is allocated for it.

[share](/a/625095)|[improve this answer](/posts/625095/edit)

answered Mar 9 '09 at 5:17

![](https://www.gravatar.com/avatar/8b925a470b95b97bf25240f7a274d611?s=32&d=identicon&r=PG)

[David Z](/users/56541/david-z)

63.3k10144184

add a comment | 

up vote 4 down vote

  1. **`__init__`** is basically a function which will **"initialize"**/**"activate"** the properties of the class for a specific object, once created and matched to the corresponding class..
  2. **`self`** represents that object which will inherit those properties.

[share](/a/32386319)|[improve this answer](/posts/32386319/edit)

[edited Jan 27 at 23:54](/posts/32386319/revisions)

![](https://www.gravatar.com/avatar/49aa7c65c89ac4d7eab47391e3fb4dd4?s=32&d=identicon&r=PG)

[saladi](/users/2320823/saladi)

475216

answered Sep 3 '15 at 22:19

![](https://i.stack.imgur.com/lEhSE.jpg?s=32&g=1)

[George Zafiris](/users/4141689/george-zafiris)

54739

add a comment | 

up vote 3 down vote

Section 9.3 in the following Python tutorial gives a short introduction to the basic elements of a Python class: class variables, class methods and the roles of **init** and **self**.

<https://docs.python.org/2/tutorial/classes.html>

[share](/a/28946924)|[improve this answer](/posts/28946924/edit)

answered Mar 9 '15 at 16:23

![](https://www.gravatar.com/avatar/920c75ef17e199b07c7eebbc8d4201e2?s=32&d=identicon&r=PG&f=1)

[Vivek](/users/4199462/vivek)

692

add a comment | 

up vote 2 down vote

In this code:

`class Cat: def __init__(self, name): self.name = name def info(self): print 'I am a cat and I am called', self.name`

Here `__init__` acts as a constructor for the class and when an object is instantiated, this function is called. `self` represents the instantiating object.

`c = Cat('Kitty') c.info()`

The result of the above statements will be as follows:

`I am a cat and I am called Kitty`

[share](/a/32214839)|[improve this answer](/posts/32214839/edit)

answered Aug 25 '15 at 22:02

![](https://www.gravatar.com/avatar/7de4d6eea76465976c605b08cbed7efc?s=32&d=identicon&r=PG&f=1)

[Anagha](/users/4820929/anagha)

211

add a comment | 

up vote 0 down vote

Here, the guy has defined by the very pretty way and easy way. <https://www.jeffknupp.com/blog/2014/06/18/improve-your-python-python-classes-and-object-oriented-programming/>

Read above link as a reference to this:

> `self`? So what's with that self parameter to all of the Customer methods? What is it? Why, it's the instance, of course! Put another way, a method like withdraw defines the instructions for withdrawing money from some abstract customer's account. Calling jeff.withdraw(100.0) puts those instructions to use on the jeff instance.
> 
> So when we say def withdraw(self, amount):, we're saying, "here's how you withdraw money from a Customer object (which we'll call self) and a dollar figure (which we'll call amount). self is the instance of the Customer that withdraw is being called on. That's not me making analogies, either. jeff.withdraw(100.0) is just shorthand for Customer.withdraw(jeff, 100.0), which is perfectly valid (if not often seen) code.
> 
> **init** self may make sense for other methods, but what about **init**? When we call **init**, we're in the process of creating an object, so how can there already be a self? Python allows us to extend the self pattern to when objects are constructed as well, even though it doesn't exactly fit. Just imagine that jeff = Customer('Jeff Knupp', 1000.0) is the same as calling jeff = Customer(jeff, 'Jeff Knupp', 1000.0); the jeff that's passed in is also made the result.
> 
> This is why when we call **init**, we initialize objects by saying things like self.name = name. Remember, since self is the instance, this is equivalent to saying jeff.name = name, which is the same as jeff.name = 'Jeff Knupp. Similarly, self.balance = balance is the same as jeff.balance = 1000.0. After these two lines, we consider the Customer object "initialized" and ready for use.
> 
> **Be careful what you `__init__`**
> 
> After **init** has finished, the caller can rightly assume that the object is ready to use. That is, after jeff = Customer('Jeff Knupp', 1000.0), we can start making deposit and withdraw calls on jeff; jeff is a fully-initialized object.

[share](/a/31988134)|[improve this answer](/posts/31988134/edit)

answered Aug 13 '15 at 12:22

![](https://www.gravatar.com/avatar/60e144ea15d38f8e476bd8fb009418a5?s=32&d=identicon&r=PG&f=1)

[Laxmikant](/users/4881948/laxmikant)

18711

add a comment | 

