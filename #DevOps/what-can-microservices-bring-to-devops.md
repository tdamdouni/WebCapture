# What Can Microservices Bring to DevOps?

_Captured: 2018-01-08 at 06:07 from [dzone.com](https://dzone.com/articles/what-can-microservices-bring-to-devops?edition=351091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-07)_

In response to accelerated release cycles, a new set of testing capabilities is now required to deliver quality at speed. This is why there is a shake-up in the testing tools landscape--and a new leader has emerged in the just released [Gartner Magic Quadrant for Software Test Automation](https://dzone.com/go?i=265440&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fgartner-magic-quadrant-software-test-automation%2F%3Futm_source%3DDZone_Pre_Roll%26utm_medium%3DText_Ads%26utm_campaign%3DDZoneDevOps%26utm_content%3D2017GartnerMQ).

_[The prompt for this blog post was taken from DZone's Bounty Board. Check it out to see how you can write articles to win prizes!](http://bounty.dzone.com/)_

## Background

Some organizations historically have shied away from periodic investments in architecture decoupling and modernized techniques, and consequently are now stuck with monolithic product architectures that make releases unpredictable.

A monolith is like a "big ball of mud" that rolls down the hill and collects dirt on its way down. There are several disadvantages to monoliths:

  1. If and when this unwieldy, densely-packed mass reaches Production, the probability that something will blow up is higher than it would be if it were of a more manageable size.
  2. Given the sheer density of the monolith, accountability is spread across a large team, and sometimes across multiple teams. Shared accountability usually means no one is accountable.
  3. To make matters worse, this large mass has to be built, packaged, and tested every time there is a change, even if the change is minute and constitutes only a wee percentage of the entire monolith.

If a monolith faces a Production issue that requires an urgent fix, it may not give the teams any more comfort to know that the fixed version of that same monolith has started to slowly roll down that same perilous hill. If the first fix does not work, we would go back to square one, and 1-peat, 2-peat, 3-peat and repeat till the product performs as expected. Sounds pretty downhill, right? It is.

## Enter Microservices and DevOps

There isn't a one-liner that summarizes the intent of all the diverse tech companies across the globe. However, there is one universal truth.

> Organizations all over the map try to release quality products frequently and predictably to enhance customer delight. 

As a Dev Advocate for [Atlassian Bitbucket](https://bitbucket.org/), I'm well familiar with this truth as it's our goal to help tech organizations everywhere to deliver better software faster. This is why we [continuously improve Bitbucket Pipelines](https://blog.bitbucket.org/2017/12/20/pipelines-stocking-stuffers-test-reporting-docker-run-large-builds/) and [add new options in our suite like Bitbucket Deployments](https://blog.bitbucket.org/2017/12/05/introducing-bitbucket-deployments/)--to provide tools that make it easier to deliver quality products efficiently.

And to that extent, we will review three ways in which:

  * Microservices benefit DevOps, and
  * How their coexistence improves speed, quality, and predictability of product releases.

### i. Microservices Architecture and DevOps Empower Decentralized Teams to Control Their Own Destiny

Centralization allows a single group of people to make decisions on the tech stack, tools, and standards that the rest of the organization has to adhere to. While this sounds like a streamlined approach to reduce duplication and overhead, it could lead to suffocation and low morale. To foster innovation, we must empower small teams to innovate at their own pace and to control their own destiny.

Microservices architecture is all about doing one thing well, and this is a paradigm shift from designing monoliths that are conglomerates of many "services" lumped into one. Strangulation of monoliths gives birth to smaller microservices and facilitates breaking down the large bulky team that developed the monolith into multiple smaller (and more nimble) teams.

Since microservices are organized around independent business capabilities, they could be developed with the help of different programming languages. The key concept here is to institute well-defined sharp interfaces, which determine interactions between these modular polyglot services. This frees up the smaller teams to choose their own standards and success metrics, and also honor organizational KPIs (key performance indicators). The interfaces determine how the services (and hence the teams) interact, thereby letting architecture decide organization, and not the other way round. This is also the essence of Conway's Law:

> "Any organization that designs a system (defined broadly) will produce a design whose structure is a copy of the organization's communication structure."

Additionally, decentralization plays right into the core principles of DevOps and narrows the gaps between:

  1. UI, middle-tier and backend specialists, who tend to operate in their own silos, and
  2. Business, Product Management, Dev, QA, Release, Security, Operations, and whatever you have, who tend to operate in their own departments.

The bottom line is that both microservices architecture and DevOps favor the product model versus the project model, whereby 5-7 member teams design, build, test, release, monitor and maintain their applications on Dev/Test, Stage, and Production.

### ii. Compartmentalized Services Can Be Released as Independently Deployable Artifacts That Are Not Tied at Their Hips for Success

Most organizations bet on designing and implementing resilient Continuous Delivery pipelines that help them:

  * Experiment with new features in a safe, secure, and auditable manner, and
  * Recover from failures quickly without disturbing their customers.

Continuous Delivery pipelines are fully automated solutions that promote independently deployable versioned artifacts from lower environments like Dev/Test and Stage to higher environments like Production. Pipelines have little to no tolerance for handoffs between silos since handoffs are non-value adding "waste", as can be determined by a VSM (Value Stream Map).

If the system is assembled from multiple subsystems and can be released only as a whole, cliche, as it may sound, "A chain is only as strong as its weakest link" rings a resounding bell. On the contrary, microservices architecture is essentially a suite of services that have a clean boundary. Typically, each microservice translates to an independently deployable (versioned) artifact that generates a linear pipeline anatomy. Each modular service is organized around a business capability that could (and should) be released independently of its neighbors to improve developer productivity and team velocity. These compartmentalized (or componentized) services are not tied at their hips for success and enable faster teams to go ahead of the slower ones.

Albeit monolithic architectural patterns can be successful, the modularity offered by microservices enables releases to happen rapidly in incremental batches. DevOps favors small batch sizes too and allows small teams to own the services and ship them as well.

Yet again, we see microservices and DevOps playing in harmony to help organizations scale.

### iii. Microservices and DevOps Improve Test Cycle Time, and Hence Time2Market

Organizations like to outmaneuver competition or at the very least stay close on their heels. They try to build sustainable business models whereby they can reduce shelf time of new ideas without burning out the team. It is possible to achieve this with cumbersome monoliths, however, less probable than it is with the granular microservices. Here's why.

A monolith, or a "big ball of mud" often leads to a "big ball of tests" that:

  * Were designed and implemented over a significant period of time, during which team members may have churned multiple times.
  * May not allow parallel execution of individual tests, since test cases, test data, and test config were not designed for independent and idempotent execution.
  * Inflates with every new release due to the addition of new test cases. Sometimes there is slow (or no) archival of dilapidated tests, even for features that are no longer active in Production. There could be fear and uncertainty over the test archival process, since there may not be a single person who fully understands the system architecture.

All tests, relevant or otherwise, execute with each change to the monolith to ensure that the densely packed mass has not inadvertently regressed. This exponentially inflates the organization's test cycle time, which is the test execution time to decide whether to proceed with the release or abort. Test cycle time is directly proportional to FeatureLeadTime, which is the time required to release a feature to Production. That, in turn, blows up Time2Market for new business features, which makes the organization susceptible to disruption.

Microservices, being more granular, are released to Production via independently deployable versioned artifacts that are validated separately. Microservices interact with each other, to provide specific customer use cases, and thus require smart integration tests. During integration tests, some of these neighboring services are represented by their test doubles with sharply defined contracts. The test doubles and contracts should be treated like first-class citizens and should be owned by small teams who own, ship, and maintain the real services and the interfaces.

The bottom line is that we should avoid a highly integrated validation environment where all subsystems are assembled into a system or several mini-systems, and then validated and released as a whole. DevOps advocates small and incremental batch sizes, and the microservices architecture helps us do just that - develop, test, and release services in a granular fashion. It avoids the composition (or assembly) pattern and executes selective test suites for isolated changes instead of taking an all-or-none approach.

## In Summary

The key takeaways are that microservices and DevOps:

  1. Complement each other
  2. Fuel experimentation, and
  3. Accelerate adoption.

It would have been a shame if they were in conflict in some way, and if organizations were forced to choose one over the other. Moreover, microservices architecture and DevOps feed into simplification of the software delivery methodologies, like Continuous Delivery and Deployment, and help generate delivery pipelines that scale.

_[The prompt for this blog post was taken from DZone's Bounty Board. Check it out to see how you can write articles to win prizes!](http://bounty.dzone.com/)_

Recently published [Gartner Magic Quadrant Report for Software Test Automation ](https://dzone.com/go?i=265436&u=https%3A%2F%2Fwww.tricentis.com%2Fresource-assets%2Fgartner-magic-quadrant-software-test-automation%2F%3Futm_source%3DDZone_Pre_Roll%26utm_medium%3DText_Ads%26utm_campaign%3DDZoneDevOps%26utm_content%3D2017GartnerMQ)provides an objective benchmark of all test automation solutions based on industry surveys, customer inquiries, product evaluations, and more.

Topics:

devops adoption ,microservice architecture ,microservices ,microservice deployment ,devops transformation ,devops development ,pipeline ,continuous delivery ,release automation ,devops

Opinions expressed by DZone contributors are their own.

![](https://dz2cdn1.dzone.com/storage/rc-covers/7391100-dzone-aicover.jpg)
