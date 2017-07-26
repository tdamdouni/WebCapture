# Structure and Interpretation of Computer Programmers

_Captured: 2015-06-16 at 00:14 from [www.sicpers.info](http://www.sicpers.info/)_

The objects that [I've been building up](https://github.com/iamleeg/Objective-Swift) over the last few posts have arbitrarily broad behaviours. They can respond to any selector drawn from the set of all possible strings.

As with all art, beauty is produced by imposing constraints. An important class (pardon the pun) of objects only has a meaningful response to one selector (`value` or, if it takes an additional argument, `value:`) which causes the object to do the one thing it knows how and return a result.

In many object-oriented programming circles, including the Smalltalk world, these objects are called _blocks_. They're useful because they enable multiple uses of the same algorithm to be extracted into a single place, with the block customising the significant activity that happens in the algorithm. As an example, iterating an array to square numbers and iterating an array to load images from paths both involve iterating an array. The algorithm that iterates an array can be expressed in a form that accepts a block that does the work: squaring some numbers or loading some images.

Without going in to the details of the implementation (which is a collection of classes in the Objective-Swift system), here's how a block could be used:

    let myArray = newObject(NSArray(Integer(1, proto: o),Integer(2, proto: o),Integer(3, proto: o),Integer(4, proto: o)))let evens =(myArray,"filter:")✍OneArgBlock({ obj inreturn(ℹ︎(obj)!%2)==0?True:False}, proto: o)ℹ︎(evens→"count")// 2((evens,"objectAtIndex:")✍Integer(0, proto: o))// "2"((evens,"objectAtIndex:")✍Integer(1, proto: o))// "4"

The `NSArray->filter:` selector takes a block, and for each element in the array it sends the `value:` message with the element as the argument. In fact, it passes _another_ block to the result of this block. Both `True` and `False` respond to the `ifTrue:` message. `True->ifTrue:` executes its argument, `False->ifTrue:` doesn't.

Now we already have a name for the concept of an object that does exactly one thing, returning some result based on its input parameters. That's a function. Yes, we finally got there:

## Swiftception

So just as Object-Oriented Programming was a restricted application of a subset of Functional Programming, we can see Functional Programming as a restricted application of a subset of Object-Oriented Programming.

And that's pretty much the point of this series of posts. These two ways of thinking about computer programs get you to the same place, as long as you apply the thinking. Neither is a silver bullet, neither is subsumed nor obsoleted by the other.

## Coda

Now imagine a block that takes a selector and returns another block…

So far, Objective-Swift objects have used prototypical inheritance, in which they supply some methods but also know about another object to which they can forward messages they don't understand themselves. This pattern is used in languages like Self, JavaScript and Io but is not common to other languages that also call themselves object-oriented programming languages.

Most OO languages have the idea of a "class" that supplies the methods for each object. An object knows that it "is a" specific realisation of its class, so when it receives a message it can look up the corresponding method in that class's method table.

## Like this.
    
    
    typealias Class=Dictionary// define a "Non-Standalone" Object that relies on a class for its methods.letNSObject:Class=["description": IMP.description({ _ inreturn"An NSObject"})]
    
    func newObject(isa :Class)->Object{return{ aSelector iniflet anImplementation = isa[aSelector]{return anImplementation
        }else{return IMP.methodMissing({ _ inprint("Does not recognize selector \(aSelector)")returnnil})}}}let anObject = newObject(NSObject)(anObject)// "An NSObject"

Objects returned by the `newObject()` function look up their methods in their class dictionary, a table of method implementations for the corresponding selectors.

## Not like that.

Mapping things to other things, that's a function, isn't it? And indeed there already _is_ a type of function that takes selectors to methods, the object. A class should just be an object. Let's try that again.
    
    
    typealias Class=ObjectletNSObject:Class={ aSelector inswitch aSelector {case"description":return IMP.description({ _ inreturn"An NSObject"})default:return IMP.methodMissing({ _ inprint("Instance does not recognize selector \(aSelector)")returnnil})}}
    
    func newObject(isa :Class)->Object{return{ aSelector inreturn isa(aSelector)}}let anObject = newObject(NSObject)(anObject)// "An NSObject"

Great. Classes are objects, just as we're used to. And indeed, a class could get its own methods from _another_ class: a metaclass.

Notice that class-based objects walk and quack like the earlier, prototypical objects, so interoperate completely. That's the point of message passing. No object needs to know how any other object _works_, just that it will respond to messages.

That's what makes all of the bridges that let other languages interoperate with Objective-C. As long as `objc_msgSend()` can find your code and run it, we're all good. In Objective-Swift, as long as passing you a selector gives me an `IMP`, we're all good.

## Instance variables.

Methods defined by classes should be able to see the object's instance variables. The instance variables should, per their definition, be unique to each instance. However the best place to define them is in the class, for three reasons:

  1. The class knows which instance variables its methods expect to be present.
  2. The class's constructor function captured the values (or the initial values, if they're mutable) of the instance variables.
  3. If I'm subclassing, I want to be able to add the subclass's instance variables to the superclass's, without having to redefine the whole shebang.

So a class should tell its objects what instance variables it needs, and the values. Now, how should an instance look up its instance variables? We need to go from the name of an instance variable to its value, and I'll save us both some embarrassment by cutting straight to the conclusion that an object is a great way to do this.

Each object in the class-based system will therefore be composed of two others: the class encapsulates what the object _is_ and the methods it responds to, while the instance variable store encapsulates what the object _is made of_ and what variables it has. Both are accessed through selectors, in a design choice that follows Eiffel and its Uniform-Access Principle (and the later Self language).

The same selector cannot refer both to a method and an ivar, because they're both in the same namespace. One of them has to win, and in this case I've chosen the instance variable lookup to win.

Here's a non-standalone version of `Point`, with its two instance variables. In the code shown here, `o` is a previously-defined object on which all methods are missing.
   
    func NSPoint(x:Int, y:Int)->Class{let superclass =NSObjectlet ivars:Object={ variableName inswitch variableName {case"x":return.method({_ inreturnInteger(x, proto: o)})case"y":return.method({_ inreturnInteger(y, proto: o)})default:return(superclass→"instanceVariables")!(variableName)}}let thisClass:Class={ aSelector inswitch aSelector {case"instanceVariables":return.method({_ inreturn ivars})case"distanceFromOrigin":return.method({(this, _cmd, args:Object...)inlet thisX =ℹ︎(this→"x")!let thisY =ℹ︎(this→"y")!let distance = sqrt(Double(thisX*thisX + thisY*thisY))returnInteger(Int(distance), proto: o)})default:return superclass(aSelector)}}return thisClass
    }let aPoint = newObject(NSPoint(3,y:4))(aPoint)// "An NSObject"(aPoint→"x")// "3"(aPoint→"distanceFromOrigin")// "5"

## Super calls.

You can see that `NSPoint` is a subclass of `NSObject`, although this isn't amazingly useful. `NSPoint` gets all zero of `NSObject`'s instance variables, and the not-particularly-descriptive `description` method.

In what might be the worst design choice of this blog, I'll say that a 3D point is a specialisation of a 2D point. I'll need to override `distanceFromOrigin` to calculate the distance in three dimensions, but I can use the result from the superclass's two-dimensional calculation to do this.

As with Objective-C, this will require a _different_ method lookup system, one that says "ask your superclass" instead of "ask yourself". To do this, the object must know what its superclass _is_: it can ask its class. Here is a new method on `NS3DPoint`:
   
    case"superclass":return.method({ _ inreturn superclass })

Now, because I'm _really_ running out of ideas on how to name these operators, here are some doubly-long operators that call into the superclass for an object:
   
    infix operator....{}
    
    func ....(receiver:Object?, _cmd:Selector)-> IMP?{
      guard letthis= receiver else{returnnil}let method =(this→"superclass")!(_cmd)switch(method){case IMP.methodMissing(let f):return f(this, _cmd)...._cmd
      default:return method
      }}
    
    infix operator→→{}
    
    func →→(receiver:Object?, _cmd:Selector)->Object?{
      guard let imp = receiver...._cmd else{returnnil}switch imp {case.method(let f):return f(receiver!, _cmd)default:returnnil}}

Now, with all of this notation in place, it's possible to create a method `NS3DPoint->distanceFromOrigin` that both overrides its parent method, and uses that overridden method in its calculation. Here's the method:

    case"distanceFromOrigin":return.method({(this, _cmd, args:Object...)inlet twoDDistance =ℹ︎(this→→"distanceFromOrigin")!let thisZ =ℹ︎(this→"z")!let distance = sqrt(Double(twoDDistance*twoDDistance + thisZ*thisZ))returnInteger(Int(distance), proto: o)})

Here it is in use:

    let anotherPoint = newObject(NS3DPoint(10, y:12, z:14))(anotherPoint→"distanceFromOrigin")// "20"

## Conclusion

In many "classical" object-oriented programming systems, classes are just objects, which instances can use to find the methods they respond to. If you've already got objects that don't use classes, it's possible to make objects that do use classes by giving each object a class object. You need somewhere to hold the instance variables for an object, and it happens that objects are good for that too.

More useful to notice is that objects are really just a way to do late binding of functions to their names. It doesn't really matter what rules you use, as long as the result is a map of names to functions you've got yourself an object that will work with other objects.

I didn't realise this at the time, the previous entry wasn't the last Objective-Swift post.

The inheritance mechanism in [ObjS](http://www.sicpers.info/2015/05/dynamic-method-dispatch-in-object-oriented-programming-in-functional-programming-in-swift/) is _prototypical_, meaning that an object inherits from a single other object rather than getting its behaviour from a class. This is the same system that Self and languages that, um, inherit its approach use.

This form of inheritance gives us two capabilities: decorating an object by attaching new methods, or updating an object by shadowing existing methods. And _that_ means that setting a variable can be mimicked by returning an object where the accessor for that variable has been overridden. So in fact the objects in this system won't be mutable at all, but they will have mutators that return replacement values.

It sounds weird, but there are reasons to really do this. In Postscript, you can mimic variables by creating named functions that just push a value onto the stack. Rather than mutating the data, you "set" the variable by rebinding the name to a function that pushes the updated value.

## Digression: updating the dispatch system

In rewriting setters to be immutable I also noticed it was possible to consolidate the "accessor" and "mutator" implementation types into a single type, using variadic arguments. I have genuinely no idea why I didn't realise that before, when the type of an ObjC method is usually expected to be `(id, SEL, id...) -> id`.

    enum IMP {case method((Selector->IMP,Selector,Selector->IMP...)->(Selector->IMP)?)case asInteger((Selector->IMP,Selector,Selector->IMP...)->Int?)case methodMissing((Selector->IMP,Selector,Selector->IMP...)->(Selector->IMP)?)case description((Selector->IMP,Selector,Selector->IMP...)->String?)}

The `asInteger` and `description` types gain variadic arguments but still need to be present so you can exit the O-O type system and get back to Swift types. For the moment, `methodMissing` is still modelled as a separate case in the enumeration, even though it has the same type as a regular method.

## Mutation as a function

Given an object, a selector to override, and the replacement value, return a new object that will return that value when messaged with that selector.

    infix operator☞{}
    
    func mutate(receiver:Object, selector:Selector, value:Object)->Object{return{ _cmd inswitch(_cmd){case selector:return.method({ _ inreturn value })default:return receiver(_cmd)}}}
    
    func ☞(message:(receiver:Object?, selector:Selector), value:Object)->Object?{iflet receiver = message.receiver {return mutate(receiver, message.selector, value)}else{returnnil}}

Taking the `Point` objects from the [further advances](http://www.sicpers.info/2015/06/further-advances-in-objective-swift/) post, but deleting their mutators, this can be used to make updated objects.

    let p =Point(3,4, o)(p)// (3,4)let p2 =(p,"x")☞(Integer(1,o))(p2)// (1,4)

## Mutation as a method

The same function can be used in the implementation of an Objective-Swift method. Here's the `setY:` method on `Point`s:

    return IMP.method({(this, aSelector, args :Object...)inreturn(this,"y")☞args[0]})

Now a bit of notation to make calling mutator methods easier (I'm starting to run out of reasonable symbols):

    infix operator✍{}
    
    func ✍(message:(receiver:Object?, selector:Selector), value:Object)->Object?{iflet imp = message.receiver..message.selector {switch imp {case.method(let f):return f(message.receiver!, message.selector, value)default:returnnil}}else{returnnil}}
    
    
    let p3 =(p2,"setY:")✍(Integer(42, o))(p3)// (1,42)

## Fork me

I have put the current playground (which is written for the Swift 1.2 compiler, because I'm risk averseold fashioned) [on GitHub](https://github.com/iamleeg/Objective-Swift).

![Life](http://www.sicpers.info/wp-content/uploads/2015/05/life.png)
