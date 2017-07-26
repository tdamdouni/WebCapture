# How to Make Service Virtualization a Reality for Testers

_Captured: 2017-04-20 at 16:46 from [dzone.com](https://dzone.com/articles/test-driven-service-virtualization-how-to-make-ser?oid=twitter&utm_content=buffer98368&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The first time that most software testers hear the term "service virtualization," they immediately think of server virtualization (i.e., VMware). _Server_ virtualization is undeniably a valuable tool for creating and maintaining test environments, but _service_ virtualization is something altogether different.

Service virtualization is the simulation of interfaces -- not the virtualization of systems. Service virtualization lets you automatically execute tests even when the application under test's dependent system components (APIs, third-party applications, etc.) cannot be properly accessed or configured for testing.

By simulating these dependencies, you can ensure that your tests will encounter the appropriate dependency behavior and data each and every time that they execute. It's commonly used when integration tests or end-to-end tests need to interact with dependent system components that are:

  * Unreliable, evolving, or not yet completed.
  * Beyond your scope of control (i.e., operated by another company or division).
  * Available for testing only in limited capacity or at inconvenient time.
  * Challenging to provision or configure in a test environment.
  * Simultaneously needed by different teams with varied test data setup and other requirement.
  * Too restricted or costly to use for automated regression testing.

Service virtualization has become recognized as one of the best ways to speed up testing and accelerate your time to market. In a recent Gartner research note, _[A Guidance Framework for Testing Web APIs_](https://www.gartner.com/document/3647917?ref=solrAll&refval=182319639&qid=a278746f895dae8e313a72f00fed23a1), Gartner Analyst Sean Kenefick talked about the importance of finding performance issues and bugs earlier in the software development process by using service virtualization. Kenefick emphasized that simulating an entire application environment where missing applications or third-party applications have been virtualized ensures fast feedback loops, and ensures that you have the right tools for continuous testing.

In short, service virtualization holds tremendous potential to help testers boost test automation and keep pace with Agile and DevOps demands. If you're being pressured to test faster and/or earlier in each release cycle (i.e., "shift left"), I encourage you to learn more about service virtualization and decide if it could help you advance your team's Continuous Testing efforts.

Interestingly, although [service virtualization has been around for years now](http://sdtimes.com/building-up-service-virtualization/), it's more "virtual reality" than "real reality" for many software testers -- even those whose organizations have already deployed service virtualization tools. In theory, service virtualization is all about removing constraints for software testing. In reality, many testers have found that service virtualization falls short of its promise to end delays and provide them direct ad easy control over the test environment -- especially for stateful tests interacting with multiple dependencies.

One promising solution for making Service Virtualization more than a virtual reality for testers is a new approach called [test-driven service virtualization](https://www.tricentis.com/resource-assets/test-driven-service-virtualization-2017-04-04-emea-usa/), referring to service virtualization performed in the context of a test and architected for the needs of a tester.
