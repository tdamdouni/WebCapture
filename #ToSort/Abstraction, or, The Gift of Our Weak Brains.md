# Abstraction, or, The Gift of Our Weak Brains

_Captured: 2015-12-31 at 22:28 from [engineering.pivotal.io](http://engineering.pivotal.io/post/abstraction-or-the-gift-of-our-weak-brains/)_

## Our brains are naturally limited. This can be a curse, or it can be a gift, depending on how you look at it.

**TL;DR**:

  * Intelligent developers can, at times, fail to seek out better abstractions in their code.
  * But empathy for our peers drives us towards finding abstractions.
  * Better abstractions lead to better outcomes, and clearer problem-solving.
  * There exist practices to ensure that empathy is top of mind, and to remind us to work towards better abstractions in our code.

## NASA's Voyager: Legacy Code Like You've Never Seen

Recently, NASA put a call out for FORTRAN developers to [continue work on the Voyager spacecraft software](http://www.theregister.co.uk/2015/10/31/brush_up_on_your_fortran/). Everyone on the original team has retired from NASA at this point, meaning that the code running Voyager is literally two human generations old.

What kind of problems do you think exist around such extreme legacy code? In an [interview with Popular Mechanics](http://www.popularmechanics.com/space/a17991/voyager-1-voyager-2-retiring-engineer/), the program manager for the Voyager program said:

> … it's time to turn back to old documents to figure out the logic behind some of the engineering decisions. Dodd says it's easy to find the engineering decisions, but harder to find the reasoning. This means combing through **secondary documents and correspondence** hoping to find the solution, trying to get in another engineer's head.

Holy cow.

I mean, I realize that the solution had severe constraints placed on it (miniscule processing power, and 64KB of RAM). But the situation being described sounds like it's orthogonal to those constraints.

> _"trying to get in another engineer's head."_

Think about that for a moment. Not "trying to understand the code", not "trying to understand the implementation", but **"trying to understand how the author was reasoning about the universe at the time."**

Wouldn't it have been easier if the relevant abstractions had been captured when that code was written?

## Tale of a Prodigy

There's a famous story about [John von Neumann](https://en.wikipedia.org/wiki/John_von_Neumann) and the "[Two Trains Puzzle"](http://mathworld.wolfram.com/TwoTrainsPuzzle.html).

This particular puzzle is a math problem, involving two trains travelling towards each other, and a fly that's whizzing back and forth between their windshields: How far does the fly travel before it gets squashed?

The hard way to solve this problem is to [generate an infinite series](http://mathworld.wolfram.com/TwoTrainsPuzzle.html) representing the fly's path, and to compute its sum. Most humans aren't capable of doing this calculation in their head; but there's a shortcut to the solution, which some people will find obvious once they realize that:

  1. you know the **total time** the fly is traveling (based on the trains' relative speeds);
  2. and you're given the **fly's speed**.

A simple velocity calculation later, and you have the answer.

![](http://engineering.pivotal.io/images/abstraction-or-the-gift-of-our-weak-brains/von-neumann.jpg)

According to _[The Legend of von Neumann](https://www.jstor.org/stable/2319080)_, here's what happened when the puzzle was posed to Von Neumann:

> … he solved it in an instant, and thereby disappointed the questioner: "Oh, you must have heard the trick before!" "What trick?" asked von Neumann, "All I did was sum the geometric series."

Von Neumann was a remarkable math prodigy who was famous for his [extraordinary cognitive abilities](https://en.wikipedia.org/wiki/John_von_Neumann#Cognitive_abilities), so perhaps it's unsurprising that he was able to compute an infinite series so quickly.

If you're paying attention, though, it should be very surprising that such an extraordinary intellect didn't see and use the shortcut to solve the problem.

**Why didn't Von Neumann see and use the shortcut?** Was it easier for him to do the calculation than to search for an unnecessary (to him) abstraction?

## The History of Science is a History of Abstractions

Recently, [Brian Skinner](http://www.ribbonfarm.com/author/brian/) wrote an [amazing post](http://www.ribbonfarm.com/2015/10/29/quasiparticles-and-the-miracle-of-emergence/) about how many of our scientific observations are a direct result of humans seeking to find intuitive abstractions to explain complex phenomena:

> As an extreme example, consider that human thinking struggles to describe even individual atoms with real precision. How is it, then, that we can possibly have good science about things that are made up of many atoms, like magnets or tornadoes or eukaryotic cells or planets or animals? It seems like a miracle that the natural world can contain patterns and objects that lie within our understanding, because the **individual constituents of those objects are usually far too complex for us to parse**.

In that post, Brian differentiates between how humans _choose to reason_ about electrons in an electric circuit, versus how electrons _actually_ behave.

The key point being that electron behavior is actually so complicated, involving complex interactions between quantum probabilities, electromagnetic interactions, and macroscopic electric fields, that human brains are piteously underpowered to calculate what's going on in an individual atom.

The result, though, is that we model the _aggregate_ behavior of all the electrons in the circuit, instead of modelling _each and every_ electron. And that statistical abstraction is a model that works amazingly well in a wide range of circumstances.

![](http://engineering.pivotal.io/images/abstraction-or-the-gift-of-our-weak-brains/star-trek-aliens1.jpg)

**Imagine an alien race with the cognitive faculties to reason about individual electron trajectories**. Would those aliens fall back to the same abstraction? Or would they simply continue, as Von Neumann did, to do the calculations the hard way?

## The Impact of Ability on Developing Abstraction

These stories anecdotally support a hypothesis: Humans develop the proper abstraction only when they hit the limit of their computational power.

  * NASA computer scientists (perhaps some of the smartest, most exacting and meticulous people assembled since the Manhattan Project) write code that is so inscrutable that modern-day maintainers are forced to read the authors' mail to figure out what the hell the software was intended to do.
  * John von Neumann didn't bother to look for a more elegant solution, because he was able to brute force an infinite series so easily.
  * When science exceeds the physiological limits of our brains' capabilities, scientists seek and find appropriate abstractions that allow civilization to advance.

I can only hold one or two things in mind at a time. Maybe three, tops. I want to think deeply about a thing until I'm done, and then move on. Ask anyone who's tried to have a conversation with me when I have two or three things already in my head - I'm a total basket case.

Some people appear to be able to hold much more state in their brain than I can. It's the only way I can explain spaghetti code with light test coverage. When I ask myself, "How can anyone understand this?", the answer is usually, "Because the author must have more prodigious computing power in their brain than I do." (Maybe I'm being generous, but that's another blog post.)

And that's OK. **Except for when you have to deal with other people.** Which is probably most of the time. Whoops.

## Complexity Without Empathy Considered Harmful

How are you, as one of the best and brightest, preparing for the inevitable day when someone less talented than you has to modify the software you wrote?

Let's be honest and empathize that most people who currently have the title of "software developer" are not going to have the time, patience, or talent to wade through spaghetti code with dependencies pointed in the wrong direction, with poorly-named variables, and with poor test coverage.

![](http://engineering.pivotal.io/images/abstraction-or-the-gift-of-our-weak-brains/summer.jpg)

Worse, though, is the example being set for people who are new to the craft. There's a self-perpetuating cycle here, particularly given that very few developers have any sort of exposure to the "[team sport](http://engineering.pivotal.io/post/welcome/)" that is growing and maintaining large software systems. **If all I see when I look around is poorly-abstracted software, then are you surprised when I generate code of the same quality?**

(This, by the way, is why I feel strongly that most colleges and universities are cheating their CS grads by not preparing them for a career working in large, complex teams on large, complex projects. Again, this is for another blog post.)

## How To Do Better

Obviously, there are smart people who **do** seek and find proper abstractions. Most of them (at least the ones I know personally) share a common value: **empathy**. They all have empathy for their current teammates and future developers.

This empathy for fellow developers can emerge in a number of ways. Perhaps the best known manifestation is [Knuth](https://en.wikipedia.org/wiki/Donald_Knuth)'s "[Literate Programming"](http://www.literateprogramming.com/knuthweb.pdf):

> Let us change our traditional attitude to the construction of programs: Instead of imagining that our main task is to instruct a computer what to do, **let us concentrate rather on explaining to human beings what we want a computer to do**.

![](http://engineering.pivotal.io/images/abstraction-or-the-gift-of-our-weak-brains/hal-abelson.jpg)

Which is simply a restatement of [Hal Abelson](https://groups.csail.mit.edu/mac/users/hal/hal.html)'s famous quote:

> "Programs must be written for people to read, and only incidentally for machines to execute."

My own personal interpretation of Literate Programming is: prefer self-explanatory code over comments. I often urge my pairs to write tests and implementations as if it were English, and in so doing help drive out the right abstractions.

That tactic is actually a variation on an idea presented in Eric Evans's "[Domain Driven Design"](https://en.wikipedia.org/wiki/Domain-driven_design) philosophy, which is to use the language of the domain to articulate requirements as well as implement the code. As explained in his [book of the same name](http://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215):

> A domain model … is not just the knowledge in a domain expert's head; it is a **rigorously organized and selective abstraction of that knowledge**. … The model is the backbone of a language used by all team members.

## Engineering Practices to Encourage Empathy and Abstraction

At Pivotal, as in any [XP shop](https://en.wikipedia.org/wiki/Extreme_programming), empathy takes form in our engineering practices.

**We test-drive**, which forces us to think deeply about the proper abstractions in the code as we're writing it. Testing first generally drives out better design; and allows us to safely introduce or change the abstractions later.

**We pair program**, which forces us to explain, before the code gets committed, the reasoning and intentions behind the code. Explaining it to the person sitting next to you is the first step towards explaining it to future readers of your code.

**We rotate frequently between teams**, meaning that we're almost always teaching someone the domain, the architecture, and the codebase. As a result, we are incentivized to make sure the code is understandable and abstracted correctly; and we feel acute pain around explaining poorly abstracted code.

Generally speaking, these practices lower the threshold at which our brains might otherwise naturally seek for better abstractions. This is good!

## If You're Reading This, It's For You

These practices may be more important for people with greater computational abilities. **This is actually the reverse of most people's intuition**, which is (derogatorily) that Smart People don't need to follow the same practices as Ordinary People.

Don't fall into this trap around testing and abstractions. If you think you're so smart, then consider Abstraction to be an act of _[noblesse oblige_](https://en.wikipedia.org/wiki/Noblesse_oblige) for the rest of us, and challenge yourself to find better abstractions than the next guy or girl.

## … And A Warning

**You get to choose what you spend your brain's CPU cycles on.** Well-abstracted code is easier to reason about and safer to change. If your brain is occupied with poorly-abstracted details, you're going to miss opportunities for creative problem solving, and you won't get the flashes of insight that can be critical to solving problems well.

**Smart people who claim to not need practices are often productive … alone.** But software (and life) is a [team sport](http://engineering.pivotal.io/post/welcome/). So even if you won't find good abstractions for your own sake, do it for your fellow developers. They'll thank you for it.

Our brains are naturally limited. This can be a curse, or it can be a gift, depending on how you look at it.
