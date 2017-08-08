# SOLID Principles in Software Development

_Captured: 2017-08-04 at 22:33 from [www.growthaccelerationpartners.com](https://www.growthaccelerationpartners.com/blog/solid-principles-software-development/?ref=quuu&utm_content=buffer37f81&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

As a software developer, you'll work on a variety of applications each with their own unique architecture. Or maybe you've inherited a brownfield legacy mess! You can make your life and other developers' lives less painful by adopting some patterns and best practices.

When building an object-oriented system, in a language such as _[Microsoft.NET_](https://www.growthaccelerationpartners.com/services/cloud-app-development/dotnet/) C#, you'll want to make it easier to maintain and extend over time. This is especially true when working on enterprise systems that often contain hundreds of thousands of lines of code.

Throw in a few offshore development teams and suddenly enforcing company wide development standards that adhere to best practice isn't relegated to those in architectural ivory towers; it can become mandatory to help ensure the development factory is running efficiently.

In this article, we explore a set of principles called SOLID that can help alleviate some of these pain points and help remove code smells.

## **Origins**

The SOLID mnemonic was introduced by _[Michael Feathers](https://en.wikipedia.org/wiki/SOLID_\(object-oriented_design\))_ in around 2000 and stands for the 5 main concepts of object oriented coding and software design.

  * **S**ingle responsibility
  * **O**pen-closed
  * **L**iskov substitution
  * **I**nterface segregation
  * **D**ependency inversion

The idea behind these principles is that when each is observed, the developer is more likely to create a system that is easier to maintain and extend. In the following sections, we'll discuss each of these points in turn.

### **Single Responsibility**

This principle basically states that each class should have single responsibility for one area of functionality provided by the solution, and that all required code should be encapsulated by that class.

Take the example below. We have a loan calculator interface and a class that implements it. The class is responsible for only one thing, any new features or methods that get added to this interface or class must purely related to the "loans".

![SOLID principles single responsibility](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/pasted-image-0-6.png)

### **Open Closed**

The Open Closed principle states that:

"_software entities, classes, methods etc. should be open for extension but closed for modification_".

Modification to the entities behaviour can be achieved by **extending** its features but not modifying its source code.

One way to adhere to this principle is by using inheritance as it allows you to take a class, inherit from it and extend the existing functionality where you need to.

Imagine our Loan Calculator had to be used in a different bank or State, we may wish to keep some existing functionality but have different implementations of the **ProcessApplication** method which determines if a person has been accepted for a loan:

![SOLID principles open closed](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/pasted-image-0-1.png)

### **Liskov Substitution **

This principle is named after _[Barbara Liskov](http://amturing.acm.org/award_winners/liskov_1108679.cfm)_ who originally talked about the problem in 1998. She states that:

_"you should be able to use any derived class in place of a parent class and have it behave in the same manner without modification "_

It ensures that derived classes do not affect the behavior of the classes they are inheriting from. Or put another way, that any derived class can take the place of its parent class.

Here is a real-world example to bring this concept to life.

**Perfect substitution**

![Cylindrical glass Liskov substitution](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/image1-2-300x300.jpg)

![Conical glass Liskov substitution](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/image2-2-300x300.jpg)

If the parent glass is broken, it can be replaced with the child. A person can drink from each cup, and it belongs to a kitchen.

**Violating substitution**

![Metal jug Liskov substitution](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/image3-2-300x300.jpg)

The images above show a violation of the principle. Water can be poured into both, but a person cannot drink from the watering can.

Consider the following class hierarchy where we have three types of bank account that implement an interface **IBankAccount**:

![SOLID principles class heirachy](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/image4-2.png)

> _For completeness, the following code is present in each class:_

![SOLID principles code](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/pasted-image-0-5.png)

As per imaginary business rules, the ChildAccount doesn't allow any withdrawals for the time being whereas other account types (Pensioner and Adult) are allowed.

Consider the following method in our AccountManager class:

![pasted image 0 8](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/pasted-image-0-8.png)

> _Which in turn invokes either of the following methods:_

![SOLID principles code withdraw from account](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/pasted-image-0-2.png)

_An exception is being thrown from the Child Account class, because of this, the Liskov Substitution principle is being violated._

Remember the principle states that functionality from the parent class should not be broken in child classes?

**How can this be fixed?**

We need to verify the inheritance hierarchy isn't broken as we create classes. In the following revised class diagram, two new classes have been added and the child classes inherit from the relevant parent class:

![SOLID principles class heirachy](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/image5-2.png)

> _The code can now be written as follows:_

![code](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/pasted-image-0-7.png)

The AccountManager class can now be invoked via the following method. Note the "account type" must be of type **BankAccountWithWithDraw**.

![pasted image 0 10](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/pasted-image-0-10.png)

However, when trying to perform a withdraw against a child account, the compiler will notify the developer:

![code](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/pasted-image-0.png)

This is because the ChildAccount _does not_ inherit from **IBankAccountWithWithdraw**.

You can see that by implementing this principle we **prevent the possibility of runtime exceptions being introduced** or business rules from potentially miscalculating values.

### **Interface Segregation**

This principle states:

"_that clients should not be forced to depend on interfaces they do not use_".

This principle is about **breaking down monster interfaces into more specialized ****fine grained**** ones**.

Imagine there were 10 more methods in the **ILoanAccount** interface and we didn't have direct access to the interface source code. We may not want to implement every single method either. Our only choice would be to implement the methods we're interested in and ignore the methods that aren't relevant to our class.

It's not ideal but it would work.

You could throw a **NotImplementedException** for guidance in terms of the methods we didn't need to implement but the interface explicitly mandated.

If you're a [Microsoft.NET](https://www.growthaccelerationpartners.com/services/cloud-app-development/dotnet/) developer, you will be aware of the _[Membership Provider](https://msdn.microsoft.com/en-us/library/system.web.security.membershipprovider\(v=vs.110\).aspx)_. This was great when integrated with SQL Server and gave you lots of user administration methods such as Change Password, DeleteUser etc.

But say you wanted to roll your own implementations of the _[Membership Provider](https://msdn.microsoft.com/en-us/library/system.web.security.membershipprovider\(v=vs.110\).aspx)_. You were forced to implement almost 30 methods! You may not want to do that though, and only need to change one or two.

### **Dependency Inversion**

This principle consists of two points:

  1. _High-level modules should not depend on low-level modules. Both should depend on abstractions._
  1. _Abstractions should not depend on details. Details should depend on abstractions._

This principle is about reducing the dependencies amongst classes in an application.

You can think of it as low-level objects providing _[coarse grained interfaces](https://stackoverflow.com/questions/3766845/coarse-grained-vs-fine-grained)_ that high-level objects can use, without the high-level objects having to know or care about the specific implementations provided by low-level objects.

Examples of this may be system auditing, notification mechanisms or database layers. Imagine our LoanCalculator had to perform an audit of each user interaction in the system, either to the file system or database.

A class called **AuditManager** resides in the business logic layer and is responsible for invoking the audit mechanism via the method **LogMessage(string message)**. In most well-architected systems you'd have a business logic layer to house complex rules.

The **LoanCalculator** solution contains the following interface:

And the following concrete classes implement the **ILogger** interface:

![code ilogger](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/pasted-image-0-4.png)

Now here is where it gets interesting. We know that **AuditManager** needs to invoke LogMessage("Customer Processed") but we aren't interested in the implementation of _how_ it achieves this "under the hood".

Prior to adopting SOLID principles, the AuditManager may have directly called something like .LogMessageToFile() or .LogMessageToDatabase().

By adopting the dependency inversion principle, the AuditManager can be written like this:

![code audit manager](https://tz49q191hubp5f4qy2ym714z-wpengine.netdna-ssl.com/wp-content/uploads/2017/06/pasted-image-0-9.png)

> _So, what's going on here?_

The AuditManagers constructor accepts any class that implements the ILogger interface. This is called constructor injection.

Depending on the type being passed into the constructor (DBLogger or FileLogger in our case), the application will write audit records to the database or file system.

It means that whenever .LogMessage() is called by AuditManager, it doesn't care how the low level audit operation is being dealt with. It's only concern is to invoke LogMessage() and let the low level (concrete) logging classes deal with writing to the file system or database.

In an ASP.NET application, the config option could be controlled via the web.config file or a similar XML application settings file thereby meaning audit providers can be swapped in and out easily, (providing they adhere to ILogger interface).

### **Summary**

In this article, we've run through the SOLID principles in turn and some examples. Whilst they aren't a "silver bullet", by implementing them you can ensure that your application's code base will be easier to maintain and support.

What's been your experience with SOLID principles?
