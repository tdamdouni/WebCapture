# Object-Oriented Analysis and Design (Part 4)

_Captured: 2017-04-11 at 19:23 from [dzone.com](https://dzone.com/articles/object-oriented-analysis-and-design-part-4?edition=290882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-11)_

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

This is the last article in four part series. Here I will discuss some non-technical issues that I faced in my object-oriented design and programming journey. If you're new to the series, feel free to check out [Part 1](https://dzone.com/articles/object-oriented-analysis-and-design-part-1), [Part 2](https://dzone.com/articles/object-oriented-analysis-and-design-part-2), and [Part 3](https://dzone.com/articles/object-oriented-analysis-and-design-part-3)!

## Why Your Last Design Attempt Failed

Many developers have attempted to design a software project properly but have failed or could not continue. Therefore, I have put together a list of problems or misconceptions about object-oriented analysis and design and how to tackle them.

### If You Could Just Learn How to Design Perfectly

Perfect design at the start of the project is a myth. Your design will evolve, change, be corrected and modified over time. Many people think that they have to design perfectly at the beginning and then consider that design document as a sacred scripture. The truth is no one can come up with a perfect design at the start.

Software design is a heuristic process. It's something that you update over the lifetime of your project. There is no formula that you can use to produce best object-oriented design every time. It involves trials and painful errors from which you can learn and then apply what you've learned to your future projects.

### You Have to Do Complete Analysis and Design Before Coding

Many developers and students believe that analyzing all requirements and all designing should be done before coding starts and during construction, one cannot change or extend it.

This is not true. If during coding, a team or developer realizes that the design can be extended or reduced, then it should be.

Similarly, when working in iterative development, usually 10 percent of all the requirements are tackled during one iteration. Therefore, you have to design for only 10 percent of all the requirements or user stories. If you have 10 user stories, then tackle the most important story (as indicated by the customer) in the first iteration and design for that only.

### You Have to Give Enough Time to Design

When I started to become seriously interested in object-oriented design, I was spending weeks on design, thinking about how to come up with a perfect and complete design. But during coding, things did not work out as they were supposed to and I was disappointed.

The rule of thumb is that you should not give more than one day for a three-week iteration. I only give 2 to 4 hours to design before jumping to code. This does not mean you cannot go back to designing for a couple of hours during construction. You can meet with your teammates and discuss design decisions during construction as well.

### You Believe UML (Unified Modeling Language) is Everything

If someone told you that UML modeling is everything and recommends some expensive CASE (Computer-Aided Software Engineering) tool, then you should come and look at my journal. Most of my designs never get to the CASE tool that our company has. When designing in teams, we use whiteboards and take a picture of them and then post these pictures in the project directory.

![UML Diagrams](https://dzone.com/storage/temp/4440288-uml-diagrams.jpg)

> _UML Diagrams_

I believe design is not something that you draw using beautiful boxes of colors and properly align them. A rough diagram on paper is as effective as a diagram drawn using a CASE tool. OOAD is about getting a big picture and communicating this with your peers and with yourself when you are writing the code.

UML is just a tool that you can use to translate your design ideas and which can be shared with other developers. Simply learning UML will not make you a good designer.

### You Have to Apply All the Patterns and Principles

If you know about all the object-oriented design principles and patterns, then you might have realized that you want to apply all of these principles and patterns before moving to construction. If you do this, then you will not be successful. Use the principles and patterns according to the situation or problem at hand and you will be able to design a good piece of software.

I suggest that you develop your own priority list of patterns and principles that you fully understand. Then, apply these patterns according to the problem that is in front of you.

### You Don't Know How to Handle Your Boss / Manager

It is possible that your boss may resist while you come up with the idea of object-oriented analysis and design. In your boss's eyes, it looks like an additional task which will not add any lines of code to your software. Also, it is also possible that your boss is not from a programming background and will not realize the importance of OOAD.

![object oriented design](https://dzone.com/storage/temp/4440290-object-oriented-design.png)

> _object oriented design_

There are two kinds of bosses:

  1. Quality driven.
  2. Schedule driven.

Identify what influences your boss or manager. If your boss is quality driven, then you can show him the benefits of an object-oriented analysis and design and how it help him achieve the better quality features like modularity, readability, and reliability.

If your boss is schedule driven, then the first thing that you can do is show him that analysis and design activities will not take much time (only 2-8 hours in a 3 weeks iteration). You can also show them how other time-saving benefits, such as a good design, can save time later in the project, like when you have to update or change some features of a piece of code.

## What Next?

Write what you like about the post in the comments section. You can visit [www.objectorienteddesign.org](http://www.objectorienteddesign.org/) for a small report that discussed applying object-oriented principles to real life examples.

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).

  


Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

## Introduction

Welcome to article part two of a 4 part series. In the [previous article](https://dzone.com/articles/object-oriented-analysis-and-design-part-1), you learned about the basics of object-oriented design. I also discussed what will you learn and what will not.

In this article, you will not need to feel overwhelmed by learning every definition pertaining to object-oriented design. You will learn important definitions. These are necessary to initiate a design process. Learn them and start applying them to your next project.

## Object-Oriented Analysis and Design - Most Needed Definitions

When I developed my first project, which I developed using VB 6.0, I was disappointed in myself. This is because a single change in a small portion of the code propagated to all other parts of the software.

The reason was that I didn't know about how to write modular code. Although it is possible to write modular code in a procedural language (VB 6.0 was procedural), it was difficult and not supported inherently in VB 6.0.

It was a nightmare to develop a simple software with only 4 features. It was terrifying to make any changes in the code because I didn't know about object-oriented programming.

The solution to this problem is object-oriented programming. This enables me to write modular programs. Before explaining how OOP and OOAD helped me out, first, let's discuss the difference between the development process and a development methodology.

### Difference Between Development Process and Development Methodology

Development methodology is something within the process. Examples of development methodologies are structured programming, object-oriented and service-oriented programming.

The development process defines a set of steps to carry out software development activities. Examples of software development processes are the Waterfall process, rational unified process, Scrum, and extreme programming. Generally, you can pick any process methodology and then adopt any development methodology within that process.

### Object-Oriented Analysis

One important benefit of object-oriented methodology which no one tells you is that you have the ability to design using real-world terms or domain specific terms. For example, if you are working on a piece of software related to banking services, then you can use terms like Account, Ledger, and Balance Sheet within the software code (as Names or attributes of classes).

How is this beneficial? You can design the software like real systems in the real world work. This makes it easy for you to update, modify, and communicate with the customers. Hence object-oriented analysis is about identifying opportunities where you can represent real world objects in the software world.

The first step in object-oriented analysis is listening to a customer story and writing it down. A story is a description of customer pains and gains in his own words. Your job is to solve these customer pains and/or help the customer to achieve positive gains.

There can be more than one customer story. You can tackle one or two user stories in a single iteration. But do not tackle more than 10 percent of all the stories in a single iteration. The next step is to design the domain model from user stories.

To the design domain model, one simple technique that I used over time is reading the user story and underlining the nouns. These nouns are potential candidates for classes in your domain model. The domain model simply describes the names of the classes and/or attributes of the classes. A domain model does not describe any implementation detail such as function within a class.

In summary, there are two steps:

  1. Writing down user stories.
  2. Designing the domain model.

A demonstration of these ideas will be given in the upcoming example.

### Object-Oriented Design

It's quite easier to look at an object and say, "yeah, it is a collection of variables." Let me share a personal story: once I refactored a piece of code and designed a separate class which consisted of two primitive types. The funny thing was that another developer cheered me for developing a new variable.

There are many developers around who think like that. That is, creating a class means creating a new variable. This is not the reason people use the object-oriented methodology. If you just want a collection of variable names, then you can use `struct` in C (which is a not an object-oriented programming language).

Object-oriented design is about how your objects collaborate with each other. Here, you will decide who will create which objects and how they will interact to fulfill the needs of a user story.

The most import thing about analysis is identifying the domain classes from the user story and the most important thing in object-oriented design is identifying the collaboration between the objects to satisfy the user story.

In addition to designing the collaboration, there are principles and patterns which are followed by the software community. A group of four patterns is extensively used in software designing, but these patterns deserve another post (I will soon share with you and my personal story of my journey to design patterns).

If you are new to designs, then don't get overwhelmed by all these pattern things. Just focus on one or two principles to start with. Then extend your learning towards more principles and design patterns.

### What Are the Most Important Principles You Should Start With?

Don't get overwhelmed with principles and design patterns. My suggestion is to focus on few principles and design patterns you are comfortable with in the start and then develop from there.

![object oriented design principles](https://dzone.com/storage/temp/4439178-object-oriented-design-principles.png)

> _object oriented design principles_

An important principle that I found very useful and I suggest that you should use is:

> Prefer composition over inheritance. 

That is, avoid using inheritance whenever possible. Use composition in any situation wherever you think inheritance is the answer.

Also, if you have never used interfaces in your code, then start using interface from today. This will enable you to write reusable and modular software.

Apply these two principles in the upcoming weeks and you will realize the power of object-oriented analysis and design.

### Advantages of Object-Oriented Analysis and Design

With these principles and knowledge of object-oriented programming, I was able to write a software which was modular and easy to read. Also, if I open the code today which I wrote 10 years ago, I can easily understand and update the code.

This ends article two of my four parts article series. In this article, I discussed the difference between process and methodology. Also, the principles that every beginner object-oriented programmer should learn.

In part 3, I will share an example and I will discuss the following:

  * Outline all the steps needed for object-oriented analysis and design.

  * Applying design steps to a simple example.

  * I will show why you don't need a fancy UML software package for object-oriented design.

To learn more about object-oriented design, visit [here](http://www.objectorienteddesign.org/).

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).
