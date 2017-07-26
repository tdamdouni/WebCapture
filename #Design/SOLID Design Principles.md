# SOLID Design Principles

_Captured: 2015-10-14 at 23:18 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/solid-design-principles)_

## SOLID Software Engineering Principles

In the previous lesson, you learned that successful systems contain modules which have the following three characteristics:

  1. **Low Coupling** \-- modules should be minimally dependent on each other and communicate using specified interfaces
  2. **High Cohesion** \-- modules should be focused completely on achieving the overall goal
  3. **High Encapsulation** \-- modules shouldn't reveal their implementation details to anyone else (and shouldn't need to)

While these characteristics guide our overall thinking, specifically implementing them in software modules has led to 5 key engineering principles. These principles, originally compiled by Robert C Martin in the 1990's, are best known by their acronym SOLID.

They are:

  1. **Single Responsibility Principle (SRP)** \-- modules should only exist to serve one purpose and may only change if that purpose is modified
  2. **Open/Closed Principle (OCP)** \-- modules should be open for extension but closed to modification
  3. **Liskov Substitution Principle (LSP)** \-- modules that inherit from a parent should not alter any of that parent's functionality
  4. **Interface Segregation Principle (ISP)** \-- each different user of a module should get to access it via a specialized interface that only requires them to supply the minimal amount of information.
  5. **Dependency Inversion Principle (DIP)** \-- Higher level modules should dictate the implementation details of lower level modules, not the other way around.

In this lesson, we'll show you through the use of examples how each of these principles is applied to modular software design.

### Our Examples

We haven't gotten into code yet so some of the specific terminology wouldn't make much sense to you (for instance, the official definitions talk about "classes" not modules). Because of that, we'll explain each of the principles using real-world examples based on the idea of modularity we covered in the previous lessons.

The first is a concrete example of a power drill. It's the kind of thing that typically lends itself well to illustrating the ideas behind the principles but it isn't always as easy to see how that analogy relates to software.

The other example we'll use extends the birthday party from before. Specifically, we'll think about the bakery that produces the cakes. The reason this is particularly helpful is because software more closely resembles the kinds of interactions you see around performing services than the use of power tools. As we've said before, the components of a software system can really be thought of as individual services interacting with each other, just like when people interact in the real world.

### 1\. Single Responsibility Principle, aka "Do Just One Thing Well"

![SRP Swiss Army Knife](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/srp_knife.jpg)

> _SRP Swiss Army Knife_

_Source: [Zero Turnaround](http://zeroturnaround.com/rebellabs/object-oriented-design-principles-and-the-5-ways-of-creating-solid-applications/)_

The Single Responsibility Principle states that:

> There should never be more than one reason for a [module] to change

That means that each of your modules should only serve one greater purpose and the only reason for them to change is if that greater purpose changes. It doesn't mean they need to stick to just one task or contain only one component, but these tasks or components all need to cohesively relate to the greater purpose of the module.

This is very helpful in software because it prevents your system components from becoming all-knowing all-powerful god modules which are way too big to fully understand or fix if broken or ever do without. Stick to the Single Responsibility Principle and you'll have a maintainable, fixable, extendable and cleaner code. The same applies to the "real world"...

#### SRP with the Drill

A power drill can be thought of as a system made up of modular components or as the module itself. In either case, the module(s) should have just a single responsibility.

If the user of the drill was a drill mechanic, it would make sense to treat the drill as a larger system where each separate part was a different module. You'd want to know that the components each performed only a single task so you could easily identify which part was broken and replace it. If you had to replace the gearbox and battery in order to fix a simple broken trigger, there's something wrong with the design.

If the user of the drill is your average homeowner, there's no reason to know anything specific about the sub-components of the drill so the drill itself becomes the module. You only care if the drill does its drilling well. It's probably a waste of cost and effort if the drill also tells time and has a flashlight on the end.

#### SRP with the Bakery

We'll treat the bakery as a module. When you go down to the bakery to order your birthday cake, you want to make sure your baker is specialized at making cakes. It's okay if he's taking night classes, but if he's also a lawyer and construction worker on the side then you should probably find someone who's got more time to devote to the act of baking cakes to make sure the job is done right.

### Open/Closed Principle, aka "Allow for Interchangeable Parts"

![Open-closed principle brain surgery](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/ocp_brain.jpg)

> _Open-closed principle brain surgery_

_Source: [DevIQ](http://deviq.com/open-closed-principle)_

The Open/Closed principle means that you should be able to extend the functionality of the module without having to go digging into its guts. Formally said:

> The [module] is open for extension but closed to modification.

Because you'll constantly get new requirements added onto existing code, you'll want to make sure your systems can be extended to meet the new requirements but without forcing you to go in and rework the details of the existing system.

#### OCP with the Drill

A typical drill has a series of interchangeable drill bits. To put on a new bit as the end user, you just need to plug it into the drill head and you're good to go. Thus it is open to extension. Because you don't need to take apart the drill to do so (and can't without much effort), it is also closed to modification.

#### OCP with the Bakery

The bakery example more closely resembles software systems. The bakery normally just produces birthday cakes by employing a single BirthdayCakeChef using a standard kitchen.

Let's say you also need to buy a wedding cake. The bakery owner decides to hire a WeddingCakeChef who can make wedding cakes using his existing infrastructure. The bakery just extended its capabilities! Because the owner uses a standard kitchen that doesn't need to be modified to handle the new chef, the bakery is also "closed to modification".

If the bakery had to add a new production line and machinery to their kitchen in order to handle the WeddingCakeChef, it would be open to extension but not closed to modification because the new client-facing service would require them to change their core infrastructure. As the bakery owner (and any clients waiting for new cakes), you would prefer to be able to extend your bakery's functionality without needing to rebuild the kitchen each time!

### Liskov Substitution Principle, aka "Be What They Expect You to Be"

![Liskov ducks](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/lsp_duck.jpg)

> _Liskov ducks_

_Source: [Zero Turnaround](http://zeroturnaround.com/rebellabs/object-oriented-design-principles-and-the-5-ways-of-creating-solid-applications/)_

Liskov Substitution states that a module which inherits the characteristics of a parent module should not only display all the behavior of its parent but also stay true to the parent's intended purpose.

In software, LSP violations can be difficult to debug so it's always good to make sure children who inherit from their parents don't lose or alter any of the functionality of those parents. Practically speaking, this means you really need to understand all the functionality of a particular module before making it the parent of another module.

#### LSP with the Drill

Let's say you buy a high end drill from the same manufacturer as your previous drill. This new drill has a higher torque setting so you can use it with a sanding attachment. You would expect the drill to otherwise operate with at least the same level of functionality as the base model, right?

If you took your fancy new drill and tried to use it to make a hole in the wall but it only spun in the reverse direction with the high torque setting enabled, that would be a Liskov Substitution violation. It walked like a drill, talked like a drill, but turned out not to be a drill when you needed it!

The engineers may have reasonably assumed that you wouldn't try to use it like a drill with the high torque setting enabled but that's not a safe assumption.

#### LSP with the Bakery

Let's say Joe, the owner of "Joe's Cake Shop" opened up a giant "Joe's Cakes-and-More Shop" in the next town over.

Let's also say that your child wanted a chocolate cake with vanilla frosting that he saw on the menu of the original Joe's Cake Shop. You are busy one day and come home from work a different way, passing by the new "Joe's Cake and More Shop". You walk in and ask to order a chocolate cake with vanilla frosting but the manager tells you they don't allow you to specify the frosting flavor. Huh!?

Because you expect that the bakery with more functionality will at least have the same characteristics as the old one, that is a Liskov Substitution violation.

In this case, it may have seemed reasonable for Joe to test out a slightly different menu at the new location but it resulted in a very unhappy customer.

### Interface Segregation Principle, aka "Don't Make Me Specify Things I Don't Care About"

![ISP cords](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/isp_cords.jpg)

> _ISP cords_

_Source: [DevIQ](http://deviq.com/interface-segregation-principle)_

The Interface Segregation Principle states that you shouldn't force the user to depend on interface members that she doesn't need to use. This is a very similar idea to the Single Responsibility Principle but instead of applying to the module itself, it applies to the interface of the module. A more casual way to put it might be "Don't make me specify options that have nothing to do with what I care about".

In a practical sense, it means that, even if your module is capable of producing different results for different users based on lots of potential inputs, each user should receive a separate interface that removes all the extra crap they don't need. This creates a much more cohesive interface and also minimizes coupling between modules based on completely irrelevant items.

#### ISP with the Drill

What if the drill had a switch for determining whether you were using the American 120v or European 230v outlet power? You might accidentally set it to the wrong thing and blow up your drill! Hairdryers frequently had this feature and it resulted in plenty of meltdowns.

This violates the Interface Segregation Principle -- even though the internals of the drill might contain both the option for 120v or 230v based on some little internal widget, consumers really shouldn't have to access that interface to use the drill. The drills sold in the USA should already have the 120v mode set by default and the European drills should have the 230v mode in action so you don't need to make a choice.

#### ISP with the Bakery

If you go to Joe's Cake Shop to order your birthday cake and Joe asks you at the counter how many layers you want, whether you would like the little bride and groom figurine on top, and what color of flowers to put around the outside, you'd probably be annoyed at the waste of time. When you order off the birthday cake menu, you don't want to have to specify the wedding cake options even though the bakery needs to make some assumptions about those options to produce your birthday cake.

This may seem impractical in person but happens all the time with online ordering systems -- developers put every possible option in the form whether or not it has anything to do with what you're trying to order. Instead, customers going through the wedding cake ordering process should be shown just the options that matter.

This is good user-centered design and also good software design.

### Dependency Inversion Principle, aka "I Don't Care How, Just Give Me What I Want"

![DIP outlet](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/dip_socket.jpg)

> _DIP outlet_

_Source: [DevIQ](http://deviq.com/dependency-inversion-principle)_

The Dependency Inversion Principle is all about reversing how you think about the way your modules interact with each other. It states that the implementation details of your system should depend on the system's interface with the outside and not the other way around.

If you've been following user-centered design principles when designing websites, this idea should make sense -- it's basically "I don't care how you work, just give me what I want".

More generally:

> High level modules should not depend upon low-level modules, they should depend upon abstractions. Also, abstractions should not depend on details -- details should depend on abstractions.

Practically speaking, it means we should isolate our module behind an interface and let other modules communicate only with that interface instead of directly with our module. That way, the other modules wouldn't know the difference if we completely change the details of how one of them works.

A common real-world example is with light sockets -- you use the interface of the socket to plug a lamp into the electrical system of your house. The lamp doesn't care how the wiring is done or if you're going to rebuild the system, and that's precisely because it uses the interface instead of plugging directly into the wiring in the walls.

This should further illustrate the power of thinking in terms of interfaces between modules to abstract away the implementation details of those modules.

In software, this means that your code will be much safer to change and less tightly coupled together.

#### DIP and the Drill

Drills already use this principle well -- the drill bit interface is typically standardized. Even if the manufacturer replaces the drill guts, you don't care because it will still use all the same bits it always did.

The reverse is also true -- if users were trying to constantly drill through very difficult materials, the company might be forced to send more torque to the bit through a motor upgrade. The user drives changes in the implementation details, not the other way around.

#### DIP and the Bakery

If Joe the bakery owner decides to rebuild his kitchen, it might make sense from his perspective to change around the menu, including perhaps removing some items. He really shouldn't do that because it violates the Dependency Inversion Principle -- his interface with you shouldn't change just because his implementation (the kitchen) is different. You should still be able to order the same birthday cake.

From the opposite perspective, though, if you wanted to pay for gluten-free cakes, he might need to change his production process to accommodate you. In baking and in software, the customer is always right.

### Wrapping Up

In this lesson, we learned how to apply the 3 characteristics of good system modules through the use of the 5 SOLID design principles. It was a lot to chew on so it's fine if you didn't absorb the details of it. The main takeaways are simply:

  * You **don't** want your modules to be tightly coupled together or it defeats the purpose of having them.
  * You **do** want your modules to be highly cohesive so they are all working efficiently towards the same goal.
  * You **do** want to keep your modules as encapsulated as possible so no one else knows (or needs to know) about their implementation details.
  * The SOLID design principles essentially represent tests as to whether you are properly implementing those 3 characteristics.

If you've absorbed that much, then you've got enough to chew on. By the time we get deeper into this during our Object-Oriented Design lessons in the Ruby section of the Intensive Program, you'll be ready for more. For now, this represents the end of your formal engineering training! We'll wrap things up over the next few lessons and then get into some coding.

###  Next Lesson: Pseudocoding Modular Design 

[ Onward! ](http://www.vikingcodeschool.com/software-engineering-basics/pseudocoding-modular-design) [ or go to previous lesson... ](http://www.vikingcodeschool.com/software-engineering-basics/characteristics-of-good-systems)
