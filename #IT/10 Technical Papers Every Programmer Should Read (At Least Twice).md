# 10 Technical Papers Every Programmer Should Read (At Least Twice)

_Captured: 2015-11-19 at 23:53 from [blog.fogus.me](http://blog.fogus.me/2011/09/08/10-technical-papers-every-programmer-should-read-at-least-twice/)_

_Let me preface this post by saying that no programmer **should** feel compelled to read any of these papers. I list them because I think that they provide a breadth of information that is generally useful and interesting from a computer science perspective. What you do with that information is your prerogative, including ignoring it completely. Instead, learn what you think is important for what you need to accomplish your job, education, interests, etc._

Inspired by a fabulous post by [Michael Feathers along a similar vein](http://web.archive.org/web/20121024173845/http://blog.objectmentor.com/articles/2009/02/26/10-papers-every-programmer-should-read-at-least-twice), I've composed this post as a sequel to the original. That is, while I agree almost wholly with Mr. Feather's[1](http://blog.fogus.me/2011/09/08/10-technical-papers-every-programmer-should-read-at-least-twice/) choices, I tend to think that his choices are design-oriented[2](http://blog.fogus.me/2011/09/08/10-technical-papers-every-programmer-should-read-at-least-twice/) and/or philosophical. In no way, do I disparage that approach, instead I think that there is room for another list that is more technical in nature, but the question remains, where to go next? In this post I will offer some guidance based on my own readings. The papers chosen herein are not intended to act as a C.S. hall of fame, but instead hope to accomplish the following:

  * All papers are freely available online (i.e. not pay-walled)
  * They are technical (at times highly so)
  * They cover a wide-range of topics
  * The form the basis of knowledge that every great programmer should know, and may already

Because of these constraints I will have missed some great papers, but for the most part I think this list is solid. Please feel free to disagree and offer alternatives in the comments.

## A Visionary Flood of Alcohol

#### Fundamental Concepts in Programming Languages [(link to paper)](https://github.com/papers-we-love/papers-we-love/blob/master/plt/fundamental-concepts-in-programming-languages.pdf?raw=true)

**by Christopher Strachey**

Quite possibly the most influential set of lecture notes in the history of computer science. Left and Right-values, Parametric and Ad-hoc polymorphism were all defined in this paper. Much of the content may already occupy your mind, but the sheer weight of the heady topics assembled in one place is stunning to observe.

#### Why Functional Programming Matters [(link to paper)](https://github.com/papers-we-love/papers-we-love/blob/master/functional_programming/why-functional-programming-matters.pdf)

**by John Hughes**

I found this paper extremely lucid on the advantages of functional programming with the added advantage of showing off examples of beautiful code. There are seemingly an infinite number of papers on the topic of laziness with streams and generators, but I've yet to find a better treatment. Finally, I've always been partial to [Reginald Braithwaite's "Why Why Functional Programming Matters Matters"](http://weblog.raganwald.com/2007/03/why-why-functional-programming-matters.html) as a complement to this paper.

#### An Axiomatic Basis for Computer Programming [(link to paper)](https://github.com/papers-we-love/papers-we-love/blob/master/comp_sci_fundamentals_and_history/axiomatic-basis-computer-programming.pdf?raw=true)

**by C. A. R. HOARE**

I came to this paper late in my career, but when I finally found it I felt like I had been hit by a bus. At the core of the paper lies the following assertion:
    
    
    P {Q} R
    

Taken to mean:

> If the assertion P is true before initiation of a program Q, then the assertion R will be true on its completion

Where `P` is a precondition, `Q` is the execution of a program, and `R` is the result.

In other words, as long as a program/function/method/etc. receives a set of parameters conforming to its preconditions, its execution is guaranteed to produce a well-formed result. This paper inspired me to explore [contracts programming in Clojure](http://github.com/fogus/trammel), but the proof implications reached in Hoare's paper run much deeper.

#### Time, Clocks, and the Ordering of Events in a Distributed System [(link to paper)](http://research.microsoft.com/en-us/um/people/lamport/pubs/time-clocks.pdf)

**by Leslie Lamport (1978)**

Lamport has been highly influential in the field of distributed computation for a very long time and almost any of his papers on the subject should impress. However, this particular paper is likely his most influential and single-handed defined two branches of study in distributed computing since:

  1. The reasoning of event ordering in distributed systems and protocols
  2. The state machine approach to redundancy

The most amazing aspect of this paper is that after you read it you might think to yourself, "Well, of course that's how it should work." [Jim Gray](http://www.amazon.com/o/asin/1558601902?tag=fogus-20) once said that this paper was both obvious and brilliant. I would say that there is no higher compliment.

#### On Understanding Types, Data Abstraction, and Polymorphism [(link to paper)](http://citeseer.ist.psu.edu/viewdoc/summary?doi=10.1.1.117.695)

**by Luca Cardelli and Peter Wegner**

I had originally thought to list Milner's _A Theory of Type Polymorphism in Programming_, but thought that a survey paper would be better. I must admit that my own readings have not gone deep into the exploration of type systems, so any additional suggestions would be greatly appreciated.

#### Recursive Functions of Symbolic Expressions and Their Computation by Machine, Part I [(link to paper)](http://www-formal.stanford.edu/jmc/recursive.html)

**by John McCarthy**

It's become a cliche to recommend McCarthy's seminal paper introducing LISP. I will not count this toward the target of 10, but I would be remiss to excluse it because it's a great read that is nicely supplemented with the study of [a simple implementation of McCarthy's original specification](http://fogus.me/fun/lithp).[3](http://blog.fogus.me/2011/09/08/10-technical-papers-every-programmer-should-read-at-least-twice/)

## The Machinery for Change

#### Predicate Dispatch: A Unified Theory of Dispatch [(link to paper)](https://github.com/papers-we-love/papers-we-love/blob/master/plt/predicate-dispatching.pdf?raw=true)

**by Michael Ernst, Craig Kaplan, and Craig Chambers**

Describes a method for dispatching functions based not on a static set of rules, but instead as the traversal of a decision tree that could be built at compile-time and extended incrementally at runtime. What this means is that dispatch is controlled and adapted based on an open set of conditions describing the rules of dispatch. This stands opposed to the current popular trend of languages whose dispatch is hard-coded and not open for extension at all.

#### Equal Rights for Functional Objects or, The More Things Change, The More They Are the Same [(link to paper)](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.23.9999)

**by Henry G. Baker**

At the heart of Clojure and ClojureScript's implementation is `#equiv` that is in turn based off of Henry Baker's `egal` operator introduced in this paper. Briefly, equality in Clojure is defined by equality of value, which is facilitated by pervasive immutability. Equality in the presence of mutability has no meaning.

**by David Ungar, Craig Chambers, Bay-wei Chang, and Urs Holzle**

The greatest crime perpetrated in the name of JavaScript is the propensity for every framework, library, and trifle uses the prototypal inheritance capabilities of the language to implement class-based inheritance. [I propose that this behavior stunts the power of JavaScript](http://blog.fogus.me/2010/12/20/self/). However, the class-based mentality is pervasive, and is only likely to grow stronger as JavaScript moves toward "modernized" data-modeling techniques. Having said that, [I love the prototypal model](http://www.infoq.com/resource/articles/the-joy-of-clojure/en/resources/JoyofClojureCH09.pdf). It's flexibility and simplicity is astounding, and this paper[4](http://blog.fogus.me/2011/09/08/10-technical-papers-every-programmer-should-read-at-least-twice/) will show how it can be leveraged for practical purposes. While a design oriented paper, I think that the knowledge is contrary enough to pop-programming to warrant inclusion. Self is a fascinating language on its own merit, but especially in that its influence[5](http://blog.fogus.me/2011/09/08/10-technical-papers-every-programmer-should-read-at-least-twice/) on modern dynamic languages is growing ever more pervassive.

## I've Seen the Future, Brother: It is Murder

**by Giuseppe DeCandia, Deniz Hastorun, Madan Jampani, Gunavardhan Kakulapati, Avinash Lakshman, Alex Pilchin, Swaminathan Sivasubramanian, Peter Vosshall and Werner Vogels**

It's rare for a paper describing a system in active production to influence the state of research in any industry, and especially so in computing. Papers describing thought-stuff are pure and elegant while "real-world" systems tend to be ugly, hackish, and brutish, even if they are rock-solid otherwise. The case of Dynamo is quite different. That is, the system itself is based on simple principles and solves a hard problem, highly available and fault-tolerant online database storage, in an elegant way. Dynamo was not a new idea, but this paper is necessity as we move forward into the age of Big Data.

**by Ben Moseley and Peter Marks**

Now we reach my favorite paper of the bunch - one that I try to read and absorb every 6 months (give or take). The gist is that the primary sources of complexity in our programs are caused by mutable state. With that as the premise, the authors build the idea of "functional relational programming" that espouses minimizing mutable state, moving whatever remains into relations, and then manipulating said relations using a declarative programming language. Simple right? Well, yes it is simple; and that's what makes it so difficult.

This list should be a good start, but where to go next? My personal approach is summarized simply as: follow the bibliographies. If you like any of these papers then look at their bibliographies for other papers that sound interesting and read those too. Likewise, you can use services like [Citeseer](http://citeseerx.ist.psu.edu/) and the [ACM Digital Library](http://dl.acm.org/) to backtrace citations.

Happy reading.

:F

  1. Apart from a spectacular ear for music, Mr. Feathers is also a [fount of wisdom](http://news.ycombinator.com/item?id=2978806), including this gem from the linked post:

> When I first started writing, one of the pieces of advice that I heard was that you should always imagine that you are writing to a particular person.

  2. Design is a vastly overloaded term, but it's the best word that I can think of. Suggestions for something better? 

  3. A have some ideas for a Lisp-centric essential papers list also, but have not yet formalized the content. 

  4. It was difficult picking a paper from the treasure-trove that is the [comprehensive list of Self publications](http://www.cs.ucsb.edu/~urs/oocsb/self/papers/papers.html). These papers represent the vanguard of performance in dynamic languages. 

  5. Although Self does not hold a monopoly on dynamic performance revolutions. Smalltalk implementations have also driven innovation in said space, and a taste for this influence is found in _Efficient Implementation of the Smalltalk-80 System_ by Peter Deutsch and _The Design and Evaluation of a High Performance Smalltalk System_ by David Ungar. 

  6. The Dynamo paper is probably the most controversial choice for this list, so if it bothers you then perhaps _Software Transactional Memory_ by Nir Shavit and Dan Touitou would suffice as an alternative. I was bouncing back and forth between these choices and only settled on Dynamo in the spirit of controversy. ;-) 
