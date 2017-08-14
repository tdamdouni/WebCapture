# What's So Evil About Singletons?

_Captured: 2017-08-04 at 19:40 from [dzone.com](https://dzone.com/articles/whats-so-evil-about-singletons?edition=0&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-04)_

We've all come across this word 'singleton,' and most of us even know the definition of it. As Wikipedia says, "Singletons are classes which have a restriction to have only one instance."

Maybe a few of were lucky enough to use it, but believe me, even if you have used it, you might not know how evil it is.

![](https://cdn-images-1.medium.com/max/600/1*iRhfIjbFc8hkict9om-Kjg.jpeg)

> _ _Single by choice_ _

But first of all, let me get everyone on the same page.

So to be more clear, "This pattern involves a single class which is responsible for creating an object while making sure that only one object gets created."

> **Note:** Most of the code is in Java, but it is so simple that anybody can understand it. 

By now, we know what a singleton class is and how it works. So where is the defect? Hint: The most obvious problem is hidden in line 7.

Since a synchronized block can be accessed one thread at a time, this might create a bottleneck for even getting the instance of the object.

But there are other, lesser-known problems.

## **Singletons and State**

Singletons are enemies of unit testing. One of the major requirements of unit testing is that each test should be independent of others. This can cause tests to pass when, really, it's because they were called in a particular order

## One Object Created

Isn't it a complete violation of the _[Single Responsibility Principle_](https://sites.google.com/site/steveyegge2/singleton-considered-stupid), which states, "_A class should have one, and only one, reason to change._" Basically, a class should not know whether it is a singleton or not. So if you want to limit the ability to instantiate, use the factory or builder patterns, which encapsulates creation. There, you can limit the number of objects to one or whatever you wish for.

> 'Singleton' is a fancy word for 'global variable.'

## Singletons Provide Global State

Exactly, that's why we have singletons. Yes. But at what cost? (_Global variables were bad! Remember?_) This provides a gateway to some service in your application so that we don't have to pass around a reference to the service. The urge to create something global to avoid passing it around is a smell in your design.
