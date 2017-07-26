# The Strange Relationship Between Duplication and Coupling

_Captured: 2017-05-26 at 18:23 from [dzone.com](https://dzone.com/articles/the-strange-relationship-between-duplication-and-c?oid=twitter&utm_content=buffer5c6fc&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Learn how to troubleshoot and diagnose some of [the most common performance issues in Java today](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

This short post hopefully contains no new knowledge for you. Its mere intention is to make you contemplate an interesting relationship between coupling and duplication for a while.

## Duplication Is Bad!

As professional programmers, [true software craftsmen](http://amzn.to/2r6SfhE), [the clean coders](http://amzn.to/2rFDT53), [insert your title here], we're often taught that duplication is bad and should be avoided at all cost. We even have (at least) two widely known principles related to this problem, namely, "[Don't Repeat Yourself](http://wiki.c2.com/?DontRepeatYourself)" and "[Once And Only Once](http://wiki.c2.com/?OnceAndOnlyOnce)."

The idea behind these principles is obvious -- if some piece of information/behavior is represented in two separate places, we have to update both when our understanding changes. If it's in five places, we have to update all five, and so on. As we all know, this is both annoying and error prone. How the hell am I supposed to track all such places in a codebase with thousands or millions of lines of code?

And so we, professional programmers, eliminate duplication mercilessly whenever we see it.

## But So Is Coupling!

The principle is often taken to the extreme where every piece of code that looks like some other piece of code has to be eliminated. A prime example of this being all the systems where the same class is used to model the domain, to be a REST request, to be saved in the database, and sometimes even more. Well, why would I create three classes that look exactly the same, just to, later on, map between the three?

Heck, I even copy-pasted the class when writing this small example! That's an obvious violation! Kill it!

The thing is, you should actually consider that kind of design. Really carefully. And, as you probably figured out already, you could do that for the sake of decoupling.

Whenever you add a new field to the Employee class, you have to update all three. That's the obvious downside of duplication. What many people fail to see, is that this kind of "update", does not have to be exactly the same in all three cases. Let's consider a simple evolution of the Employee class:

This paymentStrategy could be different kinds of payment methods, or different payment intervals, or whatever alike. Anyway, it's a classical strategy example. How would the two other classes evolve now?

Obviously, we are not going to serialize the strategy as-is. We need some enum or a String, that will appropriately represent the kind of strategy. If we were to use the same class for serializing purposes, **our mind will keep suggesting that we drop the pattern altogether and do it some other way**.

Now, there are "workaround patterns" like an enum-based strategy, but does that really make your code simpler? Let's consider the two snippets:
    
    
        Employee create(String firstName, String lastName, BigDecimal salary, String paymentMethod) {

It's like… how much time did you save? How much better is the code below than the one above?

And that's not everything. If the paymentStrategy is required to add an employee, and you're using the Employee class as a request, you just changed your API contract in a breaking way! How nice of you, huh?

## There's More!

Let's say that you're given a requirement to add some information about the organizational hierarchy to the system and display that as a nice "tree". Simple change, we just need the immediate manager and we can go from there.

The tree does the job and everybody's happy. As a next step, they ask you to add department information to the few. Another simple change to the Employee class!

I hope that there's a big, red light shining in your head now. We're filling our simple payroll system with irrelevant information! What's more, **we're tying the payroll stuff with the organizational stuff** by making them use the same Employee class all over the place. That's bad coupling, again!

In such a case, if you were to think about a possible solution, you might easily end up with this:

That's… dddd… duplication! Wooops!

## Summary

As I said, I hope that nothing here was new to you. At the same time, I find this relationship between coupling and duplication something important enough to mention here. If you were having a hard time justifying to yourself the use of patterns like DTO, or [architectural styles](http://tidyjava.com/category/architecture/page/2/) such as [Clean Architecture](http://tidyjava.com/clean-architecture-screaming/), now you have at least two extra arguments. Unless you accept some data duplication here and there, you're dragging yourself into problems like "I can't update my domain class, because it will break some contract" or "every single thing in my system depends on this class." Don't go there.

Understand the needs and benefits around implementing [the right monitoring solution for a growing containerized market](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics.](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital)

### Like This Article? Read More From DZone
