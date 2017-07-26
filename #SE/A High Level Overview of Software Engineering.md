# A High Level Overview

_Captured: 2015-10-14 at 23:02 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/a-high-level-overview)_

## A High Level Overview of Software Engineering

We'll cover a lot of material in this mini-course. The purpose of this lesson is to get your feet wet with some of the very high level concepts and vocabulary you'll see later so you aren't totally suprised. As we mentioned before, the three sections that follow cover the high level **principles of software engineering**, how software projects are managed using **Agile Development** methods, and finally how **pseudocode and modular thinking** form the core of an effective problem-solving approach.

### The Principles of Software Engineering

The first section will take a historical look at software engineering so you get some context for what exactly you're getting into and how quickly the pace of change has been. You'll see how software engineering is an outgrowth of more concrete engineering disciplines because it started during the 1950's and 1960's when software and hardware were basically indistinguishable. This isn't just helpful context -- understanding the larger arc of progress will hopefully motivate you to keep learning the right things instead of letting your skills stagnate.

In that section we'll also cover the high level principles of software engineering. These are the kinds of things that will help you write better code from the beginning and again when you revisit them months or years later. Most importantly, we'll talk about the 4-step engineering problem solving approach:

  1. Understand the problem
  2. Plan a solution
  3. Carry out that plan
  4. Examine your results for accuracy  


This engineering approach isn't just used to build the physical _solution_ to your problem (ie. the "Product"), but it also applies to following an approach that will get you there properly (ie. the "Process"). Building the "right" piece of software with a poorly organized process will almost certainly result in failures of timeliness, cost, and/or usefulness.

### Introduction to Agile Development

The following section covers Agile Software Development, the project-management technique and development philosophy adopted by some of today's most effective software development firms.

Early engineers took the 4-step engineering approach fairly literally when managing software projects. That led to a highly structured (and appropriate for the time) process called "Waterfall", where formal specifications are laid out ahead of time and each step is completely finished prior to the commencement of the next. As software technology and its markets became more nimble, developers began to accept the new Agile approach.

Essentially, Agile embraces adaptability and rapid iteration instead of long formal planning and development processes. Agile teams commonly work to release software in short (1-2 week) sprints which makes it both more responsive to customer needs and more interesting for engineers to work on (everyone loves shipping!) than traditional long-term methods.

Two of the best known Agile project management techniques are "eXtreme Programming (XP)" and "SCRUM". They both use short cycle times and frequent client/user interaction to keep the project focused on relevant tasks instead of relying on heavily documented specifications. XP also advocates for certain specific development practices like pairing developers together at workstations ("pair programming").

The Agile process also puts a lot of emphasis on keeping software _user-driven_ which, if you've been through our [mini-course on Design](http://www.vikingcodeschool.com/web-design-basics), should sound quite familiar. Both SCRUM and XP rely on breaking down the problem at hand into bite-sized and prioritized pieces called "User Stories" which specify each feature from the user's perspective.

Project management tools like "Pivotal Tracker" help you keep track of your user stories. Even if you're not implementing the full workflow of an Agile methodology like SCRUM, these tools can help you stay organized and on task.

Finally, software testing has an important role in every development project because it allows you to confidently make changes to large code bases and deliver on specified acceptance criteria. Some approaches actually use testing to drive the development process, called "Test-Driven Development (TDD)".

### Pseudocoding and Good Software Design

Applying the engineering approach to actually solving the problem at hand encourages you to plan your solution first. The best way to do this for programming challenges is by first writing out the logic of the solution in English, called "pseudocoding".

We have two reasons for teaching you "pseudocode" before you learn "real" code. First, we want you to understand the logical underpinnings code because this is far more important than actually picking up the syntax (which most students rush into before they're ready). Second, pseudocoding a problem on a whiteboard is probably the single most helpful act you can do as part of your development process. It's helping you practice our philosophy of solving the problem first THEN coding the solution.

What do you do when confronted with larger problems or processes than you can comfortably solve with a single script? The key is to break them apart into individual sub-processes called "Modules" and think about how these modules interact with each other via "Interfaces". This approach can be applied to explore real world problems like planning a birthday party or to software challenges like scaling a multi-billion-dollar company.

Engineers have a fair bit of practice solving problems by breaking them into systems of modules so they've developed best practices for making the system more effective:

  1. Keep modules as independent as practically possible, ie. aim for low "Coupling"
  2. Make sure modules are all working towards the same goal, ie. are highly "Cohesive"
  3. Try to keep modules insulated from how other modules actually do their job, ie. keep them highly "Encapsulated"

Finally, those three characteristics are applied to object-oriented software through the application of the so-called "SOLID" principles of design. You probably won't apply them directly to the sites you build on Day 1 but understanding them will help you build and take part in more sophisticated systems down the road.

![Software](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/software_concept_small.png)
