# A Guide to Parsing: Algorithms and Technology (Part 9)

_Captured: 2018-01-04 at 06:15 from [dzone.com](https://dzone.com/articles/a-guide-to-parsing-algorithms-and-technology-part-1?edition=347152&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-03)_

[Find out how AI-Fueled APIs from Neura](https://dzone.com/go?i=244221&u=https%3A%2F%2Fhubs.ly%2FH08wTJ10) can make interesting products more exciting and engaging.

We've reached the end! If you're encountering this series for the first time, check out the rest of the posts below:

## Parsing Algorithms

Our last focus is going to be on bottom-up algorithms.

### Bottom-Up Algorithms

The bottom-up strategy's main success is the family of many different LR parsers. The reason for their relative unpopularity is that historically, they've been harder to build, although LR parsers are more powerful than traditional LL(1) grammars. So, we mostly concentrate on them, apart from a brief description of CYK parsers.

This means that we avoid talking about the more generic class of [shift-reduce parser](https://en.wikipedia.org/wiki/Shift-reduce_parser), which also includes LR parsers.

Shift-reduce algorithms work with two steps:

  1. **Shift**: Read one token from the input, which will become a new (momentarily isolated) node.
  2. **Reduce**: Once the proper rule is matched, join the resulting tree with a precedent existing subtree.

Basically, the Shift step reads the input until completion, while the Reduce step joins the subtrees until the final parse tree is built.

#### CYK Parser

The Cocke-Younger-Kasami (CYK) algorithm was formulated independently by three authors. Its notability is due to a great worst-case performance (O(n3)), although it is hampered by comparatively bad performance in most common scenarios.

However, the real disadvantage of the algorithm is that it requires grammars to be expressed in [Chomsky normal form](https://en.wikipedia.org/wiki/Chomsky_normal_form).

That is because the algorithm relies on the properties of this particular form to be able to split the input in half to try to match all the possibilities. In theory, any context-free grammar can be transformed into a corresponding CNF, but this is seldom practical to do by hand. Imagine being annoyed by the fact that you can't use left-recursive rules and then being asked to learn a special kind of form.

The CYK algorithm is used mostly for specific problems; for instance, the membership problem: to determine if a string is compatible with a certain grammar. It can also be used in natural language processing to find the most probable parsing between many options.

For all practical purposes, if you need to parse all context-free grammar with great worst-case performance, you want to use an Earley parser.

#### LR Parser

LR (Left-to-right read of the input; Rightmost derivation) parsers are bottom-up parsers that can handle deterministic context-free languages in linear time with lookahead and without backtracking. The invention of LR parsers is credited to the renowned Donald Knuth.

Traditionally, they have been compared to and have competed with LL parsers. There's a similar analysis related to the number of lookahead tokens necessary to parse a language. An LR(_k_) parser can parse grammars that need _k_ tokens of lookahead to be parsed. However, LR grammars are less restrictive, and thus more powerful, than the corresponding LL grammars. For example, there is no need to exclude left-recursive rules.

Technically, LR grammars are a superset of LL grammars. One consequence of this is that you need only LR(1) grammars, so usually, the (_k_) is omitted.

They are also table-based, just like LL-parsers, but they need two complicated tables. In very simple terms:

  1. One table tells the parser what to do depending on the current token, the state it's in, and the tokens that could possibly follow the current one (lookahead sets).
  2. The other one tells the parser to which state move next.

LR parsers are powerful and have great performance -- so where is the catch? The tables they need are hard to build by hand and can grow very large for normal computer languages, so usually, they are used through parser generators. If you need to build a parser by hand, you would probably prefer a top-down parser.

##### Simple LR and Lookahead LR

Parser generators avoid the problem of creating such tables, but they do not solve the issue of the cost of generating and navigating such large tables. There are simpler alternatives to the canonical LR(1) parser described by Knuth. These alternatives are less powerful than the original. They are the simple LR parser (SLR) and lookahead LR parser (LALR). So, in order of power we have:

  1. LR(1)

  2. LALR(1)

  3. SLR(1)

  4. LR(0)

The names of the two parsers, both invented by Frank DeRemer, are somewhat misleading: one is not really that simple and the other is not the only one that uses lookahead. We can say that one is simpler and the other relies more heavily on lookahead to make decisions.

Basically, they differ in the tables they employ. Mostly, they change the "what to do" part and the lookahead sets, which in turn pose different restrictions on the grammars that they can parse. In other words, they use different algorithms to derive parsing tables from the grammar.

An SLR parser is quite restrictive in practical terms and it is not often used. A LALR parser instead works for most practical grammars and is widely employed. In fact, the popular tools yacc and bisonwork with LALR parser tables.

Contrary to LR grammars, LALR and SLR grammars are not supersets of LL grammars. They are not easily comparable; some grammars can be covered by one class and not the other, or vice versa.

##### Generalized LR Parser

Generalized LR parsers (GLR) are more powerful variants of LR parsers. They were described by Bernard Land in 1974 and implemented for the first time by Masaru Tomita in 1984. The reason for GLR's existence is the need to parse nondeterministic and ambiguous grammars.

The power of a GLR parser is not found on its tables, which are equivalent to the table of a traditional LR parser. Instead, it can move to different states. In practice, when there is ambiguity, it forks a new parser (or parsers) that handle(s) that particular case. These parsers might fail at a later stage and be discarded.

The worst-case complexity of a GLR parser is the same as Earley (O(n3)), though it may have better performance with the best case of deterministic grammars. A GLR parser is also harder to build than an Earley one.

## Summary

With this large series, we hope to have solved most of your doubts about parsing terms and algorithms, such as what the terms mean and why to pick a certain algorithm over another one. We have not just explained them but we have also given a few pointers for solving common issues with parsing programming languages.

For reasons of space, we could not provide a detailed explanation of _all_ parsing algorithms. So, we've have also provided a few links to give you a deeper understanding of these algorithms, the theory behind them, and how they work. If you are specifically interested in building things like compilers and interpreters, you can read another one of our articles to find [resources to create programming languages](https://tomassetti.me/resources-create-programming-languages/).

If you are just interested in parsing, you may want to read _[Parsing Techniques_](http://www.springer.com/us/book/9780387202488), a book that is as comprehensive as it is expensive. It obviously goes much more in depth than we could, but it also covers less-used parsing algorithms.

To find out how AI-Fueled APIs can increase engagement and retention, [download Six Ways to Boost Engagement for Your IoT Device or App with AI](https://dzone.com/go?i=244222&u=https%3A%2F%2Fhubs.ly%2FH08wTJ50) today.
