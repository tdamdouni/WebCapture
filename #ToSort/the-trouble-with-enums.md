# The Trouble With Enums

_Captured: 2017-03-01 at 21:08 from [dzone.com](https://dzone.com/articles/the-trouble-with-enums?edition=273881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-01)_

Java's enums have been around for a while, and it's no surprise that you might run into trouble as new features have been released. This article attempts to cover a few odd cases of enum in action so you don't repeat mistakes of the past.

## Enum Abstract Method

An enum type can have abstract methods just like a class. Each enum constant needs to implement the abstract method. An example is as follows:

Use it as follows:
    
    
    System.out.println(animal + " makes sound: " + animal.sound());

## String to Enum

Use _[valueOf()_](https://docs.oracle.com/javase/8/docs/api/java/lang/Enum.html#valueOf-java.lang.Class-java.lang.String-) to look up an enum by the name.
    
    
    Day day = Day.valueOf(Day.class, "MONDAY");

The method throws an _[IllegalArgumentException](http://IllegalArgumentException) _if the name (with the exact case) is not found.

## String to Enum Ignore Case

To lookup an enum by string ignoring the case, you can add a static method to the enum class and use it as shown.

No exceptions are thrown by this code.

## EnumSet: Set of Enums

Java also provides a new type _[EnumSet](https://docs.oracle.com/javase/8/docs/api/java/util/EnumSet.html)_, which is a _[Set ](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html)_of Enums and provides a bunch of useful operations.

Select a range of enums using _[EnumSet.range()](https://docs.oracle.com/javase/8/docs/api/java/util/EnumSet.html#range-E-E-)_. Enum constants are returned in the order of declaration.

The _EnumSet_ can also be used as a type-safe alternative to traditional bit flags.

You can also add to the set using the normal _[Set.add()](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html#add-E-)_ operation. Note that the order of looping is the declared order (and not the add order).

Remove also works in a similar way. In the following example, we are adding all the enum constants to the set using _[EnumSet.allOf()](https://docs.oracle.com/javase/8/docs/api/java/util/EnumSet.html#allOf-java.lang.Class-)_.

## EnumMap: Enum as a Key

_[EnumMap](https://docs.oracle.com/javase/8/docs/api/java/util/EnumMap.html) _is a specialized implementation of _[Map_](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) provided for cases where an enum is used as the key. According to the Javadocs, the storage is compact and efficient. It is used similarly to the way regular _Maps_ are used, with some change in construction; the enum class must be passed into the constructor.

## Enum Name Map

The implementation of the _values()_ method creates an array every time it is invoked. To avoid invoking this method too many times, you can create a name map and use it for lookup. (Yes, that might possibly count as "premature optimization" but hopefully you are resorting to this approach only when invoking _values()_ multiple times.)

And use it like this. Note again that looking up a non-existent name does not result in an _IllegalArgumentException_.

## Comparing Enums: == or equals()?

When comparing enum instances, what should you use?

Both are correct. In fact, [equals() is implemented](http://grepcode.com/file/repository.grepcode.com/java/root/jdk/openjdk/6-b14/java/lang/Enum.java#129) using ==. Since == never throws a NullPointerException, one might prefer using that.

## Should I Use Enum Ordinals?

Enum ordinal is the index of the enum in the list returned by values().

Sometimes you may want to store or transmit the ordinal as a part of storing the state. Should you use the ordinal in such cases? For instance:

The answer is no, it is not a good idea to store or use the ordinal. It is a much better idea to store and transmit the name. Since the _values()_ method returns the array in the order of declaration, using the ordinal might return wrong values if the enum definition is modified to add or remove entries.

Store and use the name. If the enum entry is removed later, _valueOf()_ will throw an exception. Which is much better than using wrong values and not knowing about it.

## Summary

We have now learned some basics about enums in Java. Enums in java are more powerful than in most other languages. Abstract methods can be declared for the enum and specialized implementation can be defined for each enum constant. Looking up enum constants in a case-insensitive operation is another area arising frequently.
