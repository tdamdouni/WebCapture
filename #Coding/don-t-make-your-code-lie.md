# Don't Make Your Code Lie

_Captured: 2017-08-03 at 21:50 from [dzone.com](https://dzone.com/articles/dont-make-your-code-lie?edition=0&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-03)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

This short little post you're reading was inspired by all the code reviews that I've done in the past month. I don't know if that's a coincidence or I haven't paid too much attention to it before, but people have a strong tendency to make their code lie.

## What Do You Mean by the Word "Lie"?

A piece of code lies when it tells you that it does something, while in reality, it does something else. Of course, by "something else" I don't only mean the cases of someone forgetting to update a name or putting something totally wrong. I also mean some more subtle cases. For example:

  * You add a little bit of extra functionality in there that you might not expect just by reading method names.
  * You do not add some "obviously expected" logic because it seems unnecessary at the moment.

I guess some examples will be worth way more than any kind of explanation.

## Null Return Value

This is probably the single most common lie in the whole Java (and not only) programming world. Somebody gives you a method that supposedly returns _something _and, in some rare cases, returns null (AKA nothing). If the code you're using is some internal API or a less popular library, there's a high chance there will be documentation informing you of such a possibility. You use the method, try to do something with the returned value, and… you know how this ends.

Luckily, as the years pass and the tooling/language evolves, this problem is less and less common. We've got a growing number of ways to make our code more expressive and prevent the null-lie. The (arguably) most common would be to use the Java 8 Optional type. If you're not yet using Java 8 or simply hate Optional for some reason, there are at least a couple of libraries with @Null/@NotNullable annotations supported by common IDEs. And, if you really want to go fancy, you can try switching to a language with better null handling mechanisms like Kotlin.

## Hidden Special Case

A particularly crazy example of a code lie that I've seen recently was returning an undocumented, non-constant empty String to handle a special business case. An analogous code example to the one I've seen could look like this:
    
    
            return passport != null ? passport.getCountry() : "";

Now, from the business perspective, the isCitizen method could work as expected - if we don't have somebody's passport information, we assume that he's not a citizen. This could be a valid requirement. But it doesn't change the fact that the passportService tells a terrible lie there. The empty String might work just fine for this particular case, but makes the getPassportCountry method harder to reuse and could potentially lead to a dangerous bug if someone used it without checking its implementation up front.

In this particular case (and many similar), using an Optional instead of the empty String or implementing the special case pattern explicitly would solve the issue.

## "YAGNI" Laziness

As the YAGNI principle nicely suggests, we should not implement things that we don't need. Unfortunately, people frequently take this notion too far and propagate hard-to-debug lies. Consider the following piece of code:

Maybe, just maybe, the imaginary person writing the getBrother method made sure that it's never called for people that do not have their brother in the first position of the siblings list. Maybe. But it still doesn't justify such a sloppy implementation.

Firstly, there's no guarantee that this piece of code won't be reused in other cases. Again, it's unlikely but it could lead to some crazy bugs. And secondly, even if it isn't reused, it's extremely confusing. If I saw a piece of code like this, I'd make sure to track down how, when and where it's used and whether it would surely work as expected. So, as much as it might save you some typing during implementation, it might waste much more time for your colleagues when they come across something like this.

Solution? Implement as much logic of a method as it's reasonable to expect by reading its header. Don't be too lazy in the name of YAGNI.

## Extra Piece of Logic

The last, particularly bad piece of a lie that I'd like to mention is adding an extra piece of logic to a method so that you don't have to add it elsewhere. Here's an example:

Let's leave the performance factor outside of the discussion, I created this implementation just for the sake of the example. Can you spot the "extra" logic in there?

That's right! For some reason, the method that is supposed to return a given person's friends also performs an adult check. Again, while this might work just fine for the current implementation needs, it's extremely confusing and could cause costly bugs.

Solution? Simply rename the method to correctly describe its behavior or move the extraneous piece outside of it. (I know that's trivial but that's because the problem is so stupid. It feels weird that I even have to write something like this, but I recently came across an analogous case, so maybe it's needed.)

## Summary

Lying in code leads to confusion, bugs and, in most cases, money loss for your employer. At the same time, it's very, very easy to prevent. Nothing I wrote here is hard or particularly unknown to people. And yet, for some reason, these kinds of monsters still pop up in our codebases. I think that's more because we're lazy and sloppy than because we lack skills. Therefore, my only final advice is: Don't be lazy, don't make your code lie!

[Download Building Reactive Microservices in Java](https://dzone.com/go?i=219225&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F166031): Asynchronous and Event-Based Application Design. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=219225&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F166031).

### Like This Article? Read More From DZone
