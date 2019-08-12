# How to Specify Multiple Resources in a Single Try-With-Resources Statement

_Captured: 2018-09-01 at 09:23 from [dzone.com](https://dzone.com/articles/carefully-specify-multiple-resources-in-single-try?edition=387238&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-31)_

How do you break a Monolith into Microservices at Scale? [This ebook](https://dzone.com/go?i=296455&u=https%3A%2F%2Finfo.lightbend.com%2Febook-reactive-microservices-the-evolution-of-microservices-at-scale-register.html%3Futm_source%3Ddzone%26utm_medium%3Dpost-roll-text%26utm_campaign%3DCOLL-2017-Reactive-Microsystems-The-Evolution-of-Microservices-at-Scale%26utm_term%3Dnone%26utm_content%3Djava-zone) shows strategies and techniques for building scalable and resilient microservices.

One of the more useful [features of Java 7](https://www.oracle.com/technetwork/java/javase/jdk7-relnotes-418459.html) was the introduction of the [try-with-resources statement](https://docs.oracle.com/javase/7/docs/technotes/guides/language/try-with-resources.html), also known as the [Automatic Resource Management](https://www.theserverside.com/tutorial/OCPJP-Exam-Objective-How-to-Use-Try-With-Resources-to-Clean-Up-Closeable-Resources) ([ARM](http://mail.openjdk.java.net/pipermail/coin-dev/2009-March/000128.html)). The attractiveness of the [try-with-resources statement](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html) lies in its [promise](https://docs.oracle.com/javase/7/docs/technotes/guides/language/try-with-resources.html) to "ensure that each resource is closed at the end of the statement." A "resource" in this context is any class that implements [AutoCloseable](https://docs.oracle.com/javase/10/docs/api/java/lang/AutoCloseable.html) and its [close()](https://docs.oracle.com/javase/10/docs/api/java/lang/AutoCloseable.html#close\(\)) method and is instantiated inside the "try" clause of the [try-with-resources statement](https://www.baeldung.com/java-try-with-resources).

The [Java Language Specification](https://docs.oracle.com/javase/specs/) (JLS) describes the [try-with-resources statement](https://docs.oracle.com/javase/specs/jls/se10/html/jls-14.html#jls-14.20.3) in detail in [Section 14.20.3](https://docs.oracle.com/javase/specs/jls/se10/html/jls-14.html#jls-14.20.3) of [Java SE 10 JLS](https://docs.oracle.com/javase/specs/jls/se10/jls10.pdf) in this case. The JLS states that the " `try`-with-resources statement is parameterized with local variables (known as _resources_) that are initialized before execution of the `try` block and closed automatically, in the reverse order from which they were initialized, after execution of the `try` block."

The JLS clearly specifies that multiple resources can be defined in relation to a single `try`-with-resources statement, and it specifies how multiple resources are specified. Specifically, it indicates that `try` can be followed by a " [ResourceSpecification](https://docs.oracle.com/javase/specs/jls/se10/html/jls-14.html#jls-ResourceSpecification)" that is composed of a " [ResourceList](https://docs.oracle.com/javase/specs/jls/se10/html/jls-14.html#jls-ResourceList)" that is composed of one or more "[Resource](https://docs.oracle.com/javase/specs/jls/se10/html/jls-14.html#jls-Resource)'s." When there is more than a single declared resource, the multiple resources are delimited by a semicolon (`;`). This specification of multiple resources in a semicolon-delimited list is important because any candidate resources not declared in this manner will not be supported (will not be closed automatically) by the `try`-with-resources statement.

The most likely source of errors when specifying multiple resources in a `try`-with-resources statement is "nesting" instantiations of "resources," instead of explicitly instantiating local variables of each of them separately with semicolons between each instantiation. The examples below will illustrate the difference.

Two ridiculous but illustrative classes are shown next. Each class implements an [AutoCloseable](https://docs.oracle.com/javase/10/docs/api/java/lang/AutoCloseable.html) and can be used in conjunction with `try`-with-resources and will have its `close()` method called automatically when used correctly with the `try`-with-resources statement. They are named to reflect that the `OuterResource` can be instantiated with an instance of the `InnerResource`.

**InnerResource.java**

**OuterResource.java**

The two classes defined can now be used to demonstrate the difference between correctly declaring instances of each in the same `try`-with-resources statement in a semicolon-delimited list and incorrectly nesting instantiation of the inner resource within the constructor of the outer resource. The latter approach doesn't work as well as hoped, because the inner resource --without a locally defined variable -- is not treated as a "resource" in terms of invoking its `AutoCloseable.close()` method.

The next code listing demonstrates the **incorrect** approach for instantiating "resources" in the `try`-with-resources statement.

**Incorrect Approach for Instantiating Resources in `try`-with-resources Statement**

When the code above is executed, the output " `InnerResource created`" is seen, but no output is ever presented related to the resource's closure. This is because the instance of `InnerResource` was instantiated within the call to the constructor of the `OuterResource` class and was never assigned to its own separate variable in the resource list of the `try`-with-resource statement. With a real resource, the implication of this is that the resource is not closed properly.

The next code listing demonstrates the **correct** approach for instantiating "resources" in the `try`-with-resources statement.

**Correct Approach for Instantiating Resources in `try`-with-resources Statement**

When the code above is executed, the output includes both `InnerResource created` and `InnerResource closed` , because the `InnerResource` instance was properly assigned to a variable within the `try`-with-resources statement. Therefore, its `close()` method is properly called, even when an exception occurs during its instantiation.

The [try-with-resources statement](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html) section of the [Java Tutorials](https://docs.oracle.com/javase/tutorial/index.html) includes examples of correctly specifying the resources in the `try`-with-resources as semicolon-delimited individual variable definitions. One example shows this correct approach with [java.util.zip.ZipFile](https://docs.oracle.com/javase/10/docs/api/java/util/zip/ZipFile.html) and [java.io.BufferedWriter](https://docs.oracle.com/javase/10/docs/api/java/io/BufferedWriter.html). Another example shows this correct approach with instances of [java.sql.Statement](https://docs.oracle.com/javase/10/docs/api/java/sql/Statement.html) and [java.sql.ResultSet](https://docs.oracle.com/javase/10/docs/api/java/sql/ResultSet.html).

The introduction of `try`-with-resources in JDK 7 was a welcome addition to the language that it made it easier for Java developers to write resource-safe applications that were not as likely to leak or waste resources. However, when multiple resources are declared within a single `try`-with-resources statement, it's important to ensure that each resource is individually instantiated and assigned to its own variable declared within the `try`'s resource specifier list to ensure that each and every resource is properly closed. A quick way to check this is to ensure that for _n, _`AutoCloseable `is implementing resources specified in the `try.`There should be _n-1_ semicolons, separating those instantiated resources.

How do you break a Monolith into Microservices at Scale? [This ebook](https://dzone.com/go?i=296456&u=https%3A%2F%2Finfo.lightbend.com%2Febook-reactive-microservices-the-evolution-of-microservices-at-scale-register.html%3Futm_source%3Ddzone%26utm_medium%3Dpost-roll-text%26utm_campaign%3DCOLL-2017-Reactive-Microsystems-The-Evolution-of-Microservices-at-Scale%26utm_term%3Dnone%26utm_content%3Djava-zone) shows strategies and techniques for building scalable and resilient microservices.

Topics:

java ,try-with-resources ,code ,example ,tutorial ,jls ,java 7
