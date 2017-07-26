# Object-Oriented Analysis and Design (Part 2)

_Captured: 2017-04-07 at 23:23 from [dzone.com](https://dzone.com/articles/object-oriented-analysis-and-design-part-2?edition=288885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-07)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

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

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
