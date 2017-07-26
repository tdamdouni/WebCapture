# Hexagonal Architecture Is Powerful

_Captured: 2017-02-15 at 19:46 from [dzone.com](https://dzone.com/articles/hexagonal-architecture-is-powerful?edition=269881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-15)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

Continuing [our journey](https://dzone.com/articles/layered-architecture-is-good) through various architectural styles, we're now headed for Hexagonal Architecture, also known as Ports and Adapters.

## What Is Hexagonal Architecture?

[Hexagonal Architecture](http://alistair.cockburn.us/Hexagonal+architecture) is an architectural style that moves a programmer's focus from conceptual layers to a distinction between the software's _inside _and _outside _parts. The _inside _part consists of what we would call application and domain layers in a [Layered Architecture](https://dzone.com/articles/layered-architecture-is-good) - its use cases and the domain model it's built upon. The outside part consists of everything else - UI, database, messaging, and other stuff. The connection between the _inside _and the _outside _part of our application is realized via abstractions called _ports_ and their implementation counterparts called _adapters_. For this reason, this architectural style is often called Ports and Adapters. The metaphor of a hexagon comes from the discreteness of the ports - each one is distinct and there will be a few of them, and for the visualization purpose - to avoid one-dimensional thinking about the architecture (remember that in Layered Architecture all dependencies go in one direction, right?).

![](http://tidyjava.com/wp-content/uploads/2017/02/2301.gif)

Similarly as in Layered Architecture, there are some principles to be followed:

  1. The _inside _part knows nothing about the outside part.
  2. You should be able to use any _adapter_ that fits a given _port._
  3. No use case or domain logic goes to the _outside_ part.

## The Essence of Hexagonal Architecture

I see two important concepts that really make Hexagonal Architecture distinct and lead to its power: separating the core of your application and thinking in terms of _ports_ and _adapters_.

By separating the core, I mean making the use case and domain logic free of any _outside _dependencies. We're putting the application behavior and business rules in terms of abstract _ports_, making our application logic agnostic to the delivery model. Thanks to this, the most crucial logic of our application is pure and clean and can be understood without the clutter of different technologies used to make it work in the production environment. We can also test this "most crucial logic" without spinning up all those technologies.

The second important concept is thinking in terms of _ports _and _adapters_. In Layered Architecture, there is a significant distinction between the presentation part and the infrastructure part. The latter is "so important" that we allow the application and domain logic to depend directly on it. In Hexagonal Architecture this distinction is non-existent - both presentation and the infrastructure are just the _outside_. We simply provide abstract _ports _and implement _adapters _to them, regardless of the type of actor the _inside _is communicating with. This means we can swap out the UI, the same way we swap out the database. We can easily swap out both for the testing purposes and there won't be any significant implementation differences.

We should also note here that Hexagonal Architecture does not make any assumptions when it comes to code organization and, similarly to Layered Architecture, it does not tell us much about system's design itself.

## Implementing Hexagonal Architecture

I don't know if I described the concept of _ports_ and _adapters_ simply, but it actually is so. As most of you probably guessed or knew already, the natural counterpart of a _port _in Java is an interface and the _adapter _is the one described in the [GoF book](http://amzn.to/2kzxfcv).

### Basic Example

Let's start small. [Imagine we're implementing a console Tic-Tac-Toe game](https://dzone.com/articles/java-code-challenge-tic-tac-toe) and we want to ask the player for his next move. We could, of course, bash a Scanner somewhere and read it directly, but that would not be very testable. We would also have problems to swap out the human player with a computer - should we make the computer write to standard input? The Hexagonal approach would be to create a _port_ for the communication with the player, as the input handling is the part of the _outside_ and should not be mixed with our Tic-Tac-Toe _inside _logic:

Then, we would create an _adapter _to this _port_ that actually does the job:

Now that we understand the basics, we can move to implementing something more serious. Once again, we will take a look at the [Spring Pet Clinic](https://github.com/spring-projects/spring-petclinic) project and try to apply the newly learned architectural principles.

Look at the current packages and classes and try to identify what's the _inside _and what's the _outside_:

![Image title](http://tidyjava.com/wp-content/uploads/2017/02/ss2017-02-12at05.21.58.png)

Obviously, the controllers and config classes are parts of the _outside_. Domain classes like Owner or Pet will be parts of the _inside_. The repositories are interfaces, which fits our idea of a _port_, but they can contain dependencies on Spring and use a query language in @Query annotations. This leads to an interesting question…

### Are Spring, JPA, and Others Part of the _Outside_?

I believe you can answer this question both ways and still consider your architecture Hexagonal. As we already said, by hiding certain technical details behind a _port, _we remove some clutter from our use case/domain logic and gain more flexibility as the _port _can have multiple _adapter _implementations. The more appropriate questions are then:

  * Does it clutter your business code too much?
  * Do you want to have a flexibility of swapping stuff at the cost of adding extra indirections and thus complexity?

This seems like a black and white problem, but there are some shades of gray in there actually. One could e.g. accept annotations as a necessary evil but refuse to use framework's utility classes directly and expose a port for each of them. The final choice is yours, no strong rules here (at least in my world).

### Back to the Clinic

Let's assume that we ignore framework dependencies for a moment and try to deal with the rest. The first step would be to separate the _outside_ classes from the _inside _classes in the current structure:

![Image title](http://tidyjava.com/wp-content/uploads/2017/02/ss2017-02-12at06.15.08.png)

As you can see, we just had to create a presentation layer, same as we did in the Layered Architecture article.

The second step towards more a Hexagonal Architecture would be to get the use case logic out of the controllers. Let's do it for one of the use cases - scheduling a visit:

From this method, we can derive that the application presents the owner page if Visit data is valid and prompts the user to correct the data otherwise. Let's create a _port _that handles the UI in these cases:

With this port in place, we can abstract specific view details out of our use case logic:
    
    
        public void scheduleNewVisit(Visit visit, BindingResult result, UserInterfacePort userInterfacePort) {

The last step would be to create an _adapter_ and use it in our controller:

It's easy to see how powerful the application service is and how stupid the controller is in the Hexagonal approach. We could literally implement that part of Pet Clinic to work in the console while saving the visits to a text file -- and the service logic would remain untouched (as long as we keep using Spring). On the other hand, it's even easier to see that we replaced a single small method in a single class with five methods in four classes.

## Benefits of a Hexagonal Architecture

  * **Easy to learn **- it's just _ports _and _adapters _baby.
  * **Application and domain purity **- the most important code in your application is not cluttered by technical details.
  * **Flexibility **- you can swap out _adapters_ easily.
  * **Testability **- you can provide test replacements for the _outside _dependencies without using extra mocking tools.

## Drawbacks of a Hexagonal Architecture

  * **Heaviness **- it's a lot of extra classes, especially when you have only one UI and one database to support.
  * **Indirections **- you need to search for _port's _implementations and be aware of your system's state to follow the flow of control.
  * **Confusing to apply with frameworks **- as we've seen, it's not always clear what you should consider the _outside._
  * **No code organization guidelines **- you need to keep things tidy by yourself; it's just _ports _and _adapters _baby.

## When to Apply Hexagonal Architecture?

I've got mixed feelings for the Hexagonal Architecture. That's because the benefits it builds upon do not require an all-in approach:

  * **Purity **- most applications that I work with use request/response communication, which means no UI clutter and I'm free from other details by using patterns like Repository or Gateway.
  * **Flexibility** - you can create interfaces **when you really need** to swap something out.
  * **Testability **- with new frameworks, the concept of swapping something out for test purposes is less relevant than in the past. Also, I'm usually fine with using mocking tools for test doubles.

At the same time, I totally agree that we should strive to keep our business logic clutter-free and we should keep things as testable as possible. Therefore, use common sense to evaluate your situation. In general, I think that this might be more of a problem with monoliths that I'm happy not to work with right now.

## Summary

To sum things up, Hexagonal Architecture is an approach that divides our software into an _inside _and an _outside _part. The former contains use case and domain logic, while the latter contains technical stuff like UI, databases and messaging. The two parts are connected using _ports, _exposed by the _inside_, and _adapters_, implemented by the _outside_. By applying this approach, we make our most important code free of unnecessary technical details and we gain flexibility and testability. Since going "full hexagonal" is not required to get the benefits it provides, I'd be skeptical to do that and instead apply interfaces and patterns selectively.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).
