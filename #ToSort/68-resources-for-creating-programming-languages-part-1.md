# 68 Resources for Creating Programming Languages, Part 1

_Captured: 2017-04-24 at 08:09 from [dzone.com](https://dzone.com/articles/68-resources-for-creating-programming-languages-pa?oid=twitter&utm_content=buffer15627&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

Here it is - a new **guide, to collect and organize all the knowledge that you need to create your own programming language from scratch**.

Creating a programming language is one of the most fascinating challenges you can dream of as a developer.

The problem is that there are a lot of moving parts, a lot of things to do right and it is difficult to find a well-detailed map to show you the way. Sure, you can find a tutorial on writing half a parser, a half-baked list of advice on language design, an example of a naive interpreter. To find those things you will need to spend hours navigating forums and following links.

We thought it would be interesting to collect relevant resources, evaluate them and organize them, so you can **spend time using good resources, not looking for them**.

We organized the resources around the three stages in the creation of a programming language: design, parsing, and execution. In this article, we'll go over the resources you need to get an understanding of designing a language, and parsing.

## Designing the Language

When creating a programming language you need to take ideas and transform them into decisions. This is what you do during the design phase.

Let's go over some good resources to beef up your knowledge on language design.

  * [Designing the next programming language? Understand how people learn!](http://www.theenterprisearchitect.eu/blog/2013/02/14/designing-the-next-programming-language-understand-how-people-learn/) This article presents a few considerations on how to design a programming language so that it's easy to understand.
  * [Five Questions About Language Design](http://www.paulgraham.com/langdes.html). Some good (and some random) notes on programming language design by Paul Graham.
  * [Design Concepts in Programming Languages](https://mitpress.mit.edu/books/design-concepts-programming-languages). If you want to make deliberate choices in the creation of your programming language, this is the book you need. Otherwise, if you don't already have the necessary theoretical background, you risk doing things the way everybody else does them. It's also useful to develop a general framework to understand how the different programming languages behave and why.
  * [Practical Foundations for Programming Languages](http://www.cambridge.org/it/academic/subjects/computer-science/programming-languages-and-applied-logic/practical-foundations-programming-languages-2nd-edition). This is, for the most part, a book about studying and classifying programming languages. But by understanding the different options available it can also be used to guide the implementation of your programming language.
  * [Programming Language Pragmatics, 4th Edition](https://www.elsevier.com/books/programming-language-pragmatics/scott/978-0-12-410409-9). This is the most comprehensive book to read when one is trying to understand contemporary programming languages. It discusses different aspects of everything from C# to OCaml and even the different kinds of programming languages such as functional and logical ones. It also covers the several steps and parts of the implementation, such as an intermediate language, linking, virtual machines, etc.
  * [Structure and Interpretation of Computer Programs, Second Edition](https://mitpress.mit.edu/books/structure-and-interpretation-computer-programs). This an introduction to computer science for people that already have a degree in it. A book widely praised by programmers, including Paul Graham (directly on the book's [Amazon Page](https://www.amazon.com/Structure-Interpretation-Computer-Programs-Second/dp/0070004846/)), that helps you develop a new way of thinking about programming languages. It's quite abstract and examples are proposed in Scheme. It also covers many different aspects of programming languages, including advanced topics like garbage collection.

Long discussions and infinite disputes are fought around type systems. Whatever choices you end up making it make sense to know the different positions.

  * These are two good introductory articles on the subject of type systems. The first article discusses the dichotomy [Static/Dynamic](https://thesocietea.org/2015/11/programming-concepts-static-vs-dynamic-type-checking/) type checking, and the second one dives into [Introspection](https://thesocietea.org/2016/02/programming-concepts-type-introspection-and-reflection/).
  * [What To Know Before Debating Type Systems](https://cdsmith.wordpress.com/2011/01/09/an-old-article-i-wrote/). If you already know the basics of type systems, then this article is for you. It will allow you to understand them better by going into definitions and details.
  * [Type Systems (PDF)](http://lucacardelli.name/Papers/TypeSystems.pdf). This a paper on the formalization of Type Systems that also introduces more precise definitions of the different type systems.
  * [Types and Programming Languages](https://mitpress.mit.edu/books/types-and-programming-languages). A comprehensive book on understanding type systems. It will definitely have an impact on your ability to design programming languages and compilers. It has a strong theoretical basis, but it also explains the practical importance of individual concepts.
  * [Functional Programming and Type Systems](http://gallium.inria.fr/~remy/mpri/). An interesting university course on type systems for functional programming. It is used in a well-known French university. There is also notes and presentation material available. It is as advanced, as you would expect.
  * [Type Systems for Programming Languages](http://www.doc.ic.ac.uk/~svb/TSfPL/). This is a simpler course on Type Systems for (functional) programming languages.

## Parsing

Parsing transforms concrete syntax into a form that is more manageable for computers. This usually means transforming text written by humans into a more useful representation of the source code, an Abstract Syntax Tree.

![An abstract syntax tree for the Euclidean algorithm](https://i0.wp.com/tomassetti.me/wp-content/uploads/2017/01/798px-Abstract_syntax_tree_for_Euclidean_algorithm.svg_.png?resize=266%2C300&ssl=1)

There are usually two components in parsing: a lexical analyzer and the proper parser. Lexers, which are also known as tokenizers or scanners, transform the individual characters into tokens, the atom of meaning. Parsers instead organize the tokens in the proper Abstract Syntax Tree for the program. But since they are usually meant to work together you may use a single tool that does both tasks.

  * Using [Flex](https://github.com/westes/flex) as a lexer generator, and [(Berkeley) Yacc](http://invisible-island.net/byacc/byacc.html) or [Bison](https://www.gnu.org/software/bison/) to generate the proper parser, are the venerable choices to generate a complete parser. They are a few decades old and they are still maintained as open source software. They are written in and created for C/C++. They still work, but they have limitations in features and support for other languages.
  * [ANTLR](https://github.com/antlr/antlr4) is both a lexer and a parser generator. It's also more actively developed as open source software. It is written in Java, but it can generate both the lexer and the parser in languages as varied as C#, C++, Python, Javascript, Go, etc.
  * _Your own lexer and parser. _If you need the best performance and you can create your own parser. You just need to have the necessary computer science knowledge.
  * [Flex and Bison tutorial](http://aquamentus.com/flex_bison.html) offers a good introduction to the two tools with bonus tips.
  * [Lex and Yacc Tutorial](http://epaperpress.com/lexandyacc/index.html). At 40 pages, this is the ideal starting point to learn how to put together lex and yacc in a few hours.
  * The best video tutorial that I've found on lex/Yacc comes in two parts ([Part 1](https://www.youtube.com/watch?v=54bo1qaHAfk), [Part 2](https://www.youtube.com/watch?v=__-wUHG2rfM)). In an hour of video, you can learn the basics of using lex and yacc.
  * [ANTLR Mega Tutorial](https://tomassetti.me/antlr-mega-tutorial/) is a renowned and beloved tutorial that explains everything you need to know about ANTLR, with bonus tips and tricks and extra resources to help you learn even more.
  * [lex & yacc](http://shop.oreilly.com/product/9781565920002.do). Despite being a book written in 1992 it's still the most recommended book on the subject. Some people say that's because of the lack of competition, others because it is just that good.
  * [flex & bison: Text Processing Tools](http://shop.oreilly.com/product/9780596155988.do). The best book on the subject written in this millennium.
  * [The Definitive ANTLR 4 Reference](https://pragprog.com/book/tpantlr2/the-definitive-antlr-4-reference). Written by the main author of the tool, this is really the definitive book on ANTLR 4. It explains all of its secrets and it's also a good introduction to how the whole parsing thing works.
  * [Parsing Techniques, 2nd edition](http://www.springer.com/us/book/9780387202488). A comprehensive, advanced, and costly book to know more than you possibly need about parsing.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
