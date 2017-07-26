# Data Structures Are Antithetical to Functional Programming

_Captured: 2017-06-13 at 23:07 from [dzone.com](https://dzone.com/articles/data-structures-are-antithetical-to-functional-pro?edition=303098&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-13)_

### I recommend that you stick to data structures when you must, and judiciously incorporate data polymorphism only where it makes sense to do so.

Need to build an application around your data? [Learn more](https://dzone.com/go?i=200129&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) about dataflow programming for rapid development and greater creativity.

Functional programmers are incredibly lazy.

More precisely, we defer commitment as late as possible. In extreme examples like Haskell, we defer the computation of every part of every expression until the last possible moment.

Even in less extreme cases, however, we push effects (such as input/output) to the edges of our program. With Monad Transformers Library (MTL) or FTL, we defer committing to specific effect types until our application's main function.

This commitment to non-commitment tends to have several benefits:

  * It improves comprehension because low-level portions of the code needn't be concerned with unnecessary and distracting details.
  * It improves reusability since the higher-level code has more control over decisions.
  * Sometimes, it even improves performance (algorithm fusion in the case of Haskell's non-strict evaluation model).

Sadly, there's something about even the most functional code that is inherently not lazy. Instead, almost all functional code eagerly commits to more than it needs to, obfuscating intent and decreasing reusability.

I'm referring to the tendency of functional code to use hard-coded data structures.

## Devil in the Data

Let's take the following code example, which tries to find an employee's manager or returns an error message:
    
    
      (find (\m -> m.id == e.managerId) es)

Notice how the code commits to returning the result in a hard-coded `Either` data structure.

This is far more specific than the code actually requires. All the function really needs is the ability to construct error and success cases, without the ability to know anything about the data structure or to deconstruct it.

The code is prematurely committing to a concrete data structure, which removes the choice from all higher-level code (you don't have the choice to return the error in an `IO` or `Future` monad, for example), making the implementation both unnecessarily complex and more difficult to reuse.

In an ideal world, the `findManager` function would be polymorphic in the type of data structure it returned. Further, the function would not require the ability to construct and deconstruct error/success values, since it depends only on construction.

In an ideal world, our code would commit to no data structures.

## Constructing Polymorphic Data

To purge the blight of concrete data structures from our functional programs, our first step is going to be to separate the capability of construction from the capability of deconstruction.

Using an MTL-like approach, we're going to describe the capability of constructing an `Either`-like structure:
    
    
      left :: forall a b. a -> e a b
    
    
      right :: forall a b. b -> e a b

These classes promise the ability to construct an `Either`-like structure from a left or a right value. However, the structure they are constructing could be anything--including a sum type with many more terms than just right and left, or even a `Monad` with an error and success case.

With this type class, we can now make the original code polymorphic in the type of data structure it returns:
    
    
    findManager :: forall e. EitherLike e => List Employee -> Employee -> e String Employee
    
    
      (find (\m -> m.id == e.managerId) es)

This was an easy change to make, but what happens when we need not just the ability to _construct_ a data structure, but also the ability to _deconstruct_ it?

The solution to this problem is surprisingly elegant.

## Deconstructing Polymorphic Data

The capability of deconstruction can be expressed directly as a catamorphism or fold from the representation of a data structure.

In the case of an `Either`-like data structure, we can represent this catamorphism with the following type class:
    
    
      either :: forall a b z. (a -> z) -> (b -> z) -> e a b -> z

Here's how we could use this type class to construct a `leftOrElse` combinator, which extracts the left side of an either if it's there, or else uses a specified default value:
    
    
    def leftOrElse[E[_, _], A, B](a: A, e: E[A, B])(implicit E: DeconstructEither[E]): A =
    
    
      E.either[A, B, A](identity, Function.const(a))(e)

This code is completely polymorphic in the type of data structure it operates on, requiring only the ability to deconstruct an `Either`-like data structure into its components.

However, it's hard to look at this code without noticing there's a lot of boilerplate. The catamorphism of deconstruction is eerily similar to the anamorphism of construction, yet we have two type classes, one for construction, and one for deconstruction.

With a little bit of abstraction, we can completely eliminate all this boilerplate and make generic abstractions for construction and deconstruction.

## Generic Constructors and Deconstructors

As a first step, we'll refactor the constructors and deconstructors for `Either` as follows:
    
    
      def deconstruct[E2[_, _], A, B](e1: E1[A, B])(m: EitherConstructor[E2, A, B]): E2[A, B]

These classes lets you simply build and match against either-like structures as follows:

Notice that we can abstract over all constructors of a given arity in straightforward fashion:
    
    
    class Construct1 m1 (repr :: * -> *) where
    
    
      make1 :: forall a. m1 repr a
    
    
    class Construct2 m2 (repr :: * -> * -> *) where
    
    
      make2 :: forall a b. m2 repr a b
    
    
      switch0 :: forall rep2. rep1 -> m0 rep2 -> rep2
    
    
      switch1 :: forall rep2 a. rep1 a ->
    
    
      switch2 :: forall rep2 a b. rep1 a b ->
    
    
    trait Construct1[M1[_[_], _], Rep[_]] {
    
    
    trait Construct2[M2[_[_, _], _, _], Rep[_, _]] {
    
    
      def switch0[Rep2](rep1: Rep1)(m: M0[Rep2]): Rep2
    
    
    trait Deconstruct1[M1[_[_], _], Rep1[_]] {
    
    
      def switch1[Rep2[_], A](rep1: Rep1[A])(m: M1[Rep2, A]): Rep2[A]
    
    
    trait Deconstruct2[M2[_[_, _], _, _], Rep1[_, _]] {
    
    
      def swtich2[Rep2[_, _], A, B](rep1: Rep1[A, B])(m: M2[Rep2, A, B]): Rep2[A, B]

Here's a concrete example of instances of these classes for constructing and deconstructing the `Either` data structure:
    
    
      def make2[A, B] = new EitherConstructor[Either, A, B] {
    
    
        def left(a: A): Either[A, B] = Left(a)
    
    
        def right(b: B): Either[A, B] = Right(b)
    
    
      def switch2[Rep2[_, _], A, B](e: Either[A, B])(m: EitherConstructor[Rep2, A, B]): Either[A, B] =
    
    
          case Right(v) => m.right(v)

Finally, we can refactor our toy example to use this machinery as follows:

There you have it -- code that's fully polymorphic in construction and deconstruction. It works with any data structure that can provide the capabilities it needs, and _only_ the capabilities it needs.

Now let's revisit our original example.

## Polymorphic Overload

Our original example that motivated this development was the `findManger` function:

If we modified this example to use a polymorphic return value, we'd end up with the following type signature:

This function could be used to return any type of structure which is at least as capable as `Either`'s constructors, including any `Monad` that had failure and success cases, or other sum types that have more than two terms.

While more flexible, the function is still monomorphic in the type of `List`, `Employee`, and `String`. If taken to its logical conclusion, then making this function totally polymorphic would yield something like this:
    
    
    def findManager[E[_, _], L[_], P, S](es: L[P], e: P)( implicit E: Construct2[EitherConstructor, E], implicit L: Deconstruct1[ListConstructor, L], implicit P: Deconstruct0[EmployeeConstructor, P], implicit S: Construct0[StringConstructor, S]): E[S, P]

If we change a bunch of names and use Unicode and type alias operators, we can make this horrible soup of letters and symbols a little more readable, possibly close to the following:

That's about the best we can get -- and let's be honest, it's not very good. There's still a lot of boilerplate, and while all this polymorphism is very powerful, must code won't need it.

It's a heavy price to pay for fringe use cases. Too heavy, I'd say, at least with today's programming languages.

## Looking Forward

Ultimately, I'd argue that today's programming languages are unnaturally obsessed with data. They are wedded to the idea of rigid layouts of bits in memory -- for understandably pragmatic or historic reasons.

Yet, the functions we develop in our code don't usually require bits. Instead, they require capabilities. Some to construct, some to deconstruct. If we expressed these capabilities precisely, we could free our code from having to know too much about the structures it operates on, while at the same time making our code much more reusable for different purposes.

We can model this degree of polymorphism with today's programming languages, but it's awfully cumbersome. However, if we were building a next-generation programming language, we could make it difficult or impossible to make our code depend on "layouts of bits," and instead, make it trivial to require only as much structure as we need to implement each function.

For now, though, I recommend you stick to data structures when you must, and judiciously incorporate data polymorphism where it makes sense to do so, which will be cases where the opportunities for reuse vastly outweigh the overhead.

[Check out](https://dzone.com/go?i=200130&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) the Exaptive data application Studio. Technology agnostic. No glue code. Use what you know and rely on the community for what you don't. [Try the community version](https://dzone.com/go?i=200130&u=https%3A%2F%2Fexaptive.city%2F%23%2Flanding%3Freferrer%3DGeneral).
