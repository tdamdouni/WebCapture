@Simplicity

_Captured from [Go](http://www.thedotpost.com/2015/11/rob-pike-simplicity-is-complicated)_

> "If a language has too many features, or even more than you might need, you spend time programming thinking about which features to use. If there are really a lot of features, you may look at a line of code, write it once way... Ohh, I could do something different, I could use this feature or that feature. You might even spend half an hour playing with a few lines of code to find all the right way to use different features to make the code to work in a certain way.  And its kind of a waste of time to do that."

- Simplicity
- Simplicity has many facets.
- Simplicity is complicated.
- Simplicity is the art of hiding complexity.
- Simple can be expressive.
- Features add complexity without clarity.

## Convergence

Heard talks about new versions of Java, JavaScript (ECMAScript), Typescript, C#, C++, Hack (PHP), and more.
These languages actively borrow features from one another.
They are converging into a single huge language.

## Language relativity

Sapir-Whorf hypothesis: Language influences thought.
Controversial with regard to human languages.
Close to a fact for computer languages. 
Consider:

•	logic programming
•	procedural programming
•	functional programming
•	object-oriented programming
•	concurrent programming

Like disciplines in mathematics.

## Convergence and relativity

If the languages all converge, we will all think the same.
But different ways of thinking are good.
Need different languages for different problems.
We don't want just one tool, we want a set of tools, each best at one task.

## Convergence and features

The talks at Lang.Next were about new language versions (Java 8, ECMAScript 6, C#, C++14) and were lists of features.
These languages evolve and compete by adding features.
The languages grow in complexity while becoming more similar.
Bloat without distinction.

## But you need features!

Of course, there must be some features.
But which ones? The right ones!
Design by consensus.

## Readability

If a language has too many features, you waste time choosing which ones to use.   
Then implement, refine, possibly rethink and redo.
Later, "Why does the code work this way?"
The code is harder to understand simply because it is using a more complex language.
Preferable to have just one way, or at least fewer, simpler ways.
Features add complexity. We want simplicity.
Features hurt readability. We want readability.
Readability is paramount.

Readable means Reliable
Readable code is reliable code.
It's easier to understand.
It's easier to work on.
If it breaks, it's easier to fix.
If the language is complicated:

•	You must understand more things to read and work on the code.
•	You must understand more things to debug and fix it.
A key tradeoff: More fun to write, or less work to maintain?

## Expressiveness

Features are often suggested to aid "expressiveness".
Conciseness can be expressive but not always readable.   
(Consider APL: ⊃ 1 ω ∨ . ∧ 3 4 = +/ +⌿ 1 0 ‾1 ∘.θ 1 - ‾1 Φ″ ⊂ ω)
Can also be expensive, implementing simple ideas with too-powerful primitives.   
Performance can also be unpredictable.
On the other hand, verbosity can inhibit readability by obscuring the intent.
Build on, but do not be limited by, familiar ideas.
Be concise while remaining expressive.

## The right set of features

Not features for features' sake.
Features that "cover the space", like a vector basis covering solution space.
Orthogonal features that interact predictably.
Simple features that interact in simple ways.
Simplicity comes from orthogonality and predictability.
Keep the language's goals in mind.

