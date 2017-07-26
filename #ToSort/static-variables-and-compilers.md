# Static Variables and Compilers

_Captured: 2017-03-09 at 00:55 from [dzone.com](https://dzone.com/articles/static-variable-and-java-compiler?edition=276897&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-08)_

I am a long time Java programmer, almost 20 years now. I love this language a lot, and I would like to share an observation.

Consider the below code snippet:

When you try to compile the above code, the Java Compiler will raise an compilation error: **"illegal forward reference"**. This is because the compiler expects the static variable 'WORLD' to be defined first before referencing it. In order to compile successfully, the code has to be modified to:

It would be convenient for Java developers if this sort of sequencing can be eliminated. Java developers are already used to this sort of flexibility when they define methods. When you define Java methods, you don't have to follow any sequence. Methods defined at the bottom of the class can be referenced by methods in top of the class. In Java, **function calls are resolved at runtime, whereas static finals are resolved at compile time.** That's what causing this inconvenience.

Advancements in technology have been progressing at an unbelievable pace. Applications are getting smarter and smarter. Applications are getting into the human mind and are starting to understand how a human is thinking and providing solutions accordingly. In this age of rapid advancement, there are a few things which are frozen in time. One of them is the sequencing of static variables in the Java language. Time for a change?
