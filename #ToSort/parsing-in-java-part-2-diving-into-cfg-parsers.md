# Parsing in Java (Part 2): Diving Into CFG Parsers

_Captured: 2017-06-09 at 03:14 from [dzone.com](https://dzone.com/articles/parsing-in-java-part-2-diving-into-cfg-parsers?edition=304143&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-07)_

In case you missed [Part 1](https://dzone.com/articles/parsing-in-java-part-1-structures-trees-and-rules), we covered the basics of how parsing works, then dove a bit deeper into the architecture of parsers, considering overviews the different types available, parse trees vs. ASTs, and more. Here in Part 2, we'll touch on parser generators before diving into context-free grammars. Part 3 will then follow up with a look at parsing expression grammars (PEGs).

## Parser Generators

The basic workflow of a parser generator tool is quite simple: You write a grammar that defines the language, or document, and you run the tool to generate a parser usable from your Java code.

The parser might produce the AST, which you may have to traverse yourself, or you can traverse with additional ready-to-use classes, such [Listeners](https://en.wikipedia.org/wiki/Observer_pattern) or [Visitors](https://en.wikipedia.org/wiki/Visitor_pattern). Some tools instead offer the chance to embed code inside the grammar to be executed every time the specific rule is matched.

Usually, you need a runtime library and/or program to use the generated parser.

### Regular (Lexer)

Tools that analyze regular languages are typically lexers.

We are not going to talk about it because it is very basic, but Java includes a library to parse data with numbers and simple patterns: [java.util.Scanner](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html). It could be defined as a smart library to read streams of data. It might be worth it to check it out if you need to quickly parse some data.

[JFlex](http://jflex.de/) is a lexical analyzer (lexer) generator based upon deterministic finite automata (DFA). A JFlex lexer matches the input according to the defined grammar (called spec) and executes the corresponding action (embedded in the grammar).

It can be used as a standalone tool, but being a lexer generator, it is designed to work with parser generators: Typically, it is used with CUP or BYacc/J. It can also work with ANTLR.

The typical grammar (spec) is divided into three parts, separated by '%%':

  1. Usercode, which will be included in the generated class
  2. Options/macros
  3. And finally the lexer rules.

A JFlex spec file:

Let's see the tools that generate Context Free parsers.

#### **ANTLR**

[ANTLR](http://www.antlr.org/) is probably the most used parser generator for Java. ANTLR is based on a new LL algorithm developed by the author and described in this paper: [Adaptive LL(*) Parsing: The Power of Dynamic Analysis (PDF)](http://www.antlr.org/papers/allstar-techreport.pdf).

It can output parsers in many languages, but the real added value of a vast community is the[ large number of grammars available](https://github.com/antlr/grammars-v4). Version 4 supports direct left-recursive rules.

It provides two ways to walk the AST, instead of embedding actions in the grammar: visitors and listeners. The first one is suited for when you have to manipulate or interact with the elements of the tree, while the second is useful when you just have to do something when a rule is matched.

The typical grammar is divided into two parts: lexer rules and parser rules. The division is implicit, since all the rules starting with an uppercase letter are lexer rules, while the ones starting with a lowercase letter are parser rules. Alternatively, lexer and parser grammars can be defined in separate files.

A very simple ANTLR grammar:

If you are interested in ANTLR, you can look into this giant [ANTLR tutorial](http://tomassetti.me/antlr-mega-tutorial) we have written.

[APG](http://www.coasttocoastresearch.com/overview) is a recursive-descent parser using a variation of **Augmented BNF**, that they call Superset Augmented BNF. ABNF is a particular variant of BNF designed to better support a bi-directional communications protocol. APG also support additional operators, like syntactic predicates and custom user-defined matching functions.

It can generate parsers in C/C++, Java, and JavaScript. Support for the last language seems superior and more up to date: It has a few more features and seems more updated. In fact, the documentation says it is designed to have the look and feel of JavaScript RegExp.

> Because it is based on ABNF, it is especially well-suited to parsing the languages of many Internet technical specifications and, in fact, is the parser of choice for a number of large Telecom companies.

An APG grammar is very clean and easy to understand:

[BYACC](http://byaccj.sourceforge.net/) is Yacc that generates Java code. That is the whole idea, and it defines its advantages and disadvantages. It is well-known, and it allows easier conversion of a Yacc and C program to a Java program -- although you obviously still need to convert all the C code embedded in semantic actions into Java code. Another advantage is that you do not need a separate runtime. The generated parser it is all you need.

On the other hand, it is old, and the parsing world has made many improvements. If you are an experienced Yacc developer with a code base to upgrade, it is a good choice. Otherwise, there are many more modern alternatives you should consider.

The typical grammar is divided into three sections, separated by '%%': DECLARATIONS, ACTIONS, and CODE. The second one contains the grammar rules and the third one has the custom user code.

A BYACC grammar:

Coco/R is a compiler generator that takes an attributed grammar and generates a scanner and a recursive descent parser. Attributed grammar means that the rules, written in an EBNF variant, can be annotated in several ways to change the methods of the generated parser.

The scanner includes support for dealing with things like compiler directives, called pragmas. They can be ignored by the parser and handled by custom code. The scanner can also be suppressed and substituted with one built by hand.

Technically, all the grammars must be LL(1). That is to say that the parser must be able to choose the correct rule only looking one symbol ahead. But Coco/R provides several methods to bypass this limitation, including semantic checks, which are basically custom functions that must return a boolean value. The manual also provides some suggestions for refactoring your code to respect this limitation.

A Coco/R grammar:

Coco/R has a good documentation, with several example grammars. It supports several languages, including Java, C#, and C++.

[CookCC](https://github.com/coconut2015/cookcc) is a LALR (1) parser generator written in Java. Grammars can be specified in three different ways:

  * In Yacc format: It can read grammars defined for Yacc.
  * In its own XML format.
  * In Java code, by using specific annotations.

A unique feature is that it can also output a Yacc grammar. This can be useful if you need to interact with a tool that supports a Yacc grammar, like some old C program with which you must maintain compatibility.

It requires Java 7 to generate the parser, but it can run on earlier versions.

A typical parser defined with annotations will look like this:

For the standard of parser generators, using Java annotations it is a peculiar choice. Compared to an alternative like ANTLR, there is certainly a less clear division between the grammar and the actions. This could make the parser harder to maintain for complex languages. Also, porting to another language could require a complete rewrite.

On the other hand, this approach permits you to mix grammar rules with the actions to perform when you match them. Furthermore, it has the advantage of being integrated into the IDE of your choice, since it is just Java code.

[CUP](http://www2.cs.tum.edu/projects/cup/) is the acronym of Construction of Useful Parsers and is a LALR parser generator for Java. It just generates the proper parser part, but it is well-suited to work with JFlex -- although, obviously, you can also build a lexer by hand to work with CUP. The grammar has a syntax similar to Yacc and it allows you to embed code for each rule.

It can automatically generate a parse tree, but not an AST.

It also has an Eclipse plugin to aid you in the creation of a grammar, so effectively it has its own IDE.

The typical grammar is similar to YACC.

A CUP grammar:

> [Grammatica](https://grammatica.percederberg.net/index.html) is a C# and Java parser generator (compiler compiler). It reads a grammar file (in an EBNF format) and creates well-commented and readable C# or Java source code for the parser. It supports LL(k) grammars, automatic error recovery, readable error messages, and a clean separation between the grammar and the source code.

The description on the Grammatica website is itself a good representation of Grammatica: simple to use, well-documented, with a good number of features. You can build a listener by subclassing the generated classes, but not a visitor. There is a good reference, but not many examples.

A typical grammar of Grammatica is divided into three sections: header, tokens, and productions. It is also clean, almost as much as an ANTLR grammar. It is also based on a similar Extended BNF, although the format is slightly different.

A Grammatica grammar:

[Jacc](https://github.com/zipwith/jacc) is similar to BYACC/J, except that is written in Java and thus it can run wherever your program can run. As a rule of thumb, it is developed as a more modern version of Yacc. The author describes small improvements in areas like error messages, modularity, and debugging support.

If you know Yacc and you do not have any code base to upgrade, it might be a great choice.

[JavaCC](https://javacc.org/) is the other widely used parser generator for Java. The grammar file contains actions and all the custom code needed by your parser.

Compared to ANTLR, the grammar file is much less clean and includes a lot of Java source code.

A JavaCC grammar:

Thanks to its long history, it is used in important projects, like JavaParser. At the same time, this has left some quirks in the documentation and usage. For instance, technically, JavaCC itself does not build an AST, but it comes with a tool that does it, JTree, so for practical purposes, it does.

[There is a grammar repository](https://javacc.org/grammar-library), but it does not have many grammars in it. It requires Java 5 or later.

> [ModelCC](http://www.modelcc.org/) is a model-based parser generator that decouples language specification from language processing [..]. ModelCC receives a conceptual model as input, along with constraints that annotate it.

In practical terms, you define a model of your language, that works as a grammar, in Java, using annotations. Then you feed the model to ModelCC to obtain a parser.

With ModelCC, you define your language in a way that is independent of the parsing algorithm used. Instead, it should be the best conceptual representation of the language -- although, under the hood, it uses a traditional parsing algorithm. So the grammar_ per se_ uses a form that is independent of any parsing algorithm, but ModelCC does not use magic and produces a normal parser.

There is a clear description of the intentions of the authors of the tools, but limited documentation. Nonetheless, there are examples available, including the following model for a calculator partially shown here.

[SableCC](http://www.sablecc.org/) is a parser generator created for a thesis and aims to be easy to use and to offer a clean separation between grammar and Java code. Version 3 should also offer an included ready-to-use way to walk the AST through using a visitor. But that is all in theory because there is virtually no documentation and we have no idea how to use any of these things.

Also, a version 4 was started in 2015 and apparently lies abandoned.

[Urchin(CC)](http://urchincc.org/) is a parser generator that allows you to define a grammar, called an Urchin parser definition. Then, you generate a Java parser from it. Urchin also generates a visitor from the UPD.

There is an exhaustive tutorial that is also used to explain how Urchin works and its limitations, but the manual is limited.

A UPD is divided into three sections: terminals, token, and rules.

A UPD file:

## Stay Tuned

Now that we've covered CFG parsers, it's time to dive into the world of PEG parsers. We'll cover a comprehensive list of those parsers in our next installment, which will cap off this series.
