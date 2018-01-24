# SRP in Object-Oriented Design

_Captured: 2017-12-12 at 21:18 from [dzone.com](https://dzone.com/articles/single-responsibility-principle-in-object-oriented?edition=342139&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-12)_

[Build vs Buy a Data Quality Solution: Which is Best for You?](https://dzone.com/go?i=251321&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) Gain insights on a hybrid approach. Download white paper now!

In object-oriented programming, there are five basic principles ([SOLID](https://apiumhub.com/services/software-architecture-services-barcelona/)) that, properly applied, make the difference between good and bad design. They're the difference between an application that is easy to maintain and one that is not. The difference between a good developer and a bad one. Today, I would like to concentrate on the first principle in object-oriented design (the **Single Responsibility Principle**) but first, let's mention the five SOLID principles:

  * **Single Responsibility Principle**
  * Open/Closed Principle
  * Liskov Substitution Principle
  * Interface Segregation Principle
  * Dependency Inversion Principle 

## Single Responsibility Principle

We're going to start with the first one, the Single Responsibility Principle (SRP) that is defined by [Robert C. Martin](https://sites.google.com/site/unclebobconsultingllc/) in his book "[Agile Software Development, Principles, Patterns, and Practices](http://druss.co/wp-content/uploads/2013/10/Agile-Principles-Patterns-and-Practices-in-C.pdf)". The principle is actually a very simple concept to explain, but it can be difficult to implement. As its name suggests, it implies that a class or module must have a unique responsibility.

Within the context of the Single Responsibility Principle, responsibility is defined as a reason to change. That is why I consider the phrase of Robert C. Martin as a perfect definition of the Single Responsibility Principle:

> "A class should have only one reason to change."

By following the Single Responsibility Principle, you make sure that your class or module has high cohesion, which means that your class does not do more than it should. In short, it should have one unique reason to change. If, on the contrary, you build a class with more than one responsibility, you're engaging these responsibilities. This leads to a design that is fragile and difficult to maintain, with all that that entails.

### Example

![srp](https://apiumhub.com/wp-content/uploads/2016/02/Screen-Shot-2016-05-31-at-10.49.28.png)

In this simple example, you can see a rectangle class that has two methods; Area () and Draw ().

  * Area () has the responsibility to return the area of a rectangle
  * Draw () has the responsibility to draw the rectangle itself 

In this design, it can be seen that, if there are changes in the GUI, we must modify the Rectangle class, then we are obliged to test the other application that attacks the same class again. The solution to this problem is to divide the class in two so that each class has a unique responsibility. One will be responsible for calculating and another one for painting:

![single responsibility principle](https://apiumhub.com/wp-content/uploads/2016/02/Screen-Shot-2016-05-31-at-10.50.06.png)

It's important to keep in mind that this principle leads to many other nuances and concepts, and not only those that fall within SOLID, but others that should be known and able to apply to get an application with a solid design.

[Build vs Buy a Data Quality Solution: Which is Best for You?](https://dzone.com/go?i=251322&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) Maintaining high quality data is essential for operational efficiency, meaningful analytics and good long-term customer relationships. But, when dealing with multiple sources of data, data quality becomes complex, so you need to know when you should build a custom data quality tools effort over canned solutions. [Download our whitepaper](https://dzone.com/go?i=251322&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) for more insights into a hybrid approach.
