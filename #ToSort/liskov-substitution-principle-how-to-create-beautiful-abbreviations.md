# Liskov Substitution Principle: How to Create Beautiful Abbreviations

_Captured: 2018-08-16 at 06:54 from [dzone.com](https://dzone.com/articles/liskov-substitution-principle-or-how-to-create-bea?edition=385377&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-08-15)_

This is the third post on [SOLID](https://hackernoon.com/solid-principles-530b2cc2badf) principles -- check out [the open-closed principle](https://dzone.com/articles/the-open-closed-principle-and-what-hides-behind-it) if you missed it. Here, I will get started with a short intro on how this concept was formed and provide a descriptive example -- no square and rectangle, I promise!

## Bertrand Meyer, 1986

[Bertrand Meyer](https://en.wikipedia.org/wiki/Design_by_contract) first introduced the concept of contract and implemented it in his language [Eiffel](https://www.eiffel.com/). The contract is identified by [preconditions](https://en.wikipedia.org/wiki/Precondition), [invariants](https://en.wikipedia.org/wiki/Invariant_%28computer_science%29), and [postconditions](https://en.wikipedia.org/wiki/Postcondition). Here is a nice summary from [Wikipedia](https://en.wikipedia.org/wiki/Design_by_contract):

> 1\. [A routine can] Expect a certain condition to be guaranteed on entry by any client module that calls it: the routine's precondition -- an obligation for the client, and a benefit for the supplier (the routine itself), as it frees it from having to handle cases outside of the precondition.   
2\. Guarantee a certain property on exit: the routine's postcondition -- an obligation for the supplier, and obviously a benefit (the main benefit of calling the routine) for the client.   
3\. Maintain a certain property, assumed on entry and guaranteed on exit: the [class invariant](https://en.wikipedia.org/wiki/Class_invariant). 

Eiffel is the only language that I'm aware of where a contract is a built-in concept. In other languages, contracts can be enforced by a method's signature, including the type of arguments, type of return values, and an exception that can be thrown. But, since it's hardly feasible to invent a type-system that can be used to enforce all existing business-rules, this approach is quite limited.

## Barbara Liskov, 1994

The way [Barbara Liskov ](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.39.1223)explained her principle represents a concept of [subtyping](https://en.wikipedia.org/wiki/Subtyping), or subtype polymorphism. This type of polymorphism is the most common in object-oriented programming and is usually referred to as simply "polymorphism." Liskov formalized Meyer's approach, and it looks more [academic](https://en.wikipedia.org/wiki/Liskov_substitution_principle):

> Let φ(x) be a property provable about objects x of type T. Then, φ(y) should be true for objects y of type S where S is a subtype of T. 

The [human-readable version](https://en.wikipedia.org/wiki/Liskov_substitution_principle#Principle) repeats pretty much everything that Bertrand Meyer already said, but it relies totally on a type-system:

> 1\. Preconditions cannot be strengthened in a subtype.   
2\. Postconditions cannot be weakened in a subtype.   
3\. Invariants of the supertype must be preserved in a subtype. 

## Robert Martin, 1996

[Robert Martin](https://web.archive.org/web/20151128004108/http://www.objectmentor.com/resources/articles/lsp.pdf) made the definition more concise:

> Functions that use pointers of references to base classes must be able to use objects of derived classes without knowing it. 

However, he hasn't introduced anything new.

## Violation of the Liskov Substitution Principle

I often find that, in order to comprehend some principles, it's important to realize when it's been violated. This is what I will do now.

What does the violation of this principle mean? It implies that an object doesn't fulfill the contract imposed by an abstraction expressed with an interface. In other words, it means that you [identified your abstractions wrong](https://medium.com/@wrong.about/on-good-domain-decomposition-385ee8ce5a3).

Consider the following example:
    
    
            if (!$this->enoughMoney($money)) {
    
    
            $this->balance->subtract($money);

Is this a violation of LSP? Yes. This is because the account's contract tells us that an account would be withdrawn, but this is not always the case. So, what should I do in order to fix it? I just modify the contract:

Voila, now the contract is satisfied.

This subtle violation often imposes client with the ability to tell the difference between concrete objects employed. For example, given the first Account's contract, it could look like the following:

And, this automatically violates the [open-closed principle](https://medium.com/@wrong.about/the-open-closed-principle-c3dc45419784). This point also addresses a misconception that I encounter quite often about LSP violation. It says the "if a parent's behavior changed in a child, then, it violates LSP." However, it doesn't -- as long as a child doesn't violate its parent's contract.

## Liskov Substitution Principle in SOLID

My problem with this abbreviation is that if "polymorphism" is present there, why are "encapsulation" and "composability" not? Those are in no way less important. Probably, it's because it's hard to come up with beautiful abbreviations using "e" and "c"? I bet it is.

## Wrapping it up

Don't get me wrong -- I like SOLID and the approaches it promotes. But, it's just a shape of deeper principles lying in its foundation. The examples above made it clear what this principle is striving for -- to [loose coupling](https://en.wikipedia.org/wiki/Loose_coupling). In other words, don't make your clients care what concrete class is in use. While this is a noble goal, how do we achieve it? First, start with [decomposing your problem space](https://medium.com/@wrong.about/how-to-avoid-anemic-domain-model-5e1c3e6fe4d0) domain. Second, express your contract in a method signature using plain English.
