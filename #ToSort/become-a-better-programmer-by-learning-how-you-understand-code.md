# Become a Better Programmer by Learning How You Understand Code

_Captured: 2017-10-19 at 19:36 from [dzone.com](https://dzone.com/articles/become-a-better-programmer-by-learning-how-you-und?edition=334792&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-19)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

**Why do some programmers seem to have this magical ability to extract meaning from code in the blink of an eye?**

To try and answer this question I've gone digging to see what science knows about how we understand code.

As it turns out, we know a lot[ about the psychology of code comprehension](http://www.cs.colostate.edu/TechReports/Reports/1994/tr-120.pdf) and we can use this knowledge to become better programmers. It allows you to develop all aspects of the understanding process so you don't end up with bottlenecks in your programming skills.

In this post, I take a look at what we know about program understanding and discuss three ways we can use this knowledge to become better programmers.

## To Understand Code You Have to Build a Mental Model

The first step when programming is to [build a mental model](http://aestheticio.com/why-your-code-is-hard-to-understand/) of the problem so you can then complete your task. Your mental model is the driver behind understanding a problem or program.

The journey from code on a screen to a model in your head follows a fairly well-understood progression. Our understanding of the process is by no means complete but what we do know can be used to identify areas to focus on for improvement.

Let's take a look at how we understand code.

## Your Mental Model Is Built Up of Matches Between General and Specific Knowledge

The knowledge you use to understand your code is either general programming knowledge or software specific knowledge.

General knowledge includes knowledge about computer science concepts, programming languages, frameworks, and programming principles. Most tutorials will focus on this type of knowledge - things like design patterns, effective web stacks, proven enterprise architectures, anything generally applicable to a variety of solutions. Specific knowledge is knowledge about the particular program or problem you are busy with.

Forming a mental model consists of making associations between the code you are reading and your existing general and specific knowledge. "_This is a class._ _That is a loop._ _This function is filtering invoices by price._ "

Both of these types of knowledge can be new or existing. Sometimes you will need to learn new general knowledge to solve a problem. How a round-robin scheduler works, for example. Specific knowledge is more often new than existing, but sometimes you will have existing knowledge about the program you are currently working on through a history with that particular codebase.

Your mental model consists of the set of links between the general and specific knowledge you have that is relevant to this problem.

## These Matches Are Formed by Making, Testing and Modifying Hypotheses

The way we form matches is by making hypotheses.

Let's say you spot something that you recognize in the code. A beacon that reminds you of some higher level concept. "_That loop looks like a sort._ "

You then look for ways to test this hypothesis. "_Let's see if we are swapping two items in the loop._"

We then modify the hypothesis or accept it and start looking for new hypotheses to build on the one we just made.

You make a prediction about what something is, find ways to prove or disprove your prediction, modify based on results and repeat.

So how does this help us in understanding how to be a better programmer?

## There Are Three Ways You Can Become a Better Programmer:

Once you know that your ability to understand code is dependent on three things:

  1. Knowledge - The building blocks to solve the problem.
  2. Links - The glue between the building blocks.
  3. Hypotheses - The tools by which you form the links.

It becomes clear that getting better at programming requires a holistic approach.

### 1\. You Can Gain More General Knowledge

Since your ability to comprehend code depends on the number of matches you can make between your existing knowledge and the problem you are trying to solve it stands to reason that the more knowledge you have to work with the more success you will have.

As programmers, we spend a large portion of our time acquiring new knowledge. It's necessary if you want to stay current in the technology world. To get the most out of your research it's important to [focus on principles and not technologies](http://aestheticio.com/can-get-ahead-focusing-principles-technologies/).

With that in mind let's look at the types of knowledge you can add to your bag of tricks:

#### Language-Specific Knowledge

Language-specific knowledge is the area many developers focus on.

It's about learning the ins and outs of your language or framework of choice. Getting to know the API and language constructs, finding the strange language quirks and knowing exactly how things work under the hood.

It is usually fairly easy to find good courses and information for this category of knowledge.

This kind of knowledge is vital and every developer needs to know his tool-set inside-and-out.

The problem with this kind of knowledge is that there's always more. A new framework comes out. The next version of a language is released. The longer you have had this knowledge the less valuable it becomes (knowing how to read a punch-card isn't a hot skill anymore).

#### Programming Concepts

This type of knowledge has a longer shelf life. A sort will still be a sort in 20 years time.

Computer Science degrees spend a lot of time on these topics. You also learn these concepts as a side effect of learning languages and frameworks. The problem with learning these concepts from a language or framework is that it's sometimes difficult to separate the underlying concept from how it is expressed in syntax.

Some languages are also better or worse at expressing certain concepts. Knowing a few different frameworks and languages is helpful here. The alternative is to learn the concepts first and then learn how it is applied in different languages. It is much harder to find information and courses that take this approach. These concepts include things like patterns, algorithms, data structures, and many more.

#### Domain Knowledge

Understanding the industry you are working in gives you an extra set of non-programming concepts to use in your mental model. Understanding how an investment instrument works helps you understand code dealing with investment instruments, for example.

### 2\. You Can Get Better at Matching Code to General Knowledge

Once you have enough general knowledge you can focus on getting better at forming matches. If you know what clues to look for in the code and practice identifying them you will quickly get better at extracting meaning from code.

#### Learn to Recognize Code Beacons

Code beacons are patterns in your code that hint at an underlying concept. These patterns can span varying levels of complexity. They are snippets of code that light the way to higher level concepts.

For example, when you see code that follows this pattern:

> _Iterate over the elements in an array. Put elements into a new array based on a condition._

You know you are dealing with a filter.

Thinking about this block of code as "_a filter_" instead of "_a loop, with an if condition that then puts some items from the old array into a new array_ " allows you to hold more ideas in your head at the same time. You chunk a few smaller ideas into a bigger one.

Traditionally in software development, a "pattern" refers to the famous gang of four book [Design Patterns: Elements of Reusable Object-Oriented Software](http://www.amazon.com/gp/product/B000SEIBB8/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B000SEIBB8&linkCode=as2&tag=aesio-20&linkId=SUPRLUY7R5TOHI3D). While code beacons and design patterns are related, they are not the same thing. For example, there are code beacons for design patterns.

#### Learn the Rules of Discourse

Rules of discourse are the conventions and coding styles used within a framework or language. Just like the dialogue rules in a conversation they set expectations in the mind of the programmer. The way you name methods is different in Ruby and C#. Rails makes heavy use of the MVC pattern, other frameworks don't (Meteor.js for example).

Writing code that follows the expected rules of discourse makes the code significantly easier to understand. Even for experts.

This bit comes fairly naturally, you pick up these rules from reading example code or from your colleagues. Sometimes when moving to a new language or framework it is worth paying special attention to this. It's a quick way to feel more comfortable in a new language.

### 3\. You Can Get Better at Forming and Revising Hypotheses

The last piece of the puzzle is getting better at forming and revising hypotheses. The better you are at making a hypothesis that is likely to be correct, the faster you will be able to build your mental model.

#### Use a Systematic Approach

A systematic approach to building a mental model involves reading every line of code and focusing on building your knowledge as you go. It generally yields the best results but quickly becomes impractical for larger code bases. This is best suited for highly critical code that is of a manageable size. I've found this to be quite rare in the real world. Usually, you deal with large, sprawling code bases that have grown over many years.

#### Use an Opportunistic Approach

With an opportunistic approach, you look for interesting pieces of code, form a hypothesis about what it does, then start digging to see if you are on the right track. Being good at recognizing beacons both at the syntax level and at the higher levels of abstractions really help you form better hypotheses.

The results in terms of complete understanding are not as good with this approach but you get to a relatively good understanding much quicker. This is also what leads to making a quick fix and then breaking some other part of the system you didn't understand though, so be careful.

## To Become a World-Class Programmer You Need to Master All Three

We all want to be the best programmers we can be. In today's technology world, where things change all the time, it can be challenging keeping up with all the latest frameworks and methodologies. Luckily you can gain an advantage over the other programmers out there. If you know what to look for and can identify your weak points, you can progress further and faster with the same amount of effort.

To me, the thing that distinguishes a decent programmer from a truly excellent one has always been how well they understand the core concepts in programming.

What makes a programmer exceptional to you? Let me know in the comments below.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
