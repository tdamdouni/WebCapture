# Code Refactoring Techniques

_Captured: 2018-01-05 at 18:14 from [dzone.com](https://dzone.com/articles/code-refactoring-techniques?edition=347165&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-04)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Code refactoring is one of the key terms in [software development](https://apiumhub.com/) and today I would like to talk about code refactoring techniques that might increase your efficiency!

But first, let's agree on what code refactoring is. Basically, code refactoring is the process of changing a program's source code without modifying its external functional behavior, in order to improve some of the nonfunctional attributes of the software. In other words, code refactoring is the process of clarifying and simplifying the design of existing code, without changing its behavior. Nowadays, [agile software development](https://apiumhub.com/tech-blog-barcelona/benefits-of-agile-project-management/) is literally a must and [agile teams](https://apiumhub.com/software-developer-jobs-barcelona/) are maintaining and extending their code a lot from iteration to iteration, and without continuous refactoring, this is hard to do. This is because un-refactored code tends to rot: unhealthy dependencies between classes or packages, bad allocation of class responsibilities, way too many responsibilities per method or class, duplicated code, and many other varieties of confusion and clutter. So, the advantages include improved code readability and reduced complexity; these can improve source-code maintainability and create a more expressive internal architecture.

Two of the [most influential people in software development](https://apiumhub.com/tech-blog-barcelona/software-development-influencers/) of recent times, Martin Fowler and Kent Beck wrote the book on the subject of refactoring called "[Refactoring: Improving the Design of Existing Code](https://martinfowler.com/books/refactoring.html)". I highly recommend you to read it, it is definitely worth it!

This book describes the process of refactoring and spends most of its time explaining how to do the various refactorings - the behavior preserving transformations. In this book you will find simple examples that describe the whole process. There are also broader issues around refactoring, the "code smells" that suggest refactoring, and the role of testing, which you will find in this book as well. What I like the most about this book is that seventy refactorings and code refactoring techniques are described in detail: the motivation for doing them, mechanics of how to do them safely, and a simple example.

A common question is whether the book is still relevant and this is a good question since technology has made many advances, but according to our experience in [Apiumhub](https://apiumhub.com/web-development-barcelona/) and listening to other software developers, the book is still very useful. For example, the code refactoring techniques described in this book have not changed, since they are part of the fundamental use of programming languages. Another reason why you should read it is that it is written by legends of our time, by people who actually tried it first and developed the concept! There are other [interesting books](https://apiumhub.com/tech-blog-barcelona/software-architecture-books/) about this topic and you can find them[ here](https://apiumhub.com/tech-blog-barcelona/software-development-books/), but this one is a high priority one.

## Some Tips for Doing Code Refactoring Techniques Right

  * Code refactoring should be done as a series of small changes, each of which makes the existing code slightly better while still leaving the program in working order. Don't mix a whole bunch of refactorings into one big change.
  * When you do refactoring, you should definitely do it using [TDD](https://apiumhub.com/tech-blog-barcelona/advantages-of-test-driven-development/) and [CI](https://apiumhub.com/tech-blog-barcelona/benefits-of-continuous-integration/). Without being able to run those tests after each little step in a refactoring, you create a risk of introducing bugs.
  * The code should become cleaner.
  * New functionality should not be created during refactoring. Do not mix refactoring and direct development of new features. Try to separate these processes at least within the confines of individual commits.

## Benefits of Code Refactoring 

#### **Seeing the Whole Picture**

If you have one main method that handles all of the functionality, it's most likely way too long and incredibly complex. But if it's broken down into parts, it's easy to see what is really being done.

#### Make It Readable for Your Team

Make it easy to understand for your peers, don't write it for yourself, think on the long-term.

#### **Maintainability**

Integration of updates and upgrades is a continuous process that is unavoidable and should be welcomed. When the codebase is unorganized and built on weak foundation, developers are often hesitant to make changes. But with code refactoring, organized code, the product will be built on a clean foundation and will be ready for future updates.

#### **Efficiency**

Code refactoring may be considered as investment, but it gets good results. You reduce the effort required for future changes to the code, either by you or other developers, thus improving efficiency.

#### **Reduce Complexity**

Make it easier for you and your team to work on the project.

## List of Main Code Refactoring Techniques 

There are many code refactoring techniques and I do not want to cover them all, as this post would end up becoming a book in itself. So, I decided to [pick](https://refactoring.guru/refactoring/catalog) the ones we feel are the most common and useful.

### **Red-Green Refactoring**

Let's start by briefly talking about the very popular red-green code refactoring technique. Red-green refactor is the Agile engineering pattern which underpins Test Driven Development. Characterized by a "test-first" approach to design and implementation, this lays the foundation for all forms of refactoring. You incorporate refactoring into the test driven development cycle by starting with a failing "red" test, writing the simplest code possible to get the test to pass "green," and finally work on improving and enhancing your code while keeping the test "green." This approach is about how one can seamlessly integrate refactoring into your overall development process and work towards keeping code clean. There are two distinct parts to this: writing code that adds a new function to your system, and improving the code that does this function. The important thing is to remember to not do both at the same time during the workflow.

### **Preparatory Refactoring**

As a developer, there are things you can do to your codebase to make the building of your next feature a little more painless. Martin Fowler calls this preparatory refactoring. This again can be executed using the red-green technique described above. Preparatory refactoring can also involve paying down technical debt that was accumulated during the earlier phases of feature development. Even though the end-users may not see eye to eye with the engineering team on such efforts, the developers almost always appreciate the value of a good refactoring exercise.

### **Branching by Abstraction Refactoring**

Abstraction has its own group of refactoring techniques, primarily associated with moving functionality along the class inheritance hierarchy, creating new classes and interfaces, and replacing inheritance with delegation and vice versa. For example: Pull up field, pull up method, pull up constructor body, push down field, push down method, extract subclass, extract superclass, extract interface, collapse hierarchy, form template method, replace inheritance with delegation, replace delegation with Inheritance, etc.

There are two types of refactoring efforts that are classified based on scope and complexity. Branching by abstraction is a technique that some of the teams use to take on large scale refactoring. The basic idea is to build an abstraction layer that wraps the part of the system that is to be refactored and the counterpart that is eventually going to replace it. For example:   
encapsulate field - force code to access the field with getter and setter methods,  
generalize type - create more general types to allow for more code sharing, replace type-checking code with state, replace conditional with polymorphism, etc.

### **Composing Methods Refactoring**

Much of refactoring is devoted to correctly composing methods. In most cases, excessively long methods are the root of all evil. The vagaries of code inside these methods conceal the execution logic and make the method extremely hard to understand and even harder to change. The code refactoring techniques in this group streamline methods, remove code duplication. Examples can be: extract method, inline method, extract variable, inline Temp, replace Temp with Query, split temporary variable, remove assignments to parameters, etc.

### Moving Features Between Objects Refactoring

These code refactoring techniques show how to safely move functionality between classes, create new classes, and hide implementation details from public access. For example: move method, move field, extract class, inline class, hide delegate, remove middle man, introduce foreign method, introduce local extension, etc.

### Simplifying Conditional Expressions Refactoring 

Conditionals tend to get more and more complicated in their logic over time, and there are yet more techniques to combat this as well. For example: consolidate conditional expression, consolidate duplicate conditional fragments, decompose conditional, replace conditional with polymorphism, remove control flag, replace nested conditional with guard clauses,etc.

### Simplifying Method Calls Refactoring

These techniques make method calls simpler and easier to understand. This simplifies the interfaces for interaction between classes. For example: add parameter, remove parameter, rename method, separate query from modifier, parameterize Method, introduce parameter object, preserve whole object, remove setting method, replace parameter with explicit methods, replace parameter with method call, etc.

### Breaking Code Apart Into More Logical Pieces Refactoring

Componentization breaks code down into reusable semantic units that present clear, well-defined, simple-to-use interfaces. For example: extract class moves part of the code from an existing class into a new class, extract method, to turn part of a larger method into a new method. By breaking down code in smaller pieces, it is more easily understandable. This is also applicable to functions.

### **User Interface Refactoring**

A simple change to the UI retains its semantics, for example: align entry field, apply common button size, apply font, indicate format, reword in active voice and increase color contrast, etc.

Here are some examples of code refactoring techniques; some of them may only be applied to certain languages or language types. A longer list can be found in Martin Fowler's refactoring book, which we discussed above.

And if you are interested in best practices in software development, I highly recommend you to [subscribe to our monthly newsletter](http://eepurl.com/cC96MY) to receive latest software development books, tips, and upcoming events.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Topics:

refactoring ,software developer ,Agile ,code architecture ,code editing ,refactoring patterns

![](https://dz2cdn1.dzone.com/storage/rc-covers/7391100-dzone-aicover.jpg)
