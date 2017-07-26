# The Best Programming Languages for Each Situation, Part 1

_Captured: 2017-06-13 at 17:14 from [dzone.com](https://dzone.com/articles/the-best-programming-languages-for-each-situation-1?edition=304170&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-12)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

There is a question that many people take as a sign that the questioner does not understand the subject at all. Some people even find it enraging. The question is usually in the form of, _What is the best X?_ What is the best car? What is the best programming language? But at the same time, it is a question that we ask ourselves every time we start a project or we pick a car.

The difference, of course, is that we ask this question in our specific context. We want to know the best programming language for us, for the situation we are in.

We obviously cannot know your situation, but with this article, we hope to provide useful information to whoever is thinking about entering a new field or just wants to know the current state of the field.

## Changing the Programming Language Has Costs

If you have a large codebase, you probably do not really choose a language for a new project. You just use the one you have used so far. The main factor is the cost of adding a new language. Hiring new developers, changing your infrastructure, learning the best practices, is simply too much for many companies.

Another problem is that while it is reasonably possible to learn a new language in a month or two, it takes much longer to become proficient in that language. So both developers and their employers prefer to take advantage of the knowledge they already have.

In such cases, the answer to the best programming language question usually becomes what you are already using, which is a boring answer. Although this does not necessarily mean that is the wrong answer.

## When to Change Programming Language

![Fail Whale of Twitter](https://i0.wp.com/tomassetti.me/wp-content/uploads/2017/06/fail_whale.jpg?w=600&ssl=1)

No language is perfect, in fact, there seem to be new problems with Scala, [such as the learning curve](https://en.wikipedia.org/wiki/Scala_\(programming_language\)#Criticism). But it is fair to say that, in some situations, it is not true that all languages are equal. Which is a common refrain.

> When you have significant and peculiar needs, some languages are really better than others.

## A Huge Amount of Money Can Change the Language Itself

![HHVM reduced the median page save time by half on Wikipedia](https://i1.wp.com/tomassetti.me/wp-content/uploads/2017/06/10333100_342177062633041_810356125_n.png?w=650&ssl=1)

HipHop for PHP, a PHP-to-C++ transpiler, and then the more famous [HHVM](https://en.wikipedia.org/wiki/HHVM), a virtual machine for PHP and Hack. In fact, they also invented a dialect of PHP called Hack.

They could keep PHP because its performance was not so bad, nor did they required it to be that much better. Twitter simply could not work with Ruby, while Facebook could work with PHP - it just simply cost a little more.

## A Few Criteria for Choosing a Language

While we all agree that there is not a best programming language in absolute terms, we think that there are _preferable programming languages for specific tasks_. We think that it is possible to set some reasonable criteria to guide professional developers and businesses alike. These criteria can help you choose the best programming language for your situation.

### Good Enough Technical Qualities

Aside from the obvious performance requirements, the language must have good technical qualities for your needs. For instance, if your software is heavily concurrent you need a language that has first-rate support for that.

Another problem that Twitter had was that the LAMP model of Ruby deployment did not support encapsulation well. So it was difficult to build a separate and independent storage or search service. This was not a case of _Ruby is bad_, but more _Ruby is designed for something else_. Remember that technical qualities do not just mean the things you can measure and see, like performance or the syntax. It also means how the language works behind the scenes.

So you do need to choose a language that fits well your use case, a language that checks all the boxes. Although you do not necessarily need to pick the one that best fits your use case. That is because it is not always possible to rank different needs or, even if it were, you might not know which one matters the most to you.

For example, imagine that you can determine that language X would be better if you have 5 million users or more, while language Y would make it easier and cheaper to reach 5 million users. How can you know if you will ever reach 5 million users? Maybe language X would be too costly to use at the start and so your company will fail before reaching that many users.

Consider technical requirements as a filter, your language must pass them, but it does not need to be the best possible language for that.

### Popularity

The language you choose should be popular enough. This can help you save money and time, especially because of open source development. For instance, if your company uses PHP, now you can take advantage of the hard work of Facebook developers. You can use HHVM to improve the performance of your software. It can also make it more probable to find good, ready-to-use libraries to speed up your development.

There are several ways to [measure the popularity of a programming language](https://en.wikipedia.org/wiki/Measuring_programming_language_popularity):

  * The number of jobs available that require knowledge of that language.
  * The number of search engine searches for that language.
  * The number of GitHub projects that use that language.

All of them are useful, none of them are perfect. For instance, there are many JavaScript projects on GitHub that are composed of one file and are currently inactive. That is simply because the language and the tools encourage you to create very small libraries. How can you understand the popularity of a language called Go (there is also another one called Go!) looking at search engine results?

### Community Fit

The language must also be popular in the community you belong to. A good community fit has many advantages: developers think the way you want them to think and they also usually have non-programming skills or knowledge that you need. Which means that you have to spend less time in training them and you are less at risk of hiring the wrong developer.

PHP has improved a lot in the technical department, but it is still chosen by people that want programming to be easy. Which means that there are many not-that-good PHP programmers and it might be hard to find the good ones. Even worse, you may not find out if they are good until you have them work on your project and you see the results.

On the other hand, maybe not all people that work professionally with C and C++ have a computer science degree, but they all probably think like the people that do have one. I say this because if you do not think, plan, and write C/C++ code in the proper way, your code will make you suffer for your mistakes soon enough.

Also, some languages are typically embraced by certain communities, so there are more libraries to cover that area. Think about the number of libraries that are being developed to analyze data in Python. This is a consequence of the fact that many data scientists have embraced Python. You can benefit from this by adopting Python if you need to develop applications in that area.

Tune in next time for Part 2 where we discuss the best programming languages for specific contexts, such as game dev, academia, and building systems.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
