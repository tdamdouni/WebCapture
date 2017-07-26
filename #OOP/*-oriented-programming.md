# *-Oriented Programming

_Captured: 2015-10-16 at 10:25 from [www.sicpers.info](http://www.sicpers.info/2015/10/oriented-programming/)_

Much is written about various _paradigms_ or _orientations_ of programming: Object- (nee Message-) Oriented, Functional, Structured, Dataflow, Logic, and probably others. These are often presented as camps or tribes with which to identify. A Smalltalk programmer will tell you that they are an Object-Oriented programmer, and furthermore those Johnny-come-latelies with their Java are certainly not members of the same group. A Haskell programmer will tell you that they are a functional programmer, and that that is the only way to make working software (though look closely; their Haskell is running on top of a large body of successful, imperative C code).

Notice the identification of paradigms with individual programming languages. Can you really not be object-oriented if you use F#, or is structured programming off-limits to an Objective-C coder? Why is the way that I _think_ so tightly coupled to the tool that I choose to express my thought?

Of course, tools are important, and they do have a bearing on the way we think. But that's at a fairly low, mechanical level, and programming is supposed to be about abstraction and high-level problem solving. You're familiar with artists working with particular tools: there are watercolour painters and there are oil painters (and there are others too). Now imagine if the watercolour painting community (there is, of course, no such thing) decreed that it's impossible to represent a landscape using oil paints and the oil painting community declared that watercolours are "the wrong tools for the job" of painting portraits.

This makes no sense. Oil paints and watercolour paints define how the paint interacts with the canvas, the brush, and the paint that's already been applied. They don't affect how the painter sees their subject, or thinks about the shapes involved and the interaction of light, shadow, reflection, and colour. They affect the presentation of those thoughts, but that's at a mechanical low level.

Programming languages define how the code interacts with the hardware, the libraries, and the code that's already been applied. They don't affect how the programmer sees their problem, or thinks about the factors involved. They affect the presentation of those thoughts, but that's at a mechanical low level.

## Function-oriented Objects

> Given a Cartesian representation of the point (x,y), find its distance from the origin and angle from the x axis.

I'm going to approach this problem using the principles of functional programming. There's clearly a function that can take us from the coordinates to the displacement, and one that can take us from the coordinates to the angle. Ignoring the implementation for the moment, they look like this:

    Point_radius::float,float->floatPoint_angle::float,float->float

This solution has its problems. I have two interchangeable arguments (both the x and y ordinates are `float`s) used in independent signatures, how do I make it clear that these are the same thing? How do I ensure that they're used in the same way?

One tool in the arsenal of the functional programmer is pattern matching. I could create a single entry point with an enumeration that selects the needed operation. Now it's clear that the operations are related, and there's a single way to interpret the arguments, guaranteeing consistency.
 
    Point::float,float,Selector->float

Good for now, but how extensible is this? What if I need to add an operation that returns a different type (for example a description that returns a string), or one that needs other arguments (for example the projection on to a different vector)? To provide that generality, I'll use a different tool from the functional toolbox: the higher-order function. Rewrite `Point` so that instead of returning a `float`, it returns a function that captures the coordinates and takes any required additional arguments to return a value of the correct type. To avoid cluttering this example with irrelevant details, I'll give that function a shorthand named type: `Method`.

    Point::float,float,Selector->Method

You may want to perform multiple operations on values that represent the same point. Using a final functional programming weapon, partial application, we can capture the coordinates and let you request different operations on the same encapsulated data.

    Point::float,float->Selector->Method

Now it's clear to see that the `Point` function is a _constructor_ of some type that encapsulates the coordinates representing a given two-dimensional Cartesian point. That type is a function that, upon being given a `Selector` representing some operation, returns a `Method` capable of implementing that operation. The function implements message sending, and `Points` are just objects!

Imagine that we wanted to represent points in a different way, maybe with polar coordinates. We could provide a different function, `Point'`, which captures those:

    Point' :: float, float -> Selector -> Method

This function has the same signature as our original function, it too encapsulates the constructor's arguments (call them instance variables) and returns methods in response to selectors. In other words, `Point` and `Point'` are polymorphic: if they have methods for the distance and angle selectors, they can be used interchangeably.

## Object-oriented Functions

> Write a compiler that takes source code in some language and creates an executable. If it encounters malformed source code, it should report an error and not produce an executable.

Thinking about this with my object-oriented head, I might have a `Compiler` object with some method `#compile(source:String)` that returns an optional `Executable`. If it doesn't work, then use the `#getErrors():List<Error>` method to find out what went wrong.

That approach will work (as with most software problems there are infinite ways to skin the same cat), but it's got some weird design features. What will the `getErrors()` method do if it's called before the `compile()` method? If `compile()` is called multiple times, do earlier errors get kept or discarded? There's some odd and unclear temporal coupling here.

To clean that up, use the object-oriented design principle "Tell, don't ask". Rather than requesting a list of errors from the compiler, have it tell an error-reporting object about the problems as they occur. How will it know what error reporter to use? That can be passed in, in accordance with another OO principle: dependency inversion.

    Compiler#compile(source:String, reporter:ErrorConsumer): Optional<Executable>ErrorConsumer#reportError(error:Error): void

Now it's clear that the reporter will receive errors related to the invocation of `#compile()` that it was passed to, and there's no need for a separate accessor for the errors. This clears up confusion as to what the stored state represents, as there isn't anyway.

Another object-oriented tool is the Single Responsibility Principle, which invites us to design objects that have exactly one reason to change. A compiler does not have exactly one reason to change: you might need to target different hardware, change the language syntax, adopt a different executable format. Separating these concerns will yield more cohesive objects.

    Tokeniser#tokenise(source:String, reporter:ErrorConsumer): Optional<TokenisedSource>Compiler#compile(source:TokenisedSource, reporter:ErrorConsumer): Optional<AssemblyProgram>Assembler#assemble(program:AssemblyProgram, reporter:ErrorConsumer): Optional<BinaryObject>Linker#link(objects:Array<BinaryObject>, reporter:ErrorConsumer): Optional<Executable>ErrorConsumer#reportError(error:Error): void

Every class in this system is named `Verber`, and has a single method, `#verb`. None of them has any (evident) internal state, they each map their arguments onto return values (with the exception of `ErrorConsumer`, which is an I/O sink). They're just stateless functions. Another function is needed to plug them together:

    Binder<T,U,V>#bind(T->Optional<U>, U->Optional<V>):(T->Optional<V>)

And now we've got a compiler constructed out of functions constructed out of objects.

## Brain-oriented programming

Those examples were very abstract, not making any use of specific programming languages. Because software design is not coupled to programming languages, and paradigmatic approaches to programming are constrained ways to think about software design. They're abstract enough to be separable from the nuts and bolts of the implementation language you choose (whether you've already chosen it or not).

Those functions in the `Point` example could be built using the blocks available in Smalltalk, Ruby or other supposedly object-oriented languages, in which case you'd have objects built out of functions that are themselves built out of objects (which are, of course, built out of functions…). The objects and classes in the `Compiler` example can easily be closures in a supposedly functional programming language. In fact, closures and blocks are not really too dissimilar.

What conclusions can be derived from all of this? Clearly different programming paradigms are far from exclusive, so the first lesson is that you don't have to let your choice of programming language dictate your choice of problem solving approach (nor do you really have to do it the other way around). Additionally where the approaches try to solve the same problem, the specific techniques they comprise are complementary or even identical. Both functional and object-oriented programming are about organisation, decomposition and comprehensibility, and using either or even both can help to further those aims.

Ultimately your choice of tools isn't going to affect your ability to think by much. Whether they help you express your thoughts is a different matter, but while expression is an important part of our work it's only a small part.

## Further Reading

The ideas here were primarily motivated by Uday Reddy's [Objects as Closures: Abstract Semantics of Object-Oriented Languages](http://www.researchgate.net/profile/Uday_Reddy5/publication/23577646_Objects_as_closures_-_Abstract_semantics_of_object_oriented_languages/links/02bfe51314af883e13000000.pdf) (weird embedded PDF reader link). In the real-life version of this presentation I also talked a bit about [Theorems for Free](http://ecee.colorado.edu/ecen5533/fall11/reading/free.pdf) (actual PDF link) by Philip Wadler, which isn't so related but is nonetheless very interesting :).

Your email is _never_ published nor shared. Required fields are marked * Comments are moderated; please make sure that your post is civil and valuable before submitting it to improve the chance it will be accepted.

Name *

Email *

Website

Comment
