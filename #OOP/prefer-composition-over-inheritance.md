# Prefer composition over inheritance?

_Captured: 2017-08-08 at 18:29 from [stackoverflow.com](https://stackoverflow.com/questions/49002/prefer-composition-over-inheritance#)_

If you understand the difference, it's easier to explain.

## Procedural Code

An example of this is PHP without the use of classes (particularly before PHP5). All logic is encoded in a set of functions. You may include other files containing helper functions and so on and conduct your business logic by passing data around in functions. This can be very hard to manage as the application grows. PHP5 tries to remedy this by offering more object oriented design.

## Inheritance

This encourages the use of classes. Inheritance is one of the three tenets of OO design (inheritance, polymorphism, encapsulation).
    
    
    class Person {
       String Title;
       String Name;
       Int Age
    }
    
    class Employee : Person {
       Int Salary;
       String Title;
    }
    

This is inheritance at work. The Employee "is a" Person or inherits from Person. All inheritance relationships are "is-a" relationships. Employee also shadows the Title property from Person, meaning Employee.Title will return the Title for the Employee not the Person.

## Composition

Composition is favoured over inheritance. To put it very simply you would have:
    
    
    class Person {
       String Title;
       String Name;
       Int Age;
    
       public Person(String title, String name, String age) {
          this.Title = title;
          this.Name = name;
          this.Age = age;
       }
    
    }
    
    class Employee {
       Int Salary;
       private Person person;
    
       public Employee(Person p, Int salary) {
           this.person = p;
           this.Salary = salary;
       }
    }
    
    Person johnny = new Person ("Mr.", "John", 25);
    Employee john = new Employee (johnny, 50000);
    

Composition is typically "has a" or "uses a" relationship. Here the Employee class has a Person. It does not inherit from Person but instead gets the Person object passed to it, which is why it "has a" Person.

## Composition over Inheritance

Now say you want to create a Manager type so you end up with:
    
    
    class Manager : Person, Employee {
       ...
    }
    

This example will work fine, however, what if Person and Employee both declared `Title`? Should Manager.Title return "Manager of Operations" or "Mr."? Under composition this ambiguity is better handled:
    
    
    Class Manager {
       public Title;
       public Manager(Person p, Employee e)
       {
          this.Title = e.Title;
       }
    }
    

The Manager object is composed as an Employee and a Person. The Title behaviour is taken from employee. This explicit composition removes ambiguity among other things and you'll encounter fewer bugs.

  


To address this question from a different perspective for newer programmers:

Inheritance is often taught early when we learn object-oriented programming, so it's seen as an easy solution to a common problem.

> I have three classes that all need some common functionality. So if I write a base class and have them all inherit from it, then they will all have that functionality and I'll only need to maintain it in once place.

It sounds great, but in practice it almost never, ever works, for one of several reasons:

  * We discover that there are some other functions that we want our classes to have. If the way that we add functionality to classes is through inheritance, we have to decide - do we add it to the existing base class, even though not every class that inherits from it needs that functionality? Do we create another base class? But what about classes that already inherit from the other base class?
  * We discover that for just one of the classes that inherits from our base class we want the base class to behave a little differently. So now we go back and tinker with our base class, maybe adding some virtual methods, or even worse, some code that says, "If I'm inherited type A, do this, but if I'm inherited type B, do that." That's bad for lots of reasons. One is that every time we change the base class, we're effectively changing every inherited class. So we're really changing class A, B, C, and D because we need a slightly different behavior in class A. As careful as we think we are, we might break one of those classes for reasons that have nothing to do with those classes.
  * We might know why we decided to make all of these classes inherit from each other, but it might not (probably won't) make sense to someone else who has to maintain our code. We might force them into a difficult choice - do I do something really ugly and messy to make the change I need (see the previous bullet point) or do I just rewrite a bunch of this.

In the end, we tie our code in some difficult knots and get no benefit whatsoever from it except that we get to say, "Cool, I learned about inheritance and now I used it." That's not meant to be condescending because we've all done it. But we all did it because no one told us not to.

As soon as someone explained "favor composition over inheritance" to me, I thought back over every time I tried to share functionality between classes using inheritance and realized that most of the time it didn't really work well.

The antidote is the [Single Responsibility Principle](https://en.wikipedia.org/wiki/Single_responsibility_principle). Think of it as a constraint. My class _must_ do one thing. I _must_ be able to give my class a name that somehow describes that one thing it does. (There are exceptions to everything, but absolute rules are sometimes better when we're learning.) It follows that I cannot write a base class called `ObjectBaseThatContainsVariousFunctionsNeededByDifferentClasses`. Whatever distinct functionality I need must be in its own class, and then other classes that need that functionality can depend on that class, _not_ inherit from it.

At the risk of oversimplifying, that's composition - composing multiple classes to work together. And once we form that habit we find that it's much more flexible, maintainable, and testable than using inheritance.

# [Prefer composition over inheritance?](/questions/49002/prefer-composition-over-inheritance)

[Ask Question](/questions/ask)

up vote 1194 down vote favorite

**705**

Why prefer composition over inheritance? What trade-offs are there for each approach? When should you choose inheritance over composition?

[language-agnostic](/questions/tagged/language-agnostic) [oop](/questions/tagged/oop) [inheritance](/questions/tagged/inheritance) [composition](/questions/tagged/composition) [aggregation](/questions/tagged/aggregation)

[share](/q/49002)|[improve this question](/posts/49002/edit)

[edited Mar 22 at 16:23](/posts/49002/revisions)

![](https://www.gravatar.com/avatar/32d2ee92e99e287861b25f508416a787?s=32&d=identicon&r=PG)

[bluefeet](/users/426671/bluefeet)♦

164k40242318

asked Sep 8 '08 at 1:58

![](https://www.gravatar.com/avatar/a92525f049e20db8f4ce3d62f3f0bb2b?s=32&d=identicon&r=PG)

[Readonly](/users/4883/readonly)

105k89182193

1

 

[Prefer Composition Over Inheritance](http://blogs.msdn.com/steverowe/archive/2008/04/28/prefer-composition-over-inheritance.aspx) - [aku](/users/1196/aku) Sep 8 '08 at 2:09

2

 

See also [which class design is better](http://stackoverflow.com/questions/38820/which-class-design-is-better) - [maccullt](/users/4945/maccullt) Sep 10 '08 at 2:22

14

 

There is a good article about that question [here](http://www.javaworld.com/javaworld/jw-11-1998/jw-11-techniques.html?page=1). My personal opinion is that there is no "better" or "worse" principle to design. There is "appropriate" and "inadequate" design for the concrete task. In other words - I use both inheritance or composition, depending on the situation. The goal is to produce smaller code, easier to read, reuse and eventually extend further. - [m_pGladiator](/users/446104/m-pgladiator) Sep 17 '08 at 20:43

  
 

in one sentence inheritance is public if you have a public method and you change it it changes the published api. if you have composition and the object composed has changed you don't have to change your published api. - [Tomer Ben David](/users/2793141/tomer-ben-david) Aug 26 '15 at 11:00

1

 

On Wikipedia see [Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance). - [DavidRR](/users/1497596/davidrr) Oct 27 '15 at 12:53

 |  show **1** more comment

##  34 Answers 34

[ active](/questions/49002/prefer-composition-over-inheritance?answertab=active#tab-top) [ oldest](/questions/49002/prefer-composition-over-inheritance?answertab=oldest#tab-top) [ votes](/questions/49002/prefer-composition-over-inheritance?answertab=votes#tab-top)

1 [ 2 ](/questions/49002/prefer-composition-over-inheritance?page=2&tab=votes#tab-top) [ next ](/questions/49002/prefer-composition-over-inheritance?page=2&tab=votes#tab-top)

up vote 915 down vote

_Prefer composition over inheritance as it is more malleable / easy to modify later, but do not use a compose-always approach._ With composition, it's easy to change behavior on the fly with Dependency Injection / Setters. Inheritance is more rigid as most languages do not allow you to derive from more than one type. So the goose is more or less cooked once you derive from TypeA.

My acid test for the above is: 

  * Does TypeB want to expose the complete interface (all public methods no less) of TypeA such that TypeB can be used where TypeA is expected? Indicates **Inheritance**. 

e.g. A Cessna biplane will expose the complete interface of an airplane, if not more. So that makes it fit to derive from Airplane. 

  * Does TypeB want only some/part of the behavior exposed by TypeA? Indicates need for **Composition.**

e.g. A Bird may need only the fly behavior of an Airplane. In this case, it makes sense to extract it out as an interface / class / both and make it a member of both classes.

**Update:** Just came back to my answer and it seems now that it is incomplete without a specific mention of Barbara Liskov's [Liskov Substitution Principle](http://en.wikipedia.org/wiki/Liskov_substitution_principle) as a test for 'Should I be inheriting from this type?'

[share](/a/53354)|[improve this answer](/posts/53354/edit)

[edited Apr 1 at 14:49](/posts/53354/revisions)

![](https://www.gravatar.com/avatar/a0e79322d4eeec698760a027911e6b19?s=32&d=identicon&r=PG)

[Galilyou](/users/70289/galilyou)

4,48494565

answered Sep 10 '08 at 3:04

![](https://www.gravatar.com/avatar/69772f0246d5013d72703967b8761e89?s=32&d=identicon&r=PG)

[Gishu](/users/1695/gishu)

89.2k38189272

55

 

The second example is straight out of the Head First Design Patterns ([amazon.com/First-Design-Patterns-Elisabeth-Freeman/dp/…](http://www.amazon.com/First-Design-Patterns-Elisabeth-Freeman/dp/0596007124)) book :) I would highly recommend that book to anyone who was googling this question. - [Jeshurun](/users/473637/jeshurun) Jun 22 '11 at 4:59

1

 

It's very clear, but it may miss something : "Does TypeB want to expose the complete interface (all public methods no less) of TypeA such that TypeB can be used where TypeA is expected?" But what if this is true, and TypeB also expose the complete interface of TypeC ? And what if TypeC hasn't been modeled yet ? - [Tristan](/users/668455/tristan) Aug 26 '11 at 12:04

3

 

You allude to what I think should be the most basic test: "Should this object be usable by code which expects objects of (what would be) the base type". If the answer is yes, the object _must_ inherit. If no, then it probably should not. If I had my druthers, languages would provide a keyword to refer to "this class", and provide a means of defining a class which should behave just like another class, but not be substitutable for it (such a class would have all "this class" references replaced with itself). - [supercat](/users/363751/supercat) Dec 8 '11 at 16:16

13

 

@Alexey - the point is 'Can I pass in a Cessna biplane to all clients that expect an airplane without surprising them?'. If yes, then chances are you want inheritance. - [Gishu](/users/1695/gishu) Oct 28 '12 at 4:18

6

 

I'm actually struggling to think of any examples where inheritance would have been my answer, I often find aggregation, composition and interfaces result in more elegant solutions. Many of the above examples could possibly be better explained using those approaches... - [Stuart Wakefield](/users/459516/stuart-wakefield) Nov 23 '12 at 11:33

 |  show **15** more comments

up vote 308 down vote

Think of containment as a **has a** relationship. A car "has an" engine, a person "has a" name, etc.

Think of inheritance as an **is a** relationship. A car "is a" vehicle, a person "is a" mammal, etc.

I take no credit for this approach. I took it straight from the [Second Edition of Code Complete](http://rads.stackoverflow.com/amzn/click/0735619670) by [Steve McConnell](http://blogs.construx.com/blogs/stevemcc/default.aspx), _Section 6.3_.

[share](/a/49016)|[improve this answer](/posts/49016/edit)

[edited Sep 8 '08 at 2:15](/posts/49016/revisions)

answered Sep 8 '08 at 2:09

![](https://i.stack.imgur.com/yOehV.png?s=32&g=1)

[Nick Zalutskiy](/users/1959/nick-zalutskiy)

8,38273643

89

 

This is not always a perfect approach, it's simply a good guideline. the Liskov Substitution Principle is much more accurate (fails less). - [Bill K](/users/12943/bill-k) Sep 17 '08 at 0:25

22

 

"My car has a vehicle." If you consider that as a separate sentence, not in a programming context, that makes absolutely no sense. And that's the whole point of this technique. If it sounds awkward, it is probably wrong. - [Nick Zalutskiy](/users/1959/nick-zalutskiy) Aug 14 '11 at 18:27

21

 

@Nick Sure, but "My Car has a VehicleBehavior" makes more sense (I guess your "Vehicle" class could be named "VehicleBehavior"). So you cannot base your decision on "has a" vs "is a" comparision, you have to use LSP, or you will make mistakes - [Tristan](/users/668455/tristan) Aug 26 '11 at 11:53

20

 

Instead of "is a" think of "behaves like." Inheritance is about inheriting behavior, not just semantics. - [ybakos](/users/129622/ybakos) Mar 31 '12 at 19:25

2

 

@ybakos "Behaves like" can be achieved via interfaces without the need for inheritance. [From Wikipedia](https://en.wikipedia.org/wiki/Composition_over_inheritance#Basics): _"An implementation of composition over inheritance typically begins with the creation of various interfaces representing the behaviors that the system must exhibit...Thus, system behaviors are realized without inheritance."_ - [DavidRR](/users/1497596/davidrr) Oct 27 '15 at 12:59

 |  show **2** more comments

up vote 160 down vote

If you understand the difference, it's easier to explain.

## Procedural Code

An example of this is PHP without the use of classes (particularly before PHP5). All logic is encoded in a set of functions. You may include other files containing helper functions and so on and conduct your business logic by passing data around in functions. This can be very hard to manage as the application grows. PHP5 tries to remedy this by offering more object oriented design.

## Inheritance

This encourages the use of classes. Inheritance is one of the three tenets of OO design (inheritance, polymorphism, encapsulation).

    
    
    class Person {
       String Title;
       String Name;
       Int Age
    }
    
    class Employee : Person {
       Int Salary;
       String Title;
    }
    

This is inheritance at work. The Employee "is a" Person or inherits from Person. All inheritance relationships are "is-a" relationships. Employee also shadows the Title property from Person, meaning Employee.Title will return the Title for the Employee not the Person.

## Composition

Composition is favoured over inheritance. To put it very simply you would have:

    
    
    class Person {
       String Title;
       String Name;
       Int Age;
    
       public Person(String title, String name, String age) {
          this.Title = title;
          this.Name = name;
          this.Age = age;
       }
    
    }
    
    class Employee {
       Int Salary;
       private Person person;
    
       public Employee(Person p, Int salary) {
           this.person = p;
           this.Salary = salary;
       }
    }
    
    Person johnny = new Person ("Mr.", "John", 25);
    Employee john = new Employee (johnny, 50000);
    

Composition is typically "has a" or "uses a" relationship. Here the Employee class has a Person. It does not inherit from Person but instead gets the Person object passed to it, which is why it "has a" Person.

## Composition over Inheritance

Now say you want to create a Manager type so you end up with:

    
    
    class Manager : Person, Employee {
       ...
    }
    

This example will work fine, however, what if Person and Employee both declared `Title`? Should Manager.Title return "Manager of Operations" or "Mr."? Under composition this ambiguity is better handled:

    
    
    Class Manager {
       public Title;
       public Manager(Person p, Employee e)
       {
          this.Title = e.Title;
       }
    }
    

The Manager object is composed as an Employee and a Person. The Title behaviour is taken from employee. This explicit composition removes ambiguity among other things and you'll encounter fewer bugs.

[share](/a/891820)|[improve this answer](/posts/891820/edit)

[edited Jul 31 '10 at 16:11](/posts/891820/revisions)

answered May 21 '09 at 7:54

![](https://www.gravatar.com/avatar/a61faad7455911544b828476e9f21a10?s=32&d=identicon&r=PG)

[aleemb](/users/50475/aleemb)

19.3k1482103

5

 

For inheritence: There is no ambiguity. You are implementing the Manager class based on requirements. So you would return "Manager of Operations" if thats what your requirements specified, else you would just use the base class's implementation. Also you could make Person an abstract class and thereby make sure down-stream classes implement a Title property. - [Raj Rao](/users/44815/raj-rao) Nov 12 '10 at 20:21

39

 

Its important to remember that one might say "Composition over inheritence" but that does not mean "Composition always over Inheritence". "Is a" means inheritence and leads to code reuse. Employee is a Person (Employee does not have a person). - [Raj Rao](/users/44815/raj-rao) Nov 12 '10 at 20:26

13

 

The example is confusing.Employee is a person, so it should use inheritance. You should not use composition for this example, because it is wrong relationship in domain model, even if technically you can declare it in the code. - [Michael Freidgeim](/users/52277/michael-freidgeim) Jul 24 '13 at 13:54

8

 

I disagree with this example. An Employee _is-a_ Person, which is a textbook case of proper use of inheritance. I also think that the "issue" the redefinition of the Title field does not make sense. The fact that Employee.Title shadows Person.Title is a sign of poor programming. After all, are "Mr." and "Manager of Operations" really referring to the same aspect of a person (lowercase)? I would rename Employee.Title, and thus be able to reference the Title and JobTitle attributes of an Employee, both of which make sense in real life. Furthermore, there is no reason for Manager (continued...) - [Radon Rosborough](/users/3538165/radon-rosborough) Nov 10 '14 at 0:09

7

 

(... continued) to inherit from both Person and Employee -- after all, Employee already inherits from Person. In more complex models, where a person might be a Manager and an Agent, it is true that multiple inheritance can be used (carefully!), but it would be preferable in many environments to have an abstract Role class from which Manager (contains Employees s/he manages) and Agent (contains Contracts, and other information) inherit. Then, an Employee is-a Person who has-multiple Roles. Thus, both composition and inheritance are used properly. - [Radon Rosborough](/users/3538165/radon-rosborough) Nov 10 '14 at 0:13

 |  show **13** more comments

up vote 83 down vote

With all the undeniable benefits provided by inheritance, here's some of its disadvantages.

**Disadvantages of Inheritance:**

  1. You can't change the implementation inherited from super classes at runtime (obviously because inheritance is defined at compile time).
  2. Inheritance exposes a subclass to details of its parent's class implementation, that's why it's often said that inheritance breaks encapsulation (in a sense that you really need to focus on interfaces only not implementation, so reusing by sub classing is not always preferred).
  3. The tight coupling provided by inheritance makes the implementation of a subclass very bound up with the implementation of a super class that any change in the parent implementation will force the sub class to change.
  4. Excessive reusing by sub-classing can make the inheritance stack very deep and very confusing too.

On the other hand **Object composition** is defined at runtime through objects acquiring references to other objects. In such a case these objects will never be able to reach each-other's protected data (no encapsulation break) and will be forced to respect each other's interface. And in this case also, implementation dependencies will be a lot less than in case of inheritance.

[share](/a/891908)|[improve this answer](/posts/891908/edit)

[edited Apr 1 '14 at 20:47](/posts/891908/revisions)

![](https://www.gravatar.com/avatar/98e635e8a2fd0ac54928153ff921a15a?s=32&d=identicon&r=PG)

[dugas](/users/255259/dugas)

9,04922240

answered May 21 '09 at 8:34

![](https://www.gravatar.com/avatar/a0e79322d4eeec698760a027911e6b19?s=32&d=identicon&r=PG)

[Galilyou](/users/70289/galilyou)

4,48494565

2

 

This is one of the better answers, in my opinion - I will add to this that trying to re-think your problems in terms of composition, in my experience, tends to lead to smaller, simpler, more self-contained, more reusable classes, with a clearer, smaller, more focused scope of responsibility. Often this means there is less need for things like dependency injection or mocking (in tests) as smaller components are usually able to stand on their own. Just my experience. YMMV :-) - [mindplay.dk](/users/283851/mindplay-dk) Jan 17 '14 at 0:51

2

 

The last paragraph in this post really clicked for me. Thank you. - [Salx](/users/904308/salx) May 25 '16 at 19:00

add a comment | 

up vote 68 down vote

Another, very pragmatic reason, to prefer composition over inheritance has to do with your domain model, and mapping it to a relational database. It's really hard to map inheritance to the SQL model (you end up with all sorts of hacky workarounds, like creating columns that aren't always used, using views, etc). Some ORMLs try to deal with this, but it always gets complicated quickly. Composition can be easily modeled through a foreign-key relationship between two tables, but inheritance is much harder.

[share](/a/49070)|[improve this answer](/posts/49070/edit)

answered Sep 8 '08 at 2:48

![](https://www.gravatar.com/avatar/6e24f47aa88626872c16e0f740739e8a?s=32&d=identicon&r=PG)

[Tim Howland](/users/4276/tim-howland)

6,38031942

add a comment | 

up vote 60 down vote

While in short words I would agree with "Prefer composition over inheritance", very often for me it sounds like "prefer potatoes over coca-cola". There are places for inheritance and places for composition. You need to understand difference, then this question will disappear. What it really means for me is "if you are going to use inheritance - think again, chances are you need composition".

You should prefer potatoes over coca cola when you want to eat, and coca cola over potatoes when you want to drink.

Creating a subclass should mean more than just a convenient way to call superclass methods. You should use inheritance when subclass "is-a" super class both structurally and functionally, when it can be used as superclass and you are going to use that. If it is not the case - it is not inheritance, but something else. Composition is when your objects consists of another, or has some relationship to them.

So for me it looks like if someone does not know if he needs inheritance or composition, the real problem is that he does not know if he want to drink or to eat. Think about your problem domain more, understand it better.

[share](/a/842089)|[improve this answer](/posts/842089/edit)

answered May 8 '09 at 22:29

![](https://www.gravatar.com/avatar/3575c78bbb4f136956fe9d33ad617ec5?s=32&d=identicon&r=PG)

[Pavel Feldman](/users/5507/pavel-feldman)

2,94832430

2

 

The right tool for the right job. A hammer may be better at pounding things than a wrench, but that doesn't mean one should view a wrench as "an inferior hammer". Inheritance can be helpful when the things that are added to the subclass are necessary for the object to behave as a superclass object. For example, consider a base class `InternalCombustionEngine` with a derived class `GasolineEngine`. The latter adds things like spark plugs, which the base class lacks, but using the thing as an `InternalCombustionEngine` will cause the spark plugs to get used. - [supercat](/users/363751/supercat) Oct 29 '12 at 15:07

add a comment | 

up vote 50 down vote

Inheritance is pretty enticing especially coming from procedural-land and it often looks deceptively elegant. I mean all I need to do is add this one bit of functionality to some other class, right? Well, one of the problems is that 

## inheritance is probably the worst form of coupling you can have

Your base class breaks encapsulation by exposing implementation details to subclasses in the form of protected members. This makes your system rigid and fragile. The more tragic flaw however is the new subclass brings with it all the baggage and opinion of the inheritance chain.

The article, [Inheritance is Evil: The Epic Fail of the DataAnnotationsModelBinder](http://www.agileatwork.com/inheritance-is-evil-the-story-of-the-epic-fail-of-dataannotationsmodelbinder/), walks through an example of this in C#. It shows the use of inheritance when composition should have been used and how it could be refactored.

[share](/a/2124476)|[improve this answer](/posts/2124476/edit)

[edited Mar 16 '14 at 15:32](/posts/2124476/revisions)

answered Jan 23 '10 at 19:55

![](https://www.gravatar.com/avatar/6a8c53811ca7f3e201802e35004e0870?s=32&d=identicon&r=PG)

[Mike Valenty](/users/124839/mike-valenty)

7,30712228

  
 

Inheritance isn't good or bad, it's merely a special case of Composition. Where, indeed, the subclass is implementing a similar functionality to the superclass. If your proposed subclass is not re-implementing but merely _using_ the functionality of the superclass, then you have used Inheritance incorrectly. That is the programmer's mistake, not a reflection on Inheritance. - [iPherian](/users/4623259/ipherian) Apr 19 at 22:31

add a comment | 

up vote 35 down vote

In Java or C#, an object cannot change its type once it has been instantiated.

So, if your object need to appear as a different object or behave differently depending on an object state or conditions, then use **Composition**: Refer to [State](http://www.dofactory.com/Patterns/PatternState.aspx) and [Strategy](http://www.dofactory.com/Patterns/PatternStrategy.aspx) Design Patterns.

If the object need to be of the same type, then use **Inheritance** or implement interfaces.

[share](/a/49037)|[improve this answer](/posts/49037/edit)

answered Sep 8 '08 at 2:25

![](https://i.stack.imgur.com/9RZFi.jpg?s=32&g=1)

[Sung](/users/4035/sung)

14k26102148

9

 

+1 I've found less and less that inheritance works in most situations. I much prefer shared/inherited interfaces and composition of objects....or is it called aggregation? Don't ask me, I've got a EE degree!! - [kenny](/users/3225/kenny) May 21 '09 at 10:46

  
 

I believe that this is the most common scenario where "composition over inheritance" applies since both could be fitting in theory. For instance, in a marketing system you might have a the concept of a `Client`. Then, a new concept of a `PreferredClient` pops up later on. Should `PreferredClient` inherit `Client`? A preferred client 'is a' client afterall, no? Well, not so fast... like you said objects cannot change their class at runtime. How would you model the `client.makePreferred()` operation? Perhaps the answer lies in using composition with a missing concept, an `Account` perhaps? - [plalx](/users/1211528/plalx) Aug 31 '15 at 17:23

  
 

Rather than having different type of `Client` classes, perhaps there's just one that encapsulates the concept of an `Account` which could be a `StandardAccount` or a `PreferredAccount`... - [plalx](/users/1211528/plalx) Aug 31 '15 at 17:25

add a comment | 

up vote 23 down vote

Personally I learned to always prefer composition over inheritance. There is no programmatic problem you can solve with inheritance which you cannot solve with composition; though you may have to use Interfaces(Java) or Protocols(Obj-C) in some cases. Since C++ doesn't know any such thing, you'll have to use abstract base classes, which means you cannot get entirely rid of inheritance in C++.

Composition is often more logical, it provides better abstraction, better encapsulation, better code reuse (especially in very large projects) and is less likely to break anything at a distance just because you made an isolated change anywhere in your code. It also makes it easier to uphold the "_Single Responsibility Principle_", which is often summarized as "_There should never be more than one reason for a class to change._", and it means that every class exists for a specific purpose and it should only have methods that are directly related to its purpose. Also having a very shallow inheritance tree makes it much easier to keep the overview even when your project starts to get really large. Many people think that inheritance represents our _real world_ pretty well, but that isn't the truth. The real world uses much more composition than inheritance. Pretty much every real world object you can hold in your hand has been composed out of other, smaller real world objects.

There are downsides of composition, though. If you skip inheritance altogether and only focus on composition, you will notice that you often have to write a couple of extra code lines that weren't necessary if you had used inheritance. You are also sometimes forced to repeat yourself and this violates the _DRY Principle_ (DRY = Don't Repeat Yourself). Also composition often requires delegation, and a method is just calling another method of another object with no other code surrounding this call. Such "double method calls" (which may easily extend to triple or quadruple method calls and even farther than that) have much worse performance than inheritance, where you simply inherit a method of your parent. Calling an inherited method may be equally fast as calling a non-inherited one, or it may be slightly slower, but is usually still faster than two consecutive method calls.

You may have noticed that most OO languages don't allow multiple inheritance. While there are a couple of cases where multiple inheritance can really buy you something, but those are rather exceptions than the rule. Whenever you run into a situation where you think "multiple inheritance would be a really cool feature to solve this problem", you are usually at a point where you should re-think inheritance altogether, since even it may require a couple of extra code lines, a solution based on composition will usually turn out to be much more elegant, flexible and future proof.

Inheritance is really a cool feature, but I'm afraid it has been overused the last couple of years. People treated inheritance as the one hammer that can nail it all, regardless if it was actually a nail, a screw, or maybe a something completely different.

[share](/a/14633709)|[improve this answer](/posts/14633709/edit)

answered Jan 31 '13 at 19:34

![](https://i.stack.imgur.com/2ULwK.jpg?s=32&g=1)

[Mecki](/users/15809/mecki)

66.2k23131165

add a comment | 

up vote 18 down vote

My general rule of thumb: _Before using inheritance, consider if composition makes more sense._

Reason: _Subclassing usually means more complexity and connectedness, i.e. harder to change, maintain, and scale without making mistakes._

A much more complete and concrete [answer from Tim Boudreau](http://www.javalobby.org/forums/thread.jspa?forumID=61&threadID=16487#91822172) of Sun:

> Common problems to the use of inheritance as I see it are:
> 
>   * _Innocent acts can have unexpected results_ \- The classic example of this is calls to overridable methods from the superclass constructor, before the subclasses instance fields have been initialized. In a perfect world, nobody would ever do that. This is not a perfect world.
>   * _It offers perverse temptations for subclassers to make assumptions about order of method calls and such_ \- such assumptions tend not to be stable if the superclass may evolve over time. See also [my toaster and coffee pot analogy](http://www.javalobby.org/forums/thread.jspa?threadID=16036&messageID=91819530#91819530).
>   * _Classes get heavier_ \- you don't necessarily know what work your superclass is doing in its constructor, or how much memory it's going to use. So constructing some innocent would-be lightweight object can be far more expensive than you think, and this may change over time if the superclass evolves
>   * _It encourages an explosion of subclasses_. Classloading costs time, more classes costs memory. This may be a non-issue until you're dealing with an app on the scale of NetBeans, but there, we had real issues with, for example, menus being slow because the first display of a menu triggered massive class loading. We fixed this by moving to more declarative syntax and other techniques, but that cost time to fix as well.
>   * _It makes it harder to change things later_ \- if you've made a class public, swapping the superclass is going to break subclasses - it's a choice which, once you've made the code public, you're married to. So if you're not altering the real functionality to your superclass, you get much more freedom to change things later if you use, rather than extend the thing you need. Take, for example, subclassing JPanel - this is usually wrong; and if the subclass is public somewhere, you never get a chance to revisit that decision. If it's accessed as JComponent getThePanel() , you can still do it (hint: expose models for the components within as your API).
>   * _Object hierarchies don't scale (or making them scale later is much harder than planning ahead)_ \- this is the classic "too many layers" problem. I'll go into this below, and how the AskTheOracle pattern can solve it (though it may offend OOP purists). 
> 
> ...
> 
> My take on what to do, if you do allow for inheritance, which you may take with a grain of salt is:
> 
>   * Expose no fields, ever, except constants
>   * Methods shall be either abstract or final
>   * Call no methods from the superclass constructor
> 
> ...
> 
> all of this applies less to small projects than large ones, and less to private classes than public ones

[share](/a/10678768)|[improve this answer](/posts/10678768/edit)

answered May 21 '12 at 1:59

![](https://www.gravatar.com/avatar/4d69fc624c9269c11b835ad1481dd794?s=32&d=identicon&r=PG)

[Peter Tseng](/users/280783/peter-tseng)

7,45313737

add a comment | 

up vote 17 down vote

Didn't find a satisfactory answer here, so I wrote a new one.

To understand why "_prefer_ composition over inheritance", we need first get back the assumption omitted in this shortened idiom.

There are two benefits of inheritance: [subtyping and subclassing](https://www.cs.princeton.edu/courses/archive/fall98/cs441/mainus/node12.html)

  1. **Subtyping** means conforming to a type (interface) signature, i.e. a set of APIs, and one can override part of the signature to achieve subtyping polymorphism.
  2. **Subclassing** means implicit reuse of method implementations.

With the two benefits comes two different purposes for doing inheritance: subtyping oriented and code reuse oriented.

If code reuse is the _sole_ purpose, subclassing may give one more than what he needs, i.e. some public methods of the parent class don't make much sense for the child class. In this case, instead of favoring composition over inheritance, composition is _demanded_. This is also where the "is-a" vs. "has-a" notion comes from.

So only when subtyping is purposed, i.e. to use the new class later in a polymorphic manner, do we face the problem of choosing inheritance or composition. This is the assumption that gets omitted in the shortened idiom under discussion.

To subtype is to conform to a type signature, this means composition has always to expose no less amount of APIs of the type. Now the trade offs kick in:

  1. Inheritance provides straightforward code reuse if not overridden, while composition has to re-code every API, even if it's just a simple job of delegation.
  2. Inheritance provides straightforward [open recursion](https://en.wikipedia.org/wiki/This_%28computer_programming%29#Open_recursion) via the internal polymorphic site `this`, i.e. invoking overriding method (or even [type](http://www.scala-lang.org/old/node/1637.html#comment-5489)) in another member function, either public or private (though [discouraged](https://softwareengineering.stackexchange.com/questions/35946/is-it-bad-code-smell-if-private-method-calls-public-one)). Open recursion can be [simulated via composition](https://github.com/akottr/edu-pattern/blob/master/org.akottr.patterns.composition/src/org/akottr/patterns/composition/inheritance/Compositon.java), but it requires extra effort and may not always viable(?). This [answer](https://stackoverflow.com/a/2238735/2073130) to a duplicated question talks something similar.
  3. Inheritance exposes _protected_ members. This breaks encapsulation of the parent class, and if used by subclass, another dependency between the child and its parent is introduced.
  4. Composition has the befit of inversion of control, and its dependency can be injected dynamically, as is shown in [decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern#Java) and [proxy pattern](https://en.wikipedia.org/wiki/Proxy_pattern#Java).
  5. Composition has the benefit of [combinator-oriented](http://www.codecommit.com/blog/scala/the-magic-behind-parser-combinators) programming, i.e. working in a way like the [composite pattern](https://en.wikipedia.org/wiki/Composite_pattern#Java).
  6. Composition immediately follows [programming to an interface](https://stackoverflow.com/questions/383947/what-does-it-mean-to-program-to-an-interface).
  7. Composition has the benefit of easy [multiple inheritance](https://stackoverflow.com/questions/3556652/how-do-java-interfaces-simulate-multiple-inheritance).

With the above trade offs in mind, we hence _prefer_ composition over inheritance. Yet for tightly related classes, i.e. when implicit code reuse really make benefits, or the magic power of open recursion is desired, inheritance shall be the choice.

[share](/a/32557773)|[improve this answer](/posts/32557773/edit)

[edited May 23 at 12:10](/posts/32557773/revisions)

![](https://www.gravatar.com/avatar/a007be5a61f6aa8f3e85ae2fc18dd66e?s=32&d=identicon&r=PG)

[Community](/users/-1/community)♦

11

answered Sep 14 '15 at 5:22

![](https://www.gravatar.com/avatar/4566228dd0ba3d5652d1f2cf47471e3a?s=32&d=identicon&r=PG)

[lcn](/users/2073130/lcn)

9761029

  
 

Good answer, deserves more +1s. - [markus](/users/11995/markus) Oct 4 '15 at 13:56

add a comment | 

up vote 15 down vote

Inheritance is very powerful, but you can't force it (see: the [circle-ellipse problem](http://en.wikipedia.org/wiki/Circle-ellipse_problem)). If you really can't be completely sure of a true "is-a" subtype relationship, then it's best to go with composition.

[share](/a/49041)|[improve this answer](/posts/49041/edit)

answered Sep 8 '08 at 2:29

![](https://i.stack.imgur.com/EbuVG.png?s=32&g=1)

[yukondude](/users/726/yukondude)

13.6k123853

add a comment | 

up vote 14 down vote

Inheritance creates a strong relationship between a subclass and super class; subclass must be aware of super class'es implementation details. Creating the super class is much harder, when you have to think about how it can be extended. You have to document class invariants carefully, and state what other methods overridable methods use internally. 

Inheritance is sometimes useful, if the hierarchy really represents a is-a-relationship. It relates to Open-Closed Principle, which states that classes should be closed for modification but open to extension. That way you can have polymorphism; to have a generic method that deals with super type and its methods, but via dynamic dispatch the method of subclass is invoked. This is flexible, and helps to create indirection, which is essential in software (to know less about implementation details).

Inheritance is easily overused, though, and creates additional complexity, with hard dependencies between classes. Also understanding what happens during execution of a program gets pretty hard due to layers and dynamic selection of method calls.

I would suggest using composing as the default. It is more modular, and gives the benefit of late binding (you can change the component dynamically). Also it's easier to test the things separately. And if you need to use a method from a class, you are not forced to be of certain form (Liskov Substitution Principle).

[share](/a/891854)|[improve this answer](/posts/891854/edit)

[edited May 21 '09 at 8:18](/posts/891854/revisions)

answered May 21 '09 at 8:11

![](https://www.gravatar.com/avatar/d05ec76b03bb3cc3f9189b0f5a9817f4?s=32&d=identicon&r=PG)

[egaga](/users/103014/egaga)

9,71593951

3

 

It's worth noting that inheritance is not the only way to achieve polymorphism. The Decorator Pattern provides the appearance of polymorphism through composition. - [BitMask777](/users/509891/bitmask777) Sep 20 '12 at 20:16

1

 

@BitMask777: Subtype polymorphism is only one kind of polymorphism, another would be parametric polymorphism, you don't need inheritance for that. Also more importantly: when talking about inheritance, one means class inheritance; .i.e. you can have subtype polymorphism by having a common interface for multiple classes, and you don't get the problems of inheritance. - [egaga](/users/103014/egaga) Sep 23 '12 at 11:41

2

 

@engaga: I interpreted your comment `Inheritance is sometimes useful... That way you can have polymorphism` as hard-linking the concepts of inheritance and polymorphism (subtyping assumed given the context). My comment was intended to point out what you clarify in your comment: that inheritance is not the only way to implement polymorphism, and in fact is not necessarily the determining factor when deciding between composition and inheritance. - [BitMask777](/users/509891/bitmask777) Oct 1 '12 at 20:09

add a comment | 

up vote 13 down vote

You need to have a look at **[The Liskov Substitution Principle](http://web.archive.org/web/20110722014513/http://www.objectmentor.com/resources/articles/lsp.pdf)** in Uncle Bob's [SOLID](http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod) principles of class design. :) 

[share](/a/3863382)|[improve this answer](/posts/3863382/edit)

[edited Dec 23 '12 at 22:35](/posts/3863382/revisions)

![](https://www.gravatar.com/avatar/c916d92c098426d84778a7910cc32b39?s=32&d=identicon&r=PG)

[Rob W](/users/938089/rob-w)

231k38553517

answered Oct 5 '10 at 11:57

![](https://www.gravatar.com/avatar/2b8e7bbc1686b12814cfb88ad22b7087?s=32&d=identicon&r=PG)

[nabeelfarid](/users/288746/nabeelfarid)

2,46152957

add a comment | 

up vote 11 down vote

Suppose an aircraft has only two parts: an engine and wings.  
Then there are two ways to design an aircraft class. 

    
    
    Class Aircraft extends Engine{
      var wings;
    }
    

Now your aircraft can start with having fixed wings  
and change them to rotary wings on the fly. It's essentially  
an engine with wings. But what if I wanted to change  
the engine on the fly as well? 

Either the base class `Engine` exposes a mutator to change its  
properties, or I redesign `Aircraft` as: 

    
    
    Class Aircraft {
      var wings;
      var engine;
    }
    

Now, I can replace my engine on the fly as well.

[share](/a/4303034)|[improve this answer](/posts/4303034/edit)

[edited May 6 '11 at 17:33](/posts/4303034/revisions)

![](https://www.gravatar.com/avatar/51b7f05de9889e7212f949f0fd975922?s=32&d=identicon&r=PG)

[Marc Mutz - mmutz](/users/134841/marc-mutz-mmutz)

16.2k66077

answered Nov 29 '10 at 10:54

![](https://www.gravatar.com/avatar/fd84d6f2c427f22ffc1b06982bb7bdf0?s=32&d=identicon&r=PG)

[dharm0us](/users/49560/dharm0us)

4,3442066118

  
 

Your post brings up a point I'd not considered before--to continue your an analogy of mechanical objects with multiple parts, on something like a firearm, there is generally one part marked with a serial number, whose serial number is considered to be that of the firearm as a whole (for a handgun, it would typically be the frame). One may replace all the other parts and still have the same firearm, but if the frame cracks and needs to be replaced, the result of assembling a new frame with all the other parts from the original gun would be a new gun. Note that... - [supercat](/users/363751/supercat) Aug 19 '12 at 16:56

  
 

...the fact that multiple parts of a gun might have serial numbers marked on them does not mean that a gun can have multiple identities. Only the serial number on the frame identifies the gun; the serial number on any other part identifies which gun those parts were manufactured to be assembled with, which may not be the gun to which they are assembled at any given time. - [supercat](/users/363751/supercat) Aug 19 '12 at 17:00

add a comment | 

up vote 8 down vote

"Prefer composition over inheritance" is a design principle, which says don't abuse inheritance when it doesn't fit. 

If no real world hierarchical relationship exists between two entities, don't use inheritance, but instead use composition. Composition represents "HAS A" relationship. 

E.g. Car HAS A Wheels, body, engine, etc. But if you inheritance here, it becomes CAR IS A Wheel - which is incorrect.

For further explanations, refer to [prefer composition over inheritance](http://rangahc.blogspot.com/2015/04/prefer-composition-over-inheritance.html)

[share](/a/30367715)|[improve this answer](/posts/30367715/edit)

[edited Jun 30 '16 at 18:25](/posts/30367715/revisions)

![](https://www.gravatar.com/avatar/508065acda08f03db54a19db4ca2b6b9?s=32&d=identicon&r=PG&f=1)

[ragingasiancoder](/users/6489306/ragingasiancoder)

609316

answered May 21 '15 at 7:52

![](https://i.stack.imgur.com/iwxfv.jpg?s=32&g=1)

[Ranganatha](/users/833265/ranganatha)

660515

5

 

Usually the core of the evil is not simply "Car is a Wheel" but "Car is Something with four wheels, steering wheel, windows, body, seats ... anything you can imagine a good car should have". Usually this ends up with a BaseCar which is almighty God Father Car for every other car. Everything works fine until you need some car which is not typical, e.g. a car with just three wheels or an automated car without a steering wheel. Only then you realize that maybe it was not that great idea to enforce all the possible features on every car out there. - [JustAMartin](/users/217823/justamartin) Jul 27 '15 at 15:13

  
 

Not a good answer for the same reason that the one about canines and dogs isn't a good one. The car problem can be solved more SOLIDly with composition too. BWM implements car instead of BMW extends car. - [markus](/users/11995/markus) Oct 4 '15 at 13:53

add a comment | 

up vote 6 down vote

When you want to "copy"/Expose the base class' API, you use inheritance. When you only want to "copy" functionality, use delegation.

One example of this: You want to create a Stack out of a List. Stack only has pop, push and peek. You shouldn't use inheritance given that you don't want push_back, push_front, removeAt, et al.-kind of functionality in a Stack.

[share](/a/832554)|[improve this answer](/posts/832554/edit)

answered May 7 '09 at 1:43

![](https://i.stack.imgur.com/DRGuG.jpg?s=32&g=1)

[Anzurio](/users/99635/anzurio)

10.8k22841

add a comment | 

up vote 6 down vote

These two ways can live together just fine and actually support each other.

Composition is just playing it modular: you create interface similar to the parent class, create new object and delegate calls to it. If these objects need not to know of each other, it's quite safe and easy to use composition. There are so many possibilites here.

However, if the parent class for some reason needs to access functions provided by the "child class" for inexperienced programmer it may look like it's a great place to use inheritance. The parent class can just call it's own abstract "foo()" which is overwritten by the subclass and then it can give the value to the abstract base.

It looks like a nice idea, but in many cases it's better just give the class an object which implements the foo() (or even set the value provided the foo() manually) than to inherit the new class from some base class which requires the function foo() to be specified.

Why?

**Because inheritance is a poor way of moving information**.

The composition has a real edge here: the relationship can be reversed: the "parent class" or "abstract worker" can aggregate any specific "child" objects implementing certain interface + **any child can be set inside any other type of parent, which accepts it's type**. And there can be any number of objects, for example MergeSort or QuickSort could sort any list of objects implementing an abstract Compare -interface. Or to put it another way: any group of objects which implement "foo()" and other group of objects which can make use of objects having "foo()" can play together. 

I can think of three real reasons for using inheritance:

  1. You have many classes with **same interface** and you want to save time writing them
  2. You have to use same Base Class for each object
  3. You need to modify the private variables, which can not be public in any case

If these are true, then it is probably necessary to use inheritance.

There is nothing bad in using reason 1, it is very good thing to have a solid interface on your objects. This can be done using composition or with inheritance, no problem - if this interface is simple and does not change. Usually inheritance is quite effective here.

If the reason is number 2 it gets a bit tricky. Do you really only need to use the same base class? In general, just using the same base class is not good enough, but it may be a requirement of your framework, a design consideration which can not be avoided.

However, if you want to use the private variables, the case 3, then you may be in trouble. **If you consider global variables unsafe, then you should consider using inheritance to get access to private variables also unsafe**. Mind you, global variables are not all THAT bad - databases are essentially big set of global variables. But if you can handle it, then it's quite fine.

[share](/a/16046223)|[improve this answer](/posts/16046223/edit)

answered Apr 16 '13 at 20:15

![](https://www.gravatar.com/avatar/ff115185606d5117c1680ef1f23353b6?s=32&d=identicon&r=PG)

[Tero Tolonen](/users/2287682/tero-tolonen)

2,22811120

add a comment | 

up vote 5 down vote

Aside from is a/has a considerations, one must also consider the "depth" of inheritance your object has to go through. Anything beyond five or six levels of inheritance deep might cause unexpected casting and boxing/unboxing problems, and in those cases it might be wise to compose your object instead.

[share](/a/49090)|[improve this answer](/posts/49090/edit)

answered Sep 8 '08 at 3:00

![](https://i.stack.imgur.com/jJ39O.jpg?s=32&g=1)

[Jon Limjap](/users/372/jon-limjap)

69.4k1488142

add a comment | 

up vote 5 down vote

A simple way to make sense of this would be that inheritance should be used when you need an object of your class to have the same _interface_ as its parent class, so that it can thereby be treated as an object of the parent class (upcasting). Moreover, function calls on a derived class object would remain the same everywhere in code, but the specific method to call would be determined at runtime (i.e. the low-level _implementation_ differs, the high-level _interface_ remains the same).

Composition should be used when you do not need the new class to have the same interface, i.e. you wish to conceal certain aspects of the class' implementation which the user of that class need not know about. So composition is more in the way of supporting _encapsulation_ (i.e. concealing the implementation) while inheritance is meant to support _abstraction_ (i.e. providing a simplified representation of something, in this case the **same** interface for a range of types with different internals).

[share](/a/24036352)|[improve this answer](/posts/24036352/edit)

[edited Mar 20 '15 at 13:57](/posts/24036352/revisions)

answered Jun 4 '14 at 11:36

![](https://i.stack.imgur.com/a1Khu.jpg?s=32&g=1)

[Y.S.](/users/3287204/y-s)

17.7k64383

  
 

+1 for mention of interface. I use this approach often to hide existing classes and make my new class properly unit testable by mocking out the object used for composition. This requires the owner of the new object to pass it the candidate parent class instead. - [Kell](/users/449404/kell) Jun 13 '14 at 10:39

add a comment | 

up vote 4 down vote

Subtyping is appropriate and more powerful where the [invariants can be enumerated](https://stackoverflow.com/a/8352969), else use function composition for extensibility.

[share](/a/8353160)|[improve this answer](/posts/8353160/edit)

[edited May 23 at 12:34](/posts/8353160/revisions)

![](https://www.gravatar.com/avatar/a007be5a61f6aa8f3e85ae2fc18dd66e?s=32&d=identicon&r=PG)

[Community](/users/-1/community)♦

11

answered Dec 2 '11 at 7:40

![](https://www.gravatar.com/avatar/def49e4f02dea4911a431380ac6ec823?s=32&d=identicon&r=PG)

[Shelby Moore III](/users/615784/shelby-moore-iii)

4,63712125

add a comment | 

up vote 4 down vote

I agree with @Pavel, when he says, there are places for composition and there are places for inheritance.

I think inheritance should be used if your answer is an affirmative to any of these questions.

  * Is your class part of a structure that benefits from polymorphism ? For example, if you had a Shape class, which declares a method called draw(), then we clearly need Circle and Square classes to be subclasses of Shape, so that their client classes would depend on Shape and not on specific subclasses.
  * Does your class need to re-use any high level interactions defined in another class ? The [template method](http://en.wikipedia.org/wiki/Template_method_pattern) design pattern would be impossible to implement without inheritance. I believe all extensible frameworks use this pattern.

However, if your intention is purely that of code re-use, then composition most likely is a better design choice.

[share](/a/8413988)|[improve this answer](/posts/8413988/edit)

answered Dec 7 '11 at 10:40

![](https://www.gravatar.com/avatar/8f210ededa655250c5ec3eecd0bef141?s=32&d=identicon&r=PG&f=1)

[Parag](/users/34956/parag)

4,31584066

add a comment | 

up vote 4 down vote

The answer is quite simple

When you have an is-a relation between two classes (example dog is a canine) you go for inheritance.

On the other hand when you have has-a or some adjective relationship between two classes (student has courses) or (teacher studies courses) you chose composition.

[share](/a/20832301)|[improve this answer](/posts/20832301/edit)

[edited Dec 31 '13 at 1:42](/posts/20832301/revisions)

answered Dec 30 '13 at 1:57

![](https://i.stack.imgur.com/jZ0if.jpg?s=32&g=1)

[Amir Aslam](/users/1505065/amir-aslam)

14216

  
 

You said inheritance and inheritance. don't you mean inheritance and composition? - [someone-or-other](/users/3002116/someone-or-other) Dec 30 '13 at 2:21

  
 

No, you don't. You can just as well define a canine interface and let every dog implement it and you'll end up with more SOLID code. - [markus](/users/11995/markus) Oct 4 '15 at 13:49

add a comment | 

up vote 4 down vote

All the existing answers are great to explain why, very often, composition is preferable over inheritance. However, there are indeed situations where inheritance is more suitable, so it's important to have a good "test" to know whether or not we are in such situation.

The [Circle-Ellipse problem](https://en.wikipedia.org/wiki/Circle-ellipse_problem) is a great illustration of why **"is-a"** is actually _not a good test alone_ to detect when to use inheritance. Indeed, **even though a circle is an ellipse**, it is a bad idea to have the `Circle` class inherit the `Ellipse` class because there are things that ellipses can do, but circles can't. For instance, ellipses can stretch, but circles can't. So you can have `ellipse.stretch()`, but not `circle.stretch()`.

I think a better test is **"is-a"** AND **"has-as-much-functionality-as"**. In other words, it is a good idea to use inheritance whenever the subclass can be used polymorphically. The "is-a" relationship is a necessary condition for polymorphic use, but it is not sufficient. It is also very important that every functionality provided by the superclass can also be provided by the subclass. So when you have a class that "is a sort of" another class, but adds some constraints to it, then you should not use inheritance, because it could not be used polymorphically. 

In other words, **inheritance is not about sharing properties, but about sharing functionality**. Typically, "is-a" works as a test whether all _getters_ of the superclass make sense in the subclass, while "has-as-much-functionality-as" works as a test whether all _setters_ of the superclass make sense in the subclass. Together, the getters and setters define the "functionality" of a class. The getters alone define the "properties" of a class. By "setter", I mean any function that mutates the state of the object., not just the trivial ones.

Other answers/comments pretty much said the same things, but I feel mine adds some clarity.

[share](/a/37624298)|[improve this answer](/posts/37624298/edit)

[edited Jun 3 '16 at 22:30](/posts/37624298/revisions)

answered Jun 3 '16 at 22:23

![](https://i.stack.imgur.com/AcrDt.jpg?s=32&g=1)

[Boris](/users/1951907/boris)

2,87331133

add a comment | 

up vote 2 down vote

A rule of thumb I have heard is inheritance should be used when its a "is-a" relationship and composition when its a "has-a". Even with that I feel that you should always lean towards composition because it eliminates a lot of complexity.

[share](/a/49028)|[improve this answer](/posts/49028/edit)

answered Sep 8 '08 at 2:14

Evrhet Milam 

add a comment | 

up vote 2 down vote

Inheritance is a very powerfull machanism for code reuse. But needs to be used properly. I would say that inheritance is used correctly if the subclass is also a subtype of the parent class. As mentioned above, the Liskov Substitution Principle is the key point here. 

Subclass is not the same as subtype. You might create subclasses that are not subtypes (and this is when you should use composition). To understand what a subtype is, lets start giving an explanation of what a type is.

When we say that the number 5 is of type integer, we are stating that 5 belongs to a set of possible values (as an example, see the possible values for the Java primitive types). We are also stating that there is a valid set of methods I can perform on the value like addition and subtraction. And finally we are stating that there are a set of properties that are always satisfied, for example, if I add the values 3 and 5, I will get 8 as a result.

To give another example, think about the abstract data types, Set of integers and List of integers, the values they can hold are restricted to integers. They both support a set of methods, like add(newValue) and size(). And they both have different properties (class invariant), Sets does not allow duplicates while List does allow duplicates (of course there are other properties that they both satisfy).

Subtype is also a type, which has a relation to another type, called parent type (or supertype). The subtype must satisfy the features (values, methods and properties) of the parent type. The relation means that in any context where the supertype is expected, it can be substitutable by a subtype, without affecting the behaviour of the execution. Let’s go to see some code to exemplify what I’m saying. Suppose I write a List of integers (in some sort of pseudo language):

    
    
    class List {
      data = new Array();
    
      Integer size() {
        return data.length;
      }
    
      add(Integer anInteger) {
        data[data.length] = anInteger;
      }
    }
    

Then, I write the Set of integers as a subclass of the List of integers:

    
    
    class Set, inheriting from: List {
      add(Integer anInteger) {
         if (data.notContains(anInteger)) {
           super.add(anInteger);
         }
      }
    }
    

Our Set of integers class is a subclass of List of Integers, but is not a subtype, due to it is not satisfying all the features of the List class. The values, and the signature of the methods are satisfied but the properties are not. The behaviour of the add(Integer) method has been clearly changed, not preserving the properties of the parent type. Think from the point of view of the client of your classes. They might receive a Set of integers where a List of integers is expected. The client might want to add a value and get that value added to the List even if that value already exist in the List. But her wont get that behaviour if the value exists. A big suprise for her!

This is a classic example of an improper use of inheritance. Use composition in this case.

(a fragment from: [use inheritance properly](http://www.copypasteisforword.com/notes/use-inheritance-properly)).

[share](/a/18548784)|[improve this answer](/posts/18548784/edit)

answered Aug 31 '13 at 13:41

![](https://i.stack.imgur.com/AyB6J.jpg?s=32&g=1)

[Enrique Molinari](/users/842533/enrique-molinari)

18915

add a comment | 

up vote 2 down vote

Composition v/s Inheritance is a wide subject. There is no real answer for what is better as I think it all depends on the design of the system.

Generally type of relationship between object provide better information to choose one of them.

If relation type is "IS-A" relation then Inheritance is better approach. otherwise relation type is "HAS-A" relation then composition will better approach.

Its totally depend on entity relationship.

[share](/a/22475358)|[improve this answer](/posts/22475358/edit)

answered Mar 18 '14 at 9:39

![](https://i.stack.imgur.com/AE5fi.jpg?s=32&g=1)

[Shami Qureshi](/users/3274044/shami-qureshi)

572

add a comment | 

up vote 1 down vote

As many people told, I will first start with the check - whether there exists an "is-a" relationship. If it exists I usually check the following:

> Whether the base class can be instantiated. That is, whether the base class can be non-abstract. If it can be non-abstract I usually prefer composition

E.g 1. Accountant **is an** Employee. But I will **not** use inheritance because a Employee object can be instantiated.

E.g 2. Book **is a** SellingItem. A SellingItem cannot be instantiated - it is abstract concept. Hence I will use inheritacne. The SellingItem is an **abstract base class (or interface** in C#)

What do you think about this approach?

Also, I support @anon answer in [Why use inheritance at all?](https://stackoverflow.com/questions/3351666/why-use-inheritance-at-all?lq=1)

> The main reason for using inheritance is not as a form of composition - it is so you can get polymorphic behaviour. If you don't need polymorphism, you probably should not be using inheritance.

@MatthieuM. says in <https://softwareengineering.stackexchange.com/questions/12439/code-smell-inheritance-abuse/12448#comment303759_12448>

> The issue with inheritance is that it can be used for two orthogonal purposes:
> 
> interface (for polymorphism)
> 
> implementation (for code reuse)

**REFERENCE**

  1. [Which class design is better?](https://stackoverflow.com/questions/38820/which-class-design-is-better?lq=1)
  2. [Inheritance vs. Aggregation](https://stackoverflow.com/questions/269496/inheritance-vs-aggregation/269553#comment15610225_269553)

[share](/a/11758048)|[improve this answer](/posts/11758048/edit)

[edited May 23 at 11:47](/posts/11758048/revisions)

![](https://www.gravatar.com/avatar/a007be5a61f6aa8f3e85ae2fc18dd66e?s=32&d=identicon&r=PG)

[Community](/users/-1/community)♦

11

answered Aug 1 '12 at 11:15

![](https://i.stack.imgur.com/x4YHl.gif?s=32&g=1)

[Lijo](/users/696627/lijo)

8,85645167285

1

 

I'm not sure why 'the base class is abstract?' figures into the discussion.. the LSP: will all functions that operate on Dogs work if Poodle objects are passed in ? If yes, then Poodle is can be substituted for Dog and hence can inherit from Dog. - [Gishu](/users/1695/gishu) Aug 1 '12 at 12:50

  
 

@Gishu Thanks. I will definitely look into LSP. But before that, can you please provide an "example where inheritance is proper in which base class cannot be abstract". What I think is, inheritance is applicable only if base class is abstract. If base class need to be instantiated separately, do not go for inheritance. That is, even though Accountant is an Employee, do not use inheritance. - [Lijo](/users/696627/lijo) Aug 2 '12 at 7:11

1

 

been reading WCF lately. An example in the .net framework is SynchronizationContext (base + can be instantiated) which queues work onto a ThreadPool thread. Derivations include WinFormsSyncContext (queue onto UI Thread) and DispatcherSyncContext (queue onto WPF Dispatcher) - [Gishu](/users/1695/gishu) Aug 2 '12 at 9:05

  
 

@Gishu Thanks. However, it would be more helpful if you can provide a scenario based on Bank domain, HR domain, Retail domain or any other popular domain. - [Lijo](/users/696627/lijo) Aug 2 '12 at 9:08

1

 

Sorry. I'm not familiar with those domains.. Another example if the previous one was too obtuse is the Control class in Winforms/WPF. The base/generic control can be instantiated. Derivations include Listboxes, Textboxes, etc. Now that I think of it, the Decorator Design pattern is a good example IMHO and useful too. The decorator derives from the non-abstract object that it wants to wrap/decorate. - [Gishu](/users/1695/gishu) Aug 2 '12 at 9:28

add a comment | 

up vote 1 down vote

What do you want to force yourself (or another programmer) to adhere to and when do you want to allow yourself (or another programmer) more freedom. It has been argued that inheritance is helpful when you want to force someone into a way of dealing with/solving a particular problem so they can't head off in the wrong direction.

`Is-a` and `Has-a` is a helpful rule of thumb.

[share](/a/1020959)|[improve this answer](/posts/1020959/edit)

[edited Nov 6 '12 at 6:55](/posts/1020959/revisions)

![](https://i.stack.imgur.com/GRoza.jpg?s=32&g=1)

[Sumit Singh](/users/942391/sumit-singh)

17.2k74789

answered Jun 20 '09 at 4:41

user125959 

add a comment | 

up vote 1 down vote

A real world example of when Composition is better than Inheritance.

Assume you have a BaseClass where T is injected by a concrete class. 

    
    
    public BaseClass<T>{}
    

At first glance this looks nice because you can inject any type you want and use this type to change property behavior within the class; whereby T is referenced like this:

    
    
    public T SomeProperty {get;set;}
    

A possible concrete class using inheritance looks like this: 

    
    
    public class SubClass : BaseClass<string>    
    

But what happens if you need to have that base property handle different types? Do you create one class per type? No just use containment instead. Like this:

    
    
    public class SubClass{
      private BaseClass<List<string>> BaseForList = new BaseClass<List<string>>();
      private BaseClass<List<ofSomeType>> BaseForListOfSometype = new BaseClass<List<ofSomeType>();
    
    }
    

You can see from the example above that the SubClass is open to expand in any way needed. It can in essence be more than one implementation of a single baseclass. It's easily morphed into just that type giving you very specific access to property types. This is better than inheriting and creating multiple class derived from the BaseClass with one caveat...

Addressibility to "Contained" things takes on a different signature which is simply preceding the thing wanted (SomeProperty) with the instance of the class. Like this:

    
    
    BaseForList.SomeProperty = something;
    BaseForListOfSomeType.SomeProperty = somethingelse;
    

Because of this, it's best to create short names for contained things...so your code can look like this (Just make sure that the short names have good meaning)...

    
    
    BA.SomeProperty = something;
    BL.SomeProperty = somethingelse;
    

[share](/a/29284907)|[improve this answer](/posts/29284907/edit)

answered Mar 26 '15 at 17:20

![](https://www.gravatar.com/avatar/b3d0b8f681ed398a28c9bd288d7c1f96?s=32&d=identicon&r=PG)

[John Peters](/users/1522548/john-peters)

3,13311737

add a comment | 

1 [ 2 ](/questions/49002/prefer-composition-over-inheritance?page=2&tab=votes#tab-top) [ next ](/questions/49002/prefer-composition-over-inheritance?page=2&tab=votes#tab-top)

##  **protected** by [Tushar Gupta](/users/2224265/tushar-gupta) Nov 18 '14 at 7:43

Thank you for your interest in this question. Because it has attracted low-quality or spam answers that had to be removed, posting an answer now requires 10 [reputation](/help/whats-reputation) on this site (the [association bonus does not count](/help/privileges/new-user)).   
  
Would you like to answer one of these [unanswered questions](/unanswered?fromProtectedNotice=true) instead? 

##  Not the answer you're looking for? Browse other questions tagged [language-agnostic](/questions/tagged/language-agnostic) [oop](/questions/tagged/oop) [inheritance](/questions/tagged/inheritance) [composition](/questions/tagged/composition) [aggregation](/questions/tagged/aggregation) or [ask your own question](/questions/ask). 

asked

**8 years, 11 months ago**

viewed

**216,007 times**

active

**[4 months ago](?lastactivity)**

Get the **weekly newsletter!** In it, you'll get:

  * The week's top questions and answers
  * Important community announcements
  * Questions that need answers

see an [example newsletter](https://stackexchange.com/newsletters/newsletter?site=stackoverflow.com)

By subscribing, you agree to the [privacy policy](https://stackexchange.com/legal/privacy-policy) and [terms of service](https://stackexchange.com/legal/terms-of-service).

#### Linked

[

37

](/q/11343840) [Favor composition over inheritance](/questions/11343840/favor-composition-over-inheritance?noredirect=1)

[

8

](/q/13245610) [What is the Difference between inheritance and delegation in java](/questions/13245610/what-is-the-difference-between-inheritance-and-delegation-in-java?noredirect=1)

[

-2

](/q/36162714) [What is the difference between IS -A relationship and HAS-A relationship? Java](/questions/36162714/what-is-the-difference-between-is-a-relationship-and-has-a-relationship-java?noredirect=1)

[

8

](/q/19146979) [why inheritence is strongly coupled where as composition is loosely coupled in Java?](/questions/19146979/why-inheritence-is-strongly-coupled-where-as-composition-is-loosely-coupled-in-j?noredirect=1)

[

3

](/q/19641899) [OOP Java: Better to extend a class or create a new instance of the subclass?](/questions/19641899/oop-java-better-to-extend-a-class-or-create-a-new-instance-of-the-subclass?noredirect=1)

[

2

](/q/11031843) [Inheritance vs Composition](/questions/11031843/inheritance-vs-composition?noredirect=1)

[

-2

](/q/24168116) [Inheritance (IS-A) vs. Composition (HAS-A) Relationship in java](/questions/24168116/inheritance-is-a-vs-composition-has-a-relationship-in-java?noredirect=1)

[

2

](/q/17256748) [PHP OOP Modular CMS Objects design](/questions/17256748/php-oop-modular-cms-objects-design?noredirect=1)

[

-5

](/q/31809498) [Java ArrayList instantiation](/questions/31809498/java-arraylist-instantiation?noredirect=1)

[

2

](/q/22816843) [Duck example for strategy pattern](/questions/22816843/duck-example-for-strategy-pattern?noredirect=1)

[see more linked questions…](/questions/linked/49002)

#### Related

[116

](/q/269496)[Inheritance vs. Aggregation](/questions/269496/inheritance-vs-aggregation)

[49

](/q/3351666)[Why use inheritance at all?](/questions/3351666/why-use-inheritance-at-all)

[7

](/q/15749316)[Can inheritance be replaced completely by composition?](/questions/15749316/can-inheritance-be-replaced-completely-by-composition)

[797

](/q/21692193)[Why not inherit from List<T>?](/questions/21692193/why-not-inherit-from-listt)

[0

](/q/27376960)[What is preferred composition or aggregation in UML?](/questions/27376960/what-is-preferred-composition-or-aggregation-in-uml)

[4

](/q/32308276)[When to Favor Inheritance Over Composition](/questions/32308276/when-to-favor-inheritance-over-composition)

[1

](/q/33205790)[Is "composition over inheritance" simply mean "If parent class is never be used except in child class, it should be composition"?](/questions/33205790/is-composition-over-inheritance-simply-mean-if-parent-class-is-never-be-used)

[1

](/q/37596286)[Composition Over Inheritance - Avoiding Abstract Classes](/questions/37596286/composition-over-inheritance-avoiding-abstract-classes)

[3

](/q/39453493)[When to use association, aggregation, composition and inheritance?](/questions/39453493/when-to-use-association-aggregation-composition-and-inheritance)

[0

](/q/45122871)[Composition over Inheritance for Javascript Example](/questions/45122871/composition-over-inheritance-for-javascript-example)

####  [ Hot Network Questions ](https://stackexchange.com/questions?tab=hot)

  * [ Is it okay to tell that my team lead I am not interested in doing an administrative task? ](https://workplace.stackexchange.com/questions/96737/is-it-okay-to-tell-that-my-team-lead-i-am-not-interested-in-doing-an-administrat)
  * [ How to permanently leave a group activity without insulting a friend ](https://interpersonal.stackexchange.com/questions/1455/how-to-permanently-leave-a-group-activity-without-insulting-a-friend)
  * [ How could a well organised and equipped army be defeated without destroying it? ](https://worldbuilding.stackexchange.com/questions/88253/how-could-a-well-organised-and-equipped-army-be-defeated-without-destroying-it)
  * [ How do you pronounce the "g" in "Heiligtum"? ](https://german.stackexchange.com/questions/38330/how-do-you-pronounce-the-g-in-heiligtum)
  * [ In The Wheel of Time, how were Aes Sedai able to be used as damane while under the Three Oaths? ](https://scifi.stackexchange.com/questions/166739/in-the-wheel-of-time-how-were-aes-sedai-able-to-be-used-as-damane-while-under-t)
  * [ Can squares of side 1/2, 1/3, 1/4, … be packed into three quarters of a unit square? ](https://mathoverflow.net/questions/278268/can-squares-of-side-1-2-1-3-1-4-be-packed-into-three-quarters-of-a-unit-squ)
  * [ prepend,append-Sequence ](https://codegolf.stackexchange.com/questions/137981/prepend-append-sequence)
  * [ Where is source code of TeX, LuateX, pdfTeX ](https://tex.stackexchange.com/questions/385380/where-is-source-code-of-tex-luatex-pdftex)
  * [ What writing utensil should I use on gaming paper? ](https://rpg.stackexchange.com/questions/104886/what-writing-utensil-should-i-use-on-gaming-paper)
  * [ How to convey how much computing power has grown since the 1960s? ](https://cseducators.stackexchange.com/questions/3105/how-to-convey-how-much-computing-power-has-grown-since-the-1960s)
  * [ Why would GPS availability be reduced by high demand (or solar eclipse)? ](https://space.stackexchange.com/questions/22555/why-would-gps-availability-be-reduced-by-high-demand-or-solar-eclipse)
  * [ Identify the era or any other clues from this soldier's picture? ](https://history.stackexchange.com/questions/39424/identify-the-era-or-any-other-clues-from-this-soldiers-picture)
  * [ How to remove the time box? ](https://tex.stackexchange.com/questions/385391/how-to-remove-the-time-box)
  * [ Should I let one of my Players control his character's kids? ](https://rpg.stackexchange.com/questions/104876/should-i-let-one-of-my-players-control-his-characters-kids)
  * [ How to convert BED to GFF3 ](https://bioinformatics.stackexchange.com/questions/2242/how-to-convert-bed-to-gff3)
  * [ Has the marijuana black market in Colorado increased since the state legalized pot? ](https://skeptics.stackexchange.com/questions/39156/has-the-marijuana-black-market-in-colorado-increased-since-the-state-legalized-p)
  * [ Lightning components, CometD - Refused to connect to ... because it violates the following Content Security Policy directive ](https://salesforce.stackexchange.com/questions/187631/lightning-components-cometd-refused-to-connect-to-because-it-violates-the)
  * [ What are Japanese rice seasoning packets called? ](https://cooking.stackexchange.com/questions/83580/what-are-japanese-rice-seasoning-packets-called)
  * [ Why didn't Tullys just order Freys to let the northmen through the bridge? ](https://scifi.stackexchange.com/questions/166691/why-didnt-tullys-just-order-freys-to-let-the-northmen-through-the-bridge)
  * [ How do you revise material that you already half-know, without getting bored and demotivated? ](https://math.stackexchange.com/questions/2384287/how-do-you-revise-material-that-you-already-half-know-without-getting-bored-and)
  * [ What happened to the "Surgical Team" pattern from "The Mythical Man-Month"? ](https://softwareengineering.stackexchange.com/questions/355203/what-happened-to-the-surgical-team-pattern-from-the-mythical-man-month)
  * [ Randomised bank accounts ](https://worldbuilding.stackexchange.com/questions/88340/randomised-bank-accounts)
  * [ Would 'magic' muskets be a significant advantage over actual muskets? ](https://worldbuilding.stackexchange.com/questions/88247/would-magic-muskets-be-a-significant-advantage-over-actual-muskets)
  * [ Why is the word "complement" used in Set Theory? ](https://math.stackexchange.com/questions/2386710/why-is-the-word-complement-used-in-set-theory)

more hot questions 

[ question feed ](/feeds/question/49002)

![](/posts/49002/ivc/09d3)

##### [Stack Overflow](https://stackoverflow.com)

  * [Questions](/questions)
  * [Jobs](/jobs)
  * [Developer Jobs Directory](https://stackoverflow.com/jobs/directory/developer-jobs)
  * [Documentation](/documentation)
  * [Help](/help)
  * Mobile

##### [Stack Overflow  
Business](https://www.stackoverflowbusiness.com/?utm_source=so-footer&utm_medium=referral&utm_campaign=brand-activation)

  * [Talent](https://www.stackoverflowbusiness.com/talent?utm_source=so-footer&utm_medium=referral&utm_campaign=brand-activation)
  * [Ads](https://www.stackoverflowbusiness.com/advertise?utm_source=so-footer&utm_medium=referral&utm_campaign=brand-activation)
  * [Enterprise](https://www.stackoverflowbusiness.com/enterprise?utm_source=so-footer&utm_medium=referral&utm_campaign=brand-activation)
  * [Insights](https://www.stackoverflowbusiness.com/insights?utm_source=so-footer&utm_medium=referral&utm_campaign=brand-activation)

##### [Company](https://stackoverflow.com/company/about)

  * [About](https://stackoverflow.com/company/about)
  * [Press](https://stackoverflow.com/company/press)
  * [Work Here](https://stackoverflow.com/company/work-here)
  * [Legal](https://stackexchange.com/legal)
  * [Privacy Policy](https://stackexchange.com/legal/privacy-policy)
  * [Contact Us](https://stackoverflow.com/company/contact)

##### [Stack Exchange  
Network](https://stackexchange.com)

  * Technology
  * Life / Arts
  * Culture / Recreation
  * Science
  * Other
  * [Stack Overflow](//stackoverflow.com)
  * [Server Fault](//serverfault.com)
  * [Super User](//superuser.com)
  * [Web Applications](//webapps.stackexchange.com)
  * [Ask Ubuntu](//askubuntu.com)
  * [Webmasters](//webmasters.stackexchange.com)
  * [Game Development](//gamedev.stackexchange.com)
  * [TeX - LaTeX](//tex.stackexchange.com)
  * [Software Engineering](//softwareengineering.stackexchange.com)
  * [Unix & Linux](//unix.stackexchange.com)
  * [Ask Different (Apple)](//apple.stackexchange.com)
  * [WordPress Development](//wordpress.stackexchange.com)
  * [Geographic Information Systems](//gis.stackexchange.com)
  * [Electrical Engineering](//electronics.stackexchange.com)
  * [Android Enthusiasts](//android.stackexchange.com)
  * [Information Security](//security.stackexchange.com)
  * [Database Administrators](//dba.stackexchange.com)
  * [Drupal Answers](//drupal.stackexchange.com)
  * [SharePoint](//sharepoint.stackexchange.com)
  * [User Experience](//ux.stackexchange.com)
  * [Mathematica](//mathematica.stackexchange.com)
  * [Salesforce](//salesforce.stackexchange.com)
  * [ExpressionEngine® Answers](//expressionengine.stackexchange.com)
  * [Blender](//blender.stackexchange.com)
  * [Network Engineering](//networkengineering.stackexchange.com)
  * [Cryptography](//crypto.stackexchange.com)
  * [Code Review](//codereview.stackexchange.com)
  * [Magento](//magento.stackexchange.com)
  * [Software Recommendations](//softwarerecs.stackexchange.com)
  * [Signal Processing](//dsp.stackexchange.com)
  * [Emacs](//emacs.stackexchange.com)
  * [Raspberry Pi](//raspberrypi.stackexchange.com)
  * [Programming Puzzles & Code Golf](//codegolf.stackexchange.com)
  * [Ethereum](//ethereum.stackexchange.com)
  * [Data Science](//datascience.stackexchange.com)
  * [Arduino](//arduino.stackexchange.com)
  * [ ** more (26) ** ](https://stackexchange.com/sites#technology)
  * [Photography](//photo.stackexchange.com)
  * [Science Fiction & Fantasy](//scifi.stackexchange.com)
  * [Graphic Design](//graphicdesign.stackexchange.com)
  * [Movies & TV](//movies.stackexchange.com)
  * [Music: Practice & Theory](//music.stackexchange.com)
  * [Worldbuilding](//worldbuilding.stackexchange.com)
  * [Seasoned Advice (cooking)](//cooking.stackexchange.com)
  * [Home Improvement](//diy.stackexchange.com)
  * [Personal Finance & Money](//money.stackexchange.com)
  * [Academia](//academia.stackexchange.com)
  * [Law](//law.stackexchange.com)
  * [ ** more (17) ** ](https://stackexchange.com/sites#lifearts)
  * [English Language & Usage](//english.stackexchange.com)
  * [Skeptics](//skeptics.stackexchange.com)
  * [Mi Yodeya (Judaism)](//judaism.stackexchange.com)
  * [Travel](//travel.stackexchange.com)
  * [Christianity](//christianity.stackexchange.com)
  * [English Language Learners](//ell.stackexchange.com)
  * [Japanese Language](//japanese.stackexchange.com)
  * [Arqade (gaming)](//gaming.stackexchange.com)
  * [Bicycles](//bicycles.stackexchange.com)
  * [Role-playing Games](//rpg.stackexchange.com)
  * [Anime & Manga](//anime.stackexchange.com)
  * [Puzzling](//puzzling.stackexchange.com)
  * [Motor Vehicle Maintenance & Repair](//mechanics.stackexchange.com)
  * [ ** more (32) ** ](https://stackexchange.com/sites#culturerecreation)
  * [MathOverflow](//mathoverflow.net)
  * [Mathematics](//math.stackexchange.com)
  * [Cross Validated (stats)](//stats.stackexchange.com)
  * [Theoretical Computer Science](//cstheory.stackexchange.com)
  * [Physics](//physics.stackexchange.com)
  * [Chemistry](//chemistry.stackexchange.com)
  * [Biology](//biology.stackexchange.com)
  * [Computer Science](//cs.stackexchange.com)
  * [Philosophy](//philosophy.stackexchange.com)
  * [ ** more (10) ** ](https://stackexchange.com/sites#science)
  * [Meta Stack Exchange](//meta.stackexchange.com)
  * [Stack Apps](//stackapps.com)
  * [API](https://api.stackexchange.com)
  * [Data](https://data.stackexchange.com)
  * [Area 51](//area51.stackexchange.com)
  * [Blog](https://stackoverflow.blog?blb=1)
  * [Facebook](https://www.facebook.com/officialstackoverflow/)
  * [Twitter](https://twitter.com/stackoverflow)
  * [LinkedIn](https://linkedin.com/company/stack-overflow)

site design / logo (C) 2017 Stack Exchange Inc; user contributions licensed under [cc by-sa 3.0](https://creativecommons.org/licenses/by-sa/3.0/) with [attribution required](https://stackoverflow.blog/2009/06/25/attribution-required/). rev 2017.8.7.26717

Stack Overflow works best with JavaScript enabled ![](https://pixel.quantserve.com/pixel/p-c1rF4kxgLUzNc.gif))
