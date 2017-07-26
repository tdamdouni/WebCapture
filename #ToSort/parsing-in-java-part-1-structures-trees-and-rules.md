# Parsing in Java (Part 1): Structures, Trees, and Rules

_Captured: 2017-06-05 at 02:25 from [dzone.com](https://dzone.com/articles/parsing-in-java-part-1-structures-trees-and-rules?edition=304121&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-04)_

Learn how to troubleshoot and diagnose some of [the most common performance issues in Java today](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

If you need to parse a language, or document, from Java there are fundamentally three ways to solve the problem:

  * Use an existing library supporting that specific language: for example a library to parse XML.
  * Building your own custom parser by hand.
  * A tool or library to generate a parser: for example ANTLR, which you can use to build parsers for any language.

## Use an Existing Library

The first option is the best for well-known and supported languages, like [XML](https://docs.oracle.com/cd/B28359_01/appdev.111/b28394/adx_j_parser.htm) or [HTML](https://jsoup.org/). A good library usually also includes an API to programmatically build and modify documents in that language. This is typically more of what you get from a basic parser. The problem is that such libraries are not so common and they support only the most common languages. In other cases, you are out of luck.

## Building Your Own Custom Parser by Hand

You could need to go for the second option if you have particular needs. Both in the sense that the language you need to parse cannot be parsed with traditional parser generators, or you have specific requirements that you cannot satisfy using a typical parser generator. For instance, because you need the best possible performance or a deep integration between different components.

## A Tool or Library to Generate a Parser

In all other cases, the third option should be the default one, because it is the one that is most flexible and has the shorter development time. That is why, in this article, we concentrate on the tools and libraries that correspond to this option.

**Note**: Text in blockquotes describing a program comes from the respective documentation.

### Tools To Create Parsers

We are going to see:

  * Tools that can generate parsers usable from Java (and possibly from other languages)
  * Java libraries to build parsers

Tools that can be used to generate the code for a parser are called **parser generators** or** compiler-compilers**. Libraries that create parsers are known as **parser combinators**.

Parser generators (or parser combinators) are not trivial: You need some time to learn how to use them, and not all types of parser generators are suitable for all kinds of languages. That is why we have prepared a list of the best-known of them, with a short introduction for each of them. We are also concentrating on one target language: Java. This also means that (usually) the parser itself will be written in Java.

To list all possible tools and libraries parser for all languages would be kind of interesting, but not that useful. That is because there would be simply too many options, and we would all get lost in them. By concentrating on one programming language, we can provide an apples-to-apples comparison and help you choose one option for your project.

## Useful Things to Know About Parsers

To make sure that this list is accessible to all programmers, we have prepared a short explanation of terms and concepts that you may encounter searching for a parser. We are not trying to give you formal explanations, but practical ones.

### Structure of a Parser

A parser is usually composed of two parts: a _lexer_, also known as _scanner_ or _tokenizer_, and the proper parser. Not all parsers adopt this two-step schema: Some parsers do not depend on a lexer. They are called _scannerless parsers_.

A lexer and a parser work in sequence: The lexer scans the input and produces the matching tokens, the parser scans the tokens and produces the parsing result.

Let's look at the following example and imagine that we are trying to parse a mathematical operation.

The lexer scans the text and finds '4', '3', '7' and then the space. The job of the lexer is to recognize that the first characters constitute one token of type _NUM._ Then the lexer finds a '+' symbol, which corresponds to a second token of type _PLUS_, and lastly, it finds another token of type _NUM_.

![The input stream is transformed in Tokens and then in an AST by the parser](https://i2.wp.com/tomassetti.me/wp-content/uploads/2017/02/lexer-parser-center.png?w=1100&ssl=1)

> _The parser will typically combine the tokens produced by the lexer and group them._

The definitions used by lexers or parser are called _rules_ or _productions_. A lexer rule will specify that a sequence of digits correspond to a token of type _NUM_, while a parser rule will specify that a sequence of tokens of type _NUM, PLUS, NUM _corresponds to an expression.

**Scannerless parsers** are different because they process directly the original text, instead of processing a list of tokens produced by a lexer.

It is now typical to find suites that can generate both a lexer and parser. In the past, it was instead more common to combine two different tools: One to produce the lexer and one to produce the parser. This was, for example, the case of the venerable lex & yacc couple: lex produced the lexer, while yacc produced the parser.

### Parse Tree and Abstract Syntax Tree

There are two terms that are related and sometimes they are used interchangeably: parse tree and Abstract SyntaxTree (AST).

Conceptually they are very similar:

  * They are both **trees**: There is a root representing the whole piece of code parsed. Then there are smaller subtrees representing portions of code that become smaller until single tokens appear in the tree
  * The difference is the level of abstraction: The parse tree contains all the tokens that appeared in the program and possibly a set of intermediate rules. The AST instead is a polished version of the parse tree where the information that could be derived or is not important to understand the piece of code is removed

In the AST, some information is lost. For instance, comments and grouping symbols (parentheses) are not represented. Things like comments are superfluous for a program and grouping symbols are implicitly defined by the structure of the tree.

A parse tree is a representation of the code closer to the concrete syntax. It shows many details of the implementation of the parser. For instance, usually rules correspond to the type of a node. They are usually transformed in AST by the user, with some help from the parser generator.

A graphical representation of an AST looks like this.

![An abstract syntax tree for the Euclidean algorithm](https://i0.wp.com/tomassetti.me/wp-content/uploads/2017/01/798px-Abstract_syntax_tree_for_Euclidean_algorithm.svg_.png?w=798&ssl=1)

Sometimes you may want to start producing a parse tree and then derive from it an AST. This can make sense because the parse tree is easier to produce for the parser (it is a direct representation of the parsing process) but the AST is simpler and easier to process via the following steps (and by the following steps, we mean all the operations that you may want to perform on the tree): code validation, interpretation, compilation, etc..

> A grammar is a formal description of a language that can be used to recognize its structure.

In simple terms, a grammar is a list of rules that define how each construct can be composed. For example, a rule for an if statement could specify that it must starts with the "if" keyword, followed by a left parenthesis, an expression, a right parenthesis, and a statement.

A rule could reference other rules or token types. In the example of the if statement, the keyword "if", the left, and the right parenthesis were token types, while the expression and statement were references to other rules.

The most used format to describe grammars is the **Backus-Naur Form (BNF)**, which also has many variants, including the **Extended Backus-Naur Form**. The Extented variant has the advantage of including a simple way to denote repetitions. A typical rule in a Backus-Naur grammar looks like this:

The `<symbol>` is usually nonterminal, which means that it can be replaced by the group of elements on the right, `__expression__`. The element `__expression__` could contain other nonterminal symbols or terminal ones. Terminal symbols are simply the ones that do not appear as a `<symbol>` anywhere in the grammar. A typical example of a terminal symbol is a string of characters, like "class".

In the context of parsers, an important feature is support for left-recursive rules. This means that a rule could start with a reference to itself. This reference could be also indirect.

Consider for example arithmetic operations. An addition could be described as two expression(s) separated by the plus (+) symbol, but an expression could also contain other additions.

This description also matches multiple additions, like 5 + 4 + 3. That is because it can be interpreted as expression (5) ('+') expression(4+3). And then 4 + 3 itself can be divided into its two components.

The problem is that these kinds of rules may not be used with some parser generators. The alternative is a long chain of expressions that takes care also of the precedence of operators.

Some parser generators support direct left-recursive rules, but not an indirect one.

### Types of Languages and Grammars

We care mostly about two types of languages that can be parsed with a parser generator:_ regular languages_ and _context-free language_s. We could give you the formal definition according to the [Chomsky hierarchy of languages](https://en.wikipedia.org/wiki/Chomsky_hierarchy), but it would not be that useful. Let's look at some practical aspects instead.

A regular language can be defined by a series of regular expressions, while a context-free one needs something more. A simple rule of thumb is that if a grammar of a language has recursive elements it is not a regular language. For instance, as we said elsewhere, [HTML is not a regular language](https://tomassetti.me/antlr-mega-tutorial/). In fact, most programming languages are context-free languages.

Usually, there are regular grammars and context-free grammars that correspond respectively to regular and context-free languages. But to complicate matters, there is a relatively new (created in 2004) kind of grammar, called Parsing Expression Grammar (PEG). These grammars are as powerful as Context-free grammars, but according to their authors, they more naturally describe programming languages.

#### The Differences Between PEG and CFG

The main difference between PEG and CFG is that the ordering of choices is meaningful in PEG, but not in CFG. If there are many possible valid ways to parse an input, a CFG will be ambiguous and thus wrong. Instead, with PEG, the first applicable choice will be chosen, and this automatically solves some ambiguities.

Another difference is that PEG uses scannerless parsers: They do not need a separate lexer or lexical analysis phase.

Traditionally, both PEG and some CFGs have been unable to deal with left-recursive rules, but some tools have found workarounds for this -- either by modifying the basic parsing algorithm, or by having the tool automatically rewrite a left-recursive rule in a nonrecursive way. Either of these ways has downsides: Wither by making the generated parser less intelligible or by worsening its performance. However, in practical terms, the advantages of easier and quicker development outweigh the drawbacks.

## Stay Tuned

That's all for Part 1, but stay close. Coming up, we'll delve into parser generators, their workflows, the various types, and some examples of them in action.

Understand the needs and benefits around implementing [the right monitoring solution for a growing containerized market](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics.](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital)
