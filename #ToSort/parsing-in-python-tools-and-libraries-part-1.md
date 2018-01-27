# Parsing in Python: Tools and Libraries (Part 1)

_Captured: 2018-01-02 at 04:30 from [dzone.com](https://dzone.com/articles/parsing-in-python-tools-and-libraries-part-1?edition=347148&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-01)_

Access NoSQL and Big Data through SQL using standard drivers (ODBC, JDBC, ADO.NET). [Free Download ](https://dzone.com/go?i=250345&u=https%3A%2F%2Fwww.cdata.com%2Ftech%2Fbigdata%2F%3Futm_source%3Ddzone%26utm_medium%3Dbump3%2520)

If you need to parse a language or document from Python, there are fundamentally three ways to do so:

  1. **Use an existing library supporting that specific language**: The first option is the best for well-known and supported languages like XML or HTML. A good library usually also includes APIs to programmatically build and modify documents in that language. This is typically more of what you get from a basic parser. The problem is that such libraries are not so common and they support only the most common languages. In other cases, you are out of luck.
  2. **Building your own custom parser by hand**: You may need to pick the second option if you have particular needs, whether the language that you need to parse cannot be parsed with traditional parser generators or you have specific requirements that you cannot satisfy using a typical parser generator. For instance, maybe you need the best possible performance or a deep integration between different components.
  3. **A tool or library to generate a parser**: In all other cases, the third option should be the default one because it is the most flexible and has a shorter development time. (For example, ANTLR can be used to build parsers for any language.) That is why, in this article, we concentrate on the tools and libraries that correspond to this option.

**Note**: Any text in a blockquote describing a program comes from the respective documentation.

## Tools to Create Parsers

We are going to see:

  * Tools that can generate parsers usable by Python (and possibly from other languages).
  * Python libraries to build parsers.

Tools that can be used to generate the code for a parser are called parser generators or compilers. Libraries that create parsers are known as parser combinators.

Parser generators (or parser combinators) are not trivial; you need some time to learn how to use them and not all types of parser generators are suitable for all kinds of languages. That is why we have prepared a list of the best known of them with a short introduction for each. We also concentrate on one target language: Python. This also means that (usually) the parser itself will be written in Python.

To list all possible tools and libraries parser for all languages would be kind of interesting, but not that useful. That is because there would be simply too many options and we would get lost in all of them. By concentrating on _one_ programming language, we can provide an apples-to-apples comparison and help you choose one option for your project.

## Useful Things to Know About Parsers

To make sure that this list is accessible to all programmers, we have prepared a short explanation of terms and concepts that you may encounter searching for a parser. We are not trying to give you formal explanations, but _practical_ ones.

### Structure of a Parser

A parser is usually composed of two parts: a lexer, also known as scanner or tokenizer, and the proper parser. Not all parsers adopt this two-step schema; some parsers do not depend on a lexer. They are called scannerless parsers.

A lexer and a parser work in sequence: the lexer scans the input and produces the matching tokens, while the parser scans the tokens and produces the parsing result.

Let's look at the following example and imagine that we are trying to parse a mathematical operation.

The lexer scans the text and finds 4, 3, and 7, and then the space. The job of the lexer is to recognize that the first characters constitute one token of type NUM_._ Then the lexer finds a + symbol, which corresponds to the second token of type PLUS, and lastly, it finds another token of type NUM.

![The input stream is transformed in Tokens and then in an AST by the parser](https://i2.wp.com/tomassetti.me/wp-content/uploads/2017/02/lexer-parser-center.png?w=1100&ssl=1)

> _The parser will typically combine the tokens produced by the lexer and group them._

The definitions used by lexers or parsers are called rules or productions. A lexer rule will specify that a sequence of digits corresponding to a token of type NUM, while a parser rule will specify that a sequence of tokens of type NUM, PLUS, NUM corresponds to an expression.

Scannerless parsers are different because they directly process the original text instead of processing a list of tokens produced by a lexer.

It is now typical to find suites that can generate both a lexer and parser. In the past, it was more common to combine two different tools: one to produce the lexer and one to produce the parser. This was, for example, the case of the venerable lex and yacc couple -- lex produced the lexer, while yacc produced the parser.

### Parse Tree and Abstract Syntax Tree

There are two terms that are related, and sometimes, they are used interchangeably: parse tree and abstract syntax tree (AST).

Conceptually, they are very similar.

**They are both trees**. There is a root representing the whole piece of code parsed. Then, there are smaller subtrees representing portions of code that become smaller until single tokens appear in the tree.

**The difference is the level of abstraction**. The parse tree contains all the tokens that appeared in the program and possibly a set of intermediate rules. The AST, instead, is a polished version of the parse tree where the information that could be derived or is not important to understand the piece of code is removed.

In the AST, some information is lost; for instance, comments and grouping symbols (parentheses) are not represented. Things like comments are superfluous for a program and grouping symbols are implicitly defined by the structure of the tree.

A parse tree is a representation of the code closer to the concrete syntax. It shows many details of the implementation of the parser. For instance, usually, a rule corresponds to the type of a node. A parse tree is usually transformed in an AST by the user, possibly with some help from the parser generator.

A graphical representation of an AST looks like this.

![An abstract syntax tree for the Euclidean algorithm](https://i0.wp.com/tomassetti.me/wp-content/uploads/2017/01/798px-Abstract_syntax_tree_for_Euclidean_algorithm.svg_.png?w=798&ssl=1)

Sometimes, you may want to start producing a parse tree and then derive from it an AST. This can make sense because the parse tree is easier to produce for the parser (it is a direct representation of the parsing process) but the AST is simpler and easier to process by following the steps that you typically want to perform on the tree: code validation, interpretation, compilation, etc.

Stay tuned for Part 2, where we'll discuss more useful things to know about parsers!

[The fastest databases need the fastest drivers](https://dzone.com/go?i=250346&u=https%3A%2F%2Fwww.cdata.com%2Fblog%2Fnews%2F20170601-bigquery-driver-comparison%3Futm_source%3Ddzone%26utm_medium%3Dbump4) \- learn how you can leverage CData Drivers for high performance NoSQL & Big Data Access.
