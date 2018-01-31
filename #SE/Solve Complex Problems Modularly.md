# Solve Complex Problems Modularly

_Captured: 2015-10-14 at 23:16 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/solve-complex-problems-modularly)_

##  Learn how breaking a complex problem into modular pieces helps you arrive at a cleaner and more scalable solution. 

## Solving Complex Problems with Modularity

![Modular exploded cube](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/modular_cube_small.jpg)

> _Modular exploded cube_

So now you know we can write simple procedures for things like checking the height of a roller coaster rider with pseudocode but what about designing solutions for the big problems like you'd find in software? Software is like a well run restaurant -- an entire system of interwoven responsibilities communicating with each other to serve its "customers". So we need to think in terms of systems in order to help crack it.

To take this next step in systems problem solving, we'll introduce you to **Modularity**. Modularity is the degree to which a system can be broken into its components. In software engineering, this simple but powerful concept extends to say that the best solution to your design challenge isn't one giant task but _a system of separate and mostly-independent sub-tasks working together towards a common goal_.

### Modularity is Just Separating and Delegating

According to [Wikipedia](http://en.wikipedia.org/wiki/Modularity):

> Modularity is the degree to which a system's components may be separated and recombined.

The way you think about solving real-life problems hopefully already uses this idea and you didn't even know it! If you need to organize a kid's birthday party, you won't do everything yourself. You'll delegate the tasks to other people or businesses, for instance:

  1. A baker to make the cake
  2. A clown to perform
  3. A toy store to carry the toys
  4. The post office to send invitations (the old fashioned way!)

Each of these people or businesses can operate independently of you once they've received their instructions. Sometimes they may need your feedback before making a decision but usually they're able to go off on their own and provide you with what you've asked of them. _All of these tasks are really just modules that form a system designed to produce a birthday party!_

Thinking in a similar fashion will help you solve complex problems with pseudocode (or code) as well. You're asking the same general questions of complex software problems as you would in a real-life system like the birthday party:

  * What parts of this problem can be broken into independent tasks (ie modules) and only called on when necessary? For the party, that means anything that you aren't best at or don't have time for.
  * What information does each task require to get started? The post office will require not just the invitations but proper addresses and stamps.
  * What do you need to know about how each task works in order to properly use it? For instance, the baker may require two weeks to make the cake or the toy store's website may not reflect updated inventory and those factors would influence how you might use them.
  * What is the minimum level of communication between tasks so you don't need to get involved more than necessary? You don't want the baker calling you every time she needs to choose a frosting color.

### So What Exactly is a Module?

To think about things a bit more formally, modules are really just groups of things, including other modules. The key here is thinking about each module as a combination of all the stuff inside of it and the **Interface** that allows the exchange of information between it and any other modules.

In the birthday party example, the bakery "module" may have an interface via their website which contains information about their menu and a form for submitting your order. The clown "module" may interface via a telephone call during which the clown will ask a series of questions about what tricks you would like him to do at the party.

You don't need to know (and usually don't care about) what's going on inside a module as long as you understand the outputs, its interface and how to provide it with the correct inputs. Just like software!

### The Benefits of Modularity

It should make intuitive sense that breaking apart a giant complicated system of tasks into individual specialized sub-tasks is a good thing. Specifically, using modularity in the design of software systems:

  1. Lets you use abstractions to avoid re-inventing the wheel. This means that you can delegate responsibility for most tasks to other modules and not worry about the specifics of how they are completed.
  2. Allows specialization of tasks so each component gets very good at its job.
  3. Allows you to identify trouble areas in your system much easier than you could if the system was just one bloated module.
  4. Allows you to add, remove, or modify specific parts of the system without needing to go in and change every other part to accommodate those changes. Think of the benefits of interchangeable parts.

### A Pseudocode Example: Yard Work

![lawnmower](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/lawnmower_small.jpg)

It's really easy to use pseudocode to break apart a task into modules or to design a modular solution to a problem. In the previous lessons, you saw that we like to start with a few high-level steps before diving into the details of the specific sub-tasks. This approach has modularity baked right in!

By definition, when you zoom in to a more specific sub-task, you are really just breaking apart the problem into pieces and defining relationships between them -- exactly like you would when building a software module.

Let's say your father has asked you to clean the yard. That might look like:
    
    
    PROGRAM CleanTheYard
        IF there are toys in the grass
            Remove the toys
        END
        IF the grass is long
            Mow the grass
        END
        IF the hedges are unkempt
            Trim the hedges
        END
    END
    

But of course each one of these tasks requires some additional instructions and conditions. We can create a new module for each one. For example, we'll just create a new program (aka module) for mowing the grass which describes how that particular sub-task is done:
    
    
    PROGRAM MowTheGrass
        Find the lawn mower in the shed
        Check the gas level of the mower
        IF there is not enough gas in the mower
            Fill the mower with gas
        END
        Move the mower to the yard
        Start the mower
        Mow a lap around the outside of the lawn
        WHILE the lawn is still not finished DO
            Mow a lap around the inside of the previous lap
        END
        Turn off the mower
        Move the mower to the shed
    END
    

That may seem like it got complex fast but we've still got subtasks to accomplish which can each be fleshed out further, for instance just the act of filling the mower up with gas:
    
    
    PROGRAM FillMowerWithGas
        Remove mower gas cap
        Find extra gas can
        Remove extra gas can cap
        IF extra gas can is empty THEN
            Replace extra gas can cap
            Go get gas for extra gas can
        END
        While mower is not full DO
            Add gas to mower
        END
        Replace mower gas cap
        Replace extra gas can cap
    END
    

You get the idea -- every task is really a series of subtasks. Every module can (and often should) either be broken into smaller modules or delegate its work to some other module via a defined interface.

In the above example, we could continue to break it apart until, at some point, we had to either hand off the task to someone else (e.g. paying our friend to trim the hedges or having a manufacturer build the mower in the first place) or define a certain maximum granularity for those tasks (e.g. you don't need to worry about what muscles in your hand are necessary to unscrew the gas cap).

A software program works in a very similar fashion! The higher order purpose of your program is accomplished by breaking down that purpose into a bunch of smaller task modules which communicate with each other as necessary. Sometimes they hand off tasks to other modules provided by your program or maybe the operating system of your computer. Just like you don't need to think about the muscles in your hand turning the gas cap, the programming language or framework itself will provide you with some basic functionality "for free".

Just by thinking about the tasks present in the world around you, you pretty much already know just about everything you need to know about solving problems with modularity. We'll use this in the coming lessons to help illustrate best practices.

### A Quick Look at Objects

Up until now, we've really been thinking more about "tasks" and "procedures" than the participants in those tasks. But the participants are also very important, especially in programming when we actually need to build those participants ourselves!

Let's think a bit more about our mower. The mower is a _thing_. It has a series of attributes that belong to it -- its height, weight, color, engine size etc. You can easily inspect it from the outside to determine these things and they persist during the lifetime of the mower.

It has other properties inside of it which are essential for it to work but which you cannot easily inspect (they are "hidden"). This might include each of the bolts that hold it together or the phase of the piston inside the engine.

Some other properties are dynamic, like how much gas is currently in the tank. You can affect the gas level by either running the mower or adding more gas yourself via the gas cap interface.

In programming, we think of _things_ like the mower or even modules themselves as **objects** and we model them in a similar fashion to reality -- we give them properties, we ask them questions, we manipulate their behavior, and we expect them to keep track of those changes. The only difference is that in programming we actually need to give each object these properties ourself (since of course they don't start with anything).

### Wrapping Up

Modularity is a powerful idea in software engineering because you don't have to waste time solving problems that you can delegate to other modules and because it lets you avoid writing one single enormous program containing every possible bit of logic.

Imagine if we wrote down every micro-level task and object required to do the yard work down to the muscles of your hand or even the electrons inside your body. Yikes! In software, we can rely on the creators of our languages and frameworks to provide that implementation-level detail so we can focus on higher level tasks like actually mowing the lawn.

Modularity also lets you produce scalable solutions -- once you've built the lawnmower module, millions of people can use them without worrying about the details of how they work just by accessing their interfaces. The same is true of using your software modules to service high volumes of requests.

In the next few lessons, we'll take this incredibly simple concept and use it to illustrate some of the foundational principles of software engineering. These are practices which guide design decisions from the highest level system architecture down to the lowest level functions.

But first, we'll look at how modularity was used by Amazon.com to clean up their development practices through the implementation of Service-Oriented Architecture.

###  Next Lesson: Amazon.com: A Modularity Case Study 

[ Onward! ](http://www.vikingcodeschool.com/software-engineering-basics/amazon-com-a-modularity-case-study) [ or go to previous lesson... ](http://www.vikingcodeschool.com/software-engineering-basics/practice-with-pseudo-coding)
