# Code Smells: Deeply Nested Code

_Captured: 2017-08-24 at 23:49 from [dzone.com](https://dzone.com/articles/code-smells-deeply-nested-code?edition=317405&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-21)_

Or: I wants all your data, give it to me… my precious….

Continuing the series of [code smells](https://blog.jetbrains.com/idea/tag/code-smells/) and what do about them, in this post, I examine some fairly innocent looking code that defies the obvious refactoring. Although the code example itself is fairly trivial, it's actually a symptom of a problem found again and again in this particular project: deep nesting of code. This can be for loops, if statements, even lambda expressions or inner classes, or combinations of all of the above.

## **The Smell: Deeply Nested Code**

The code I stumbled over was a double for loop with an inner if statement.
    
    
                for (final String n : mf.getLoadNames()) {
    
    
                    if (storedName.equals(n)) {

What's wrong with this code? It's OK to read, if we forgive the single-character variable names, and are used to working in a procedural way - we're looking at all the fields, and then for each field we look at all the names, and if a name matches the name we're looking for, we return that field. Simple.

## **Solution 1: Java 8 to the Rescue**

The lovely [arrow shape of the code](http://wiki.c2.com/?ArrowAntiPattern) here is the bit that looks suspicious. I've shown in previous [blogs](https://blog.jetbrains.com/idea/2016/12/intellij-idea-inspection-settings-for-refactoring-to-java-8/) and [talks](https://youtu.be/2xOtyGUTpQU) that nested for/if statements can often be replaced with Java 8 Streams, and this frequently gives better readability. I was wondering why IntelliJ IDEA doesn't suggest this particular code can be collapsed into a Stream operation, seems like maybe [flatMap](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html#flatMap-java.util.function.Function-)/[findFirst](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html#findFirst--) could be the answer. But it's not that simple. I tried crafting the correct expression without automagic help from the IDE, and came up with:
    
    
                                              .flatMap(mappedField -> mappedField.getLoadNames().stream())

Well, that's no good. I want to return the `mappedField` that contains the name, not an `Optional` containing the name that I found. And I can't get to `mappedField` later in the Stream. The best I can do is:

Urgh. Nasty.

## **Solution 2: Better Encapsulation**

What's the real problem here? It seems like the original code is reaching deep inside another object, stealing all its data, riffling through it and then only caring about the top level object. Removing the loop syntax, what you have is, effectively:

This what the [Law of Demeter](https://en.wikipedia.org/wiki/Law_of_Demeter) warns us against, therefore suggests to me we consider a [tell-don't-ask approach](https://martinfowler.com/bliki/TellDontAsk.html). Wouldn't it be prettier to ask `mappedField` if one of its names matched the name we wanted?

The other for loop that loops over the names is moved inside the `MappedField` class, so only this class needs to understand the internals of how these names are stored. Let's step through one way of performing this refactoring. There's more than one approach of course, this is just one example.

Firstly, extract the inner loop to a separate method. In this case, let's call it `hasName`:

![Extract Method hasName](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/01ExtractMethod-2.png)

> _Extract Method hasName_

The extracted method doesn't compile, but that's OK because I wanted to change the method signature anyway - I want the method to return true if the name matches one of the `MappedField`'s names, false otherwise.

_![Change method signature to return a boolean](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/2ChangeMethodSignature-2.gif)_

> _Change method signature to return a boolean_

Now I want to actually use this return value in the original method:

_![Use the boolean value returned](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/3UseBooleanValue-2.gif)_

> _Use the boolean value returned_

The code compiles now and behaves the same way as the original. Now I just need to move the `hasName` method into the `MappedField` class.

_![Move method into MappedClass](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/4MoveMethod-2.gif)_

> _Move method into MappedClass_

So now the `MappedField` has the `hasName` method:

…and the class containing the `getMappedField` method (`MappedClass`) no longer needs to know the internals of how the `MappedField` stores its names, or even that it can have more than one name.

## **Optional Extra Step: Java 8**

If you so wish, both of these methods can now use Java 8 syntax. In the case of `hasName`, this is more descriptive too, it states we only care if any of the names match the given one.

![Java 8 Streams version of hasName](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/5Java8NameMatches.png)

> _The hasName method can be converted to use Java 8 Streams_

We end up with:

Meanwhile, `getMappedField` can also benefit from Java 8:

![Java 8 version of getMappedField](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/6Java8GetMappedField.png)

> _The getMappedField method can be converted to use Java 8 Streams too_

The final code for `getMappedField` looks more like I wanted the first time I saw it:

## **Final Step, Unrelated To This Code Smell**

I stumbled over the original code when I was looking for methods that suit an `Optional` return type. This seems like a good candidate, it returns null in the case that the storedName doesn't match any `MappedField`. Now we're using the Java 8 syntax, not only is it clearer that we can use an `Optional`, but easier:

All we have to do now is deal with the returned `Optional` in the places that call this method, but that's the subject for another blog post…

## **In Summary**

In languages like Java, it's very normal to see multiple nested for loops and if statements dotted around the place, particularly in pre-Java-8 code. This sort of code is perfectly acceptable for manipulating low-level data structures (arrays, collections etc), but should really be treated as a smell if you see it in your domain code, particularly if the nesting gets very deep. In our example, although `MappedClass` needs to know about its `MappedField`s, it shouldn't need to poke around the internals of `MappedField` to answer questions, it should be asking `MappedField` questions of its own.

Symptoms:

  * Deeply nested code, usually loops and/or conditionals
  * Chained method calls that are all getters (or other non-builder, non-DSL method chains).

Possible solutions:

  * Consider tell, don't ask. Where the code previously grabbed internal data and did checks against it, move those checks into the object containing the data and create a method with a useful name to help other objects answer their questions.
  * Examine your encapsulation. Does the data really need to leak out into other classes? Should data and/or responsibilities be relocated so that operations on the data are moved closer to the data itself?
  * [Collection Encapsulation](https://martinfowler.com/bliki/EncapsulatedCollection.html). Sometimes this pattern is a sign that you're using a data structure as a domain object. Consider encapsulating this data structure (Collection, array, etc) inside a domain object of its own and adding helper methods to let other objects ask it questions rather than poke around its internals.
