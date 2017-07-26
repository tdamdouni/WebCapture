# Abstraction inversion

_Captured: 2015-10-24 at 19:38 from [en.m.wikipedia.org](https://en.m.wikipedia.org/wiki/Abstraction_inversion)_

In [computer programming](https://en.m.wikipedia.org/wiki/Computer_programming), **abstraction inversion** is an [anti-pattern](https://en.m.wikipedia.org/wiki/Anti-pattern) arising when users of a construct need functions implemented within it but not exposed by its [interface](https://en.m.wikipedia.org/wiki/Interface_\(computing\)). The result is that the users re-implement the required functions in terms of the interface, which in its turn uses the internal implementation of the same functions. This may result in implementing lower-level features in terms of higher-level ones, thus the term 'abstraction inversion'.

Possible ill-effects are:

  * The user of such a re-implemented function may seriously underestimate its running-costs.
  * The user of the construct is forced to obscure his implementation with complex mechanical details.
  * Many users attempt to solve the same problem, increasing the risk of error.

Ways to avoid this anti-pattern include:

    For designers of lower-level software: 

  * If your system offers formally equivalent functions, choose carefully which to implement in terms of the other.
  * Do not force unnecessarily weak constructs on your users.
    For implementers of higher-level software: 

  * Choose your infrastructure carefully.

Alleged examples from professional programming circles include:

  * In [Ada](https://en.m.wikipedia.org/wiki/Ada_programming_language), choice of the _rendezvous_ construct as a synchronisation primitive forced programmers to implement simpler constructs such as [semaphores](https://en.m.wikipedia.org/wiki/Semaphore_\(programming\)) on the more complex basis.[[1]](https://en.m.wikipedia.org/wiki/Abstraction_inversion)
  * In [Applesoft BASIC](https://en.m.wikipedia.org/wiki/Applesoft_BASIC), [integer](https://en.m.wikipedia.org/wiki/Integer) arithmetic was implemented on top of [floating-point arithmetic](https://en.m.wikipedia.org/wiki/Floating_point), and there were no [bitwise operators](https://en.m.wikipedia.org/wiki/Bitwise_operation) and no support for [blitting](https://en.m.wikipedia.org/wiki/Bit_blit) of [raster graphics](https://en.m.wikipedia.org/wiki/Raster_graphics) (even though the language supported vector graphics on the Apple II's raster hardware). This caused games and other programs written in BASIC to run slower.
  * Some people hold the opinion that [microkernel](https://en.m.wikipedia.org/wiki/Microkernel) design is an abstraction inversion (see the links). It is interesting that microkernels are also alleged to commit the design error of oversimplifying the components so as to overcomplicate their relationships.[[5]](https://en.m.wikipedia.org/wiki/Abstraction_inversion)[[6]](https://en.m.wikipedia.org/wiki/Abstraction_inversion)
  * Creating an object to represent a function is cumbersome in [object-oriented](https://en.m.wikipedia.org/wiki/Object-oriented) languages such as [Java](https://en.m.wikipedia.org/wiki/Java_\(programming_language\)) and [C++](https://en.m.wikipedia.org/wiki/C%2B%2B) (especially prior to C++11), in which functions are not [first-class objects](https://en.m.wikipedia.org/wiki/First-class_object). In C++ it is possible to make an object 'callable' by overloading the `()` operator, but it is still often necessary to implement a new class, such as the _[Functors in the STL](http://www.sgi.com/tech/stl/functors.html)_. ([C++11](https://en.m.wikipedia.org/wiki/C%2B%2B11)'s lambda function makes it much easier to create an object representing a function.)
  * Tom Lord has suggested that [Subversion](https://en.m.wikipedia.org/wiki/Subversion_\(software\)) version control system pays for the abstraction inversion of implementing a write-only database on a read/write database with poor performance.[[7]](https://en.m.wikipedia.org/wiki/Abstraction_inversion)
  * Using [stored procedures](https://en.m.wikipedia.org/wiki/Stored_procedure) to manipulate data in a relational database, without granting programmers right to deploy such procedures, leads to reimplementing queries outside the database. For example, large datasets (in extreme cases - whole tables) are fetched and actual filtering takes place in application code. Alternatively, thousands of rows are updated (inserted or even fetched) one by one instead of running a multiple row query.

Examples that are common outside professional programming circles include:

  * Using spreadsheet lookup functions to replicate the functionality of a database
  * Using variant data types as loop counters in Microsoft Visual Basic where an integer type is also available.
