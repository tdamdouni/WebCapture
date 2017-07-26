# Characteristics of Good Systems

_Captured: 2015-10-14 at 23:17 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/characteristics-of-good-systems)_

## Characteristics of Good Modular Systems

In this lesson and the next, we'll cover the characteristics of good object-oriented systems design with modularity. In plain English, that means thinking about how the design of your system should be broken into modules and how they should interact with each other so you can reap the benefits of modularity.

We'll start in this lesson by thinking about the general characteristics of good modules. In the next lesson, we'll discus the SOLID principles of object-oriented design which are used to help enforce the concepts presented in this lesson.

_As a quick note, some of the concepts in this lesson and the next will seem a bit abstract if you haven't ever worked with software before. We've provided real-world examples to help illustrate them but it's okay if you feel a bit lost. Some of this stuff is best to simply absorb in a general sense instead of trying to memorize all the details up front._

### The 3 Characteristics of Good Modules

Essentially, there are just three important guidelines for how modules should operate and interact. Modules should have:

  1. **Low Coupling** \-- they should be minimally dependent on each other and communicate using specified interfaces
  2. **High Cohesion** \-- they should be focused completely on achieving the overall goal
  3. **High Encapsulation** \-- they shouldn't reveal their implementation details to anyone else (and shouldn't need to)

These high level principles essentially guide the theory behind modularity -- it's good to break things into pieces, those pieces shouldn't rely on each other for much, each piece should do its own thing, and pieces should talk to each other using pre-determined interfaces.

Let's look a bit closer at each of those.

### 1\. Low Coupling

Coupling is just the degree to which the components of a system rely on each other. It should make intuitive sense that you don't want elements of a system relying too heavily on each other because that sort of defeats the purpose of having different components in the first place.

When thinking about modules, we encourage low coupling by forcing them to communicate with each other only by using specified interfaces. That prevents one module from getting too deeply involved in the workings of another.

If you were planning a birthday party and delegated the cake baking to your sister but she had to constantly ask you questions like how to read your recipe, how much a "teaspoon" is, or how to use the oven, then you aren't really saving yourself much effort. You haven't really specified a limited interface.

Moreover, if one of your friends really liked the cake and wanted to use it for his own kid's party, then you've got a problem. If he asks your sister to bake it, she's going to ask you all those questions again even though there's no good reason for you to be involved.

You could reduce coupling by providing your sister with the recipe and specifying that she isn't allowed to ask you any additional questions. You can point her towards Google and Youtube for advice but otherwise she'll have to figure the rest out on her own without your involvement.

In software, you want to make sure that your modules only communicate when it's necessary to do so.

### 2\. High Cohesion

Cohesion is how closely the components of a system are working towards a common goal. A system with high cohesion has many highly specialized modules instead of a few big bloated ones that try to do too much. In a cohesive system, the individual modules might not be terribly useful on their own but the system they create overall is worth much more than the sum of its parts.

In the real world, we embrace specialization because we know it provides efficiency gains. When thinking about modules in general, each one should stick with doing one thing well.

With the birthday cake example, a highly cohesive system might involve you simply hiring a baker to do the baking instead of worrying about it yourself.

In software, that means giving each component of the system a defined objective and not polluting it by introducing other functionality or trying to work with do-everything "god modules".

### 3\. Strong Encapsulation

Encapsulation is the extent to which the implementation details are hidden. Usually, when you want something done in the real world, you don't care how it gets done. The same is true with software! The more you know (or have to know) about HOW something is implemented, the more effort it requires and the more tangled things get when you try to make changes or break things apart to use them elsewhere.

In the birthday cake example, you don't want to tell the baker what type of flour to use; you'd rather just say "I want a large chocolate cake with vanilla frosting" and let the baker handle the rest. You don't care what happens in the kitchen (if it's up to health standards!) as long as it results in the right cake when you need it.

When thinking generally about software modules, you should be able to fully use a module purely by knowing how its interface works and nothing else.

### Wrapping Up

Hopefully this brief discussion of the three characteristics of good modular systems gives you a general sense for how the modules you use to solve a problem should operate. In the coming assignment, you'll design a system that will need to be broken up into modules and some of these ideas should help you think about the size and composition of those modules as well as the potential interactions between them.

###  Next Lesson: SOLID Design Principles 

[ Onward! ](http://www.vikingcodeschool.com/software-engineering-basics/solid-design-principles) [ or go to previous lesson... ](http://www.vikingcodeschool.com/software-engineering-basics/amazon-com-a-modularity-case-study)
