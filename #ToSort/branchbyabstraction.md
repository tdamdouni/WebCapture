# BranchByAbstraction

_Captured: 2017-08-09 at 17:57 from [martinfowler.com](https://martinfowler.com/bliki/BranchByAbstraction.html?utm_content=buffer2d72e&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

"Branch by Abstraction" is a technique [[1]](https://martinfowler.com/bliki/BranchByAbstraction.html?utm_content=buffer2d72e&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer) for making a large-scale change to a software system in gradual way that allows you to release the system regularly while the change is still in-progress.

We begin with a situation where various parts of the software system are dependent on a module, library, or framework that we wish to replace

![](https://martinfowler.com/bliki/images/branch-by-abstraction/step-1.png)

We create an abstraction layer that captures the interaction between one section of the client code and the current supplier. We change that section of the client code to call the supplier entirely through this abstraction layer.

![](https://martinfowler.com/bliki/images/branch-by-abstraction/step-2.png)

We gradually move all client code over to use the abstraction layer until all interaction with the supplier is done by the abstraction layer. As we do this we take the opportunity to improve the unit test coverage of the supplier through this abstraction layer.

![](https://martinfowler.com/bliki/images/branch-by-abstraction/step-3.png)

We build a new supplier that implements the features required by one part of the client code using the same abstraction layer [[2]](https://martinfowler.com/bliki/BranchByAbstraction.html?utm_content=buffer2d72e&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer). Once we are ready we switch that section of the client code to use the new supplier.

![](https://martinfowler.com/bliki/images/branch-by-abstraction/step-4.png)

We gradually swap out the flawed supplier until all the client code uses the new supplier. Once the flawed supplier isn't needed, we can delete it. We may also choose to delete the abstraction layer once we no longer need it for migration.

![](https://martinfowler.com/bliki/images/branch-by-abstraction/step-5.png)

My description above describes a common case, but there are plenty of variation that can occur. Sometimes you can't swap-out the supplier for only some clients, you have to do it all at once. Sometimes you can break down the features of the supplier into different sub-components and carry out this whole procedure one sub-component at a time.

Despite these variations, there is a common theme. Use an abstraction layer to allow multiple implementations to co-exist in the software system. Use the notion of one abstraction and multiple implementations to perform the migration from one implementation to the other. Ensure that the system builds and runs correctly at all times, so you can continue to use [Continuous Delivery](https://martinfowler.com/delivery.html) while you are doing the replacement. Look for as many ways as possible to make changes gradually.

## Further Reading

[Jez Humble describes](http://continuousdelivery.com/2011/05/make-large-scale-changes-incrementally-with-branch-by-abstraction/) how his team used Branch-by-Abstraction to replace both an object-relational mapping framework (ibatis to hibernate) and the web UI framework (velocity/JsTemplate to Ruby on Rails) for ThoughtWorks's Continuous Delivery tool "Go".

Paul Hammant provides [more details](http://paulhammant.com/blog/branch_by_abstraction.html) of using Branch-by-Abstraction, particularly as an alternative to using version-control branching.

Steve Smith [describes a variation](http://www.alwaysagileconsulting.com/articles/application-pattern-verify-branch-by-abstraction/) which involves verifying that the two implementations return the same results to requests.

## Acknowledgements

Thanks to Paul Hammant for his detailed suggestions as well as being an important primary source.

## Notes

1: This technique has been around for a long time, although it never got a popular name. Paul Hammant introduced the term "Branch by Abstraction" while arguing in favor of [Trunk Based Development](http://paulhammant.com/2013/04/05/what-is-trunk-based-development/) (he credits Stacy Curl with originally coming up with it). This name seems to have caught on and is now the term I most commonly hear.

2: While we are building the new feature we can use [FeatureToggles](https://martinfowler.com/bliki/FeatureToggle.html) to run the new supplier in test environments and compare its behavior to the flawed supplier.
