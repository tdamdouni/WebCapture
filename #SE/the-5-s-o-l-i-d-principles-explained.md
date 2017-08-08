# The 5 S.O.L.I.D. Principles Explained

_Captured: 2017-07-30 at 16:03 from [dzone.com](https://dzone.com/articles/the-5-solid-principles-explained?edition=310400&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-26)_

Speed up delivery cycles and improve software quality with [TestComplete.](https://dzone.com/go?i=228239&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad) Discover the most robust automated testing tool for end-to-end desktop, mobile, and web testing. [Try TestComplete Free.](https://dzone.com/go?i=228239&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad)

Today I would like to talk about S.O.L.I.D., the first five principles of object-oriented programming that are essential for building working software. In case you didn't know it, in computer programming, the **SOLID principles** acronym was introduced by Michael Feathers for five principles that were defined by Robert C. Martin in the early 2000s.

As you know, to get a working software, we should have a low coupling, high cohesion and strong encapsulation, which is something that the SOLID principles help us obtain. The idea is that, by applying those principles together, you are able to write better quality code that is robust. The system created becomes easy to maintain, to reuse and to extend over time. Basically, SOLID principles help software developers to achieve scalability and avoid that your code breaks every time you face a change.

Ok, so let's start with the basics. S.O.L.I.D. stands for:

**S** - Single-Responsibility Principle.

**O** - Open-Closed Principle.

**L** - Liskov Substitution Principle.

**I** - Interface Segregation Principle.

**D** - Dependency Inversion Principle.

Let's look at each principle individually to understand why S.O.L.I.D can help developers to build quality software.

## The SOLID Principles

#### 1.Single-Responsibility Principle

> "There should be never more than one reason for a class to change."

As you can see, this principle states that an object/class should only have one responsibility and that it should be completely encapsulated by the class. Here, when we talk about a responsibility, we mean a reason to change. This principle will lead to a stronger cohesion in the class and looser coupling between dependency classes, better readability, and code with lower complexity.

It is much more difficult to understand and edit a class when it has various responsibilities. So if we have more than one reason to change, the functionality will be split into two classes and each will handle its own responsibility.

We care about separating the functionalities because each responsibility is an access of change. When a class has more than a single responsibility, those responsibilities become coupled and this coupling can lead to a fragile code base that is difficult to refactor when your requirements emerge.

_If you're interested in knowing a bit more about the SRP principle, [here's a post](https://apiumhub.com/tech-blog-barcelona/single-responsibility-principle/) you will enjoy reading._

#### 2\. Open-Closed Principle

> "Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification."

Here, the idea is that an entity allows its behavior to be extended but never by modifying its source code. Any class (or whatever you write) should be written in such a way that it can be used as is. It can be extended if need be, but it can never be modified. You can consider this when you are writing your classes. Use the class in any way you need, but modifying its behavior comes by adding new code, never by modifying the old. The same principle can be applied to modules, packages, and libraries.

By applying the open-closed principle you will get a loose coupling, you will improve readability and, finally, you will be reducing the risk of breaking existing functionality.

#### 3\. Liskov Substitution Principle

> "Subtypes must be substitutable for their base types."

As its name says, Liskov's Substitution Principle was defined by [Barbara Liskov](https://en.wikipedia.org/wiki/Barbara_Liskov). The idea here is that objects should be replaceable by instances of their subtypes without affecting the functioning of your system from a client's point of view. Basically, instead of using the actual implementation, you should always be able to use a base class and get the result you were waiting for. Often when we want to represent an object, we model our classes based on their properties, but, instead of that, we should actually be putting more of our focus on the behaviors.

This principle basically confirms that our abstractions are correct and helps us to get code that is easily reusable and class hierarchies that are very easily understood.

What many say is that Liskov's Substitution Principle has a very strong relation with the previous principle, the Open-Closed Principle. Robert C. Martin even says that "a violation of LSP is a latent violation of OCP."

#### 4\. Interface Segregation Principle

> "Classes that implement interfaces, should not be forced to implement methods they do not use."

Here, it's about how to write interfaces. So what is stated? Basically, once an interface is becoming too large/fat, we absolutely need to split it into small interfaces that are more specific. And the interface will be defined by the client that will use it, which means that the client of the interface will only know about the methods that are related to them.

Actually, if you add methods that shouldn't be there, the classes implementing the interface will have to implement those methods as well. That is why the client shouldn't be forced to depend on interfaces that they don't use. ISP is intended to keep a system decoupled and thus easier to refactor, change, and deploy.

#### 5\. Dependency Inversion Principle

> "High-level modules should not depend on low level modules, rather both should depend on abstraction. Abstraction should not depend on details; rather detail should depend on abstraction."

The last of the SOLID principles, but not the least, this principle is primarily concerned with reducing dependencies amongst the code modules. Basically, the Dependency Inversion Principle will be of a great help when it comes to understanding how to correctly tie your system together.

If your implementation detail will depend on the higher-level abstractions, it will help you to get a system that is coupled correctly. Also, it will influence the encapsulation and cohesion of that system.

## Conclusion

When developing any software, there are two concepts that are very important: cohesion (when different parts of a system will work together to get better results than if each part would be working individually) and coupling (can be seen as a degree of dependence of a class, method, or any other software entity).

Coupling is usually present in a lot of code and as I mentioned earlier, the optimal situation would be to have a low coupling and a high cohesion. With this brief introduction to the 5 SOLID principles, you must have understood that they help us when it comes to that.

There are so many principles in software engineering and I would recommend that before writing code, you do your research, read and try to understand these principles. Although it may seem like a lot, SOLID becomes a part of you and your code by using it continuously and adapting its guidelines.

## If You Enjoyed This, You Might Like…

Release quality software faster with [TestComplete.](https://dzone.com/go?i=228240&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad) Discover how to decrease testing times and expand test coverage with the most robust automated UI testing tool. [Try free for 30 days.](https://dzone.com/go?i=228240&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad)
