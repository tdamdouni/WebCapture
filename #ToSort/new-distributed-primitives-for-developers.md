# New Distributed Primitives for Developers

_Captured: 2017-05-13 at 08:46 from [dzone.com](https://dzone.com/articles/new-distributed-primitives-for-developers?edition=298091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-12)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

## Object-Oriented Primitives (In-Process Primitives)

As a Java developer, I'm well familiar with object-oriented concepts such as class, object, inheritance, encapsulation, polymorphism, etc. In addition to the object-oriented concepts, I'm also well familiar with the Java runtime, what features it provides, how I can tune it, how it manages my applications, what would be the lifecycle of my object and the application as a whole, etc.

![](https://2.bp.blogspot.com/-VlLb6psyghA/WPtANW7a9_I/AAAAAAAAIIo/sx1-SqXMYrkFHSe_ZwSu9kvr7GoyFJN8wCLcB/s400/Screen%2BShot%2B2017-04-22%2Bat%2B12.35.03.png)

And for over a decade, all that has been the primary tools, primitives, and building blocks I've used a developer to create applications. In my mental model, I would use classes as components, which would give birth to objects that are managed by the JVM. But that model has started to change recently.

## Kubernetes Primitives (Distributed Primitives)

In the last year, I began to run my Java applications on Kubernetes, and that introduced new concepts and tools for me to use. With Kubernetes, I don't rely only on object-oriented concepts and JVM primitives to implement the whole application behavior. I still need to use the object-oriented building blocks to create the components of the application, but I can also use Kubernetes primitives for some of the application behavior.

![](https://4.bp.blogspot.com/-xciSRgcbIrk/WPtATkEqFMI/AAAAAAAAIIs/m4oRt7DF6L4mCiXY_S1ksz0SuuS3zNRSACLcB/s400/Screen%2BShot%2B2017-04-22%2Bat%2B12.35.18.png)

For example, now I strive to organize the units of application behavior into independent container images, which become the main building blocks. That allows me to use a new, richer set of constructs provided by Kubernetes to implement the application behavior. For example, now I don't rely only on an implementation of ExecutorService to run some service periodically, but I can also use Kubernetes' CronJob primitive to run my container periodically. The Kubernetes CronJob will provide similar temporal behavior, but use higher level constructs and rely on the scheduler to do dynamic placement, performing health checks, and shutting down the container when the Job is done. All that ends up in a more resilient execution with better resource utilization as a bonus. If I want to perform some application initialization logic, I could use the object constructor, but I could also use init-container in Kubernetes to carry out the initialization at a higher level.

### The Distributed Mental Model

Having in-process primitives, in the form of object-oriented concepts and the JVM features, combined with distributed out-of-process primitives, provided by Kubernetes, gives developers a richer set of tools to create better applications. When building a distributed application, my mental model is no longer limited to a JVM, but spreads across a couple of nodes with multiple JVMs running in coordination.

![](https://1.bp.blogspot.com/-lhxJZ0ovg68/WPtCaWv8WnI/AAAAAAAAIJA/OeUzIOfhfLw09P-J3c6qc5LsIVdDY47LQCLcB/s400/Screen%2BShot%2B2017-04-22%2Bat%2B12.44.59.png)

The in-process primitives and the distributed primitives have commonalities, but they are not directly comparable and replaceable. They operate at different abstraction levels and have different preconditions and guarantees. Some primitives are supposed to be used together. For example, we still have to use classes to create objects and put them into container images. But some other primitives such as CronJob in Kubernetes can replace the ExecutorService behavior in Java completely. Here are few concepts that I've found commonalities for between the JVM and Kubernetes, but don't take that any further.

![](https://4.bp.blogspot.com/-nOkx2k1qr2M/WPX1xI_jjlI/AAAAAAAAIHk/HKdxzxhP88MKw7JLvDwFl9v_l7R06u19gCLcB/s400/Screen%2BShot%2B2017-04-18%2Bat%2B12.16.52.png)

With time, new primitives give birth to new ways of solving problems, and some of these repetitive solutions become patterns. Check out my in-progress

[Kubernetes Patterns](http://leanpub.com/k8spatterns/)

book for this line of thinking.

[Download Modern Java EE Design Patterns](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035): Building Scalable Architecture for Sustainable Enterprise Development. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035).
