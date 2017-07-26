# Functional Programming in Java 8 (Part 2): Optionals

_Captured: 2017-02-08 at 21:21 from [dzone.com](https://dzone.com/articles/functional-programming-in-java-8-part-2-optionals?edition=268916&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-08)_

### Use Optionals when there is a clear need to represent 'no result' or where null is likely to cause errors. Otherwise, stick to nulls.

Check out this [8-step guide](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code! Brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431).

After we made our first big steps into functional programming in the [last post](https://dzone.com/articles/functional-programming-in-java-8-part-1-functions-as-objects), we will talk about Optionals in today's part.

## Why Do We Need Optionals?

Hand on heart, you also think that null is annoying, don't you? For every argument that can be null, you have to check whether it is null or not.

These lines suck! This is a boilerplate that bloats up your code and can be easily forgotten. So how can we fix that?

## Introducing Optionals

In Java 8, [java.util.Optional<T>](https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html) was introduced to handle objects which might not exist better. It is a container object that can hold another object. The Generic _T_ is the type of the object you want to contain.

The Optional class doesn't have any public constructor. To create an optional, you have to use `Optional.of(object)` or `Optional.ofNullable(object)`. You use the first one if the object is never, ever null. The second one is used for nullable objects.

### How Do Optionals Work?

Options have two states. They either hold an object or they hold null. If they hold an object, optionals are called _present_, if they hold null, they are called _empty_. If they are not empty, you can get the object in the optional by using `Optional.get()`. But be careful, because a _get()_ on an empty optional will cause a `NoSuchElementException`. You can check if a optional is present by calling the method `Optional.isPresent()`
    
    
        Optional<String> optionalS1 = Optional.of(s); // Will work
    
    
        Optional<String> optionalS2 = Optional.ofNullable(s); // Will work too
    
    
        Optional<String> optionalNull1 = Optional.of(nullString); // -> NullPointerException
    
    
        Optional<String> optionalNull2 = Optional.ofNullable(nullString); // Will work
    
    
        System.out.println(optionalS1.get()); // prints "Hello World!"
    
    
        System.out.println(optionalNull2.get()); // -> NoSuchElementException
    
    
            System.out.println("Is empty"); // Will be printed

## Common Problems When Using Optionals

### Working With Optional **and** Null

This is just the wrong use of an Optional! If you get an Optional (in the example, you get one from the DB), you don't have to look whether the object is null or not! If there's no string in the DB, it will return `Optional.empty()`, not `null`! If you got an empty Optional from the DB, there would also be a `NoSuchElementException` in this example.

### Using isPresent() and Get()

As I already said, you should always be 100% sure if an Optional is present before you use `Optional.get()`. You wouldn't get a `NoSuchElementException` anymore in the updated function. But you shouldn't check a optional with the `isPresent() + get()` combo! Because if you do it like that, you could have used _null_ in the first place. You would replace `first.isPresent()` with `first != null` and you have the same result. But how can we replace this annoying if-block with the help of Optionals?

The `Optional.ifPresent()` method is our new best friend to replace the if. It takes a function, so a lambda or method reference, and applies it only when the value is present. If you don't remember how to use method references or Lambdas, you should read the [last part](https://dzone.com/articles/functional-programming-in-java-8-part-1-functions-as-objects) of this series again.

#### Returning a Modified Version of the Value

In this method, we want to double the value of an optional, if it is present. Otherwise, we return zero. The given example works, but it isn't the functional way of solving this problem. To make this a lot nicer, we have two function that are coming to help us. The first one's `Optional.map(Function<T, R> mapper)` and the second one's `Optional.orElse(T other)`. `map` takes a function, applies it on the value and returns the result of the function, wrapped in an Optional again. If the Optional is empty, it will return an empty Optional again. `orElse` returns the value of the Optional it is called on. If there is no value, it returns the value you gave `orElse(object)` as a parameter. With that in mind, we can make this function a one liner.

## When Should You Use Nullable Objects vs. Optionals?

You can find a lot of books, [talks](https://www.youtube.com/watch?v=Ej0sss6cq14), and discussions about the question: Should you use null or Optional in some particular case. And both have their right to be used. In the linked talk, you will find a nice rule that you can apply in most of the cases. Use Optionals when _"there is a clear need to represent 'no result' or where null is likely to cause errors."_

So you shouldn't use Optionals like this:

Because a null check is much easier to read.

You should use Optionals just as a return value from a function. It's not a good idea to create new ones to make a cool method chain like in the example above. Most of the times, null is enough.

## Conclusion

That's it for today! We have played with the Optional class. It's a container class for other classes which is either present or not present(_empty_). We have removed some common code smell that comes with Optionals and used functions as objects again. We also discussed when you should use null and when Optionals.

In the next part, we will use _Streams_ as a new way to handle a Collection of Objects, like Iterables and Collections.

Thanks for reading and have a nice day!

The Java Zone is brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered). Check out this [8-step guide](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code!
