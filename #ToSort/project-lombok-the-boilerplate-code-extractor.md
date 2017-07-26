# Project Lombok: The Boilerplate Code Extractor

_Captured: 2017-05-14 at 21:50 from [dzone.com](https://dzone.com/articles/project-lombok-the-boilerplate-code-extractor-1?edition=298100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-14)_

### Lombok can be a huge space saver for your projects by generating boilerplate code directly in your class file. See how it works and the many annotations at your disposal.

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D).

Lombok is a tool that generates code for things like getters, setters, constructors, equals, hashCode, and toString for us in the same way that our IDE does. While an IDE generates all these things in our source code file, Lombok generates them directly in the class file.

So Lombok basically takes out all these things from your source code, which means a smaller source code file. And in this article, I am going to explain how Lombok can help us in removing this kind of boilerplate code.

To understand it, let's suppose we have an entity class, Employee, and we want to use it to hold a single employee record. We can use it as a DTO or persistent entity or anything else we want, but the idea is that we want to use it to store id, firstName, lastName, and salary fields.

For this requirement, we will need a simple Employee POJO and, according to the [General directions for creating Plain Old Java Objects](https://programmingmitra.blogspot.in/2016/05/plain-old-java-object-pojo-explained.html):

  * Each variable in a POJO should be declared as private.
  * Default constructors should be overridden with public accessibility.
  * Each variable should have its Setter-Getter method with public accessibility.
  * A POJO should override equals(), hashCode(), and toString() methods of Object.

And generally, our Employee class will look like:
    
    
            if (this == o) return true;
    
    
            if (o == null || getClass() != o.getClass()) return false;
    
    
            if (id != employee.id) return false;
    
    
            if (salary != employee.salary) return false;
    
    
            if (!firstName.equals(employee.firstName)) return false;
    
    
            if (!lastName.equals(employee.lastName)) return false;
    
    
            int result = (int)(id ^ (id >>> 32));
    
    
            result = 31 * result + firstName.hashCode();
    
    
            result = 31 * result + lastName.hashCode();
    
    
            result = 31 * result + salary;
    
    
                ", firstName='" + firstName + '\'' +

But generally, we always use the auto-generation strategies of our IDE to generate getters, setters, default constructor, hashCode, equals, and toString -- e.g. alt+insert in IntelliJ.

As you can see, the size of the Employee class is more than 50 lines, while field declaration is contributing only 4 lines. And these things are not directly contributing anything to our business logic, just increasing the size of our code.

Project Lombok provides a way to remove the above boilerplate code and simplify the development process while still providing these functionalities at the bytecode level. With Project Lombok, we can combine all these things to within 10 lines:

With the **@Data** annotation on top of our class, Lombok will process our Java source code and produce a class file, which will have getters, setters, default arg constructor, hasCode, equals, and toString methods in it. So, basically, Lombok is doing the trick, and, instead of us adding all those things in our source code and then compiling it to a class file, Lombok is automatically adding all these things directly to our class files.

But if we need to write some business code in our getters or setters or in any of the above method or we want trick these methods to function a little bit differently, we can still write that method in our class and Lombok will not override it while producing all this stuff in bytecode.

In order to make it works, we need to:

  1. Install the Lombok plugin in our IDE -- e.g. In IntelliJ, we can install it from Settings -> Plugins -> Browse Repositories.![installing-lombok-plugin-in-intellij-idea](https://2.bp.blogspot.com/-Eu7FIdTR1L0/WIxXrOWXzoI/AAAAAAAAKdA/J4I7vFyq-D8NfVYPXYAFEKcYHRpTMvOIgCK4B/s640/lombok%2B2.png)

  2. Enable annotation processing -- e.g. In IntelliJ, we need to check "Enable annotation processing" option on Settings -> Compiler -> Annotation Processors.![enabling-annotation-in-intellij-idea](https://3.bp.blogspot.com/-LeYWZoVWk8A/WIxYAMH48hI/AAAAAAAAKdI/LGGpP8j-VW0oZUH53EMlwbWP-aKyOER0wCK4B/s640/lombok%2B3.png)

  3. Include the Lombok JAR in our build path. We can do that by adding the Lombok dependency in the pom.xml file if we are using Maven, or we will need to download the Lombok JAR manually and add it to our classpath.  


Lombok provides a variety of annotations that we can use and manipulate according to our needs. Some of these annotations are:

  * **@NonNull**: Can be used with fields, methods, parameters, and local variables to check for NullPointerExceptions.
  * **@ToString**: Generates a default toString method.
  * **@NoArgsConstructor**, **@RequiredArgsConstructor**, and **@AllArgsConstructor**: Generates constructors that take no arguments, one argument per final/non-null field, or one argument for every field. 
  * **@Data**: A shortcut for **@ToString **, **@EqualsAndHashCode**, **@Getter **on all fields, and** @Setter **on all non-final fields, and **@RequiredArgsConstructor**. 
  * **@Value **is the immutable variant of **@Data**. It helps in making our class Immutable. 
  * The** @Builder **annotation will generate nice static factory methods in our class, which we can use to create objects of our class in a more oriented manner -- e.g. if we will add the "@Builder" annotation to our Employee class, then we can create an object of Employee in the following manner   

  * **@SneakyThrows **allows us to throw checked exceptions without actually declaring this in our method's throws clause:  

  * **@Synchronized**: A safer variant of the synchronized method modifier. 

You can also go to the official website of project [Lombok](https://projectlombok.org/features/index.html) for the complete feature list and examples.

## Advantages of Lombok

  * Lombok helps us remove boilerplate code and decrease lines of unnecessary code
  * It makes our code highly maintainable. We don't need to worry about regenerating hashCode, equals, toString, getters, and setters whenever we change our properties.
  * Lombok provides an efficient builder API to build our object by using @Builder.
  * Lombok provides efficient way to make our class Immutable by using @Value.
  * Provides other annotations like @Log for logging, @Cleanup for cleaning resources automatically, and @SneakyThrows for throwing checked exceptions without adding try-catch or throw statements, and @Synchronized to make our methods synchronized.

## Disadvantages of Lombok

The only disadvantage Lombok comes with is its dependency. If you are using it, then everyone in your project must use it and configure it (install the plugin and enable annotation processing) to successfully compile the project. And all your project mates need to be aware of it. Otherwise, they will not be able to build the project and receive lots of compilation errors. However, this is only an initial step and will not take more than a couple of minutes.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D).
