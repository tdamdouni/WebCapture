# About Immutability in OOP

_Captured: 2018-03-06 at 23:10 from [dzone.com](https://dzone.com/articles/about-immutability-in-object-oriented-programming?edition=366209&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-06)_

[Build vs Buy a Data Quality Solution: Which is Best for You?](https://dzone.com/go?i=251321&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) Gain insights on a hybrid approach. Download white paper now!

To explain what immutability is, first we need to understand what mutability is. Mutability means the possibility to change the state of an entity while its identity remains the same. Obviously, immutability is the opposite. Once an entity exists, its state will never change.

How are these concepts represented in OOP? Well, in OOP, the entities are the objects. So, the immutability concept in OOP is characterized by immutable objects. Once an object is constructed, it will have the same state for as long as it lives.

An object has three characteristics:

  * Identity: what makes the object unique
  * Behavior: what the object does
  * State: what the object has

It's very important to understand those characteristics and the difference between them. Think of a car. What is its behavior? Well, the main behavior is that it can transport you from point A to point B. What does it have? A lot of things like doors, chairs, wheels, and an engine. But those things can be changed anytime. What makes it unique? What do the police use to report a car that goes too fast? The answer is the license plate. They use this because it is unique to your car. If you have a license plate, then no other car can have a license plate with the same code as yours.

So, if you design a car object, the license plate is what you use to implement the equals method, and it is mandatory to design the object in such a manner that the license plate will be unique and unchangeable. This way, once the car object is constructed, you can pass the car object through the whole application and no one could change its license plate. So, its engine or wheels could be changed, but it will still be the same car.

Like I've said before, for an object to be immutable, once it's created, its state, just like its identity, should be unchangeable. So, if we use the same example, no one can change the car's license plate, but also no one can change any other characteristic of the car. It will remain the same car with the same engine and wheels for as long as it lives.

## The Object's Immutable State

So how do we represent the state of an object? A generally accepted response is that the object's state is represented by its fields. So, for an object to be immutable, it means that its fields will be unchangeable in all situations.

If immutability means that the object's fields are unchangeable, what does this imply? An object could be referenced in a lot of places. Everyone can call all of its public methods or modify its public fields. So, the first step is to make all the fields private and to give access to them just through methods. We can control what happens in a method, but if a field is public, then we don't have any control over it and anyone could change it.

Another step is to make all the fields final. This guarantees that once the field is created, no one can change it.

If the field is a primitive, then making it private and final is enough for it. However, if the field is a mutable object, then this is not enough to guard it. That field isn't actually an object, it is just a reference that indicates where the object is stored. So, being final and private, then that reference can't be changed, but you have access to that object and you can call its methods. And if the object is mutable, then its state could be changed. So, how to solve this?

Well, if you need to return this object through a getter, then create a defensive copy of it and return the copy instead. For example, let's say you have an ArrayList of integers. The Integer object is immutable, but the list isn't. So, if you need to return it through a getter, then create another list, copy all the elements to it, and return the copy. Anyone who calls the getter will have just a copy of the list. They could modify it, but it will not have any impact on the original list.

With this being said for the getters, what about the setters? If your object is immutable, it's obvious that it should not have any setter. The scope of a setter is to set a field's value in your object, which, in the case of an immutable object, is not allowed.

If your class receives a mutable object as a parameter in the constructor, that must be assigned to a field, then, again, create a defensive copy of it and assign the copy to the field. But it is not enough to return defensive copies. Let's say that in your constructor, you receive a mutable object as a parameter and you assign it to a field exactly as you received it. The field is private and final and in the getter, you create a defensive copy of it and return the copy. But, if you didn't copy it in the constructor, then the object could be referenced in other places, and it could be modified, resulting in the mutation of your object's state.

What if our getters are overridden? Then they could be overridden to return the original fields instead of returning the defensive copies. So, the last rule is to not allow your methods to be overridden. There are multiple ways to achieve this. You could make your class final, or make all the getter methods final, or you can use a private constructor and a static factory method to create instances because if the class has a private constructor, it can't be extended.

So the rules are:

  * Declare all fields private and final
  * If a field is a mutable object, then create and return a defensive copy of it
  * Don't expose setter methods
  * If your class receives (in the constructor) a mutable object as a parameter that must be assigned to a field, create a defensive copy of it and assign the copy to the field
  * Don't allow your getter methods to be overridden

Java provides us with a bunch of immutable objects already. All primitive wrapper classes, like Integer, Byte, Long, Float, Double, Character, Boolean and Short, are immutable in Java. If your object has a field that, for example, is an Integer, setting it private and final is enough to guard it.

## A Short Example

According to these rules, let's see how an object should look to be immutable:
    
    
        public ImmutableObjectExample(int a, Integer b, List <Integer> c) {
    
    
            this.a = a; // a is a primitive, so it doesn’t need a defensive copy
    
    
            this.c = new ArrayList <> (c); // The list in not an immutable object so we have

Maybe you have observed that the way of creating defensive copies is different in the constructor than in the getter. I did so because I wanted to show that there is not a single way to make a defensive copy for a list. The most important thing when making a defensive copy of a list is what elements it holds. If the list's elements are immutable objects, then, for creating a defensive copy, you just have to create another list where you put the same elements, and there are multiple ways for doing this. We can use the constructor, or we can use the Java 8 Collectors class, or the Collections.copy() static method.

The copy is a mutable object, and you can modify it, you can add elements to it, or remove elements, but you will not affect the original list. And, even if, in the copied list, there are the same objects as in the original list, the elements, being Integer in this case, are immutable so they can't be modified even if they are referenced in multiple places.

Like I said before, you need to make defensive copies in the constructor and in the getters as well. But there is another option here. You can create an immutable object based on the constructor's parameter and store it instead. Then, even if you receive a mutable object, the object's field will be an immutable copy of it and you can return it directly. [Here](http://www.baeldung.com/java-immutable-list) you can see how to create immutable lists from normal ones.

Let's see how our class will look in this case.
    
    
        public ImmutableObjectExample(int a, Integer b, List <Integer> c) {
    
    
            this.c = Collections.unmodifiableList(c);

There is a small catch here. However, a List is a List. The getter returns an object that implements the List interface and, of course, it will have the List's methods like add or remove. But if you try to call one of these methods, it will throw an exception. This is how this an unmodifiable list is implemented.

Well, you got the idea. If a field is mutable, protect it with a defensive copy. If it is a primitive or an immutable object, then setting the accessor private and final is enough.

## Modifying an Immutable Object

You can't.

What you can do is another defensive copy, but this time, you have to copy the whole object and add your modification. Looking at our example, if we have an instance of our immutable class, we can create a copy of it by calling the class's constructor with the information from the existing instance. The getter methods return defensive copies of the original object's fields, so it is safe to construct the copy using the objects returned by those getters.

So let's say that we have an instance constructed this way:
    
    
    ImmutableObjectExample originalInstance = new ImmutableObjectExample(10, 20, Arrays.asList(0, 1,2));

If we want to make a copy where the first field is increased by 1 ,then we can construct it this way:

The main point is that we can't modify an immutable object, but instead, we can create another object based on it. Calling the constructor every time looks pretty ugly, but it doesn't have to be this way. We can have some factory methods that call the constructor for us and, this way, the code will not look so heavy.

## But Why?

It seems that we have to put a bigger effort when we implement an immutable class. What do we gain from this effort? Well, having an immutable object guarantees that it will stay the same for as long as it lives. Ever get one of those surprises where one object is suddenly modified and you don't know by whom? Maybe you saw some pieces of code like this:

This is one of the sources of those frustrating surprises. Modifying a parameter is an anti-pattern because it will be very hard to reason about the object's state. But this happens -- and it will continue to happen -- and the only way to secure a parameter object is to make it immutable. You should never rely on the fact that methods don't try to alter a parameter's state.

The advantages of immutable objects are more relevant in a multithread environment. Immutable objects, being impossible to be modified, are thread-safe. No matter in how many threads an immutable object is used by, it is thread-safe. An immutable object gives access to its mutable fields, if any, using defensive copies of them, so each thread that uses one of those fields actually uses a defensive copy of it, freeing us from the fear that we have escaped to synchronize some code blocks that modify that object. Cool right?

Besides the safety that immutable objects bring in our code, another advantage is garbage collection optimization. [Here](http://wiki.c2.com/?ImmutableObjectsAndGarbageCollection) is a great article about why it is simpler for the Java garbage collector to make decisions about immutable objects.

## Not a Silver Bullet

Maybe it is a bit harsh to say that silver bullets don't exist, but this is what I believe. Nothing is perfect, and there isn't a single concept that has just advantages, including immutable objects.

The main problem with immutable objects is performance because instead of modifying something, you have to build something new. If your application makes a lot of modifications, then creating lots of objects instead of modifying the existing ones is not the best approach. So we can't escape from mutation, but it is recommended to keep it at a minimum level.

However, there are a few things that we can do to make the immutable objects more optimal.

  * Hold immutable fields. If you design your class to hold just immutable fields then you don't have to create defensive copies of them in the constructor or in getters.
  * Use mutable objects in local methods. There is a way to benefit from the speed of modifying a mutable object while keeping the state immutable. The solution is to keep mutable objects local to a method. If we have to do a lot of modifications to an immutable object, we can transform it in a mutable one, modify it, and then we can create and return another immutable object based on it. If a mutable object is created and exists just in a local method and is not referenced anywhere else, then it can't be unexpectedly changed from other places, and modifying it is thread-safe. So we have all the advantages of immutability and also the speed of mutability.

For example, let's say that we want to concatenate a list of strings. This is how a basic implementation looks:

String is an immutable object. Concatenating two strings with the "+" operator actually creates another string. So, using the above implementation, we are creating a bunch of string objects for every list item. Wouldn't it be more efficient to just modify one string? Well, yes, and we can do this using a mutable variant of String called StringBuilder.

Let's see how it looks.

So, we receive a list of immutable objects as a parameter and we can't modify them. Good. And, also, we return another immutable object as it is desired. Does it matter for the state's immutability that we've created a mutable object inside a method? No, it doesn't, and it helps us with the speed.

## Conclusion

Growing the advantages while keeping the disadvantages low depends on our wisdom to choose when and how to use immutable objects. While it could be less performant, because any modification it actually means the creation of another object, immutability cleary brings huge advantages. You are free to share your immutable objects in multiple places or to use them in a multithread environment. No matter what, their state will never change and the code will be much safer -- and be easier to reason about it.

[Build vs Buy a Data Quality Solution: Which is Best for You?](https://dzone.com/go?i=251322&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) Maintaining high quality data is essential for operational efficiency, meaningful analytics and good long-term customer relationships. But, when dealing with multiple sources of data, data quality becomes complex, so you need to know when you should build a custom data quality tools effort over canned solutions. [Download our whitepaper](https://dzone.com/go?i=251322&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) for more insights into a hybrid approach.

Opinions expressed by DZone contributors are their own.
