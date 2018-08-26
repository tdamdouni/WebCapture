# How to Do a Legacy Software Migration: A Successful Checklist

_Captured: 2018-05-18 at 14:46 from [dzone.com](https://dzone.com/articles/how-to-do-a-legacy-software-migration-a-successful-1?edition=376324&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-05-18)_

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309721590%3B137110683%3Bb), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309721590%3B137110683%3Bb).

Here is a small checklist about how to migrate a legacy migration and to ensure its success. This article is part of my work to explain my knowledge about software migration in the company [Byoskill.](http://byoskill.com/)

First, measure your project according to the changes involved in the migration:

  * The organizational changes
  * The process changes
  * The technological changes

## The Organization

You will have to think about each person involved in the software that is going to be migrated. Which skills are required to develop, test, maintain, and support the software? How will you manage the brutal disruption in their daily work and motivate them to embrace the change?

I recommend you to have a clear picture of the team and not underestimate the needs of **training, evangelism, **and** change management**. Changing technologies or frameworks, even without any feature changes, may severely impact your end users, the support and maintenance teams, and the integration engineers.

## The Processes

An automated migration differs from a classical IT software project by adding a certain disruption in terms of time and practices. Since the migration has to be hastened (thanks to the usage of specialized tools), the success of the project requires a high level of software development practices. Usually, the legacy software is still hitting the wall in terms of agility, silo breakup, continuous integration, and test automation practices.

The legacy project migration requires a clear state (and view) of the following processes:

  * **SDLC: Software Development Lifecycle**
    * What is the current process?
    * Are there any traps or caveats to be aware of?
    * How much time does it take to push a new feature from the specification to production?
  * **Test automation: **You will have to answer many questions associated with well-identified risks. 
    * How is the application tested?
    * At which levels?
    * Are the tests automated?
    * What is the coverage (estimated and measure)?
    * What are the requirements to set up a new test environment?
    * How much does it cost?
    * Is test data available?
    * How accurate is the test data?
    * Which tools are required to execute the tests? Licenses?
    * What would it take to obtain sufficient coverage for the migration project?
  * **Continuous Integration**
    * How is the software built?
    * How much time does it take to produce a new release?
    * What are the steps?
    * Which parts are tricky or manual?
    * What are the components to be built?
    * How many individual parts compose the software?
    * Which tools are used?
    * What would it take to obtain complete CI/CD for the migration project?
  * **DevOps**
    * Logging and monitoring support 
      * Will the tools still be compatible with the migration?
    * Automatic deployment 
      * What are the changes required to maintain (or obtain) automatic deployment of the solution?
    * Error and exception handling 
      * Detect and document any regressions to catch and handle the errors during the run.
    * Performance testing 
      * Does the software have any automated performance tests?
      * Will they still be compatible?
  * **Release Management**
    * How many active versions are there for this software?
    * What is the branch release model?
    * Versions to maintain and port?
    * Frequency of releases and year schedule/roadmap?

## The Technologies

A good legacy migration project is preparing a clear state of the perimeter to be migrated and the targeted solution.

It comes in a phase of three steps:

  * The actual picture
  * The definition of the target
  * The migration itself
![](https://byoskill.com/wp-content/uploads/2018/03/LegacyMigrationDraw.png)

## Drawing the Current Picture

The initial software assessment does really matter. Indeed, a solution architect will detect any caveats and flaws in the current architecture that may critically slowdown the migration project.

Such assessment usually requires:

  * **A technology survey**: Which technologies are used in the software, license issues, the exact version, and possibility of an upgrade?
  * **Architecture assessment**: It will control the priority of the physical organization of the project (folders, files), the logical structure (components, package, functional and technical layers) and the dependency matrix (cycles, code weaving, code smells).
  * **Automated test assessment**: Code coverage, test documentation, test robustness/fragility, main complex components, and their level of testing.
  * **Code quality assessment**:A quick review to identify the main risks (reliability, security, maintainability).

## The Definition Phase

This phase has four objectives:

  * Get an understanding of the cost and time of the migration project.
  * Evaluate the ROI of the operation with the customer.
  * Eliminate the main technical/functional risks of the migration.
  * Communicate to the customer the organization and process changes to be done.

To achieve that, a main document (or specification) has to be produced: the migration guide. This migration guide will expose the targeted solution, the way to achieve it, the necessary steps, a risk analysis and RACI, and the cost and estimation of each task.

This definition phase may be accompanied by a Proof of Concept (POC), a short-term development performed on the current solution to assess the feasibility of the targeted solution and to allow any necessary tests to be executed. It will be critical to pay attention to any functional regressions and performance regressions in this POC.

## The Migration

The migration [is not a Big Rewrite. ](http://chadfowler.com/2006/12/27/the-big-rewrite.html) It's an incremental, well-defined process where automation removes the main source of failure of migration projects: the time of execution. Indeed, the longer the migration process takes, the more dangerous the project will become, it will be debated, and finally rejected.

A good migration project usually has the following qualities:

  * **Incremental:** In some ways, it's possible to have the two technological environments living as roommates in the software.
  * **Fast: **The amount of rewriting, manual fixes, and iterations to obtain the targeted solution have to be small.
  * **Cost-effective:** The volume of manual operation cost should be significantly smaller thanks to automation.
  * **Critical: **No legacy migration finds its justification without a real concern (security, investment, scale-up operation, business loss, or expectations).

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309721589%3B137110681%3Bh) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309721589%3B137110681%3Bh).
