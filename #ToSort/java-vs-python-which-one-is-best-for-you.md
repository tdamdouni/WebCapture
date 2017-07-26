# Java vs. Python: Which One Is Best for You?

_Captured: 2017-03-31 at 20:11 from [dzone.com](https://dzone.com/articles/java-vs-python-which-one-is-best-for-you?edition=286955&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-31)_

Learn how to troubleshoot and diagnose some of [the most common performance issues in Java today](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

Few questions in software development are more divisive or tribal than choice of programming language.

![](https://46zwyrvli634e39iq2l9mv8g-wpengine.netdna-ssl.com/wp-content/uploads/2017/03/java-or-python-which-one-is-best-for-you-header-e1490117734919.png)

Software developers often identify strongly with their tools of choice, freely mixing objective facts with subjective preference.

The last decade, however, has seen an explosion both in the number of languages used in production and the number of languages an individual developer is likely to employ day to day. That means that language affiliations are sometimes spread more loosely and broadly across different codebases, frameworks, and platforms. Modern projects and modern developers are increasingly polyglot--able to draw on more languages and libraries than ever before. Informed choice still has a part to play.

From that bustling bazaar of programming languages, let's narrow our focus to two survivors of the 1990s that have very different origin stories: Java and Python.

## Python's Story

[Python](https://www.python.org/) is the older of the two languages, first released in 1991 by its inventor, Guido van Rossum. It has been open source since its inception. The [Python Software Foundation](https://www.python.org/psf/) manages the design and standardization of the language and its libraries. The [Python Enhancement Proposal](https://www.python.org/dev/peps/pep-0001/) (PEP) process guides its development.

In programming language evolution, it is common to maintain backward compatibility indefinitely. This is not the case with Python. Python 2 arrived in 2000 and Python 3 hit the scene in 2008. They are largely compatible, but have enough functionality- and syntax-breaking differences that they can be treated as different languages. Rather than retrofit newer trends and ideas into Python 2 (complicating and compromising the language), Python 3 was conceived as a new language that had learned from Python 2's experience. Python 3--version 3.6 at the time of writing--is where current evolution and emphasis in the Python world exists. Python 2 development has continued separately, but its final incarnation is version 2.7, which will no longer be maintained after 2020.

Python's syntax embodies a philosophy of readability, with a simple and regular stykle that encourages brevity and consistent code layout. It originated as a scripting language, embodying the Unix philosophy of being able to compose new programs from old, as well as using existing code directly. This simplicity and composability is helped by Python's dynamic type system. It is an interpreted language available on many platforms, making it a portable option for general development.

Python's reference implementation, written in C and known as CPython, is available on many platforms and is the most commonly used. Other groups have created their own implementations, such as [IronPython](http://ironpython.net/), which is written in C# and offers close integration with the .NET runtime.

Python is a general-purpose language built around an extensible object model. Its object-oriented core does not necessarily mean object orientation is the most common style developers use when programming in Python. It has support for procedural programming, modular programming, and some aspects of functional programming.

The language's name--and no small amount of humor to be found peppered through its documentation and libraries--comes from British surrealist comedy group [Monty Python](https://docs.python.org/3/faq/general.html#why-is-it-called-python).

## Java's Story

Although it was not released until 1995, Java's story begins in 1991. James Gosling and others at Sun Microsystems conceived a language for programming interactive TV systems. It was released with the fanfare of being a portable internet language, particularly in the browser. It is now a long way from this starting point and the original name: Oak.

Just as it was too heavyweight at the time for its original TV target market, it lost the browser space to dynamic HTML and JavaScript (which, in spite of its name, is unrelated as a language). However, [Java](https://www.java.com/en/) rapidly found itself on the server and in the classroom, helping ensure its ranking as the dominant language at the turn of the millennium.

Part of its attraction and value is its portability and relative efficiency. Although not a native language, such as C and C++, Java is a compiled language. Its execution model is more machine-centered than purely interpreted languages, such as Python and Perl. Java is more than just a language and libraries: It is also a virtual machine and, therefore, an ecosystem. The Java Virtual Machine (JVM) is an idealized and portable platform for running Java code. Rather than worrying about hardware specifics and having to port code to new platforms, the promise of Java has been [Write Once, Run Anywhere](http://whatis.techtarget.com/definition/write-once-run-anywhere-WORA) (WORA). That is so that as long as a JVM is present, anything compiled into its bytecode can run and interact easily with anything else written for the JVM. There are many JVM languages, including the more script-like [Groovy](http://www.groovy-lang.org/), the functional [Clojure](https://clojure.org/), the object-functional hybrid [Scala](https://www.scala-lang.org/), and even a Python variant, [Jython](http://www.jython.org/).

Java is an object-oriented language with a C/C++-like syntax that is familiar to many programmers. It is dynamically linked, allowing new code to be downloaded and run, but not dynamically typed. As a language, Java's evolution has been relatively slow, only recently incorporating features that support functional programming. On the other hand, the philosophy of both the language and the VM has been to treat backward compatibility as a prime directive.

After Oracle bought Sun, the language and its compiler were eventually open-sourced. The language's evolution is guided by the [Java Community Process](https://www.jcp.org/en/home/index) (JCP), which includes companies and individuals outside Oracle.

So how do these two languages stack up? Let's break it down by category.

## Speed

![](https://46zwyrvli634e39iq2l9mv8g-wpengine.netdna-ssl.com/wp-content/uploads/2017/03/java20or20paython01.png)

Although performance is not always a problem in software, it should always be a consideration. Where network I/O costs or database access dominate, the specific efficiency of a language is less significant than other aspects of technology choice and design when it comes to overall efficiency.

Although neither Java nor Python is especially suited to high-performance computing, when performance matters, Java has the edge by platform and by design. Although some Python implementations, such as [PyPy](http://pypy.org/), are fine-tuned for performance, raw portable performance is not where Python shines.

A lot of Java efficiency comes from optimizations to virtual machine execution. A JVM can translate bytecode into native machine code as a program executes. This Just-In-Time (JIT) compilation is why Java's performance can often rival that of native languages. Relying on JIT is a reasonably portable assumption as HotSpot, the default Oracle JVM, offers it.

Java has had support for concurrency from its first public version, whereas Python is more resolutely a sequential language. This has implications for taking advantage of current multi-core processor trends, with Java code more readily able to do so. The [Global Interpreter Lock](https://wiki.python.org/moin/GlobalInterpreterLock) (GIL) in the dominant implementation of Python, CPython, stands in the way of such scaling. Python implementations without hits restriction exist, but relying on them can interfere with some of the portability assumptions underpinning Python code.

## Legacy

![](https://46zwyrvli634e39iq2l9mv8g-wpengine.netdna-ssl.com/wp-content/uploads/2017/03/java20or20paython02.png)

Often language choice is not about the design and intrinsic qualities of the language itself. Languages exist to create code, and that code has a context in business, economics, history, software architecture, skills, and development culture.

Legacy systems have inertia around their incumbent technologies. Changes will more easily follow the path already laid down, shifting gradually and incrementally rather than by rewrite and revolution. For example, an existing Python 2 codebase is more likely to find a new lease on life in Python 3 than in a rewrite. The back-end of an existing Java enterprise project is likely to grow its functionality with more Java code, perhaps migrating to a more current version of the language, or by adding new features in other JVM languages such as Scala and Groovy.

Java's history in the enterprise and its slightly more verbose coding style mean that Java legacy systems are typically larger and more numerous than Python legacy. On the other hand, organizations may be surprised to find how many of the scripts and glue code that hold their IT infrastructure together are made up of Python. Both languages have a legacy problem, but it typically presents differently.

## Practical Agility

![](https://46zwyrvli634e39iq2l9mv8g-wpengine.netdna-ssl.com/wp-content/uploads/2017/03/java20or20paython03.png)

Development culture and trends have benefited both Java and Python. By virtue of publications that have used Java as their lingua franca and tools that focused on working with Java, Java is often seen to have the closer association with agile development and its community. But no community is static and so easily defined. Python has always had a presence in the agile space and has grown in popularity for many reasons, including the rise of the [DevOps](https://www.appdynamics.com/role/devops/) movement.

Java enjoys more consistent refactoring support than Python thanks on one hand to its static type system which makes automated refactored more predictable and reliable, and on the other to the prevalence of IDEs in Java development (IntelliJ, Eclipse, and NetBeans, for example). Python's more dynamic type system encourages a different kind of agility in code, focusing on brevity, fluidity, and experimentation, where Java is perhaps seen as a more rigid option. That very same type system, however, can be an obstacle to automated refactoring in Python. Pythonic culture favors a diverse range of editors rather than being grounded in IDEs, which means there is less expectation of strong automated refactoring support.

The early popularity of [JUnit](http://junit.org/) and its association with test-driven development (TDD) has meant that, of all languages, Java enjoys perhaps the most consistent developer enthusiasm for unit testing of any language. The automatic inclusion of JUnit in IDEs has, in no small part, helped.

That said, Python's origins in scripting and the inclusion of test features in its standard library mean that Python is no stranger to the emphasis on automated testing found in modern development, although it is more often likely to be integration rather than unit testing.

## Human Resources

![](https://46zwyrvli634e39iq2l9mv8g-wpengine.netdna-ssl.com/wp-content/uploads/2017/03/java20or20paython04.png)

Sometimes language choice is more about the application of skills than it is about the software applications themselves. Staffing may count for more than language design and tooling. If the ideal language for the job is one that no one has skills in--and no one wants skills in--then it is probably not the ideal language for the job after all. On the other hand, if developers are keen to embrace a new technology then all other things being equal, this can be a good enough reason to go with that technology. In the Java world, the pill of a legacy Java codebase can often be sweetened by embracing another JVM language, such as using Groovy or Clojure for automated testing, or stepping outside the Java universe altogether, such as using Python to handle the operations side of the system.

Another side to the staffing question is the skills market. Both Java and Python are stalwarts of the [TIOBE Index](http://www.tiobe.com/tiobe-index/) programming language popularity top 10 list. Java has consistently been more popular than Python, but Python has experienced the greater growth of the two languages, picking up where Perl and Ruby are falling.

Following the idea that one of the greatest influences on both personal choice and employment interest is going with what you know, both languages have a strong foothold in education, with Java more typically used on university courses and Python used in high school. Current IT graduates have one or both of these languages on their resume almost by default.

## Architecture

![](https://46zwyrvli634e39iq2l9mv8g-wpengine.netdna-ssl.com/wp-content/uploads/2017/03/java20or20paython05.png)

Skills and existing software systems and choices inform the programming languages used in any given software architecture. Software architecture is also matter of frameworks and libraries, reuse, and integration. In many cases, it is the technologies people want to take advantage of that dictate language choice rather than the other way around. A software architecture conceived around a Python web framework will not get far with a Java-only development team.

Both Java and Python enjoy a seemingly endless supply of open-source libraries populated by code from individuals and companies who have solved common and uncommon problems, and who are happy to share so others can take advantage of their solutions. Indeed, both languages have benefited from--and been shaped by--online forums and open-source development.

When questions of legacy, reuse, performance, and development skills have all been accounted for, some architectural decisions can still leave the choice of language open. For example, the rise of microservice architectures (where internet-facing systems are partitioned into small, cooperating processes) make the choice of language more of a localized detail than a dominant consideration across a project.

For all the diversity present in the modern programming landscape and its software architectures, some teams and businesses prefer to reduce some of their technology choices rather than live with a jumble of past decisions and personal whim. But consolidation can reduce options, so this is not a decision to be taken lightly. It is worth keeping an eye on trends in languages and frameworks to avoid taking the wrong fork in the road.

## Conclusion

Java and Python are both in it for the long haul. Along with their development communities, they've evolved and adapted since the 1990s, finding new niches and replacing other languages--sometimes competing in the same space. Both languages are associated with openness, so companies, teams, and developers are best keeping an open mind when it comes to making a decision.

Understand the needs and benefits around implementing [the right monitoring solution for a growing containerized market](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics.](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital)
