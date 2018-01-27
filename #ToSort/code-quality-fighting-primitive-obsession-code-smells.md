# Code Quality: Fighting Primitive Obsession Code Smells

_Captured: 2017-11-28 at 13:46 from [dzone.com](https://dzone.com/articles/code-quality-fighting-primitive-obsession-code-sme-1?edition=338993&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202017-11-28)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Most of the time, programmers are aware of common code imperfections and intuitively know how to deal with them. Long methods, large classes, a long list of parameters, duplicated code or code with a lot of comments are well-known problems that are easy to recognize. However, there are some smells that most developers can't detect intuitively. So in this article, I'll focus on the Primitive Obsession code smell. I'll show you how to recognize it, explain why it's important to fight it, and describe ways to avoid or deal with it.

[Bad smells in code ](https://blog.codinghorror.com/code-smells/) refer to code quality issues that may indicate deeper problems now or in the future. They're a diagnostic tool used when you're considering refactoring, or watching out for warning signs in your own code. Code smells come as a list of problems that the code may be dealing with. Additionally, they come with a description of the symptoms, as well as methods and reasons to overcome them.

## Primitive Obsession Code Smells

Before we can start, it's important to describe what primitive fields are. Primitive data types are basic built-in building blocks of a language. They're usually typed as int, string, or constants. As creating such fields is much easier than making a whole new class, this leads to abuse. Therefore, this makes this smell one of the most common ones.

  * Using **primitive data types to represent domain ideas**. For example, using an integer to represent an amount of money or a string for a phone number.
  * Using **variables or constants for coding information**. An often-encountered case is using constants for referring to users roles or credentials (like const USER_ADMIN = 1).
  * Using **strings as field names** in data arrays.

## Consequences

  * Code becomes** less flexible** because of use of primitives instead of objects.
  * Primitive data types are much **harder to control**. As a result, we may get variables that aren't valid (supported by the type) or meaningful.
  * Primitives are often related to dedicated business logic. Therefore, leaving this logic unseparated may **violate the Single Responsibility Principle and the Open/Closed Principle**.
  * When data type logic is not separated in a dedicated class, adding a new type or behavior makes the basic class **grow and get unwieldy**.
  * By using primitives, the developer **loses the benefits that come with [object-oriented design](http://espeo.eu/blog/object-oriented-design-guide/)**, like data typing by class name or type hinting.

## Treatment

### Replace Data Value With Object

In most cases, a refactoring method called _Replace Data Value with Object _will cure the code. When the field has its own behavior, associated data or validation rules, creating a class to represent it is the first thing to do. Place the old field and its behavior in the new class, then replace the old data value field that occurs in other parts of the code with an **object instance of the new class.**

Let's say we have a User class that stores the person portfolio URL.

You can code this as follows, using a primitive data type :

![](http://espeo.eu/wp-content/uploads/2017/10/Zaznaczenie_382.png)

> _Refactoring the above to use an object as a data type can result in the following code:_

![](http://espeo.eu/wp-content/uploads/2017/10/Zaznaczenie_383.png)

What did the developer achieve by separating the URL logic to its own class? There's a bit more code, but:

  * The User class is no longer responsible for URL validation.
  * URLs can be used in other classes without code duplication (duplicating validation).
  * It's possible that the URL logic will expand (e.g. with a method to return the transfer protocol, like FTP, HTTP), and when separated, the User class won't get longer and grow from the logic that doesn't directly concern it.

### Dealing With Type Code

Type code occurs when a developer wants to set allowable values, but instead of creating a separated data type, he or she creates a bunch of numeric or string constants with the purpose to represent all possible values for his/her custom 'type.'

When dealing with fields known as type code, the developer needs to consider using one of 3 methods. These are **Replace Type Code with Class, Replace Type Code with Subclasses or Replace Type Code with State/Strategy**. Each method has its benefits and checks in different cases. Knowledge of the disadvantages and advantages of each solution will allow the developer to choose the best one to suits his/her needs.

### Replace Type Code With Class

If the developer doesn't use values of type code in operator conditions and doesn't affect the behavior of the program, he or she can use _Replace Type Code with Class _to get rid of the smell. To do so, the programmer needs to create a new class and use its objects instead of the type code values.

An example may be the User class, which contains information about the status of the relationship.

![](http://espeo.eu/wp-content/uploads/2017/10/Zaznaczenie_384.png)

> _After full refactoring, the logic mentioned above can be coded as below:_

![](http://espeo.eu/wp-content/uploads/2017/10/Zaznaczenie_386.png)

> _What did the developer gain from refactoring?_

  * Instead of a set of primitive values, the programmer has full-fledged classes with all the benefits that object-oriented programming has to offer (typing data by class name, type hinting, etc.).
  * There is no need to worry about data validation, as only expected values can be set.
  * When relationship logic extends, it will be placed in one place dedicated to it.

You shouldn't use this solution when values of a coded type aim to control the behavior of the program. If you want to determine application flow (conditions) with them, I recommend one of the following solutions.

### Replace Type Code With Subclasses, State, or Strategy

When dealing with type code that directly affects program behavior, creating a **subclass for each value of the coded type** or **implementing a State or Strategy pattern** may be the right solution. All of the mentioned methods of refactoring have a lot in common, but each of them has different advantages and disadvantages. The developer needs to decide which one will better suit his/her needs. The choice of solution mainly depends on **how often a class changes its type** and whether **subclassing** is available (due to an already existing hierarchy).

Below, I will focus on showing how you can use the State pattern to remove the smell. You can find the implementation methods of other solutions and a detailed description of when to use them in Martin Fowler's [book about refactoring ](https://martinfowler.com/books/refactoring.html) or on his [blog](https://refactoring.com/catalog/).

When subclassing isn't available and/or an object changes its state (type) often, the _Replace Type Code with State _ method may be the best solution.

To show how you can use it I'll assume that we have an Offer class with a status field. Just like the one below:

![](http://espeo.eu/wp-content/uploads/2017/10/Zaznaczenie_387.png)

> _At the end of refactoring, the code I've shown above can look like this:_

![](http://espeo.eu/wp-content/uploads/2017/10/Zaznaczenie_388.png)

> _What are the benefits of refactoring?_

  * Code gets the same benefits as I mentioned in the Replace Type Code with Class example.
  * Additionally, if the developer needs to add a new value of a coded type, all that needs to be done is to add a new state subclass without altering the existing code (_Open/Closed Principle_).

## Replace Array With Object

When strings are used as field names (keys) in data arrays, it is highly possible that developers will have to switch to objects. So, let's say that we have an array that represents a todo list like this:

![](http://espeo.eu/wp-content/uploads/2017/10/Zaznaczenie_389.png)

> _After refactoring, you can code the logic shown above like this:_

![](http://espeo.eu/wp-content/uploads/2017/10/Zaznaczenie_390.png)

> _What did the developer gain from refactoring?_

  * Instead of a set of primitive values, the programmer has a full-fledged class with all the benefits that object-oriented programming has to offer (typing data by class name, type hinting, etc.).
  * There's no need to worry about data validation, as only expected values can be set.
  * When Relationship logic extends, it will be placed in one place that's dedicated to it.

## Endnotes: Code Smells and Refactoring

The definitions and examples presented in this guide explain what Primitive Obsession is and what its consequences are. **By knowing how to recognize a problem we can avoid it.** Creating separated class/classes requires a bit more effort at the beginning than when using primitives. However, in time, it will surely pay off. If a developer recognizes a problem in existing code, he or she can solve it with one of the suggested techniques. I hope my tips will improve your code quality!

Refactoring is, however, a process that entails following multiple steps to achieve the desired result. In Martin Fowler's book '[Refactoring: Improving the Design of Existing Code](https://martinfowler.com/books/refactoring.html),' you'll find exact instructions for the transformations that you need to do in order to maintain compatibility with code that hasn't been refactored yet.

You can see my gist files right [here](https://gist.github.com/anonymous/c7c275305a57b5391f5c5d32efe40132).

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
