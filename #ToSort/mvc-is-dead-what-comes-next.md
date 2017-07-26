# MVC Is Dead, What Comes Next?

_Captured: 2017-05-08 at 11:15 from [dzone.com](https://dzone.com/articles/mvc-is-dead-what-comes-next?oid=twitter&utm_content=buffer1155a&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190137&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190137&u=https%3A%2F%2Fwww.wakanda.io%2F).

[React.js](https://facebook.github.io/react/), [Elm](http://elm-lang.org/), [Cycle.js](https://cycle.js.org/), and other UI frameworks introduced a new way of building user interfaces. By applying principles from functional reactive programming to UI development, they even changed how we think about user interfaces. In no time, these approaches have simply smashed the seemingly inevitable dominance of MVC and its siblings (MVP, MVVM etc.). This article, which is the first in a series, will give a brief introduction into this new way of building UIs and list some of the advantages it has over traditional approaches. These factors are so strong, that in my opinion there is a good chance that we are right now witnessing the end of the MVC-era.

##### ![Graph showing the cyclic dependency between DOM Driver, ActionCreator, Updater, and View\(\)](http://blog.netopyr.com/wp-content/uploads/frp_cycle-2.jpg)

> _Concept of functional reactive UI development_

On the face of it, frameworks like React.js with the [Redux-architecture](https://github.com/reactjs/redux), Elm, and Cycle.js seem quite different. Redux applications initially appear to be similar to regular JavaScript application, perhaps with a strong focus on functional programming. Elm-applications come with their own language, while Cycle.js applications consist of reactive streams only which are knotted together in astonishing ways.

> But under the hood, all of these frameworks have something in common: the essence of functional reactive UI development.

The picture above shows a rough overview of the concepts, which are shared between pretty much all modern UI frameworks that foster reactive programming. The first thing to note is that everything - all changes, events, and updates - flow in a single direction to form a cycle. This article will give just a brief explanation of the cycle, while later articles will go into more details.

## Functional Reactive UI-development

The cycle consists of four data-structures (State, Virtual DOM, Event, and Action) and four components (View()-Function, DOM-Driver, ActionCreator, and Updater). The DOM-Driver is provided by the framework, while the other components have to be implemented by the application developer.

Let's assume our application, a todo-list, is already running for a while and the user presses a button to create a new entry in the todo-list. This will result in a button-clicked event in the DOM, which is captured by the DOM-Driver and forwarded to one of our ActionCreators.

The ActionCreator takes the DOM-event and maps it to an action. Actions are an implementation of the Command Pattern, i.e. they describe what should be done, but do not modify anything themselves. In our example, we create an AddToDoItemAction and pass it to the Updater.

The Updater contains the application logic. It keeps a reference to the current state of the application. Every time it receives an action from one of the ActionCreators, it generates the new state. In our example, if the current state contains three todo-items and we receive the AddToDoItemAction, the Updater will create a new state that contains the existing todo-items plus a new one.

The state is passed to the View()-Function, which creates the so-called Virtual DOM. As the name suggests, the Virtual DOM is not the real DOM, but it is a data-structure that describes how the DOM should look like. The code snippet above shows an example of a Virtual DOM for a simple <div>. A later article will explain the Virtual DOM and its advantages in detail.

The Virtual DOM is passed to the DOM-Driver which will update the DOM and wait for the next user input. With this, the cycle ends.

## Advantages

Functional reactive UI Development has three major advantages over traditional approaches, all of them are huge: straightforward testing, a comprehensive flow of events, and time travels (yes, seriously).

### Straightforward testing

The View()-Function and the ActionCreators are simple mappings, while the Updater performs a fold (also often called a reduce) on the Actions it receives.

> All components are pure functions and pure functions are extremely easy to test.

The outcome of a pure function depends only on the input parameters and they do not have any side effects. To test a pure function, it is sufficient to create the input parameter, run the "function under test" and compare the outcome. No mockups, no dependency injection, no complex setup, and no other techniques are necessary that take the fun out of testing.

### Comprehensive Flow of Events

Reactive programming is a lot of fun - except when it is not. The control flow of graphical user interfaces is inherently event-based. An application has to react to button-clicks, keyboard input, and other events from users or servers. Applying reactive techniques, be it the Observer Pattern, data-bindings, or reactive streams, comes naturally.

Unfortunately, these techniques come with a price. If a component A calls a component B, it is simple to see the connection in your IDE or debugger. But if both components are connected via events, the relationship is not as obvious. The larger the application becomes, the harder it gets to understand its internals.

The architecture of a functional reactive application avoids these problems by defining a simple flow of events that all components must follow.

> No matter how large your application grows, the flow of events will never change.

### Time Travel

Functional reactive applications allow you to travel back and forth in time - at least in the context of your application. If we store the initial state and all actions, we can use a technique called "Event Sourcing". By replaying the actions, we can recalculate every state the application was in. If we replay only the last n-1, n-2, n-3… actions, we can actually step back in time. And by modifying the recorded stream of actions while applying them, we can even change the past. As you can imagine this can be very handy during development and bugfixing.

> The first [time-traveling debuggers](https://github.com/calesce/redux-slider-monitor) have been built, but I think we have only started to understand the possibilities, and more [amazing tools](https://github.com/gaearon/redux-devtools) will be released in the future.

## Summary

So far we have only touched the surface of functional reactive UI development, but by now it should be clear that this approach has some tremendous advantages. Future articles will go deeper into the technical details, but also show the disadvantages (or let's call them "yet-to-solve-challenges"), and show an example how the lessons learned can be applied to JavaFX applications.

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190138&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190138&u=https%3A%2F%2Fwww.wakanda.io%2F).

### Like This Article? Read More From DZone

Topics:

development ,dom ,functional ,reactive ,ui ,application ,programming ,mvc
