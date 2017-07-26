# How to Avoid Messy Code

_Captured: 2017-02-24 at 23:42 from [dzone.com](https://dzone.com/articles/how-to-avoid-messy-code?edition=271920&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-24)_

![](https://servedbyadbutler.com/getad.img/;libID=300340)

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

Few programmers explicitly intend to write poorly structured source code.

They don't sit down, whip out their _Bad Code Design Patterns_ book, and wreak meticulous spaghettipocalypse. Rather, poorly structured code is what happens when programmers don't know what they're doing.

![Figure 2: Two Java package structutes](http://edmundkirwan.com/image/common/comparison.png)

> _Figure 1: Two Java package structures: one well-designed, the other, not so much._

So, why is this difficult?

Source code has many properties -- and of different kinds.

One property, for instance, is the number of public methods in a program. Programmers easily control this property: making a private method public increases the number by 1. And that's it. In a sense, this is a "Linear" property, in that small changes produce small effects.

Structure also represents a source code property, but calling method _b()_ from method _a()_ does not only affect those two methods. New transitive dependencies form from all methods depending on _a()_ and on all methods depended upon by _b()_.

Furthermore, Java has three structural levels: method, class, and package, and method connections need not affect method-level alone. If the owning classes had not been connected, then new transitive dependencies pop into being on class level, too. And similarly on package level. Structure thus represents a "Non-linear" property, in that small changes may trigger large consequences.

This non-linearity makes writing well-structured programs hard.

It would be helpful if we could forget about this grand, over-arching structure and focus instead on small, linear properties that somehow magically lead to well-structured code.

Alas, no such linear properties exist.

But there are hidden clues.

Because source code properties are objective, we can measure them. We can certainly count the number of public methods in a program, and hosts of other linear properties besides. We can also measure the "Messiness" of a program via the [structural disorder](https://dzone.com/articles/are-we-still-writing-spaghetti-code), a percentage which rises as source code structure decays. If we measure over a large number of programs, we can then calculate the mathematical correlation between structural disorder and all those other properties.

A negligible correlation would imply no connection between a particular linear property and overall program structure. A large correlation, however, suggests that careful management of that linear property may contribute towards overall well-structured awesomeness.

For example, if structural disorder correlated 100% with the number of public methods, then we might suggest minimizing the numbers of public methods in order to minimize structural disorder, thereby using a simple, linear property to control a difficult non-linear one.

Let's give it a whirl.

Let's blitz 4 million lines of code from 38 Java systems[1](http://edmundkirwan.com/general/disorder-correlation-notes.html#1) in a code analyzer and get correlatin' over dozens of its structural properties. Table 1 shows the strongest structural disorder correlations discovered[2](http://edmundkirwan.com/general/disorder-correlation-notes.html#2) (full matrices: [method](http://edmundkirwan.com/general/disorder-correlation/method-correlations.xlsx), [class](http://edmundkirwan.com/general/disorder-correlation/class-correlations.xlsx), and [package](http://edmundkirwan.com/general/disorder-correlation/package-correlations.xlsx)).

Method
Class
Package

Average circular dependencies
0.62
0.21
0.58

Average complectation
0.75
0.39
0.02

Average depth
0.66
0.71
0.89

Average impact set
0.59
0.35
0.42

Average impacted set
0.56
0.35
0.42

Average middle-man
0.7
0.23
-0.1

Average transitive dependencies
0.56
0.24
0.35

Average transitive dependency length
0.64
0.24
0.42

_  
Table 1: Structural disorder correlations with other properties._

Only one property correlates strongly with structural disorder over all three levels: [depth](http://edmundkirwan.com/general/tuples.html).

The depth of a method (class, or package) is just its position in a transitive dependency. In figure 1, on the left, the depth of method _a()_ is 0, the depth of _b()_ is 1, _c()_ is 2, etc. These depths sum to 21. On the right, however, _a()_ still has a depth of 0, but all other methods - being directly called from _a()_ \- each have a depth of 1, making the total depth of the right structure just 6.

![Example: Original method drawLine\(\)](http://edmundkirwan.com/image/disorder-correlation/depth.png)

> _Figure 1: A deep transitive dependency on the left, and shallow dependencies on the right._

It is this depth total that correlates with structural disorder. The deeper your code, the more disordered it'll probably be. If you want to manage your program's structural disorder, avoid deep dependencies[3](http://edmundkirwan.com/general/disorder-correlation-notes.html#3).

One way to do this is to use a coordinator ([sunburst](http://edmundkirwan.com/general/serpent.html)) method, which calls other methods to do the heavy lifting, with the coordinator reduced to a sequencing role. Then repeat this pattern on class- and package-level, where possible.

## Summary

A [previous post](https://dzone.com/articles/evidence-based-principles) introduced four evidence-based principles for code structure, where the justifying correlations were weak but non-negligible.

This post adds a fifth principle, "Manage depth," but with a much stronger correlation, making the list of evidence-based structural principles now:

SIPTD.

(Admittedly, not the catchiest acronym.)

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).

Opinions expressed by DZone contributors are their own.
