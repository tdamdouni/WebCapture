# How to convince customers of design decisions by the use of traceability

_Captured: 2017-07-07 at 06:59 from [blogs.itemis.com](https://blogs.itemis.com/en/how-to-convince-customers-of-design-decisions-by-the-use-of-traceability)_

During the software development process various partial results are generated, but it is not always easy to maintain an overview of them. This is however essential for monitoring progress, analysis of the impact of changes and the justification of (design) decisions.

In this blog article we describe how you can maintain this overview, and we also provide a downloadable summary.

## Partial results in software development - an information flood

Consider the following: You are working as a usability engineer on a software development project with various other roles: clients and stakeholders, the marketing team, developers, architects, testers and a project manager. How many partial results arise in an average project?

![convice-desig-decision-traceability.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Usability/people-talking-puzzles.jpg?t=1499351211930&width=2172&name=people-talking-puzzles.jpg)

For example, we might carry out contextual interviews in requirements analysis and specification, which lead to different partial results: an interview guide, context scenarios, requirements, and usage requirements derived from them. We also have documents from other sources, such as stakeholder and marketing requirements. In addition there may be an aggregated request list in which we collect the information from the different documents, as well as so-called 'personas' to clarify the requirements. For this phase alone there are eight different partial result types.

The design, development and test phases also show results such as prototypes and wireframes, style guides, architectures, source code, tickets, usability test tasks, test logs, result lists and so on. As if that were not enough, emails, meeting protocols, change requests and much more are generated in a normal project day.

There is therefore an important question…

## How can I keep track of all the partial results?

Obviously this question must be answered, simply because we are faced with different challenges on our project every day.

### **Challenge 1 - Convince the client about your design decision**

How often might we find ourselves in the following situation? We present a concept or design to the client, but it challenges a design decision taken at an earlier stage. It is now up to us to explain why we have made our decision. Fortunately nothing is done without a reason in usability engineering - the problem is only to find the relevant documents quickly enough to be able to point out the connections.

### **Challenge 2 - Prove that all requirements have been implemented**

In client discussions questions about the actual project status and whether all requirements have been implemented arise repeatedly. But when does a requirement apply? This question can arise for example when positive results are obtained from both usability and software tests of a prototype. To be able to visualize the context, however, we first need to identify the status of all requirements and all partial results. This involves a huge amount of effort.

### **Challenge 3 - Find out which requirements are affected by a change request**

We can often get a change request from a client after we have already done important work, for example for a requirements change. If the requirement has been implemented, however, partial results that are already part of the program are linked, such as concepts, personas, sections of the source code or tests. It is now necessary to determine to which partial results the requirement change applies, which is not easy when a multiplicity of partial results are involved.

### **Challenge 4 - Get involved when something has changed**

This sounds so simple, but it is elementary that every role should be informed when something has changed, and of what has changed. This generates tasks. A developer must, for example, be made aware that the usability engineer has modified the concept, and adapt the implementation accordingly.

## The light at the end of the tunnel

The good thing is that all the partial results that arise in the development process are all connected in some way. The figure below shows this context graphically:

![traceability-in-usability-engineering-link-your-artifacts.png](https://blogs.itemis.com/hs-fs/hubfs/link-your-artifacts.png?t=1499351211930&width=2172&name=link-your-artifacts.png)

In usability engineering particularly, there is a predefined scheme of how usage requirements are established that makes the connection between partial results clear. For example, we have key questions for context interviews, which in turn result in protocols. From these we successively derive context scenarios, requirements and usage requirements. If we have a consolidated list of requirements, this in turn addresses the usage requirements as well as other requirements documents, and perhaps also requests from emails. Change requests also enter at this point. The consolidated requirement list, on the other hand, is the basis for personas; these in turn are used for usage scenarios, which provide a bridge to prototyping. The prototypes are then the basis for the source code, and so on. As a rule no partial result and no requirement is detached from all the others.

### Traceability as an approach to a solution

If you are aware of this connection, the first step is established; this provides the basis for a concrete approach to a solution - traceability management.

Specifically, traceability means establishing an understanding of where partial results come from and how they relate to one another. To do this, links must be made between individual partial results, as in the graphic above. We link a concrete context scenario to a concrete requirement, then to a concrete usage requirement, and so on. The links help to navigate quickly between artefacts and avoid long search times. The relationships can also be visualized graphically, but complete traceability management is even more empowering.

### **Traceability as a support for reasoning**

Let's review the challenges. If we want to convince our client that our design decisions are not merely plucked from thin air, we merely have to demonstrate the visualization of the links. This allows our client to see exactly which aspects have influenced our design decisions. At the same time we can quickly navigate to the linked artefacts using the visualization, thus avoiding cumbersome searching and opening of documents.

### **Traceability as an aid to progress tracing**

If we link all the elements we can use the links to identify the status of the requirements. We only have to make an evaluation of the current link status, and can see for which requirements links are already established - these are then considered implemented. For all other requirements we can display the partial result to which they are linked, and derive open tasks from this.

### **Traceability as a tool for impact analysis**

We can rapidly provide an effort estimate for change requests by visualizing the links to assess their impact. We can see directly which partial results are linked to a requirement, can navigate to the partial results and check how extensively they are. This enables a realistic estimate of effort.

### **Traceability for change tracking**

The presence or absence of links can show us whether or not we have open tasks for our role. If for example a link to an implementation is not yet available for a prototype, this means that development is still required. Whether existing links have changed can also be checked by automatic validation.

### **The need for cross-tool traceability**

The use of traceability can therefore help in principle in various situations. There is however a major problem: the various roles in the development process usually work in - use - different tools. This demands a cross-tool application if all the advantages of traceability are to be available. Applications that only allow linking between partial results within one or two tools will not help.

## YAKINDU Traceability - support for the entire project process

[YAKINDU Traceability](https://www.itemis.com/en/yakindu/traceability/) allows us to create reliable and seamless traceability across different tools. It offers the opportunity to meet the challenges above successfully, and thus support the entire project process.

At UX Barcamp Europe 2017 I showed in my talk 'Traceability in Usability Engineering - Or: How to convince customers of your design desicions' how YAKINDU Traceability could be used to ensure traceability between Usability artifacts. If you are interested in the slides, please download them here.
