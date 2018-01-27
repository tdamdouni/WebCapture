# The Beautiful Law of Demeter

_Captured: 2017-11-10 at 01:00 from [dzone.com](https://dzone.com/articles/the-beautiful-law-of-demeter?edition=334849&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-07)_

"[Automated Testing: The Glue That Holds DevOps Together"](https://dzone.com/go?i=236222&u=http%3A%2F%2Finfo.saucelabs.com%2FAutomated_Testing_Glue_LP-DZone.html%3Futm_medium%3Dpre-roll_textlink%26utm_content%3Darticle) to learn about the key role automated testing plays in a DevOps workflow, brought to you in partnership with Sauce Labs.

We all know, and I hope that we try, to apply the "rules" of Object Oriented Programming when we code. We want our code to be properly encapsulated, loosely coupled, robust, and reusable, and our application to be more scalable and maintainable.

But all of those rules are a bit too abstract to apply them directly, and the decision on how to apply them is often led by our experience and intuition.

But there is a law that comes to help us in making these decisions: the Law of Demeter.

One of the most concise laws of Object Oriented Programming, the beauty of it is that it can be applied directly and guarantees all the abstract rules that I mentioned before.

## So What Is It?

The law sounds like this: only talk to your immediate friends. That's it. It is really that simple. So what does this mean in Object Oriented Programming? Well, the "talking" with an object is actually calling one of its methods.

So, according to the Law of Demeter, a method M of object O should only call following methods:

  * Methods of Object O itself (because you could talk with yourself)

  * Methods of objects passed as arguments to M

  * Methods of objects held in instance variable

  * Methods of objects which are created locally in method M

  * Methods of static fields

What the law says is that you don't need to know the internals of an object that you receive or any other object that you need. You are just concerned by the method's own business logic and if you need something from other objects you [tell, don't ask](https://martinfowler.com/bliki/TellDontAsk.html). You let the other objects to be responsible for their internal states and what they are giving to you.

Let's see an example. We have a list of employees and we want to get their street name. Here is a typical method to do this.

What is wrong with it and why this does not respect the Law of Demeter? Here you have access to the employee object and, to get the street name, you access his address field.

Why do you need to know that the Employee object has an Address field in this case? You just need to take an information from the Employee and you don't care how the Employee class stores it.

This is a violation of the law because the address object it is not an "immediate" friend. We had access to it because we got it from the employee object.

In this case, we should change the code like this to respect the law.

This is better. Now, when you need an information from the employee, you just ask him to get it. If the way of how Employee class stores his address will be changed then you have to change just the Employee's methods and there will be no impact in other classes that ask for this information.

## Chain Calls

What about them? Are they allowed? It depends. Let's say we have code like this:

If those methods are getters that return different fields, then this does not respect the law. If a method of an immediate friend returns another object- for example, one of if its fields- then you should not "talk" with that returned object. o.getA() is an acceptable call, but this getter will return one of object o's field so the law forbids future calls.

But when are chain calls allowed? Well, the law specifies that you can call Methods of objects which are created locally in method M. So if we have a method that returns a new object, like this one:

then this call

respects the law. The new object M that we get when we call the createM() method is a new object just for us. That object will not exist anywhere else. It lives just in the current block scope and we can call its methods without a problem. We could say that this aspect of the law offers safety, because, if the new object is not referred in other places then calling its methods will have just a local impact.

So, we saw here that the law has nothing against chain calls.

## The Law and the Builder Pattern
    
    
      pizza.topping = this.topping;
    
    
      Pizza pizza = pizzaBuilder.setSize(30).setTopping(“Cheese”).build();

One of my favorite design patterns, and also, it respects the law. We saw that the law has nothing against chain calls if you call methods of objects that are created locally in the current method. Well, let's see each call separately.

And now we've created our pizza. And we see that the pizza object is created locally, which means that we can call any of its methods. So, we saw here that, even if the method looks like it does not respect the law with all the chain calls, it does! The law works very well, even with the builder pattern, and chain calls are the essence of this pattern.

## Exceptions (That Prove the Rule)

Let's say that we receive a data structure as a parameter. We can call its methods and we can iterate it while respecting the law, obviously. But what about accessing the elements of the list? Is this acceptable?

Let's see a method that iterates a list in an old-fashioned way:

It is obvious that orders.size() and orders.get(i) are calls that respect the Law of Demeter. With orders.get(i) we get the order object, which, in this case, it is not an object that is created in this call, so strictly speaking, order.buy() is not respecting the law. But the "orders" object is a list, a collection of objects, by definition, that we receive as a parameter. That's the whole purpose of collections. So we could say that we aren't receiving just one object in this method, but all the list's elements as our parameters. The list's elements we could say that are immediate friends, and it is acceptable to call their methods.

We could use some decorators to wrap the list into another object and to access the items in another way, but it is not necessary.

## Summary

The law is not universal. It does not provide all that we need in Object Oriented Programming. But we clearly get huge advantages if we respect it. We will have a clear, more flexible and more maintainable code.

In our day job, very often we have to work on different projects, some of them older than others, with a lot of new and old classes. We see, of course, well-written code, but we also see code that we are too scared to touch because it could impact things that we couldn't imagine yet because it is too tightly coupled. We encounter code on which we stay more than one day on reading it, and after that, we don't understand anything because some objects are refereed everywhere and it takes hours to detect where their internal state is changed, and we go home and we start questioning our career. Yes, in our life as software developers, we encounter a situation like this very often. But just imagine how it will be to work on an application that is written by respecting the Law of Demeter. How loosely coupled will be the code, how easy it would be to read it. You would not be scared to start and digging and modify things because you are sure that methods are called from the right places. You talk just with your immediate friends, and you should trust your friends.

[Learn about the importance of automated testing](https://dzone.com/go?i=236223&u=http%3A%2F%2Finfo.saucelabs.com%2FAutomated_Testing_Glue_LP-DZone.html%3Futm_medium%3Dpost-roll_textlink%26utm_content%3Darticle) as part of a healthy DevOps practice, brought to you in partnership with Sauce Labs.

Opinions expressed by DZone contributors are their own.
