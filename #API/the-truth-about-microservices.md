# The Truth About Microservices

_Captured: 2017-05-08 at 10:42 from [dzone.com](https://dzone.com/articles/the-truth-about-microservices?edition=298008&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-07)_

Build APIs from SQL and NoSQL or Salesforce data sources in seconds.[ Read the Creating REST APIs white paper](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D), brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

John Frizelle, a Mobile Platform Architect at Red Hat, gave a talk on microservices wherein he provided some great advice about microservices. Most importantly, he provided guidance on when, where, and why (or why not) you should deploy them.

![](https://developers.redhat.com/blog/wp-content/uploads/2016/06/microservices.png)

## What Are Microservices?

Microservices are a method of breaking down an application into a suite of small, lightweight services, and are processes that typically communicate over HTTP. Building a single microservice is easy, building a microservice architecture is extremely hard. It is basically distributed system design and development. If you are going to embark on a new microservice architecture, here are some challenges you will likely face.

### Building Microservices

  * How do you identify dependencies between services? A change to one can result in multiple service rebuilds.
  * You must carefully track individual service versions and then determine what versions of what services constitute a release.

### Testing

  * Unit testing is super easy with microservices, by definition.
  * Integration testing requires figuring out what actually needs to be tested, what are its neighbors?
  * End-to-End testing requires standing up the entire microservice architecture with the right versions, but by its nature, these microservices are all versioned independently. It can be difficult to event determine what versions of other microservices you need to test.

### Versioning

  * Each service will have a unique, independent version.
  * The collection of microservices will have a version.
  * Maintaining a version matrix becomes very complex, especially maintaining this over time.
  * How do you release and maintain backward compatibility? Do you maintain the old code and add the new features? This will lead to code bloat, which is contrary to the nature of microservices. Your other option is to release breaking changes, where you have to release multiple dependent versions all at the same time.

### Deploying

  * Deploying microservices requires strong automation, as the system is too complex to deploy by hand. This is a prerequisite to moving to microservices.
  * Blue/Green deployments are a desirable deployment methodology for microservices. The system is too complex to try to back-out changes.

### Logging

  * Microservices require centralized logging, as there is no one place to figure out what is going on. Logging into tens or hundreds of services to tail logs is pretty useless.
  * You will also require some type of global request tracing, assigning a request ID to each request such that you can figure out how things flow.

### Monitoring

  * Microservices should only be deployed along with a centralized dashboard. Monitoring multiple microservices is a very difficult task, you need something to aggregate the service data.
  * Your monitoring solution also requires distributed request tracing. Microservice architectures really require a mechanism to visualize a request ID across the services and measure performance. One slow microservice can slow down the application to a halt.

### Debugging

  * Root cause analysis - how to determine where the problem exists with microservices. It is virtually impossible to tell where the failure is without the monitoring solution. Only then can you begin to isolate the actual problem.
  * Remote debugging is not feasible across many microservices at once. You need to be able to iterate the microservice versions very quickly, sometimes guessing to solve your problem.

### Connectivity

  * Microservice architectures should include a service discovery registry. You don't want to hardcode URLs into your microservices, especially with moving between CI/CD environments. How do they contact each other? How do they contact the right version of each other?
  * Network - there are network hops between each service, these add latency and possibly data loss between each service. Your architecture needs to accommodate failures gracefully. Build in short TTLs, fail quickly to bubble up the failures rather than a slow crawl to death. Failing quickly lets you retry quickly.

## When Should You Consider Moving to Microservices?

Traditional monolithic architectures have their own unique and well-understood challenges. If you are starting to see these block development efforts, microservices might be your answer.

### Size

  * The monolith application code base size has grown too large for local development. Can you even load all the code in your IDE at once?

### Stack

  * Your monolith will be a single technology stack rather than the right stack for the right purpose.
  * The initial large jump from one stack to another is very difficult, subsequent jumps are much easier to make.

### Failure

  * If anything fails in a monolith, everything fails… it is all one system.
  * Much larger surface area to attack and to be exposed to external conditions.

### Scaling

  * You can only really scale a monolith vertically, you have to increase everything at the same time. This leads to excessive cost and resource consumption.
  * A few large VMs are usually much more expensive than many small VMs or containers.

### Developer Productivity

  * Developers cannot work independently, rather in fewer, and larger teams.
  * In a single code-base, CI takes much longer occurs much less frequently. You typically have to wait for nightly or weekly builds to see if anything breaks.

If you do decide to move to microservices, you might realize these benefits:

  * Agility and flexibility.
  * Smaller code-base, easier to wrap your head around.
  * More, smaller teams rather than one larger team.
  * Easier to scale microservices, only scale the ones that are hot.
  * The right stack for the right job, you are no longer bound to one stack.

If you are going to run microservices, understand why and what benefits you will receive. Start out from day one with automation. Trying to add it later will ultimately make your effort fail, you need to invest in the automation before starting to build.

Finally, remember Conway's law - moving to microservices will likely require an "Agile Transformation." Your organization should mirror the microservice architecture.

The Integration Zone is brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Use CA Live API Creator to quickly [create complete application backends, with secure APIs and robust application logic](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D), in an easy to use interface.
