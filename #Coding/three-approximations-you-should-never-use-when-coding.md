# Three Approximations You Should Never Use When Coding

_Captured: 2017-08-09 at 18:22 from [dzone.com](https://dzone.com/articles/the-three-approximations-you-should-never-use-when?edition=310393&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-21)_

The path travelled by the software industry since its inception and the accomplishments in scale and scope are simply astonishing: from creating a network the size of the planet, indexing the world's information, connecting billions of people, to driving a car or flying an aircraft, or even an application such as Excel which enables [500M people to program a computer](https://www.infoq.com/presentations/panel-languages-future)… Turing would be amazed at what can be done with computers today and how many people use one every day, if not every minute.

In this context, innovations in software engineering have been running amok, from operating systems, runtimes, programming languages, frameworks, to methodologies, infrastructure, and operations.

However, even though "the software industry has been very successful," [Ivar Jacobson and Roly Stimson](https://www.infoq.com/articles/escape-method-prson) report that "under the surface, everything is not as beautiful: too many failed endeavors, quality in all areas is generally too low, costs are too high, speed is too low, etc."

In particular, the evolution of programming paradigms has been slow, and we should not be afraid to say that it is currently holding back our industry. The emergence of modern languages such as Java and C#, their success, but also their unhealthy competition, have created a conceptual molasse that generations upon generations of developers cannot seem to escape. Even modern languages such as JavaScript are expected to align to their antiquated conceptual foundations from OOP to MVC.

Our goal in this article is to kick start an open discussion on the evolution of programming paradigms and offer a contribution founded on, perhaps, the most robust theory in Computer Science: [TLA+](http://lamport.azurewebsites.net/tla/tla.html).

The paper is divided into three sections:

  * Computation and State Machines.

  * An Advanced State Machine Model.

  * A New Programming Model.

If you have not read [this article](https://www.microsoft.com/en-us/research/publication/computation-state-machines/) which provides an introduction to TLA+ from its author, Dr. Leslie Lamport, please do. Anything we could write in comparison is just scribbles.

## Computing Is About State Machines

In [his book](http://lamport.azurewebsites.net/tla/hyperbook.html), Dr. Lamport uses [the Die Hard problem](http://www.math.tamu.edu/~dallen/hollywood/diehard/diehard.htm) to illustrate why "State Machines Provide a Framework for much of Computer Science."

> In the movie Die Hard 3, the heroes, John McClain (Bruce Willis) and Zeus (Samuel L. Jackson), must make exactly four gallons from five and three gallon jugs to prevent a bomb from exploding. 

We have represented in Fig.1 the graph of possible states and actions that Dr. Lamport uses in his example. The state labels are encoded as follows: [jug_size][full,empty,partial][jug_size][full,empty,partial].

**![](https://lh5.googleusercontent.com/Plh8DMqyMsZsUdcQhkF398aOfRJeU0qeDe-JvDuj5R-8Q9kt7zH62QDTI9PgGsSeTcTn5o7Ei6mIn1eXVJyuHdssvbJluAaQz3NuxB44YyROKUaDonrZEwqKcEG5SXYbRab6oA8PDLB2t5fJTA)**

> _Fig. 1 - The state machine of the Die-Hard Problem and its solution (path in green)_

The solution to the problem can be found by traveling a specific path.

[Dr. Lamport explains](https://www.microsoft.com/en-us/research/publication/computation-state-machines/) that "a computation is a sequence of steps, called a behavior," and there are three common choices for what a "step" is, leading to three different kinds of behaviors:

Action Behavior

A step is an action, an action behavior is a sequence of actions.

State Behavior

A step is a pair <Si, Si+1> of states, a state behavior is a sequence

s1 -> s2 -> s3 -> * * * of states.

  


State-Action Behavior

A step is a triple < Si, α, Si+1 > where S are states and α an action

From the state machine from Fig. 1, we can define an "action behavior" as a series of actions:

  1. Fill Big.

  2. Fill Small from Big.

  3. Empty Small.

  4. Fill small from Big.

  5. Fill Big.

  6. Fill Small from Big.

Incidentally, we just created a new "programming language" based on the "Die-Hard" state machine. We don't expect it will become popular anytime soon, but in essence, that is how action-based programming languages are created: there is an underlying state machine from which actions are derived, which then can be composed any way we wish without paying much attention to the underlying state machine. Programming languages are "action based" since the vast majority of "states" in our programs are irrelevant.

Let's go the other way and derive the underlying state machine from a code snippet, for instance, the factorial function (From Dr. Lamport's article):
    
    
        return (n == 1) ? 1 : n * fact(n-1); 
    
    
        var f = 1, i =1 ; 
    
    
        for (i = 1; i <= n; ++i) { f = i * f; } 

We can infer a representation of the corresponding (classical) state machine for each function:

**![](https://lh5.googleusercontent.com/j06h2sGYbBYaj8JkZKF6ykB8N8_0xvP6xX-9DhZAxwlfUOTJ0J1qOBjJL7ILz82At9zfYdCOe_HzZ86ZN6a1_UumCx6Y_vdOro7Y9Lm_gu_25Z8loo_xVp3m5xFGq_4WKInhcT5G2BlnKcUzNg)**

> _Fig. 2a - The State Machine of the Factorial Function_

The behavior of the State Machine is straightforward, we initialize it with the values of i (input) and f (output) and the state machine will transition to the computing "state" until i is equal to 1, at that point f contains the expected result.

The same could be done for the recursive version. You will notice that the memory requirements are different as the state machine needs to be designed to keep at least one intermediate value (fi-1). You may also decide to keep all intermediate values to speed up future computation.

**![](https://lh3.googleusercontent.com/xXiIrGGbRDdNb0PJa47WPa0xawqzyQh2fO3sTPy3siDc2lWQvajgqH_ARaKcyRcwJCxsOlrQlNGZIeGrT_xmnrAOmre3jhafkUDm3lgV3YV6vfAVEtB4VGaY1QVwYoYsNxJp-9v_D0X_hESn5w)**

> _Fig. 2a - The State Machine of the Factorial Function (Recursive)_

In this first section, we have demonstrated that [state machines can compute](http://www.ebpml.org/blog15/2015/01/tla-the-die-hard-problem/) and conversely (action-based) computations can be represented as state machines, but for the most part, states of the state machine are redundant, merely the shadow of actions. In the factorial functions, the (control) states (computing, done, error) would not add any clarity to the implementation. That is why for the vast majority of programs we never bother making the states explicit, and there is no argument there.

## A New Kind of State Machines Based on TLA+ Semantics

There is, however, a problem with "action-Based" formalisms and programming languages. It can be illustrated with a simple observation using a glass of water.

In an action-based behavior, this system would be described by a state variable v (volume of water in the glass) and two actions: add water, drink.

On the other hand, the state-action behavior of the glass relies on three control states, and the corresponding next-actions:

  * full: drink.

  * in-between: drink, add water.

  * empty: add water.

****![Image title](https://dzone.com/storage/temp/5860999-glass.png)****

We apologize for the triviality of this example, but we must come to the realization that in an action-based programming model the concept of "control state" will have to be emulated in some ways, or the system will not be able to respond to actions correctly (fill the glass infinitely, drink from a negative value).

In structured programming, correctness is achieved with the use of conditional expressions: "if-then-else" or "switch-case," which tend to focus the attention of the developer on what happens next, i.e. the sequence of actions, without requiring the precise identification of (control) states, i.e. where the system is currently at, and consequently without explicitly specifying the actions that are enabled in each (control) state.

To some extent, even state-action behaviors are challenged to provide a formalism where "control states" are modeled properly because the classical State Machine metamodel connects the action to the end state, as if, the action of adding water to the glass would be able to know when the glass is full.

When you think of it, it must be the target of the action which should decide on the resulting (control) state when applying an action. Actions should have no knowledge whatsoever of the "current state" (let alone current control state) of its target. An action should only present a series of variable assignments to its target which may or may not accept them, and, as a result, reach a new control state (or not). This seemingly mundane argument is perhaps why writing code is so error prone, because we use two approximations: either we ignore the (control) states and let actions assign variables directly, or, when (control) states are explicit, the classical state machine semantics enables the actions to decide which control state should be reached. It is possible to write code using these two approximations because in some cases, this works, but they are nevertheless approximations and cannot be generalized to every use case.

TLA+ introduces new semantics that defines a new structure for state machines that we feel can be used to write code without relying on these approximations. TLA stands for the Temporal Logic of Action and [TLA+ uses simple mathematics to specify computations](https://en.wikipedia.org/wiki/TLA%2B). TLA+ is a formal specification language which is often used to test the correctness of the most challenging algorithms.

[The TLA+ specification of the factorial algorithm](https://www.microsoft.com/en-us/research/publication/computation-state-machines/) is as follows:

**![https://lh3.googleusercontent.com/VpU5HTLUDvBkgC2H4tsOYyThwdOoxvO-24IBpa1nvM5PkH4Fg2rd5Jdrru_O1ayVC7v8NGUAKJcg_k9H2zcqBdDK9kaYOFR2R9_N6Ba0MdJHstlqM0TdaRXh_ltfj2d0E3Uorfs](https://lh6.googleusercontent.com/QrxP35G9vDQVQvnzG8IX8Djv8w8YM3G68_ihvX1EM_XPllWwpqlQzh6zG-gCVCkMxy6c4dP0KsoBNjW641ik1kOxY0XXkcAvqHG7WmGzWEG3DSwyQrGZQz0fcXJygPUHCFudZrsYVwHHg-jxrA)**

> _Fig. 4 - The TLA+ Specification of the Factorial Algorithm_

Init is a state predicate which initializes the state machine and next is a transition predicate which specifies the behavior of the state machine. The transition predicate is composed of disjunct formulas, each describing a piece of code that generates a step.

You will note that:

  * The (application) "state" is a series of property values (not to be confused with control state).

  * [In reference to Von Neumann](https://en.wikipedia.org/wiki/Program_counter), Dr. Lamport often uses the "pc" variable (program counter) to store the control state of the state machine.

  * Variables are primed or unprimed. The "prime" notation indicates the property values of the (application) state after the current step completes.

  * [An action is an ordinary mathematical formula](https://www.microsoft.com/en-us/research/wp-content/uploads/2002/12/The-TLA-Language-and-Tools-for-Hardware-and-Software-Engineers-Book.pdf) that contains primed as well as unprimed variables (in this case, the transition predicate is composed of two Actions).

We are now in the position of redefining a new set of semantics for state machines based on TLA+.

**![](https://lh5.googleusercontent.com/M9IAID3lnf3QVy4qdBXaerG8jWeLee03HorGN7g2MhBkG0fhrY8fsiCFq-0bX0V4MuwH1hBkipZPvGIf5kV_gUNkkpRjxsqUmCj5jCFGMcrLeDQHIPr5ykZK9Wfq02eeznlkSnzuCI8Uyz-tOg)**

> _Fig. 5 - A new kind of State Machine based on TLA+ Semantics_

In this state machine, the actions compute the next state property values (1), then the (application) state is updated (2), including the control state (as property values) and the transition predicate decides (3) if another step is needed (based on the control state of the state machine).

This new State Machine structure allows us to write code without the two approximations that we have identified earlier: the actions are never in the position to choose which resulting (control) state will occur from their effect. Hence, the relationship between actions and (control) states is simply observed. This approach also corrects the second approximation since actions do not mutate the property values of the state, it merely proposes new property values which will be used to compute the final state of the step.

Actually, this new structure corrects the third approximation that Dr. Lamport identified when asking the question: [what is a programming step](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/12/Computation-and-State-Machines.pdf)?

How many steps are performed in executing the statement f = i ∗ f ?

  * Does a single step change the value of f to the product of the current values of i and f?

  * Is the evaluation of i ∗ f and the assignment to f two steps?

  * Are there three steps--the reading of i, the reading of f, and the assignment to f?

When we write code, we generally think of a line of code as being a programming step, but this could not be further from the truth. A step here is an action, a mutation, and a resulting (control) state.

## The SAM Pattern

The State-Action-Model Pattern (SAM) [was introduced](http://www.ebpml.org/blog15/2015/06/sam-the-state-action-model-pattern/) by Jean-Jacques Dubray in June 2015 [and became popular throughout 2016](https://www.infoq.com/articles/no-more-mvc-frameworks). As a preamble to this section, we would like to change the meaning of the word "State." Even though these semantics are well defined and widely accepted in the software industry, they encourage the confusion of ignoring the (control) states of State Machines, which are always reified as properties of the so called (application) "State" (including in TLA+). We would like to suggest instead that we call the set of property values (unprimed variables) of a system, the "Model" and reserve the word "State" for control States, as it is used in classical State Machines.

We can then map the SAM Pattern to TLA+ as shown in Fig. 6.

![](https://lh3.googleusercontent.com/WZJvF7TyRFeqGPPoP8QMaujx-_4JSXnAXm9gj74iqE85aP33cdPJJZKZn2xmKLWWTKdOoBlJ-upxDAhh_QnNhspPB3SoME2ZvGBeKqE3tXx0BdREwYzsBNpeuIXFNro270HJRt0O8z-u0bbvMQ)

> _Fig. 6 - State, Action, Model mapping to TLA+_

pc
f' = i * f  
i' = i - 1
f,i  
In TLA+ assignments, primed variables to non-primed variables are implicit but controlled via logic predicates.

The SAM Pattern corrects the three approximations that we have identified in the previous section, with SAM:

  * Actions cannot mutate the properties of the model.

  * Assignments are not mutations, mutations must be explicit.

  * Action->Model->State specify the "programming step," a line of code is not a step.

In SAM, Actions are functions which input is an event and output is a proposal (primed variables) to mutate the property values of the Model (unprimed variable). The Model is an instance of a class (or a closure) generally with a single method which is used to receive proposals to mutate the property values. When the mutation is complete, the model invokes the "State" function whose role is to compute the (control) state, which can also be viewed as the state representation of the model. Last but not least, the State function invokes the next-action predicate which computes whether an action needs to be triggered in the current (new) occurrence of a control state. The next-action predicate will return true if one action was triggered and false otherwise.

There are multiple ways to implement the SAM pattern. A "[reactive loop](https://www.infoq.com/articles/no-more-mvc-frameworks)" is generally preferred. In its simplest form, in JavaScript, for instance, the pattern would look like this code snippet:

_Fig. 7 - The SAM Implementation of a Counter in JavaScript_

In this example, the Reactive Loop is enacted by an event triggering the countByOne() action, continues with the accept method of the model, and then the State render function. At a high level, you can start using SAM today if you follow this simple recipe: each time you need to write an event handler, you split your code into three buckets: action/model/state.

  * Actions are responsible for validating, transforming, and enriching events.

  * The Model is responsible for mutating the property values (aka the application state).

  * The State responsible for computing the State Representation (aka the control state) that other parts of your application will want to consume.

Actions can be grouped into two different categories: idempotent and non-idempotent. Idempotent actions result in a constant state representation, no matter when or how many times they are applied. In REST terms, a path to a resource should rather be viewed as an idempotent action which, when triggered, moves the system to a constant state.

One of the key advantages of SAM is that you no longer need ancillary state machines to manage side effects. Actions can call APIs and propose the results to the model, there is no particular reason to enter the model and mutate a property such as "fetching," just to keep track of the API call lifecycle.

It's also easy for each state representation, to keep track of "allowed actions," such that when an action is triggered it should result in an error condition or if it should proceed to create a proposal. The [SAM-SAFE](https://www.npmjs.com/package/sam-safe) library was designed to illustrate that aspect.

The semantics of the SAM pattern are simple, but not simplistic. They are derived from TLA+, perhaps the most robust theory in Computer Science today. Even though there might be some specific optimizations in a given context, you should proceed with great care when you feel some semantics would fit better. You should contrast this approach with [the history of programming languages](https://www.youtube.com/watch?v=jmRE5pXFi04) and how their semantics came about from [Grace Hopper](https://en.wikipedia.org/wiki/Grace_Hopper) to [Elm](https://en.wikipedia.org/wiki/Elm_\(programming_language\)). Very few, if any, of the programming languages, were founded on Computer Science itself. [For instance](http://www.artima.com/articles/dci_vision.html), "Object Oriented Programming grew out of Doug Englebart's vision of the computer as an extension of the human mind and the goal of object-oriented programming pioneers [such as Alan Kay] was to capture end user mental models in the code." Mark Allen reports that the foundation of Cobol [was designed by a committee](https://en.wikipedia.org/wiki/COBOL), in six months, with the goal of creating a portable programming language (across proprietary platforms at the time). As a matter of fact, programming languages are either built on a "functional foundation" (from Fortran and on) or a "Data Type" foundation (starting with Lisp). Let's assume you knew nothing about programming, and someone would explain to you what programming is, and continue by saying the fundamental building block of programming is: a) a pure function or b) a class, wouldn't you ask the question why? Have you ever asked that question? Is there a chance these statements could be fallacies?

## Conclusion

Since the first structured programming language and its compiler were created, software engineering has been using the same three approximations. These are not only unnecessary but possibly make it harder to write correct software. The goal of this paper was to identify these approximations, offer a new path to software engineering based on TLA+ semantics, and illustrate how simple it is to write code without using these approximations.

Since the development of the SAM pattern in the spring of 2015, several big projects have been developed on that foundation demonstrating its benefits and robustness.

Many thanks to Mark Allen and Jouko Salonen for reviewing this article.

Additional references:

Some of the content in this article was given during a Lecture at [Mae Fah Luang University](http://www.mfu.ac.th/eng/), [Computer Science Department](https://www.youtube.com/watch?v=2-nXlIr6r0Y), by Jean-Jacques Dubray
