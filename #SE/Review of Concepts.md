# Review of Concepts

_Captured: 2015-10-14 at 23:20 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/review-of-concepts)_

## Review of Concepts

We've covered a lot of new material in this mini-course. You should have a pretty good general feeling for both what a software engineer does and how established engineering approaches can be used to improve your ability to solve software challenges and manage software projects. You'll probably want to come back and take a peek at this mini-course again when you've started building web applications so you can really absorb the concepts it contains.

Speaking of concepts, there are probably all kinds of things floating around in your head so let's nail down the important bits of each section.

### On the Principles of Software Engineering

We started with an introduction to the history of software engineering, all the way from its roots in 1950's hardware to the current era of web and mobile programming. You learned about engineers' fondness for acronyms like **"Keep It Simple, Stupid (KISS)"** and became quite familiar with the logical and structured process that engineers use to approach new problems:

  1. **Understand the problem**
  2. **Plan a solution**
  3. **Carry out that plan**
  4. **Examine your results for accuracy**

Over the following lessons and sections you saw how this general approach was applied to solving problems on both a 10,000 foot level and an implementation level. We specifically looked at how it can be applied to a concrete problem (building a car) or a software problem (building Facebook).

You started to see that engineering isn't just about building the solution to the problem (the **Product**) but also making sure you follow an approach that will get you there properly (the **Process**).

### On Agile Development

We started our investigation of the Process of software development by looking at **Project Management** techniques.

Longtime project management methods like Waterfall, though logical, failed to embrace the real-world nature of changing requirements in many consumer-facing projects. That shortfall, coupled with the increasing flexibility of software itself through the web, led to the introduction of **Agile Development** philosophies which embrace the idea of short development cycles and changing requirements.

Agile projects are often managed and implemented using **eXtreme Programming (XP)** or **SCRUM** techniques, both of which use short cycle times and frequent client/user interaction to keep the project focused on relevant tasks instead of relying on heavily documented specifications. XP also advocates for certain specific development practices like pair programming.

Both methods rely on breaking down the problem at hand into bite-sized production pieces called **User Stories** and then prioritizing them in the **Product Backlog**. These stories tie into the idea of User-Centered Design by specifying each feature from the user's perspective, in the form:

**As a** [kind of user], **I want to** [accomplish some specific goal] **so that I can** [derive some benefit]

Stories also help you think in a more structured way about some of the necessary interactions the user will have with your feature because you need to specify the story's **Acceptance Criteria**. These criteria may cover both main user flows and particular edge cases that the story needs to address but are ultimately meant to start as a conversation piece between the development team and either the **Product Owner** or the client.

Project management tools like **Pivotal Tracker** help you keep track of stories. Even if you're not implementing the full workflow of an Agile methodology like SCRUM, these tools can help you stay organized and on task.

To apply the engineering approach from above to a new Agile software project, your team would likely follow the steps of:

  1. **Gathering Requirements** for the project
  2. **Breaking Down** the project into user stories
  3. **Estimating** the "points" value of the user stories
  4. **Prioritizing** the stories
  5. **Building** the stories
  6. Going through the **Acceptance** process for each story and ultimately the project as a whole

Testing has an important role in every software project. **Test Driven Development (TDD)** uses the **"Red -> Green -> Refactor"** approach so the tests actually guide the development process. A specific implementation of TDD is called **Behavior Driven Development (BDD)**, and it uses automated testing of the acceptance criteria to formally connect Agile stories to the TDD process.

Finally, you had a chance to tackle a new software project by breaking down the Viking Store e-commerce app into stories and recording them in your Tracker.

### On Pseudocoding and Good Software Design

Since you now understand the "Process" side of software engineering, the last section moved into the "Product" side of things. It covered some key software engineering concepts while sticking to a more general form of code called **Pseudocode**.

Designing the solution to a problem using pseudocode helps both beginners and experienced engineers to get their thoughts out "on paper" before actually coding. The logical building blocks of coding like **Flow Control** and **Iteration (loops)** help you to create your own "pseudocode programs".

You hopefully got a good appreciation for how important it is to think through a problem and do this "whiteboarding" step before diving into the code.

The idea of **Modularity** is just a fancy way of saying "break a problem or process into separate pieces" (like you've been doing all along). A **Module** can represent a high level set of processes or the tiny little detailed sub-processes that they implement. How you decide to define your modules depends on your perspective and what you're using them for.

Software is a lot like the kinds of processes you see in the world around you. Those real-life processes can be also represented as a bunch of modules communicating with each other via **Interfaces**, including tasks like setting up a birthday party or cleaning the yard.

Amazon.com's transition to a **Service-Oriented Architecture (SOA)** illustrates how the idea of modularity is used on a large scale to improve the processes of major production software.

There are three key characteristics of good modular systems:

  1. Keeping **Low Coupling** between modules so they can do their jobs in peace
  2. Achieving **High Cohesion** among modules so they are all aiming for the same goal
  3. Keeping modules **Highly Encapsulated** so you can swap them out or change details without disturbing the whole system.

Those three characteristics are tested and enforced through the application of the **SOLID** principles of **Object-Oriented** software design. Though they're a bit more detailed than you need to know right now, they are:

  1. **Single Responsibility Principle (SRP)** \-- do just one thing well
  2. **Open/Closed Principle (OCP)** \-- allow for interchangeable parts
  3. **Liskov Substitution Principle (LSP)** \-- be what they expect you to be
  4. **Interface Segregation Principle (ISP)** \-- don't make me specify things I don't care about
  5. **Dependency Inversion Principle (DIP)** \-- I don't care how, just give me what I want

You got to try out pseudocoding and modular design by actually pseudocoding some real life examples and processes like making a sandwich, solving a logical challenge, and designing an elevator system.

### Final Thoughts

The final project gave you an opportunity to step onto an overworked development team implementing a new feature for our e-commerce app. It hopefully allowed you to tie everything together and see how these concepts apply to the real world of software development.

And that's the point here -- you should now have a good sense for what software engineering is and how software development works. You should be fired up and ready to actually apply these things to real code, which we'll cover in the [next mini-course on Coding](http://www.vikingcodeschool.com/web-markup-and-coding).

![Success Silhouette](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/success_silhouette_small.jpg)

> _Success Silhouette_

###  Next Lesson: Test Yourself 

[ Onward! ](http://www.vikingcodeschool.com/software-engineering-basics/test-yourself) [ or go to previous lesson... ](http://www.vikingcodeschool.com/software-engineering-basics/turning-a-new-feature-into-agile-stories-and-pseudocode)
