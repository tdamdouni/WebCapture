# Less is more: language features by Mark Seemann

_Captured: 2016-07-14 at 09:28 from [blog.ploeh.dk](http://blog.ploeh.dk/2015/04/13/less-is-more-language-features/)_

_Many languages have redundant features; progress in language design includes removing those features._

(This post is also [available in Japanese](http://postd.cc/less-is-more).) 

There are many programming languages, and new ones are being introduced all the time. Are these languages better than previous languages? Obviously, that's impossible to answer, since there's no clear measurement of what constitutes a 'better' programming language. 

Still, if you look at a historical trend, it looks as though one way to make a better language is to identify a redundant language feature, and design a new language that doesn't have that feature. 

> "perfection is attained not when there is nothing more to add, but when there is nothing more to remove." \- Antoine de Saint Exupéry 

In this article, you'll see various examples of language features that have already proven to be redundant, and other features where we are seeing strong indications that they are redundant. 

**Limitless ways to shoot yourself in the foot.**

When the first computers were created, programs had to be written in machine code or assembly language. In machine code, you can express everything the CPU can do, because the machine code is written it terms of a CPU's instruction set. While it's possible to write correct programs in machine code, you can also write a lot of incorrect programs, including programs that crash horribly, or perhaps even destroy the machine on which they are running. 

You're most likely used to writing code in a higher-level language, but even so, if you share my experience with this, you'll agree that it takes a lot of trial and error to get things right. For every correct program, there are many incorrect variations. The set of incorrect programs is much bigger than the set of correct programs. 

With machine code, you have limitless ways to create incorrect programs. Yes: you can express everything the CPU can execute, but most of it will be incorrect. Thus, the set of valid programs is a small subset of the set of all possible instructions. 

![The set of all valid programs, inside the much larger set of all possible instructions.](/content/binary/less-is-more-language-features-figure-01.png)

Early computer programmers quickly discovered that writing in machine code was extremely error-prone, and the code was also as unreadable as it could be. One way to address this problem was to introduce assembly language, but it didn't solve the underlying problems: most assembly languages were just 'human-readable' one-to-one mappings over machine code, so you still have unlimited ways to express incorrect programs. 

**High-level languages**

After having suffered with machine code and assembly language for some time, programmers figured out how to express programs in high-level languages. The first programming languages aren't in much use today, but a good example of a 'low-level' high-level language still in use today is C. 

![The set of all valid programs, inside the much larger set of all possible instructions, with the overlay of all possible instructions in a high-level language.](/content/binary/less-is-more-language-features-figure-02.png)

In C, you can express almost all valid programs. There are still tons of ways to write incorrect programs that will crash the program (or the computer), but since the language is an abstraction over machine code, there are instructions you can't express. Most of these are invalid instruction sequences anyway, so it's for the better. 

Notice what happened: moving from machine code to a high-level programming language removes a feature of the language. In machine code, you can express _anything_; in a high-level language, there are things you can't express. You're okay with that, because the options that were taken away from you were bad for you. 

**GOTO**

In 1968, Edsger Dijkstra published his (in)famous paper _Go To Statement Considered Harmful_. In it, he argued that the GOTO statement was an bad idea, and that programs would be 'better' without the GOTO statement. This sparked a decade-long controversy, but these days we've come to understand that Dijkstra was right. Some of the most popular languages in use today (e.g. Java and JavaScript) don't have GOTO at all. 

![The set of all valid programs, inside the much larger set of all possible instructions, with the overlay of all possible instructions in a high-level language without GOTO.](/content/binary/less-is-more-language-features-figure-03.png)

Since GOTO has turned out to be an entirely redundant language feature, a language without it doesn't limit your ability to express _valid_ programs, but it does limit your ability to express _invalid_ programs. 

Do you notice a pattern? 

Take something away, and make an improvement. 

There's nothing new about this; [Robert C. Martin told us that years ago](https://skillsmatter.com/skillscasts/2323-bobs-last-language). 

You can't just arbitrarily take away _anything_, because that may constrain you in such a way that there are valid programs you can no longer write: 

![The set of all valid programs, inside the much larger set of all possible instructions, with the overlay of a language that takes away the wrong features.](/content/binary/less-is-more-language-features-figure-04.png)

You have to take away the _right_ features. 

**Exceptions**

Today, everyone seems to agree that errors should be handled via some sort of exception mechanisms; at least, everyone can agree that _error codes_ are _not_ the way to go (and I agree). We need something richer than error codes, and something that balances usefulness with robustness. 

The problem with exceptions is that this mechanism is really only [GOTO statements in disguise](http://c2.com/cgi/wiki?DontUseExceptionsForFlowControl) \- and we've already learned that GOTO is considered harmful. 

A better approach is to use a [sum type](http://en.wikipedia.org/wiki/Tagged_union) to indicate _either_ [success or failure in a composable form](http://fsharpforfunandprofit.com/posts/recipe-part2). 

**Pointers**

As Robert C. Martin also pointed out, in older languages, including C and C++, you can manipulate pointers, but as soon as you introduce polymorphism, you no longer need 'raw' pointers. Java doesn't have pointers; JavaScript doesn't do pointers; C# _does_ allow you to use pointers, but I've personally never needed them outside of interop with the Windows API. 

As these languages have demonstrated, you don't need access to pointers in order to be able to pass values by reference. Pointers can be abstracted away. 

**Numbers**

Most strongly typed languages give you an opportunity to choose between various different number types: bytes, 16-bit integers, 32-bit integers, 32-bit _unsigned_ integers, single precision floating point numbers, etc. That made sense in the 1950s, but is rarely important these days; we waste time worrying about the micro-optimization it is to pick the right number type, while we lose sight of the bigger picture. As [Douglas Crockford explains, in JavaScript there's only a _single_ number type, which is a great idea - just too bad it's the wrong single number type](http://hanselminutes.com/396/bugs-considered-harmful-with-douglas-crockford). 

![The set of all valid programs, inside the much larger set of all possible instructions, with the overlay of a language with a single, sane number type.](/content/binary/less-is-more-language-features-figure-05.png)

With the modern computer resources we have today, a programming language that would restrict you to a single, sane number type would be superior to the mess we have today. 

**Null pointers**

Nulls are one of the most misunderstood language constructs. There's nothing wrong with the concept of a value that may or may not be present. Many great programming languages have this concept. In Haskell, it's called _Maybe_; in F#, it's called _option_; in T-SQL it's called _null_. What's common in all these languages is that it's an _opt-in_ language feature: you can declare a value as being 'nullable', but by default, _it isn't_ (nullable). 

However, due to [Tony Hoare's self-admitted billion-dollar mistake](http://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare), mainstream languages have null pointers: C, C++, Java, C#. The problem isn't the _concept_ of 'null', but rather that everything _can_ be null, which makes it impossible to distinguish between the cases where null is an appropriate and expected value, from the cases where null is a defect. 

Design a language without null pointers, and you take away the ability to produce null pointer exceptions. 

![The set of all valid programs, inside the much larger set of all possible instructions, with the overlay of a language without null pointers.](/content/binary/less-is-more-language-features-figure-06.png)

If Tony Hoare is correct that null pointers cost billions of dollars in the last few decades, getting rid of that source of defects can save you lots of money. From Turing-complete languages like T-SQL, Haskell, and F# we know that you can express all valid programs without null pointers, while a huge source of defects is removed. 

**Mutation**

A central concept in Procedural, Imperative, and Object-Oriented languages is that you can change the value of a variable while executing your program. That's the reason it's called a _variable_. This seems intuitive, since a CPU contains registers, and what you actually do when you execute a program is that you move values in and out of those registers. It's also intuitive because the purpose of most programs is to change the state of the world: Store a record in a database. Send an email. Repaint the screen. Print a document. Etc. 

However, it turns out that mutation is also a large source of defects in software, because it makes it much harder to reason about code. Consider a line of C# code like this: 

    
    
    var r = this.mapper.Map(rendition);

When the `Map` method returns, has `rendition` been modified? Well, if you follow [Command Query Separation](http://en.wikipedia.org/wiki/Command%E2%80%93query_separation), it shouldn't, but the only way you can be sure is to review the implementation of the Map method. What if that method exhibits the same problem, by calling into other methods that _could_ mutate the state of the application? There's nothing in C# (or Java, or JavaScript, etc.) that prevents this from happening. 

In a complicated program with a big call stack, it's impossible to reason about the code, because _everything_ could mutate, and once you have tens or hundreds of variables in play, you can no longer keep track of them. Did the `isDirty` flag change? Where? What about the `customerStatus`? 

Imagine taking away the ability to mutate state: 

![The set of all valid programs, inside the much larger set of all possible instructions, with the overlay of the set of possible instructions in a language without mutation.](/content/binary/less-is-more-language-features-figure-07.png)

Most languages don't completely take away this ability, but as Haskell (a Turing complete language) demonstrates, it's possible to write any program without implicit state mutation. 

At this point, many people might object that Haskell is too difficult and unintuitive, but to me, that kind of argumentation is reminiscent of the resistance to removing GOTO. If you are used to relying on GOTO, you have to learn alternative ways to model the same behaviour without GOTO. Likewise, if you are used to relying on state mutation, you have to learn alternative ways to model the same behaviour without state mutation. 

**Reference Equality**

In Object-Oriented languages like C# and Java, the default equality comparison is Reference Equality. If two variables point to the same memory address, the variables are considered equal. If two variables have all identical constituent values, but point to two different memory addresses, they are considered different. That's not intuitive, and many software defects are caused by this. 

What if you take away Reference Equality from a language? 

![The set of all valid programs, inside the much larger set of all possible instructions, with the overlay of the set of possible instructions in a language without Reference Equality.](/content/binary/less-is-more-language-features-figure-08.png)

What if all data structures instead had [Structural Equality](http://en.wikipedia.org/wiki/Relational_operator)? 

This one I'm not entirely sure about, but in my experience, I almost never need Reference Equality. For Basic Correctness you never need it, but I wonder if you may need the occasional reference comparison in order to implement some performance optimizations... Still, it wouldn't hurt to switch the defaults so that Structural Equality was the default, and there was a special function you could invoke to compare two variables for Reference Equality. 

**Inheritance**

Even in 2015, inheritance is everywhere, although it's more than 20 years ago the Gang of Four taught us to [favor object composition over class inheritance](http://amzn.to/XBYukB). It turns out that there's nothing you can do with inheritance that you can't also do with composition with interfaces. The converse doesn't hold in languages with single inheritance: there are things you can do with interfaces (such as implement more than one), that you can't do with inheritance. Composition is a superset of inheritance. 

This isn't just theory: in my experience, I've been able to avoid inheritance in the way I've designed my code for many years. Once you get the hang of it, it's not even difficult. 

**Interfaces**

Many strongly typed languages (for example Java and C#) have interfaces, which is a mechanism to implement polymorphism. In this way, you can bundle various operations together as methods on an interface. However, one of [the consequences of SOLID](http://www.shareasale.com/r.cfm?u=1017843&b=611266&m=53701&afftrack=&urllink=www%2Epluralsight%2Ecom%2Fcourses%2Fencapsulation%2Dsolid) is that you should favour [Role Interfaces](http://martinfowler.com/bliki/RoleInterface.html) over [Header Interfaces](http://martinfowler.com/bliki/HeaderInterface.html), and as I've previously explained, [the logical conclusion is that all interfaces should only have a single member](http://blog.ploeh.dk/2014/03/10/solid-the-next-step-is-functional). 

When interfaces only have a single member, the interface declaration itself tends to mostly be in the way - the only thing that matters is the operation. [In C#, you could just use a delegate instead](http://blog.ploeh.dk/2009/05/28/DelegatesAreAnonymousInterfaces), and even Java has lambdas now. 

There's nothing new about this. Functional languages have used _functions_ as the basic compositional unit for years. 

In my experience, you can model everything with single-member interfaces, which also implies that you can model everything with functions. Again, this isn't really surprising, since functional languages like Haskell are Turing complete too. 

It's possible to get by without interfaces. In fact, [Robert C. Martin finds them harmful](http://blog.cleancoder.com/uncle-bob/2015/01/08/InterfaceConsideredHarmful.html). 

**Reflection**

If you've ever done any sort of meta-programming in .NET or Java, you probably know what Reflection is. It's a set of APIs and language or platform features that enable you to inspect, query, manipulate, or emit code. 

_Meta-programming_ is an indispensable tool, so I'd be sorry to lose it. However, Reflection isn't the _only_ way to enable meta-programming. Some languages are [homoiconic](http://en.wikipedia.org/wiki/Homoiconicity), which means that a program in such languages is structured as data, which itself can be queried and manipulated like any other data. Such languages don't need Reflection as a feature, because meta-programming is baked into the language, so to speak. 

In other words: Reflection is a language feature aimed at the goal of meta-programming. If meta-programming can be achieved via homoiconicity instead, it would imply that Reflection is a redundant feature. 

**Cyclic Dependencies**

While it may be true that null pointers are the biggest single source of software defects, in my experience the greatest single source of unmaintainable code is _coupling_. One of the most problematic types of coupling is cyclic dependencies. In languages like C# and Java, cyclic dependencies are almost impossible to avoid. 

Here's one of my own mistakes that I only discovered because I started to look for it: in the otherwise nice and maintainable [AtomEventStore](https://github.com/GreanTech/AtomEventStore), there's an interface called [IXmlWritable](https://github.com/GreanTech/AtomEventStore/blob/master/AtomEventStore/IXmlWritable.cs): 

    
    
    public interface IXmlWritable
    {
        void WriteTo(XmlWriter xmlWriter, IContentSerializer serializer);
    }

As you can tell, the WriteTo method takes an [IContentSerializer](https://github.com/GreanTech/AtomEventStore/blob/master/AtomEventStore/IContentSerializer.cs) argument. 

    
    
    public interface IContentSerializer
    {
        void Serialize(XmlWriter xmlWriter, object value);
     
        XmlAtomContent Deserialize(XmlReader xmlReader);
    }

Notice that the Deserialize method returns an [XmlAtomContent](https://github.com/GreanTech/AtomEventStore/blob/master/AtomEventStore/XmlAtomContent.cs) value. How is XmlAtomContent defined? Like this: 

    
    
    public class XmlAtomContent : IXmlWritable

Notice that it implements IXmlWritable. Oh, dear! 

Although I'm _constantly_ on the lookout for these kinds of things, that one slipped right past me. 

In F# (and, I believe, OCaml), on the other hand, this wouldn't even have compiled! 

While F# has a way to introduce small cycles _within_ a module using the `and` and `rec` keywords, there are no accidental cycles. You have to explicitly use those keywords to enable limited cycles - and there's no way to define cycles that span modules or libraries. 

What an excellent protection against tightly coupled code! Take away the ability to (inadvertently) introduce Cyclic Dependencies, and get a better language! 

![The set of all valid programs, inside the much larger set of all possible instructions, with the overlay of the set of possible instructions in a language that disallows cycles.](/content/binary/less-is-more-language-features-figure-09.png)

This has even been shown to work in the wild: [Scott Wlaschin examined C# and F# projects for cycles](http://fsharpforfunandprofit.com/posts/cycles-and-modularity-in-the-wild), and found that F# projects have fewer and smaller cycles than C# projects. This analysis was later [enhanced and corroborated by Evelina Gabasova](http://evelinag.com/blog/2014/06-09-comparing-dependency-networks). 

**Summary**

What I've tried to illustrate in this article is that there are many ways in which you could make a better language by taking away a particular feature from an existing language. Take away a redundant feature, and you'll still have a Turing complete language that can do (close to) anything, but with fewer options for shooting yourself in the foot. 

Perhaps the ultimate programming language is a language _without_: 

  * GOTO
  * Exceptions
  * Pointers
  * Lots of specialized number types
  * Null pointers
  * Mutation
  * Reference equality
  * Inheritance
  * Interfaces
  * Reflection
  * Cyclic dependencies

Have I identified all possible redundant features? Most likely not, so here's a great opportunity for language designers to define an even better language, by finding something new to take away! 

**Update September 14 2015:** This article sparked a [.NET Rocks! episode with even more discussion about this topic](http://www.dotnetrocks.com/default.aspx?showNum=1170). 

* * *
