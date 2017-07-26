# Total and Partial Functions in FP

_Captured: 2017-02-09 at 21:17 from [dzone.com](https://dzone.com/articles/total-and-partial-functions-in-fp?edition=267886&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-09)_

Navigate the Maze of the End-User Experience and pick up this [APM Essential guide](https://dzone.com/go?i=147026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fapm-essentials-navigating-the-maze-of-end-user-experience-solutions.register.html%3Fmrm%3D519574), brought to you in partnership with [CA Technologies](https://dzone.com/go?i=147026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fapm-essentials-navigating-the-maze-of-end-user-experience-solutions.register.html%3Fmrm%3D519574).

## **What Are Total Functions?**

Once you get started down the road of applying [functional principles](https://dzone.com/articles/functional-programming-is-not-what-you-probably-th) to your programming, eventually you will stumble across some academic white beard mumbling something about total functions, or your local FP evangelist bemoaning that the third of the deadly coding sins (after mutation and side-effects of course) is the rampant blasphemy of programmers either knowingly or unknowingly writing partial functions.

So you may be wondering now what exactly total and partial function are. I mean, most people don't write half a method, right? So how can any function not be total as long as it compiles? And what's so bad about partially applied functions? Isn't that supposed to be a functional programming thing? (Hint: That's not the same as a partial function).

If that's what you are thinking, please allow me to enlighten you. But before proceeding, let me thank and give credit to the following people for my inspiration and knowledge on this topic:

  * Pierre-Yves Saumont, for mentioning the importance of total functions in his upcoming book [Functional Programming in Java](https://www.manning.com/books/functional-programming-in-java).

  * Bartosz Milewski, for talking about runtime exceptions and [bottom](https://bartoszmilewski.com/2014/11/24/types-and-functions/).

  * Nebu Pookins, for illustrating the relationship of [pure and total functions](http://nebupookins.github.io/2015/08/05/pure-functions-and-total-functions.html).

## **Getting All Math-y and Stuff**

I promise, I won't go into [category theory](https://bartoszmilewski.com/2014/10/28/category-theory-for-programmers-the-preface/), but you do need to understand something you probably learned back when you took algebra or maybe calculus. A mathematical definition of a function is that it takes some argument, which is a member of a set called the domain, and it returns a value that belongs to some set called the codomain (which is subtly different than the range, but I'm going to be like Bill Nye and not get too math-y here).

If you didn't read [my other article on FP](https://dzone.com/articles/functional-programming-is-not-what-you-probably-th), a function is really just a mapping of an input value to an output value. The input values must be members of a set, so in our case, you can think of a type like a set, and the output values must also be a member of some set, which may or may not be of the same set as the input values.

The diagram below shows a function that maps the natural numbers to their string representation. For every element in the domain (in this case, all Integers), there is a corresponding element in the codomain (a String representing that integer value). There is no value in the domain in which there is not a corresponding element in the codomain. Moreover, each element in the domain maps to one, and only one element in the codomain (you can't have an integer that has more than one string representation, for example, unless you wanted to do another representation like hex or binary... but this is a function from integer to decimal representation). So this function is both pure and total.

![Image title](https://dzone.com/storage/temp/4234188-dzone-function.png)

> _Extra Credit: You can skip to Total Functions below if math isn't your thing._

The function above also happens to be injective, but not surjective. An injective function is one in which every element in the domain is uniquely mapped to an element in the codomain. You can't have two values in the domain map to the same element in the domain. A surjective function means that every element in the codomain is mapped to at least one element in the domain. In our above function however, not all elements in the codomain are mapped from an element in the domain (there are strings that are not mapped to an Integer like "hello" and "world"). If a function is both surjective and injective it is bijective.

Why is all this important? If a function is injective it has an inverse function. Inverse functions are sometimes useful when you want to reverse or "rollback" a function. However, if you think about the definition of an injective function, it is possible that the inverse is not total. This is because if you "flip" the codomain as your input, and your domain as your output for your inverse function, there can be elements in your new domain that are not mapped to an element in the new codomain (eg, what Integer would the string "hello" map to?). If however your function is bijective, then not only is your function is total, the inverse function exists and is total too! Being able to safely and reliably rollback a function comes in handy in some scenarios (for example backtracking, path finding, or transaction rollbacks).

## Total Function

Here is a simple definition of a total function. A function is total when:

  * The argument passed into the function is an element of the domain

  * For the given argument passed in, the return value must be an element of the codomain

To put this another way, for every possible value that the argument can take, the return value of the computation must be an element from the codomain.

So let's look at a real world example of a total function as defined above. Here's a simple method called **_append _**that adds two Integers and returns an Integer:
    
    
        public FMap<Integer, Integer> append(Integer s1) {
    
    
            return this.append(s1).map(s2);
    
    
        public static void main(String[] args) {
    
    
            Integer result = example.appender(5, 10);

Ok, you're probably thinking this isn't so simple. Well, I made the **_append_** method like this for a reason: It follows the mathematical definition of a function. This is actually a function that takes one argument, and it returns a Functional Interface, which you can think of as a lambda (an anonymous function). This returned Functional Interface, in turn, takes some type A, and returns some type R.

_**"Ughhh, why'd you make it all complicated? Just use the one you commented out. It's more obvious."**_

More obvious? Perhaps. I would have said that the implementation would have been more _concrete _(hint: There is a reason I made FMap use generics. Plus, you can't do things like partial application)_._ That being said, this is an unfortunate limitation with the syntax of Java. I had to manually do the currying here, which sort of obfuscates the process. Haskell and its dialects do this currying process automatically.

Haskell for the win!! And people say Haskell is complicated. :P

As for Java, I probably could have written a custom Annotation Processor and generated a new curried method automatically, but that's beyond the scope of this article. There is, however, a small advantage in making the code this way, but I've already digressed enough. Perhaps I will discuss this advantage in a later article. The main point I wanted to show here is that append is a true pure function that takes one argument of an element in a domain and returns a value that is an element of the codomain.

Ok, back to explaining domains, codomains, and how all this relates to total functions. In the **_append _**method, our domain is the set of Integers and the codomain is a set of methods that takes an Integer and returns another Integer. You can basically think of types as a set, and objects of a type as being a member of a set of that type.

Perhaps it is easier to think of the domain and codomain for the **_appender _**function. You can think of the domain for this method as the set of two-element Tuple of Integers, and the codomain as the set of Integers. Since we can pick any two objects of type Integer, and the resulting value of **_append _**is also an Integer, we can say that this function is total. There are no "unaccounted" for values in the arguments we can pass in, and there is no way that the addition of two Integers is not also an Integer. (Yes, I know there's a bug here. Keep reading the section on Partial Functions.)

## **Partial Functions **

Now, before I go off and explain that I actually pulled the wool over your eyes and the _append _(and therefore the _appender_) function above is not total, let me clear up one confusion first. Don't get confused between Partial Functions and partially applied functions. A partially applied function is one where some of the arguments to a function have been "pre-supplied," and a new function is returned that only takes any remaining arguments not yet supplied. For example:

So, as I mentioned above, I was being tricksy and making sure you were paying attention. Do you see something wrong with the definition of the **_append _**method? Just to give you a hint, this function can blow up. Don't worry, I'll give you a minute or two to spot the problem... no pressure or anything.

Found it yet? The problem is that the set of the domain contains an element that is a valid value for an Integer type, and yet the result of this function would not be an element of the codomain (ie, the returned method would not be a function from Integer to Integer). Because if I were the evil sort, or just didn't have enough coffee before thinking about what the possible values of the arguments could be, I could make that method behave badly. What possible value could be passed into that method that is a valid member of Integer, but does not return a method from Integers to Integers? Got it yet?

_I could have passed in a null (but you know I'd never do that to you.... on purpose)._

So really, this function is what is called a partial function. This means that you can pass in a valid member of your domain as an argument to the function, but the returned value of the function is not a member of the codomain. Remember, a null is a valid value for an Integer type, but the return value has no corresponding element in the codomain. We'd throw an Exception if one of the args was a null, and an Exception is not a valid member of the Integer type as required by our codomain. -By the way, what _would _the corresponding output value be, and of what type, if I happened to pass in a null in either of the two arguments? Or perhaps a better question would be, do I need to change set of the domain and/or the codomain? Mull that question over, preferably over a nice cup of tea, so that I can get back to that in a bit.

## Why Partial Functions Are Troublesome

Do you see now why partial functions are one of the sins to watch out for? If you aren't careful with how you design your functions and consider all the valid and invalid values you can pass into your function, you might wind up with a runtime Exception being thrown. Perhaps you are thinking now that null can be any valid type, so all methods in Java would be partial, and in some sense, this is true but I'll talk about that a little later. But taking into consideration null as a possible value isn't the only thing to worry about.

This problem seems innocuous, but remember that Integers are signed values. What if a = 4, b = 2, and c = -2? What would be all possible types in our codomain here? In the append method above, I could have restricted our domain, perhaps setting @NonNull, although that would only help at runtime. Or, I could have simply checked for null values and supplied a default. But how would you solve this problem to make divide a total function? This problem doesn't just exist for math problems. If you have a switch type statement in your language, or pattern matching, but fail to cover all the possible cases/patterns, you could possibly end up with a partial function. There are many other ways to end up inadvertently writing partial functions.

Unfortunately, even pure FP languages can be subverted by this sin. There is no silver bullet to this problem in general (dependent types might be a solution for the divide function above). Many FP languages help mitigate this problem, however. For example, the compiler can warn you if you haven't covered all patterns in your pattern matching. Also, FP programmers are usually more aware of this problem because Total functions and Pure functions go together like peanut butter and chocolate.

In fact, when I first thought about Total Functions, it seemed to me like a pure function by definition had to be a total function. After all, pure functions aren't supposed to go postal and then commit hara-kiri on you like a partial function can right? How could you have a pure function that's not total? Well, it turns out that Total Functions don't have to be pure (any function with side effects is not pure, but can be total), and not all pure functions are total. Don't worry, I won't leave you hanging for an explanation, but I need to cover one more concept first.

## Extend With the Bottom (or Does My Butt Look Big?)

Ok, I lied a little bit again, and I am going to touch on Category Theory just a teensy weensy. All credit in the next 2 paragraphs here goes to Bartosz Milewski's very good tutorial on Category Theory. So in Haskell, there's an implicit value that is a member of every type called bottom _|_ (hey, that does kinda look like my bottom when I sit on a park bench (_|_)). Bottom represents functions that don't terminate in Haskell. This is unlike null for Java, which, although it is also a valid member of every type, its purpose is to represent no actual value. Why does Haskell include bottoms for every type?

Unlike math, in which no actual computation is going on, in our programs, the output of a function has to actually be calculated. Unfortunately, there's a very famous problem in computer science called the [Halting Problem](https://www.scientificamerican.com/article/why-is-turings-halting-pr/). Interestingly, this happens to be equivalent to [Kurt Godel's Incompleteness Theorem](https://plato.stanford.edu/entries/goedel-incompleteness/), which is another fascinating topic, but I'm going off into the weeds again. The Halting Problem basically says that it is impossible for the computer to know if a function will terminate. A method might do recursion or corecursion, which never cease, for example. Since it is undecidable if a function might terminate, the bottom can represent a non-terminating function. It is, therefore, useful to treat bottom as some kind of runtime exception.

So don't think of bottom like null. In Java, null represents that the type has no actual value, as opposed to whether or not a function will terminate. One way to represent the equivalent of a null in Haskell is something called the Maybe Monad. Maybe you heard about it? Ughhhh sorry, even I cringed at that joke, but it handles the possibility that there may be no value for your function.

## Pure and Total Are Separate Notions

It is possible for a function to be:

  1. impure and total

  2. impure and partial

  3. pure and total

  4. pure and partial

If you were like me, you were probably wondering how the last one could be possible. Now that I explained bottom, the runtime exceptions, and the halting problem, I can talk about how a function can be pure and yet not total. Recall that it is undecidable if a function will terminate. It is possible, therefore, to invoke a function that will never return (not just an endless recursion or loop, but also no value may be yielded). Since the function never returns, there is no way to see any effect, and thus it is pure. And yet, since you don't get a return value, the function is also partial.

## Strategies to Make Functions Total

Why did I bring up bottom which is a Haskell-ism? Because other languages can make use of this concept, too. One way to solve the problem of partial functions is to just tack on a runtime exception as a valid member of your codomain set. This is sort of what happens in Java when you declare a method that throws an exception. In essence, you can think of the throws keyword as an extra element that could be "returned," and therefore as another member of the codomain. However, having the possibility of a runtime Exception explicitly as part of the return type itself is an even more intriguing possibility.

I'll explore this option in yet another article, but another possible solution is to restrict the elements of your domain. This can be a little tricky in practice, though.

## Conclusion

I hope you have a better picture of what total functions are, and why you should strive to make all your functions total.

Thrive in the application economy with [an APM model that is strategic](https://dzone.com/go?i=147025&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fepic-apm-toward-a-better-apm-model-for-the-application-economy.register.html%3Fmrm%3D519574). Be E.P.I.C. with CA APM. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=147025&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fepic-apm-toward-a-better-apm-model-for-the-application-economy.register.html%3Fmrm%3D519574).
