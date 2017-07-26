# Naming abstractions

_Captured: 2017-04-15 at 18:16 from [academiccomputing.wordpress.com](https://academiccomputing.wordpress.com/2017/03/14/naming-abstractions/)_

Naming things is important: names permit more precise and concise communication. We don't say "the movable clickable pointer controller box", we say "mouse". In computing we face the challenge of naming a lot of things, both physical and virtual. Some names are intended to be useful analogies: files or documents are like [their physical equivalent](https://en.wikipedia.org/wiki/Document). This can quickly get quite tenuous: scrolling is named after the action needed to read a [historical scroll](https://en.wikipedia.org/wiki/Scroll) despite most people having never scrolled a physical roll of paper, and a mouse was named due to its tail.

Computing has been surprisingly effective at digging up and re-using words which pre-date computing, and vastly increasing their use:

![](https://academiccomputing.files.wordpress.com/2017/03/computing-words.png?w=250&h=343)

> _(What was delete used for before computing, I wonder? Ledgers?)_

### Naming difficulties

Sometimes we can find useful words to refer to computing concepts, even as the concepts become more abstract. A sequence of items is a list. An group without duplicates is a set. A list/set is a collection. That's not too bad. It gets harder when you need a name for a data structure which corresponds one value to another. We usually talk about keys and values, and variously call this collection a "associative array", "dictionary" or "map". It's clear that there is no useful existing word to borrow which carries the right meaning, so we must just pick one and collectively learn what it means.

A list is a type, as is a string or integer. But a list can have different inner types, so we want a different name for that: a polymorphic type. But a list (which has one inner type) is different from a map (which has two), and so we need a name to talk about different types of types. For this, type theory refers to kinds: the arity of types, where arity is the name for the number of parameters that something takes. If your brain is creaking at this point: is that because type, kind and arity are poorly chosen words, or just because the concepts themselves are abstract and difficult? Not to mention all the other abstractly-named programming terms: class, interface, protocol, metaclass, polymorphism -- the list goes on.

I think people struggling to learn something with a non-obvious name (i.e. most programming concepts!) often make a false assumption: that the concept is difficult to learn because the name is unhelpful. (And thus if it was just named better, it would be easier to understand.)

Names can be helpful if they are descriptive (e.g. a network star topology) or transfer intuition (e.g. memory in computers). But intuition is not always available for abstract concepts, such as classes in object-oriented programming. As we get progressively more abstract, names aren't going to save you from the difficulty of understanding an abstraction: the name isn't the problem, the concept is.
