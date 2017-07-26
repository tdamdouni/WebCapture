# ClassNotFoundException vs. NoClassDefFoundError

_Captured: 2017-05-14 at 21:51 from [dzone.com](https://dzone.com/articles/classnotfoundexception-vs-noclassdeffounderror?edition=298100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-14)_

What every Java engineer should know about microservices: [Reactive Microservices Architecture](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone). Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).

We know that Java is an OOP language and that almost everything is an object in Java. And in order to create an object, we need a class.

While executing our program, whenever the JVM find a class, first it will try to load that class into memory if it has not done so already.

For example, if the JVM is executing the line of code below, before creating the object of the Employee class, the JVM will load this class into memory using a ClassLoader.

In the above example, the JVM will load the Employee class because it is present in the execution path -- and the JVM wants to create an object of this class.

But we can also ask the JVM to just load a class through its string name using Class.forName() or ClassLoader.findSystemClass() or ClassLoader.loadClass() methods. For Example, the following line of code will only load the Employee class into memory and do nothing else.

Both **ClassNotFoundException **and **NoClassDefFoundError **occur when a particular class is not found at runtime -- but under different scenarios. And here in this article, we going to study these different scenarios.

## ClassNotFoundException

ClassNotFoundException is a checked exception that occurs when we tell the JVM to load a class by its string name using the Class.forName() or ClassLoader.findSystemClass() or ClassLoader.loadClass() methods and the mentioned class is not found in the classpath.

Most of the time, this exception occurs when you try to run an application without updating the classpath with the required JAR files. For example, you may have seen this exception when doing the JDBC code to connect to your database, i.e.MySQL, but your classpath does not have the JAR for it.

If we compile the example below, the compiler will produce two class files Test.class and Person.class. And now, if we execute the program, it will successfully print `Hello`. But if we delete the Person.class file and try to execute the program again, we will receive a ClassNotFoundException.

## NoClassDefFoundError

NoClassDefFoundError is a subtype of java.lang.Error, and the Error class indicates an abnormal behavior that really should not happen with an application. Meanwhile, application developers should not try to catch it -- it is there for JVM use only.

NoClassDefFoundError occurs when the JVM tries to load a particular class that is the part of your code execution (as part of a normal method call or as part of creating an instance using the `new` keyword) and that class is not present in your classpath -- but was present at compile time. In order to execute your program, you need to compile it, and if you are trying use a class that is not present, the compiler will raise a compilation error.

Similar to the above example, if we try to compile the program below, we will get two class files: `Test.class` and ` Employee.class`. Upon execution, it will print ` Hello`.

But if we delete Employee.class and try to execute the program, we will get a NoClassDefFoundError.

As you can see in above stack trace, NoClassDefFoundError is caused by ClassNotFoundException, because the JVM is not able to find the Employee

class in the classpath.

## Conclusion

![Difference-Between-ClassNotFoundException-and-NoClassDefFoundError](https://4.bp.blogspot.com/-C_sn-jti8HE/WOioqaoU0UI/AAAAAAAAK7w/ps_eyJ3QVHkju5CAWdoQM_2IvgneT21nwCK4B/s1600/Difference-Between-ClassNotFoundException-and-NoClassDefFoundError.png)

You can find complete code on this [GitHub repository](https://github.com/njnareshjoshi/exercises/blob/master/src/org/programming/mitra/exercises/ClassNotFoundExceptionExample.java), and please feel free to provide your valuable feedback.

Microservices for Java, explained. Revitalize your legacy systems (and your career) with [Reactive Microservices Architecture](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone), a free O'Reilly book. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).
