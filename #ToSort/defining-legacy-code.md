# Defining Legacy Code

_Captured: 2018-05-16 at 22:15 from [dzone.com](https://dzone.com/articles/defining-legacy-code?edition=376314&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-05-16)_

Monitor your CI/CD pipelines end-to-end with [Hygieia,](https://dzone.com/go?i=283444&u=https%3A%2F%2Fcapital.one%2F2pPdVfl) an open source dashboard from Capital One.

Last night I realized that strangely enough, we are the only profession that can take a positive word like "legacy" and turn it on its head to mean something bad. You can listen to the [audio track here](http://bit.ly/2Iowjal).

We are probably the only field that has a bad and messy association when hearing "legacy," perhaps because we happen to be a new field that strives to move forward to new languages to create better code.

I was asked by a non-coder what legacy code is, and found that defining legacy code is surprisingly hard. You might think this wouldn't be the case as we use the term considerably when describing code. And we tend not to use it fondly...

  * "I'm tired of working on legacy codebases--I want a greenfield project for a change."
  * "We shouldn't touch that. It's legacy code."

But when you go looking for a definition on the internet, you don't find consensus. [This Stack Exchange question asking for a definition ](https://softwareengineering.stackexchange.com/questions/94007/when-is-code-legacy)has, at the time of writing, ten different answers with hundreds of votes and no real consensus. Look at [something more concrete, like "what is mocking,"](https://stackoverflow.com/questions/2665812/what-is-mocking) and you'll see more definition clarity.

We use the term legacy code all the time, but we don't necessarily agree on what it means, so let's explore some common definitions:

## **Legacy Code: ˈ/lɛɡəsi kəʊd/**

## **"All Code Is Legacy Code"**

Believe it or not, some people will make the argument that _all _code is legacy code. As soon as you write it and deploy it, it becomes legacy code.

This definition is interesting in a philosophical or pedantic sense. After all, any code does have a maintenance footprint and a cost. And if you think about it, while tossing around this term, and trying to distinguish the difference between legacy code and just code, you come to realize that "legacy code" seems redundant as it's just a synonym for "code."

## **"It's Code That Developers Don't Like"**

Next, let's consider a commonly implied definition. Legacy code is any code that the developer using the term doesn't like.

"You seriously want me to go into that messy legacy code and start making changes!?"

I don't think anyone would actually _cite _this definition. However plenty of people certainly _imply_ it, so we might as well talk about it. With this definition, legacy code becomes a synonym for "bad code" or for "code I don't like."

It's important to understand this context when you hear the term legacy code in conversation. A given developer _might_ mean something more precise when tossing this term around, or that developer might just be expressing disgust with the code.

Understanding this usage of the term is important, but that doesn't mean we should adopt this definition--not by a long shot. Just as making legacy code a synonym for "code" doesn't meaningfully advance the discussion, making it a synonym for "bad code" doesn't either.

## **"It's Code That Developers Don't Understand"**

Let's now move past the definitions that simply make legacy code a synonym for something else. This important term deserves a definition that lets it stand on its own. So, how about the idea that legacy code is code that developers don't understand?

You'll often hear this connotation when people toss the term around in conversation. Someone expresses reluctance to make code changes, not because they dislike the code, but because they don't understand how it works. The reluctance is really a pragmatic reaction: "I don't understand this code, so changing it is risky."

I think this definition is more reasonable than the last two. However, it's still lacking something because it's not specific enough. Take into consideration that a novice software developer may not understand advanced language concepts, or that _anyone_ looking at unfamiliar code for the first time may not understand it initially.

This attempt at a definition is accurate in one way; it describes a _characteristic_ of legacy code. Often, we don't understand it when looking at it, but a lack of understanding does not necessarily make it legacy code.

## **"It's Code You Inherit"**

With this definition, we move toward the sorts of classical definitions that you'll find when scouring the internet. There's a line of thinking that code is legacy not on the basis of its intrinsic properties, but rather on the basis of who wrote it. Did your team write it? If so, then it's not legacy code. It's code that you've created and is actively being maintained. Did some other team full of long-departed developers write it, and you simply inherited it as is? Then this orphaned code is legacy code. Therefore, as the "legacy code is code you inherit" definition goes, you categorize code on the basis of whether someone who understands the code is still around. If not, it's legacy code.

## **"It's Code Built Using Obsolete Practices and Platforms"**

Just as you'll find people using the term "legacy code" to convey the idea of inheritance, you'll also hear it in reference to obsolescence. The [Wikipedia definition](https://en.wikipedia.org/wiki/Legacy_code), for instance, makes this distinction (and also speaks to the maintenance of code written by someone else).

This definition of legacy code talks about code written for old operating systems or frameworks that no longer receive support. Do you have a piece of software that runs only on Windows XP? Or perhaps you wrote it in VB6? These would both be examples of legacy code.

This definition is the most compelling one yet. I say this because it makes a tangible, objective distinction, and it describes an actual problem. It doesn't matter who, when, or why anyone wrote it, neither does it matter what anyone thinks about it. It matters only what the software depends on and whether those dependencies are fully supported.

Still, I don't consider this to be the most useful possible definition. It fails to capture the reality that the _structure_ of your code matters. Your code's status as legacy or not legacy shouldn't be purely a matter of its dependencies.

## **"It's Code Without Unit Tests"**

In his seminal book, _[Working Effectively with Legacy Code](https://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052)_, Michael Feathers offers a different definition. His definition is objective, incredibly simple, and elegant: legacy code is code without tests.

He's talking specifically about the idea of automated regression tests, often in the form of unit tests. The reasoning is that automated tests capture the intended behavior of a system. They then give you feedback as you make changes, letting you know if the changes have unintended consequences. The result is code that you can change efficiently and with relatively low risk. So, non-legacy code is code that's simple and low-risk to change. Legacy code, on the other hand, lacks tests, making it difficult, risky, and expensive to change.

This is an excellent definition of legacy code. Nevertheless, I'm going to close by offering a slight variation on it as my favorite definition.

## **"It's Code That Is High-Risk to Change"**

I think of legacy code as code that [developers are _afraid _to change](https://www.typemock.com/blog/legacy-code-5-tips-handling/). This definition puts the other ones nicely into context (omitting the first definition).

  * Dislike or disgust is often a response to anger or uncertainty. We may react to a piece of code with disgust because we're worried about the prospect of touching it.
  * If we inherit a piece of code, we're probably worried about modifying it.
  * We'll hesitate to touch code written on obsolete frameworks or platforms, particularly if we aren't familiar with them.
  * Without unit tests to reassure us that we're not breaking things, we worry about our changes.

All roads lead back to fear.

I like some of the other definitions (especially Michael Feathers'), but it's possible to have code written on modern platforms and even code with badly written unit tests that developers fear to change. And I would still consider that to be legacy code.

Legacy code is problematic for the very reason that it inspires fear. Changes are risky and likely to go poorly, and anyone who touches it is likely to be rewarded with an inbox full of defect reports and issues. Developers intuitively understand all of this, and it manifests as fear of the codebase; its high risk and low reward.

Legacy code is code you're afraid to touch. So, the secret of avoiding legacy codebases is to build them in such a way that other developers are never afraid to change them.

Track and monitor your entire CI/CD pipeline on a single pane of glass. [Hygieia](https://dzone.com/go?i=283445&u=https%3A%2F%2Fcapital.one%2F2E1Hb7J) is an open source, visual dashboard for keeping CI/CD pipelines green.
