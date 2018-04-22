# Object-Oriented Analysis and Design (Part 1)

_Captured: 2018-02-25 at 18:57 from [dzone.com](https://dzone.com/articles/object-oriented-analysis-and-design-part-1?edition=364096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-25)_

**[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). **

Who does this thing? Does it have any benefit? If I do this, will my boss think that I am wasting my time or making excuses to not work? Have these thoughts ever come to your mind when you were desperate to properly design your next software?

It is also possible that you have tried designing some piece of software before, but you found that it was too just time-consuming and it had no benefits. But throughout your career, you might have had these recurring thoughts that you should learn more about design patterns, mastering MVC, and designing something reusable, modular, and easy to read.

In this multi-part article series, I will cover the basics about how you can properly design your next software even if you have failed last time.

### What Will You Learn?

  * Why your last design attempt failed
  * How to handle your manager/boss when you wanted to design
  * How to succeed in designing
  * The software development process
  * What is object-oriented analysis?
  * What is object-oriented design?
  * What are design patterns?
  * And anything in between that is confusing you

### What Will You Not Learn?

  * You will not learn the syntax of Java, C#, or C++
  * You will not learn the difference between functions and variables
  * You will not be overwhelmed with a list of design patterns
  * You will not learn object-oriented programming here

"What?" you might say after reading the last line. "No object oriented programming? Then why am I wasting my time here?" This post is about object-oriented design, but not programming. We all know about object-oriented programming, i.e., how to write a class in C#.

As one quote says, "Knowing how to hold a hammer does not make you an architect." True? Similarly, learning Java programming will not make you a good software engineer (or software programmer or developer or software architect).

## Background

During the initial years of my undergraduate programs, I thought designing was the same as writing an algorithm because I did not study object-oriented programming. Later, when I learned about object-oriented programming, I thought someone could conquer the world if they just learned everything that is there in 1,000 pages of a Deitel and Deitel book.

![object oriented programming book](https://dzone.com/storage/temp/4439112-object-oriented-programming-book.png)

> _object oriented programming book_

But that was not the case. I could not write a program without tearing my hair apart. I also noticed that if I opened my program again after six months, it looked like such a mystery that even Sherlock Holmes could not solve it.

Then, in my fourth semester, I learned about object-oriented analysis and design as a subject. But unfortunately, the focus was on UML modeling. I thought that UML was a cool thing -- you just generate some diagrams and hand them over to developers and they will come up with code using your designs (which will make you proud).

But there was even an option in the UML modeling tool that our class was using at that time to automatically generate the code from your UML class diagrams. What a beauty, I thought. I could design using UML models and then generate the code, compile it, ship it to a customer, and get rich like Bill Gates. Awesome.

![UML](https://dzone.com/storage/temp/4439162-uml.gif)

Afterward, reality set in. I was never able to generate designs that were modular, easy to extend, and easy to understand (The code generated from these tools was never compiled, since it only generated stubs). Then, a period of chaos began.

Later in my undergraduate study, I learned subjects related to software engineering, software architecture, software process models and software project management. But I was unable to fit all things together until very late.

Still, I see people struggling with these concepts, unable to fit things together. They are overwhelmed with the unstructured data available to them. One key to comprehending all this information is to involve yourself in a project. The only output for that project should be a software that your users can use.

In this post, I will share some basic object-oriented analysis and design principles, practices, and some of my experiences that you can use in your next project.

## Introduction to Software Development Process Models

We all use some process or steps to develop software. The simplest process model that I use is just writing 6 lines on the back of a piece of paper and call them feature list. Then, I open Visual Studio and start writing code. That's it. It's a process model I used during my college years.

I wrote my first commercial software (which had 1 user, who abandoned it later) using Visual Basic 6.0 in my second year of college using this process model.

There are many software development process models that I have studied and applied throughout many projects.

One process model (which is scolded by many authorities) is waterfall, which uses the process of gathering requirements, analysis, design, implementation, and testing.

The problem with the waterfall process model is that you do all the things in the same exact sequence as written above. First, **all the requirements** are collected from the customers. A team analyzes requirements, then documents and prepares specifications for the design team. The design team then develops the design using the specification and hands over the design to the implementation team. The implementation team writes code with respect to the design. Finally, test team tests the software against the specifications.

![software process model](https://dzone.com/storage/temp/4439168-software-process-model-waterfall.png)

> _software process model_

Everything is done sequentially, and a lot of time is spent (months and even years) before the final product is shipped to the customer. Statistics tell us that when a product is shipped to the customer using waterfall process models, a huge number of customers rejected it = because it did not meet their requirements.

You may have heard the phrase, "The customer is always right." This truly applies to software development. If the customer does not like the final product, then all the effort (months and years) is wasted.

To cater to this problem, there is another philosophy -- iterative and evolutionary development. Based on this philosophy, there are many software development process models. Some examples are Scrum, extreme programming(XP), and Rational Unified Process. They are the Agile development processes.

The concept of iterative development is simple. Software development is organized into a series of small projects called iterations. Each iteration has its analysis, design, implementation, and testing. At the end of each iteration, the customer input is taken. If a customer did not agree, then the loss is minimal (usually weeks) as compared to waterfall process model.

Now you understand the basic difference between iterative and sequential process models. Many organizations now use iterative development process models, as the idea is to minimize waste (months vs. weeks).

## Why I Need to Understand Process Models

For a long time, I believed that designing software was something like that: I design everything in the beginning and then, using this design, start coding. Then, once it compiles, I handed over the running software to the end user.

It turns out that this is not the best approach. You will have to change your design strategy, which evolves over time. Therefore, the incremental and evolutionary process model is important to understand. Flawless design is a myth. After subsequent iterations, one may realize that his or her initial design sucks.

Another point is that one should not design for all the requirements at the beginning. Make a detailed design map for the iteration you're currently working on.

Therefore, the key takeaway is that you should use an iterative development process where the complete design is not done at the start of the project. Similarly, whatever you design will not perfect and will be changed or evolved during the lifecycle of the project.

This ends the first article of this four-part series. In this article, I discussed the importance of process models in object-oriented design. I also mentioned the common misconception attached to UML.

In** part 2**, you will learn the following

  * Difference between process and methodology

  * 2 most important object-oriented design principles that everyone should know

  * 1 advantage of OOP that every developer would love to have in his or her code

To learn more about object oriented programming visit [here](http://www.objectorienteddesign.org/).

**Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). **

Topics:

object oriented programming ,software design ,iterative ,tutorial ,agile 2018 ,agile application delivery
