# A Guide to Parsing: Algorithms and Technology (Part 2)

_Captured: 2017-12-19 at 04:46 from [dzone.com](https://dzone.com/articles/a-guide-to-parsing-algorithms-and-technology-part-8?edition=345100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-18)_

Insight for I&O leaders on deploying AIOps platforms to enhance performance monitoring today. [Read the Guide](https://dzone.com/go?i=260321&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2Fgartner-market-guide-for-aiops-platforms-2017.html%3Fcid%3Dpt-PA_STA_All_FC_PT_Gartner_AIOps_Market_Guide_Dzone_Analyst_Report-AB-03-f-08232017%26cc%3Dpt%26elqcid%3D4114%26sfcid%3D7011O0000027wFd).

## The Big Picture

We're still talking about the big picture from [Part 1](https://dzone.com/articles/a-guide-to-parsing-algorithms-and-technology-part) here, so let's continue on...

### Grammar

A formal grammar is **a set of rules that describes syntactically a language**.

There are two important parts of this definition: a grammar describes a language, but this description pertains only the syntax of the language and not the _semantics_. That is to say, it defines its structure, but not its meaning. The correctness of the meaning of the input must be checked, if necessary, in some other way.

For instance, imagine that we want to define a grammar for the language shown in the paragraph defining parsing in [Part 1](https://dzone.com/articles/a-guide-to-parsing-algorithms-and-technology-part).

This grammar accepts input such as `"Hello Michael"` and `"Hello Programming"`. They are both syntactically correct, but we know that "Programming" it is not a name. Thus, it is semantically wrong. A grammar does not specify semantic rules, and they are not verified by a parser. You would need to ensure the validity of the provided name some other way; for example, comparing it to a database of valid names.

#### Anatomy of a Grammar

To define the elements of a grammar, let's look at an example in the most-used format to describe grammars: the **Backus-Naur Form (BNF)**. This format has many variants, including the **Extended Backus-Naur Form**. The Extended variant has the advantage of including a simple way to denote repetitions. Another notable variant is the **Augmented Backus-Naur Form**, which is mostly used to describe bi-directional communications protocols.

A typical rule in a Backus-Naur grammar looks like this:

The **<symbol>** is a _nonterminal_, which means that it can be replaced by the group of elements on the right, **__expression__**. The element **__expression__** could contain other nonterminal symbols or terminal ones. _Terminal _symbols are simply the ones that do not appear as a **<symbol>** anywhere in the grammar. A typical example of a terminal symbol is a string of characters, like "Hello".

A _rule_ can also be called _production rule_. Technically, it defines a transformation between the nonterminal and the set of nonterminals and terminals on the right.

#### Types of Grammars

There are mainly two kinds of grammars used in parsing: **regular grammars** and **context-free grammars**. Usually to one kind of grammar corresponds the same kind of language: a regular grammar defines a regular language and so on. However, there is also a more recent kind of grammars called **Parsing Expression Grammar** (PEG) that is equally powerful as context-free grammars and thus define a context-free language. The difference between the two is in the notation and the interpretation of the rules.

As we already mentioned, the two kinds of languages are in a hierarchy of complexity -- regular languages are simpler than context-free languages.

A relatively easy way to distinguish the two grammars would be that the `__expression__` of a regular grammar -- that is to say, the right side of the rule -- could be only one of:

  * The empty string
  * A single terminal symbol
  * A single terminal symbol followed by a nonterminal symbol

This is harder to check because a particular tool could allow using more terminal symbols in one definition. Then, the tool itself will automatically transform this expression into an equivalent series of expressions all belonging to one of the three mentioned cases.

So, you could write an expression that is incompatible with a regular language, but the expression will be transformed in the proper form. In other words, the tool could provide syntactic sugar for writing grammars.

In a later paragraph, we are going to discuss more at length the different kinds of grammars and their formats.

### Lexer

A lexer **transforms a sequence of characters in a sequence of tokens**.

_Lexers_ are also known as _scanners_ or _tokenizers_. Lexers play a role in parsing because they transform the initial input in a form that is more manageable by the proper parser, who works at a later stage. Typically lexers are easier to write than parsers, although there are special cases when both are quite complicated; for instance, in the case of C (see [the lexer hack](https://en.wikipedia.org/wiki/The_lexer_hack)).

A very important part of the job of the lexer is dealing with whitespace. Most of the time, you want the lexer to discard whitespace. That is because otherwise, the parser would have to check for the presence of whitespace between every single token, which would quickly become annoying.

There are cases in which you cannot do that because whitespace is relevant to the language, like in the case of Python where is used to identify blocks of code. Even in these cases, though, usually, it is the _lexer_ that deals with the problem of distinguishing the relevant whitespace from the irrelevant one -- which means that you want the lexer to understand which whitespace is relevant to parsing. For example, when parsing Python, you want the lexer to check if whitespace defines indentation (relevant) or spaces between the keyword `if` and the following expression (irrelevant).

#### Where the Lexer Ends and the Parser Begins

Given that lexers are almost exclusively used in conjunction with parsers, the dividing line between the two can be blurred at times. That is because the parsing must produce a result that is useful for the particular need of a program. So there is not just one correct way of parsing something, and you care about only the one way that serves your needs.

For example, imagine that you are creating a program that must parse the logs of a server to save them in a database. For this goal, the lexer will identify the series of numbers and dots and transform them into an IPv4 token.

Then, the parser will analyze the sequence of tokens to determine if it is a message, a warning, etc.

What would happen instead if you were developing software that had to use the IP address to identify the country of the visitor? Probably, you would want the lexer to identity the octets of the address for later use, and make IPv4 a parser element.

This is one example of how the same information can be parsed in different ways because of different goals.

**Stay tuned for Part 3, where we'll talk about syntactics, semantics, and parsers some more.**

[TrueSight is an AIOps platform](https://dzone.com/go?i=247359&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html), powered by machine learning and analytics, that elevates IT operations to address multi-cloud complexity and the speed of digital transformation.
