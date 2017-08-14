# What Is Software Architecture in Scrum?

_Captured: 2017-08-14 at 10:04 from [dzone.com](https://dzone.com/articles/what-is-software-architecture-in-scrum?edition=317392&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-13)_

Speed up delivery cycles and improve software quality with [TestComplete.](https://dzone.com/go?i=228239&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad) Discover the most robust automated testing tool for end-to-end desktop, mobile, and web testing. [Try TestComplete Free.](https://dzone.com/go?i=228239&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad)

A common and recurrent question in the context of Scrum is: when is software architecture created? During the first Sprint? The final Sprint? The issue appears to be complex as Scrum is strict on this point: at the end of the Sprint, you have to deliver a piece of working software that is built according to a Definition of Done and that sits over the past (if any) integrated pieces of working software in order to have an Increment. Wow! How can software architecture have its place in that? What is software architecture in Scrum? Is it really necessary? Are software architecture and Scrum really compatible?

Let's find out!

### Going to the Roots: What Is Software Architecture

Answering this question may bring some conflict. Some architects view architecture as residing far from implementation and only dealing with _big things in big systems_. Other architects, however, view architecture as something that sits closer to implementation. What do they have in common? Decisions. Of course, at different levels, but they do have decisions in common. Jan Bosch (Software Architecture: The Next Step, Springer, 2004) says software architecture is a composition of a set of architectural design decisions. Taylor et al. (Software Architecture: Foundations, Theory, and Practice, Wiley, 2010) say software architecture is the set of principal design decisions made about the system. So, we can have many design decisions, but not all of them are architectural. Bosch also adds that architectural design decisions have the following aspects:

  * They influence the structure of the system (for example, using a SQL database implies adding a data management component).

  * They may define one or more design rules (for example, when you decide to use MVC, there are some specific rules that specify a particular way of responding to user events in the UI).

  * They may also impose design constraints (for example, when you decide to use a relational data model, there appear to be a lot of constraints in how classes will be designed and which components could be selected).

  * They have a rationale associated with them and are decided upon after some reasoning (for example, when you decide to use a graph database because it will be easier to manage relationships between your clients).

For example, using a particular pattern for describing methods in your Java code is clearly a design decision, but not an architectural one. On the other side, the selection of a bunch of design patterns to structure the system in a layered fashion is an architectural decision. Selecting a particular NoSQL database over a traditional SQL-based database is also an architectural design decision.

### Software Architecture in Scrum

The key idea is that when we talk about software architecture, we are, indeed, talking about making decisions. Scrum mandates having a piece of working software at the end of the Sprint, which integrates with previously (if any) integrated pieces of working software (this is called an Increment) and that is built according to a Definition of Done.

Therefore, all design decisions that are made throughout the Sprint make software architecture emerge and are embodied in the piece of working software. Thus, **there is no special moment for the design of the software architecture in Scrum. There is no "software architecture Sprint." Architecture in Scrum emerges, it is not created somewhere, or at some specific time.**

We are treating design decisions like user stories. Is this correct? Yes! That's because we treat **design decisions as first-class entities,** meaning you can manage and manipulate them as any other object. In this context, a design decision can be characterized by many attributes. The most common attributes are: ID, the name of the decision, a description of the decision, the IDs of the decisions that implied or affected this decision, the IDs of the decisions that are affected by this decision, a timestamp, the people involved in taking this decision, and a rationale for the decision. This way, a design decision is worked on in a Sprint as any other element in the Sprint Backlog. Depending on the type of decision, it can be a separate element in the Sprint Backlog or it can be a specific appointment as detail in an element of the Sprint Backlog. That is something the development team will decide.

The important thing is that, at the end of the Sprint, when the development team has finished enough Sprint Backlog items to reach the Sprint Goal (including design decisions!), we will have, according to a Definition of Done, an Increment which has embodied many architectural design decisions. The **Definition of Done is very important for making design decisions, as it is more related to quality attributes than to functional requirements.** It is perfectly valid to have the Definition of Done be something like "software must be modularized to facilitate continuous integration." With that issue inside the Definition of Done, the development team has a narrower set of potential architectural design decisions.

To summarize, a software architecture in Scrum is the set of architectural design decisions that are embodied in the Increment, whether documented (diagrams and/or text) or not. Also, design decisions are made throughout the Sprints, so we have to talk about an emerging software architecture, rather than a created a software architecture.

### The 'Big Picture' Diagram in Scrum

Most architects enjoy crafting diagrams with components, connectors, and many other beautiful things, both on blackboards and directly on a UML-supported software. There is no problem with that, even in your first hours of your first Sprint. It can also be a valuable artifact for the development team in the initial discussion on which Product Backlog items will be worked on the Sprint, and how.

But, please always remember that a diagram is only a diagram! Not an architecture. At this point, you already know what software architecture is (at least in Scrum!).

### Documenting Software Architecture in Scrum

This is another controversial topic in Scrum. First, Scrum is not a methodology. It is a framework. As such, it mandates neither more nor less, documentation. The key idea here is to understand that, depending on what the Product Owner has deemed as valuable, you can also end with documentation for software architecture as a companion to the Increment. The development team can also explain to the Product Owner why and how software architecture documentation can be valuable. And if the Product Owner deems maintenance as important, then the Development Team has permission to create (some) documentation.

Release quality software faster with [TestComplete.](https://dzone.com/go?i=228240&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad) Discover how to decrease testing times and expand test coverage with the most robust automated UI testing tool. [Try free for 30 days.](https://dzone.com/go?i=228240&u=https%3A%2F%2Fsmartbear.com%2Fppc%2Ftestcomplete%2Fmain%2F%3Fsr%3Ddzone%26md%3Dad)

Opinions expressed by DZone contributors are their own.
