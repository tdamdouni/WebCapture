# Many Small Monoliths: Microservices vs. Monolithic Architecture

_Captured: 2017-08-08 at 20:08 from [dzone.com](https://dzone.com/articles/many-small-monoliths-microservices-vs-monolithic-a?edition=310399&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-25)_

### This article aims to discuss the requirements for an organization to adopt microservices architecture, and the corresponding costs.

[Modernize your application architectures with microservices and APIs](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) with best practices from this free virtual summit series. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

In this article, I will talk about Microservices vs Monolithic Architecture.

**Disclaimer**: for clarity, this article assumes that:

  * The definition of microservices in this context entails a physical separation between services.
  * A microservice architecture is considered "properly" implemented, i.e.: 
    * In the absence/minimum of RPC communications request/reply between services.
    * Each service encapsulates its persistence.
    * Each service expresses a functionality. There is no "database service."

If one of these assumptions does not exist, the conclusions may not be valid.

## Many Small Monoliths

[Martin Fowler](https://martinfowler.com/)'s conference sessions in Barcelona highlight some aspects of the "technological trends" of recent years.

In particular, we were very interested in the part about architectural models to "microservices," the formal lack of definition that the term has, and the problems that arise from its adoption to dispense with a careful analysis of requirements and the situation of the project.

The problem, of course, doesn't lie in an architectural pattern, studied to give a solution to a specific situation, but in the lack of requirements matching when it is applied.

The reflection on microservices, calls to mind a set of patterns/practices/technologies that have emerged in the recent years of technological innovation, and which have been adopted, often in an "extreme" way, by development teams.

Here's a short list:

  * Functional Programming.
  * Reactive Programming.
  * CQRS.
  * Event Sourcing.
  * Persistence actor's models.
  * Microservices.
  * Serverless architectures and BaaS.
  * New front-end trends.
  * Non-relational persistence.
  * Polyglot programming/persistence.
  * Deep learning and machine learning in general.
  * Continuous rewrites.

The purpose is to initiate a series of posts in which we will reason retrospectively about the early adoption of what is presented in each point, and our considerations based on our experiences.

Taking advantage of the topic refreshed by Martin Fowler, we will try to reason a possible answer on the requirements for microservices adoption, spelling out the costs.

## The Objectives of Style to Microservices

It is important, when it comes to valuation, to be very clear about the objectives and problems that need to be resolved with a transition to microservices, which we briefly recall here:

  * Fast builds at the component level, manageability of projects.
  * Very clear and rigid boundaries.
  * Deployment independence and quality of service.
  * The possibility of polyglot programming/persistence.

### The Costs

#### Operational Cost

We tend to underestimate the fact that each microservice requires

  * Delivery policies.
  * An automatic build, with repeated/ included/generated scripts.
  * A delivery/deployment pipeline, with scripts like the ones mentioned above.
  * Monitoring/health checking/self-healing.
  * A scaling policy, based on specific parameters.
  * A definition of common dependencies.
  * A version control repository.
  * Failure management.
  * A log, preferably centralized.
  * More specific requirements of each service.

Although it is true that technologies such as Docker and the DSLs of Jenkins help a lot in making the above points reproducible, it is impossible for the operational costs to equal those of a monolith:

  * More pipelines require more hardware and computing resources.
  * To verify an interaction, you may have to wait for more than one pipeline.
  * The same thing to reproduce/see a bug fixed.

These points are very affected by the problem of boundaries (see below).

Also, in order not to repeat the aspects of supportability and operability, we will need to extract common libraries, and the same for all common code.

This will add complexity to the solutions from point zero of the project, generate dependencies between pipelines, and generate the need for private repositories.

### Standardization

More generally, the mitigation of operating costs requires a strong culture from the point of view of automation/systems standardization. This is something that is not usually generated within one single project.

What we see is that, despite the efforts dedicated, many microservices architectures are not backed by the operational infrastructure they would require.

Like other aspects, standardization efforts are more efficient if the migration to microservices is incremental, and operational aspects naturally "emerge" from the extraction of services.

### Feedback Cycles

As mentioned above, a microservice-oriented system is still a complex system, being more than just the simple sum of its parts.

It is true, assuming you have already paid operational and standardization costs, and there is a relative stability of the boundaries of a microservice.

The feedback cycle during development is then comparable to, if not better than, the monolithic system, at the component level.

But it is very important to make it clear that there is a balance between the ease of feedback at the component level and the feedback regarding the composition of components, which will be much more complex.

For any problem at the system level, you have to look for it in messaging, with difficulty of debugging. The necessary tool is often of a low level. This problem becomes more serious in case of performance problems. Messages are often untyped, moving problems from compile-time to runtime. The fix to a problem, to be tested, may require recompilation/reconstruction of one or more components

### Complexity by Interaction (Smart Service, Dumb Pipes)

As [Michael Feathers](https://michaelfeathers.silvrback.com/) points out, if complexity is not in the components, it is necessarily in the interaction between components.

This is what Martin Fowler refers to with the principle of "smart services, dumb pipes." The idea is to minimize the dependencies when we can replace/update an instance of a microservice.

More generally, the heuristic responds, once again, to the concept of encapsulation: the more distributed the "intelligence," the more modular the system will be.

In spite of our unconditional support to the use of technologies that facilitate asynchronous communication (message brokers), we can't deny that the cost of a debug session of two lines of code and an interaction mediated by some type of bus is different.

## Many Small Monoliths

For those who write, the central point of costs is the modeling of the "service boundaries."

A redefinition (or even rewriting) of a microservice has a hidden cost that is much higher than a normal change in a code base, among other things:

  * Application of operational costs (libraries, policies, etc.).
  * Diagram/data migrations in subsystems with different life cycles.
  * Redefinition of contracts, instability of public APIs.
  * Testability only at the integration level.

The problem is that, as [Eric Evans](http://domainlanguage.com/) pointed out in the last edition of DDD Europe, the definition of boundaries is something very complicated, especially at the beginning of the evolution of a system, so much that it resembles something "elastic."

Probably, the only certainty we have is that the first design will be wrong with respect to the project's latest requirements. Moreover, the concept isn't new: it is a cornerstone of agile methodologies.

Using a microservice approach from the beginning provides the assurance that one or more (likely more) boundaries will have to be changed over the course of the project.

This implies that the "microservices premium" will inevitably be paid for

  * Each change of boundaries, as the cost of change (see above).
  * When/if we decide to minimize boundary changes, at the level of multiplication of "conversations" between services, causing problems of maintainability and even performance/scalability.

We consider the quantity and quality of interaction between services as the focal point of the service-oriented architectures, to the point that if we could replace with "many small monoliths" the expression "microservices."

## Hope for Microservices

### Quality of Service With Monolithic Architecture

We speak of the "quality of service" because, in reality, it's one of the architectural qualities we expect from a transition to microservices.

We understand, in fact, that the term "scalability" is improper (not very specific) in this context (unless it's not interpreted as functional scalability): limits to the generic "scalability" don't depend so much of a monolith distribution vs. microservices, but more of other properties of a more general character, such as the absence of shared state in services or the distribution of data.

Still, as a mental exercise, it is possible to imagine a situation in which development is about a single codebase ("monolith"), but the distribution is diversified.

So, the whole monolith would be deployed on the machines where we distribute the service "user," but only the user APIs are published. This allows the deployment of different versions of the same monolith. It would minimize the costs of physical separation, but achieving the independence of deployment, which is one of the features we seek from a microservice architecture.

We consider that, without being a particularly "communicative" architecture, this model may be viable when transitioning between monolith and microservices. You can even get out of "trouble" at times where component-level scalability is urgently needed.

### If There Are So Many Problems, Why Have Microservices?

It's important to clearly state our position. We at [Apiumhub](https://apiumhub.com/) are not at all "against" a microservice architecture. We try to _raise awareness_ of the costs involved, to make a reasoned decision. The problem that we are trying to highlight is _that perception of simplicity that is given at first to the microservice architecture, which is false and distorted_.

It's quite easy to think that a project starting from zero, reduced in size, is the easiest thing to start development by extending a system. The problem, at that moment, is to forget about all the hidden costs related to the fact that a microservice is still _one part of a whole_.

In general, it is difficult for us to propose rules regarding the adoption of architectural styles. We try to propose an approach that is "comfortable," based on our (limited) experience, which is the only thing we can do.

If we apply the agile philosophy to the problem, the idea is to perhaps start with a minimum cost situation (monolith), and, by listening carefully to the pain-points in the evolution of the project, let the physical partition "emerge" naturally.

We imagine this type of process:

  * Start with a single code base, try, as much as possible, to structure "logical" microservices and separate by "contexts."
  * Very "technical" pieces, such as proxies, or high-performance parts that are little or nothing related to the rest of the system, should constitute other "microservices" from scratch.
  * Carefully listen to pain-points that may suggest a transition start. 

Typically:

  * Compilations/constructions last a long time.
  * The life cycles of different areas of the system start to collide continuously.
  * The base code starts being unmanageable due to its size or "physical" reasons.
  * Trivial changes involve high-risk deployment.
  * There are proven needs for technological changes in some area of the system.
  * The company grows and development teams are naturally formed, organized by functional area.

If there are one or more pain-points demonstrated, before simply "breaking the system," do a contextual analysis (context-map), which will help minimize the change of boundaries.

It may not be necessary to split the monolith into macro-contexts, but if a microservice is extracted, it's advised to do so based on the previous analysis.

If a microservice is extracted and that based on the previous analysis belongs to a context of another microservice, make an analysis of advantages and disadvantages of joining the base codes.

Continuing with the origins of the microservice culture, the reasons and modes of transition aren't much different than those of SOA transitions. They differ by the fact that it is possible to extract services of small size.

We like to refer to this process with the term "microservices mitosis," to emphasize on the progressive, incremental and "natural" character of the process by which a microservice is generated by division when boundaries have demonstrated sufficient maturity.

We need to add a note about serverless technologies: the fact that these technologies typically distribute "by default" doesn't influence the present considerations, since nothing prevents the code base to be unique, and that activation codes simply change.

## Logical Microservices

While we exposed our doubts about the up-front adoption of microservices with physical separation, we don't have much regarding microservices in logical separation. A microservice in a DDD context can simply be a domain service in its bounded context, and so [Vaughn Vernon](https://vaughnvernon.co/) frequently expresses in his posts about DDD and actor model.

This isn't the place to proclaim these aspects, since DDD is a very advanced set of modeling patterns. We only care to emphasize that "logical" microservices are a necessary consequence of a good application of DDD.

## A Possible Win-Win

Simply as a hypothesis, we would like to imagine having a technology that would enable the advantages of microservices at the quality of service level and deployment independence, with the minimum costs of a monolith in its initial state.

For this to happen, we should have a single (or just a few) physical deployable artifacts, which would allow to move the number of instances of the logical microservices contained in runtime.

A system of this type would allow us to deal with other problems (build times, team organization) with more distance, without the need to make up-front decisions.

We hope that technologies that provide **location transparency**, such as actor systems in Akka, can bridge these extreme gaps between monoliths and microservices.

The Integration Zone is proudly sponsored by [CA Technologies](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Learn from expert microservices and API presentations at the [Modernizing Application Architectures Virtual Summit Series](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
