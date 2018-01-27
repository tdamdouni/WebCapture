# Kotlin DSL: From Theory to Practice

_Captured: 2017-12-29 at 20:20 from [dzone.com](https://dzone.com/articles/kotlin-dsl-from-theory-to-practice?edition=347143&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-29)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

SQL, RegExp, Gradle -- what do they have in common? All of them represent an example of using domain-specific languages, or DSLs. Languages of this type aim to solve a specific problem, such as database querying, finding matches in the text, or build process description. Kotlin offers a large number of features for building your own domain-specific language. In this article, we'll discover the developer's toolkit and implement a DSL for a real-world domain.

![Kotlin DSL](https://dzone.com/storage/temp/7600576-sugar.png)

> _Kotlin DSL_

I'll try to explain the language syntax as simple as possible, however, the article still appeals to developers who consider Kotlin as a language for custom DSL building. At the end of the article, I'll mention Kotlin drawbacks worth taking into account. The presented code snippets are relevant for Kotlin version 1.2.0 and are available on GitHub.

## What Is a DSL?

All programming languages can be divided into general-purpose and domain-specific languages. SQL, regular expressions, and build.gradle are often cited as examples of DSLs. These languages are limited in functionality, but they are able to effectively address a certain problem. They allow you to write imperative code (we shouldn't explain how to solve the problem) but in more or less a declarative way (we just declare the task) in order to obtain the solution based on the given data.

Let's say you have the standard process definition that can be eventually changed and enhanced but generally, you want to use it with different data and result formats. By creating a DSL, you create a flexible tool for solving various problems within one subject domain, no matter how the solution is obtained. So, you create a sort of API that, if mastered, can simplify your life and make it easier to keep the system up-to-date in the long-term.

The article deals with building an "embedded" DSL in Kotlin as a language implemented on the general-purpose language syntax. You can read more about it [here](https://en.wikipedia.org/wiki/Domain-specific_language#Usage_patterns).

## Implementation area

To my mind, one of the best ways to use and demonstrate Kotlin DSL is testing.

Suppose that you've come from the Java world. How often have you been faced with declaring entity instances of an extensive data model? You've been likely using some builders or, even worse, special utility classes to fill the default values under the hood. How many overridden methods have you had? How often do you have to make little changes from default values, and how much effort does this require today?

If these questions stir up nothing but negative feelings, this article is for you.

That's the way we've been doing it for a long time in our project in the area of education: We used builders and utility classes to cover one of our most important modules (school timetable scheduling) with tests. Now this approach has given way to the Kotlin language and DSL, which is used to describe test scenarios and check the results. Throughout the article, you can see how we took advantage of Kotlin so that testing of the scheduling subsystem is not a torture anymore.

In this article, we will dive into details of constructing a DSL that helps to test an algorithm building teachers and students schedules.

## Key Tools

Here are the basic language features that allow you to write cleaner code in Kotlin and create your own DSL. The table below demonstrates the main syntax enhancements that are worth using. Take a look at it carefully. If most these tools are unfamiliar to you, you might want to read the whole article. If you don't know one or two of them, feel free to fast forward to corresponding sections. In case there's nothing new for you, just skip to the DSL drawbacks review at the end of the article. Feel free to propose more tools in the comments.

_**Tool**_
**DSL syntax**
**General syntax**

Operators overloading

collection += element

collection.add(element)

Type aliases

typealias Point = Pair

Creating empty inheritor classes and other duct tape

get/set methods convention

map["key"] = "value"

map.put("key", "value")

Destructuring declaration

val (x, y) = Point(0, 0)

val p = Point(0, 0)   
val x = p.first  
val y = p.second

Lambda out of parentheses

list.forEach { ... }

list.forEach({...})

Extension functions

mylist.first();

// there isn't first() method in mylist collection

Utility functions

Infix functions

1 to "one"

1.to("one")

Lambda with receiver

Person().apply { name = "John" }

N/A

Context control

@DslMarker

N/A

Found anything new? If so, let's move on.

I omitted delegated properties intentionally, as, in my opinion, they are useless for building DSLs, at least in our case. Using the features above, we can write cleaner code and get rid of voluminous "noisy" syntax, making development even more pleasant (could it be?).

I liked the comparison I met in the "Kotlin in Action" book: In natural languages, like English, sentences are built out of words, and grammar rules define the way of combining these words.

Similarly, in DSLs, one operation can be constructed from several method calls, and the type check guarantees that the construction makes sense. For sure, the order of callings cannot always be obvious, but it is entirely up to the DSL designer.

It is important to stress that this article examines an "embedded DSL", so it is based on a general-purpose language, which is Kotlin.

## Final Result Example

Before we begin to design our own domain-specific language, I'd like to show you an example of what you'll be able to create after reading this article. The whole code is available on the GitHub repository at this [link](https://github.com/ivan-osipov/kotlin-dsl-example).

The DSL-based code below is designed to test the allocation of a teacher for students for the defined disciplines. In this example, we have a fixed timetable, and we check if classes are placed in both teacher's and students' schedules.
    
    
                    thursday("08:00") + sameDay("11:00") + sameDay("14:00")
    
    
            for ((day, lesson, student, teacher) in scheduledEvents) {
    
    
                teacherSchedule[day, lesson]!!.student shouldEqual student
    
    
                studentSchedule[day, lesson]!!.teacher shouldEqual teacher

## Toolkit

All the features for building a DSL have been listed above. Each of them is used in the example from the previous section. You can examine how to define such DSL constructs in my [project](https://github.com/ivan-osipov/kotlin-dsl-example) on GitHub.

We will refer to this example again below in order to demonstrate the usage of different tools. Please bear in mind that the described approaches are for illustrative purposes only, and there may be other options to achieve the desired result.

So, let's discover these tools one by one. Some language features are most powerful when combined with the others, and the first in this list is the lambda out of parentheses.

### Lambda Out of Parentheses

A lambda expression is a code block that can be passed into a function, saved or called. In Kotlin, the lambda type is defined in the following way: (list of param types) -> returned type. Following this rule, the most primitive lambda type is () -> Unit, where Unit is an equivalent of Void with one important exception. At the end of the lambda, we don't have to write the _return..._ construction. Therefore, we always have a returned type, but in Kotlin, this is done implicitly.

Below is a basic example of assigning a lambda to a variable:

Usually, the compiler tries to infer the type from the already known ones. In our case, there is a parameter. This lambda can be invoked as follows:

In the example above, the lambda takes one parameter. Inside the lambda, this parameter is called by default, but if there were more, you would have to specify their names explicitly or use the underscore to ignore them. See such a case below:
    
    
    val helloPrint: (String, Int) -> Unit = { _, _ -> println("Do nothing") } 

The base tool -- which you may already know from Groovy -- is the lambda out of parentheses. Look again at the example from the very beginning of the article: Almost every use of curly brackets, except the standard constructions, is a lambda. There are at least two ways of making an x { ... }:-like construction:

  * The object x and its unary operator _invoke_ (we'll discuss it later);
  * The function x that takes a lambda.

In both cases, we use lambdas. Let's suppose there is a function x(). In Kotlin, if a lambda is the last argument of a function, it can be placed out of parentheses. Furthermore, if a lambda is the only function's parameter, the parentheses can be omitted. As a result, the construction x({...}) can be transformed into x() {}, and then, by omitting the parentheses, we get x {}. This is how we declare such functions:

In a concise form, a single-line function can be also written like this:

But what if x is a class instance or an object instead of a function? Below is another interesting solution based on a fundamental domain-specific concept: operator overloading.

### Operator Overloading

Kotlin provides a wide, but somewhat limited variety of operators. The _operator_ modifier enables to define functions by conventions that will be called under certain conditions. As an obvious example, the plus function is executed if you use the "+" operator between two objects. The complete list of operators can be found in the docs by the link above.

Let's consider a less trivial operator: _invoke_. This article's main example starts with the _schedule { }_ construct that defines the code block responsible for testing the schedule. This construct is built in a slightly different way to the one mentioned above: We use the invoke operator + "lambda out of parentheses".

Having defined the invoke operator, we can now use the _schedule(...)_ construct, although _schedule_ is an object. In fact, when you call _schedule(...)_, the compiler interprets it as _schedule.invoke(...)_. Let's see how _schedule_ is declared:

The _schedule_ identifier refers us to the only _schedule_ class instance (singleton) that is marked by the special keyword _object_ (you can find more information about such objects [here](https://kotlinlang.org/docs/reference/object-declarations.html#object-declarations)). Thus, we call the _invoke_ method of the _schedule_ instance, receiving a lambda as a single parameter and placing it outside of the parentheses. As a result, the _schedule {... }_ construction matches the following:

However, if you look at the invoke method carefully, you'll see not a common lambda, but a "lambda with receiver" or "lambda with context", whose type is defined as:

Let's examine it in detail.

### Lambda With Receiver

Kotlin enables us to set a context for lambda expressions (context and receiver mean same thing here). Context is just an object. The context type is defined together with the lambda expression type. Such a lambda acquires the properties of a non-static method in the context class, but it only has access to the public methods of this class.

While the type of a normal lambda is defined like () -> Unit, the type of a lambda with X context is defined as follows: X.()-> Unit. And, if normal, lambdas can be called in a usual way:

Meanwhile, a lambda with context requires a context:

I'd like to remind you that we have defined the invoke operator in the schedule object (see the preceding paragraph) that allows us to use the construct:

The lambda we are using has the context of the SchedulingContext type. This class has a data method in it. As a result, we get the following construct:

As you have probably guessed, the data method also takes a lambda with context. However, it is a different context. Thus, we get nested structures having several contexts inside simultaneously. To get the idea of how it works, let's remove all syntactic sugar from the example:

As you can see, it's all fairly simple. Let's take a look at the invoke operator implementation.

We call the constructor for the context SchedulingContext(), and then, with the created object (_context_), we call the lambda with the _init_ identifier that we passed as a parameter. This resembles a general function call quite a bit.

As a result, in one single line -- SchedulingContext().init() -- we create the context and call the lambda passed to the operator. For more examples, consider the _apply_ and _with_ methods from Kotlin standard library.

In the last examples, we discovered the _invoke_ operator and its combination with other tools. Next, we will focus on the tool that is formally an operator and makes the code cleaner -- the _get/set methods convention_.

### get/set Method Conventions

When creating a DSL, we can implement a way to access maps by one or more keys. Let's look at the example below:

In order to use square brackets, we need to implement the _get_ or _set_ methods (depending on what we need -- read or update) with an _operator_ modifier. You can find an example of such an implementation in the _Matrix_ class on [GitHub](https://github.com/ivan-osipov/kotlin-dsl-example). It is a simple wrapper for matrix operations. Below, you can see a code snippet on the subject:

You can use any _get_ and _set_ parameter types, the only limit is your imagination. You are free to use one or more parameters for get/set functions to provide a convenient syntax for data access. Operators in Kotlin provide lots of interesting features that are described in the [documentation](https://kotlinlang.org/docs/reference/operator-overloading.html).

Surprisingly, there is a _Pair_ class in the Kotlin standard library. A larger part of the developer community finds _Pair_ harmful: When you use _Pair_, the logic of linking two objects is lost, and thus it is not transparent why they are paired. The two tools I'll show you next will demonstrate how to keep the pair making sense without creating additional classes.

### Type Aliases

Suppose we need a wrapper class for a geo point with integer coordinates. Actually, we could use the Pair class, but having such a variable, we can lose the understanding of why we have paired these values.

A straightforward solution is either to create a custom class or something even worse. Kotlin enriches the developer's toolkit via type aliases with the following notation:

In fact, it is nothing but renaming a construct. Due to this approach, we don't need to create the _Point_ class anymore, as it would only duplicate the _Pair_. Now we can create a point in this way:

However, the _Pair_ class has two attributes, _first_ and _second_, that we need to rename somehow to blur any differences between the needed _Point_ and the initial _Pair_ class. For sure, we are not able to rename the attributes themselves (however, you can create [extension properties](https://kotlinlang.org/docs/reference/extensions.html#extension-properties)), but there is one more notable feature in our toolkit called _destructuring declarations_.

### Destructuring Declarations

Let's consider a simple case: Suppose we have an object of the _Point_ type that is, as we already know, just a renamed type Pair. If we look at the _Pair_ class implementation in the standard library, we'll see that it has a data modifier that directs the compiler to implement _componentN_ methods within this class. Let's learn more about it.

For any class, we can define the _componentN_ operator that will be in charge of providing access to one of the object attributes. That means that calling _point.component1_ will be equal to calling _point.first_. Why do we need such a duplication?

A destructuring declaration is a means of "decomposing" an object to variables. This functionality allows us to write constructions of the following kind:

We can declare several variables at once, but what values will they be assigned? That's why we need the generated _componentN_ methods: Using the index starting from 1 instead of N, we can decompose an object to a set of its attributes. So, the above construct is equal to the following:

Which, in turn, is equal to:

Where _first_ and _second_ are the Point object attributes.

The _for_ loop in Kotlin looks as follows, where x takes the values 1, 2, and 3:

Pay attention to the assertions block in the DSL from the main example. I'll repeat a part of it for convenience:

This line should be evident. We iterate through a collection of _scheduledEvents_, each element of which is decomposed into four attributes.

### Extension Functions

Adding new methods to objects from third-party libraries or to the Java Collection Framework is what a lot of developers have been dreaming about. Now we have such opportunity. This is how we declare extension functions:

Compared to the standard method, we add the class name as a prefix to define the class we extend. In the example above, AvailabilityTable is an alias for the Matrix type and, as aliases in Kotlin are nothing but renaming, this declaration is equal to the one below, which is not always convenient:

Unfortunately, there's nothing we can do here except not using the tool or adding methods only to a specific context class. In this case, the magic only appears where you need it. Moreover, you can use such functions even for extending interfaces. As a good example, the _first_ method extends any _iterable object_:

In essence, any collection based on the _Iterable_ interface, despite the element type, gets the _first_ method. It is worth mentioning that we can place an extension method in the context class and thereby have access to the extension method only in this very context (similarly to a lambda with a context). Furthermore, we can create extension functions for _Nullable_ types (the explanation of _Nullable_ types is out of the scope here, but for more details, see [this link](https://kotlinlang.org/docs/reference/null-safety.html#nullable-types-and-non-null-types)). For example, that's how we can use the function _isNullOrEmpty_ from the standard Kotlin library that extends the _CharSequence _type:

Below is this function's signature:

When working with such Kotlin extension functions from Java, they are accessible as static functions.

### Infix Functions

One more way to sugarcoat our syntax is to use infix functions. Simply said, this tool helps us to get rid of excessive code in simple cases. The assertions block from the main snippet demonstrates this tool's use case:

This construction is equivalent to the following:

In some cases, brackets and dots can be redundant. For such cases, we can use the _infix_ modifier for functions.

In the code above, the construct teacherSchedule[day, lesson] returns a schedule element, and the function shouldNotEqual checks that this element is not null.

To declare an infix function, you need to:

  * Use the infix modifier.
  * Use only one parameter.

Combining the last two tools, we can get the code below:

Note that the generic type, by default, is an Any inheritor (not Nullable). However, in such cases, we cannot use null -- that's why you should explicitly define the type Any.

### Context Control

When we use a lot of nested contexts, in the lower level, we risk getting a wild mix. Due to the lack of control, the following meaningless construct becomes possible:

Before Kotlin v.1.1, there had already been a way to avoid such a mess. It lies in creating custom method data in a nested context, DataContext, and then marking it with the Deprecated annotation with the ERROR level.

This approach eliminates the possibility of building an incorrect DSL. Nevertheless, a big number of methods in SchedulingContext would have made us do a lot of routine work discouraging people from any context control.

Kotlin 1.1 offers a new control tool--\- the @DslMarker annotation. It is applied to your own annotations, which, in turn, are used for marking your contexts. Let's create an annotation and mark it with the new tool from our toolkit:

Now we need to mark up the contexts. In the main example, these are SchedulingContext and DataContext. As far as we annotate both classes with the common DSL marker, the following happens:

With all the benefits of this cool approach saving so much time and effort, one problem still remains. Take a look at the main example, or, more precisely, to this part of the code:

On the third nesting level, we get the new context, Student, which is, in fact, an entity class. So we are expected to annotate part of the data model with @MyCustomDslMarker, which is incorrect in my opinion. In the Student context, the data {} calls are still forbidden, as the external DataContext is still in its place, but the following constructions remain valid:

Attempts to solve the problem with annotations will lead to mixing business logic and testing code, and that is certainly not the best idea. Three solutions are possible here:

  1. Using an extra context for creating a student -- for example, StudentContext. This smells like madness and outweighs the benefits of @DslMarker.
  2. Creating interfaces for all entities -- for example, IStudent (no matter the name), then creating stub contexts that implement these interfaces, and, finally, delegating the implementation to the student objects. That verges on madness, too.

To sum it up, combining various tools empowers you to build a very convenient DSL for your real-world purposes.

## Cons of DSL use

Let's try to be more objective concerning the use of DSLs in Kotlin and find the drawbacks of using DSLs in your project.

### Reuse of DSL Parts

Imagine you have to reuse a part of your DSL. You want to take a piece of your code and make it easy to replicate. Of course, in the simplest cases with a single context, we can hide the repeatable part of a DSL in an extension function, but this will not work in most cases.

Perhaps you could point me toward some better options in the comments because for now, only two solutions come to my mind: adding "named callbacks" as a part of the DSL or spawning lambdas. The second one is easier but can result in a living hell when you try to understand the call sequence. The problem is that the more imperative behavior we have, the fewer benefits remain from a DSL approach.

### This?! It?!

Nothing's easier than losing the meaning of the current "this" and "it" while working with your DSL. If you use "it" as a default parameter name where it can be replaced by a meaningful name, you'd better do so. It's better to have a bit of obvious code than non-obvious bugs in it.

The notion of context can confuse someone who has never faced it. Now, as you have "lambdas with receiver" in your toolkit, unexpected methods inside DSLs are less likely to appear. Just remember, in worst case, you can set the context to a variable, for example, val mainContext = this.

### Nesting

This issue relates closely to the first drawback in this list. The use of nested in nested in nested constructions shifts all your meaningful code to the right. Up to a certain limit, this shift may be acceptable, but when it's shifted too much, it would be reasonable to use lambdas. Of course, this will not decrease your DSL's readability, but it can be a compromise in case your DSL implies not only compact structures, but also some logic. When you create tests with a DSL (the case covered by this article), this issue is not acute, as the data is described with compact structures.

### Where Are the Docs, Lebowski?

When you first try to cope with somebody's DSL, you will almost certainly wonder where the documentation is. On this point, I believe that if your DSL is to be used by others, usage examples will be the best docs. Documentation itself is important as an additional reference, but it is not very friendly to a reader. A domain-specific practitioner will normally start with the question "What do I call to get the result?" So in my experience, the examples of similar cases will better speak for themselves.

## Conclusion

We've got an overview of the tools that enable you to design your own custom domain-specific language with ease. I hope you now see how it works. Feel free to suggest more tools in the comments.

It is important to remember that DSL is not a panacea. Of course, when you get such a powerful hammer, everything looks like a nail, but it isn't. Start small, create a DSL for tests, learn from your mistakes, and then, once you're more experienced, consider other usage areas.

## About author

I'm a software developer at Haulmont. Last year my area of responsibility was table scheduling in education. I have applied the described above technologies while developing applications based on [CUBA Platform](https://www.cuba-platform.com/) Java framework. I spend free time with Spring, with Kotlin DSL for Telegram bot development and of course with my wife.

[Download Building Reactive Microservices in Java](https://dzone.com/go?i=219225&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F166031): Asynchronous and Event-Based Application Design. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=219225&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F166031).

![](https://dz2cdn1.dzone.com/storage/rc-covers/7391100-dzone-aicover.jpg)
