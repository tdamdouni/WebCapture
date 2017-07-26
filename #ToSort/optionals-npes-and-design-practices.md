# Optionals: NPEs and Design Practices

_Captured: 2017-06-18 at 21:38 from [dzone.com](https://dzone.com/articles/optionals-npes-and-design-practices?edition=305103&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-17)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D).

While programming, we have all faced the (in)famous **NullPointerException**. And I believe we all would agree that encountering **NullPointerExceptions** is also a pain. Just to keep the readers informed, the famous computer scientist Tony Hoare introduced **null** references, and even he thinks it was a** million-dollar mistake**. We all know it's very easy to implement but it's quite unpredictable as well. And that's why developers need to be very cautious.

## The Usual Way

Let's consider three simple POJOs as follows.

Just to give some context, an employee can own a car (not mandatory though), a car can have insurance (not necessarily), and the insurance must always have a name. But keep the following sections in mind.

Let's say we want to get the name of the insurance by providing a person instance.

This is what we usually do to take preventive measures so that we don't encounter the dreaded NullPointerException. But this also pollutes the source code and, in my opinion, it should be considered an antipattern.

## Another Usual Way

Such deep nesting for null checks, as mentioned in the previous section, looks a bit obtuse. And sometimes, people do it in a different way.

This looks pretty okay to me, as it doesn't comprise the deep nesting null checks. But still, it follows the same antipattern to check for nulls, just in a slightly different way.

## Why NULL Is Not Good

  1. It deteriorates the readability of the source code.
  2. It is not semantically correct to present something without a value.
  3. It is against the ideology of Java, as Java hides pointers from the developers except in the situation of null references.

## Alternatives to NULL

A few languages such as Scala and Groovy removed the dreaded use of null references to signify the absence of a value. Similar code can be written in Groovy in a very concise manner.

**The ? is the important part.** This is known as the **Safe Navigation operator** in Groovy and it clearly shows much more readable code while, at the same time, removing the possibility of encountering dreaded null references.

## Java's Endeavor

Now we should ask what a Java developer can do to achieve something similar that prevents the possibility of NullPointerExceptions while maintaining readable and maintainable source code. Java's language designers chose a similar approach to that Groovy or Scala with the introduction of a new class: **Optional.**
    
    
        public static < T > Optional < T > empty() {}
    
    
        public static < T > Optional < T > of(T value) {}
    
    
        public static < T > Optional < T > ofNullable(T value) {}
    
    
        public void ifPresent(Consumer << ? super T > consumer) {}
    
    
        public Optional < T > filter(Predicate << ? super T > predicate) {}
    
    
        public < U > Optional < U > map(Function << ? super T, ? extends U > mapper) {}
    
    
        public < U > Optional < U > flatMap(Function << ? super T, Optional < U >> mapper) {}
    
    
        public T orElseGet(Supplier << ? extends T > other) {}
    
    
        public < X extends Throwable > T orElseThrow(Supplier << ? extends X > exceptionSupplier) throws X {}

This class is primarily used to signify the absence or presence of a value. If you believe a value can or cannot be always present, it is better to use an Optional type. In our previous example, an employee may or may not contain a car, and that's why it is better to return **Optional <Car>** instead of simply returning **Car**.

Let's see how we could design our previous example:

I have not discussed the static factory **ofNullable(..)** method, but just consider it as a wrapper utility method that wraps a value irrespective of its reference.

Just by seeing the API, one could easily understand what needs to be done when an optional type is encountered. For a developer, an encounter with such optional types always signifies the possibility of the absence of a value and, hence, developers can take proper measures for this.

From the class overview, we can clearly see that an **Optional** can be created in various ways.

  1. **of(..)**: This allows the creation of an **Optional** instance wrapping a non-null value.
  2. **empty()**: This creates an empty **Optional.**
  3. **ofNullable(..)**: This allows the creation of an **Optional** instance wrapping any value (null or non-null).

### Optional Extraction and Transformation

So far, we have already seen how to create **Optional** instances. Now we should see how to extract the value or transform it to another.

**get()** returns the contained value or it throws **NoSuchElementException** if the **Optional** instance is empty.

But how should we use this?

This is what we mostly do to evade NullPointerExceptions. Now with Java 8 Optionals, we can write the same as follows:

But do you consider it as an improvement over the nasty null checks?

I used to consider it as an improvement, as it hides the null pointers, but later on, I felt it polluted the source code quite a bit. But I am not against the use of returning Optional as types from methods or wrapping variables. I will discuss my reasons behind it in the following sections.

Let's consider the previous method:

This is very clean code but the NullPointerException is lurking, and that's why we need to incorporate several null reference checks (we have already seen this previously).

If we incorporate public String Optional in designing a good API, this could have been achieved in a more concise way:

Isn't it really nice and a cleaner approach? I know this gets confusing to some programmers who are not yet comfortable with the Java Streams API. I would strongly suggest having a quick look at Java 8 Streams to understand the beauty of Optionals.

Another example would be to get the insurance name if the name of the person starts with "P":

## Design Practices

Now I would like to share some ideas on designing our previously discussed POJOs in a bit of a different way.

### API Design Practice 1

Here, I have declared the member variable to be of the Optional type. In my opinion, this is also very user-friendly, and users or consumers of this class can easily understand the nature of this class. In this context, an employee **has a** car, which is **Optional**, -- that is, an employee **may** or **may not** have a car as well.

### API Design Practice 2

This is also quite intuitive, but it lacks the idea of clearly showing the absence of a member instance. To understand any system, developers always need to understand the object model first. And understanding an object model requires us to understand the domain objects. In this scenario, an employee is a domain object that **has a** car as if it is mandatory for an employee. But in reality, an employee may or may not have a car. We could achieve it when we retrieve its value (**getCar()**) and we could then notice its possibility of the absence of a contained value, as the method returns **Optional**.

It solely depends on the developer. I personally prefer the first approach, as it is clear in understanding the domain model, while the second approach has advantages for serialization. As **Optional** doesn't implement **Serializable**, it is not serializable in our first approach. If we use DTOs, we can adapt our implementation to the second approach.

### Optional in Method or Constructor Arguments

As I have mentioned previously, Optional in classes clearly shows what the consumers are supposed to do. So, if a constructor or method accepts Optional elements as arguments, it means that the argument is not mandatory.

On the other hand, we need to pay the price of polluting the codebase with Optionals. It is at the developer's sole discretion to use it carefully. I personally prefer not to use Optional in method arguments while, if needed, we can still wrap it inside an Optional instance and perform the necessary operations on it.

### Optional in Method Return Types

Java Language Architect Brian Goetz also advises returning Optional in methods if there is a possibility of returning null. We have already seen this in our API Design Practice 2.

### Throw Exceptions From Methods or Return Optional

For years, Java developers followed the usual way to throwing exceptions to signify an erroneous situation in a method invocation.

If the consumer of this method encounters a **RuntimeException**, that's due to a problem in opening a connection to the specified URL. On the other hand, we could also use Optional the following way:

I think this is very intuitive, as it clearly says that it returns an Optional instance that may or may not have a value. And that's why my inclination is to return Optional from methods that could have such a null encounter possibility.

### Optional Return Types in Private Methods

Private methods are not clearly meant to understand or analyze any significant part of a project. Hence, I think we still can make use of null checks to get rid of overly many Optionals. But if you think you still can use the method in a more clean and concise way, you can return Optional as well.

For better comprehension, I have formulated an example as follows:
    
    
            for (int temp = 0; temp < nList.getLength(); temp++) {
    
    
                values.put(getAttribute(key).orElseThrow(IllegalArgumentException::new), value);
    
    
            logger.error("{}", ex.getMessage(), ex);
    
    
    private Optional < Attribute > getAttribute(final String key) {
    
    
            .filter(x - > x.value()

I could have written the second method in a more usual way:

### Optional Return Type in Private Methods Returning Collections or Any of Its Subtypes

As a first example, consider the code you need to implement a method to list files from a specified path in Java:
    
    
            files = Files.list(Paths.get(path));

We could achieve more concise code as follows:

Notice that the return type in the concise method still remains **List** instead of **Optional**. It is preferable to follow the usual practice of returning an empty list instead of using Optional.

It is apparent that the Stream ways of using Optional are more concise. Optional is a utility data container that helps developers to get rid of null references. In addition, it provides lots of useful methods that ease the programmer's work. But Optional can be misused heavily and can pollute the codebase if the developer is not well-aware of the primary use of Optionals. That's why I strongly suggest everyone have a go at the Stream-oriented methods in Optionals that help developers to write concise and maintainable code.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D).
