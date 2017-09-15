# How to Achieve High Velocity in Software Development

_Captured: 2017-08-24 at 23:52 from [dzone.com](https://dzone.com/articles/how-to-achieve-high-velocity-in-software-developme?edition=317404&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-20)_

### Learn why coupling is a problem in software development, and how to reduce it in the architecture for higher velocity in development.

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

How do you achieve high velocity in software development? The main challenge to high velocity is tight coupling. [Coupling](https://en.wikipedia.org/wiki/Coupling_\(computer_programming\)) is the degree of interdependence between software modules, or a measure of how closely connected two routines or modules are, or the strength of the relationships between modules. Let's break down exactly what coupling is, the problems with tightly coupled software, and how to reduce coupling.

## What Is Tight Coupling

According to John Lakos in [Large Scale C++ Software Design](https://www.amazon.com/Large-Scale-Software-Design-John-Lakos/dp/0201633620), there are two types of coupling: logical and physical. Physical coupling is putting classes, structs, etc. in the same component or creating dependencies from one component to another. Logical coupling is when types (classes, structs, etc.) that are used in one component are supplied by another component. Tight coupling is when a group of component or modules are highly dependent on one another.

![tight coupling](http://lattix.com/files/images/products/tightly_coupled.png)

Often, this happens when components assume too many responsibilities. Large files are sometimes a quick way to find tightly coupled components.

## Problems With Tightly Coupled Systems

Tight coupling is a challenge when you want to make changes to a software system. Coupling causes a ripple effect - like circles in a still pond.

![coupling ripple effect](http://lattix.com/files/images/products/345x193xwater_splash_sm.jpg.pagespeed.ic.74z8Zf1Gxq@2x.webp)

You make a small change and suddenly twenty other seemingly unrelated things need to be changed as well. While zero coupling is impossible, what level of coupling is right? The answer, according to Jeppe Cramon in his slideshare presentation "[The Why, What, and How of Microservices](https://www.slideshare.net/INPAY/the-why-what-and-how-of-microservices)," highly depends on how likely the component/system/service is to change and what components need to change together because of the design.

Maintainability suffers in tightly coupled systems. One example from "Large Scale C++ Software Design" is creating interfaces that only contain primitive functionality. If you need non-primitive functionality, it should be put into a separate class or operator without private access.

Blithe Rocher, in her talk "[Avoiding testing headaches with tightly coupled services](https://www.oreilly.com/learning/avoid-testing-headaches-with-tightly-coupled-services)," discusses how tightly coupled services are the most common mistake she sees in microservices. When services are tightly coupled they produce headaches all the way down the deployment stack. In production, if one service goes down, both (or all) services go down. In development, both services need to be running to develop either one. If one service is broken, you can't work on the other service even if another team is responsible for that service. This adds to development time and makes working in the development environment harder. All of this results in a higher learning curve for new engineers to a project because a great deal of time is spent learning the development environment.

In automated testing, tight coupling means more tests need to be created and the environment needs to be set up for all the coupled services. Blithe's advice is to not build tightly coupled services. A loosely coupled service or component can be developed, put into production, and tested independently of other services or components.

In the Harvard Business School paper "[Exploring the Relationship between Architecture Coupling and Software Vulnerabilities: A Google Chrome Case](http://www.hbs.edu/faculty/Publication%20Files/17-078_caaa9a9c-74ac-4eff-b68e-7090ed06cb81.pdf)," the authors make the case that there is a strong relationship between security vulnerabilities and architecture coupling metrics. Coupling affects quality, productivity, maintenance costs, and security vulnerabilities. In the Google Chrome codebase, component metrics and coupling metrics were significantly correlated with vulnerabilities.

## How to Reduce Coupling

Interfaces are a way to reduce tightly coupled components. By communicating through interfaces you break the dependency and any component can be on the other end of that communication. Steve McConnell, in [Code Complete](https://www.amazon.com/Code-Complete-Practical-Handbook-Construction/dp/0735619670), has these guidelines:

  * Minimize accessibility of classes and members.
  * Avoid friend classes, because they are tightly coupled.
  * Make data private rather than protected in a base class to make derived classes less tightly coupled to the base class.
  * Avoid exposing member data in a class's public interface.
  * Be wary of semantic violations of encapsulation.

Finally, John Lakos states that you should keep both physical and logical coupling to a minimum. As an example, minimize the use of external types in an interface. This will make the component easier to use and to maintain.

## Conclusion

Coupling is a measure of the dependencies between components. Tight coupling affects development velocity, quality, maintenance costs, and security.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).
