# To Framework or Not To Framework?

_Captured: 2017-07-14 at 20:13 from [dzone.com](https://dzone.com/articles/discussion-recap-to-framework-or-not-to-framework?edition=308195&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-14)_

The single app analytics solutions to [take your web and mobile apps to the next level.](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D322361301%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) Try today! Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D321036346%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

My latest little post about [programming without a framework](https://dzone.com/articles/programming-without-a-framework) has sparked some pretty interesting discussions on the topic of framework usage. Unfortunately, since I found myself with no Internet access for the last few days, I could not actively participate in the discussion. And so here I am, writing this post to share the main discussion points and my opinion on the topic(s) with a wider audience.

## The Librarians vs. the Frame-Workers

You don't have to go very deep in the discussion to notice two main kinds of opinions regarding framework usage.

The first kind of opinion, the holders of which I'll call the librarians, says that the costs and inflexibilities associated with framework usage are far bigger than the benefits they provide. Therefore, as the librarians claim, one should use a set of carefully chosen, battle-tested libraries instead of frameworks.

The second kind of opinion, proudly held by the frame-workers, says exactly otherwise. Frameworks provide a "magnification of value" over other kinds of solutions and therefore are the only right way to build production-ready applications.

If you're not yet sure which group you belong to, worry not! Things will hopefully get clearer as we move along with this post.

## Do Try This at Home

> There is a huge benefit to getting down into the details before leaping into a framework.   
-- Stephen Ferjanec 

Regardless of the tribe affiliation, most people seem to agree that building an app or two without relying on frameworks is a good exercise. Going along the argument lines of the librarians and the frame-workers, the benefits of doing so are two-fold.

On one hand, you will get a chance to notice how little value frameworks add in some areas of the project. Things that might seem like a lot of extra work if you've never given it much thought might turn out surprisingly simple. Just to name a few, starting an embedded servlet container or reading a properties file based on an environment variable is not rocket science at all.

On the other hand, you will start noticing the areas in which using the framework adds actual value to the project. A great example of this was mentioned by Jim O'Flaherty, who pictured a "brave" developer implementing Akka-like concurrency primitives. Another one could be things like out-of-the-box metrics and production-related endpoints a la Spring Actuator. These ain't rocket science but implementing them by hand for every microservice would be a huge waste of one's employer's money.

Anyway, it's important to see both sides of the coin, so please, do try this at home and your future decisions will be more informed. Also, remember that home is a far better environment to experiment than your workplace!

## The Librarians Ain't Magicians

> Use librairies, not framework[s]. No framework lock-in. No magic things that work you don't know why/how/when.   
-- Stephane Arguin 

It's not that easy to distil actual arguments from a bunch of short comments, but the general idea behind the librarian position seems to be related to frameworks doing "magic" and therefore lowering our ability to reason about and optimize the application.

I bet that anyone who ever tried to do some advanced mapping or performance optimization using Hibernate and JPA knows what the librarians are talking about. You're getting this nice black box, with a "put annotated POJOs here" label on it. At the very beginning of the project, it works like a charm. Then, over the years, the application grows, the amount of data grows, the contention grows and when you try to figure out how to make things work again, you find yourself trying to deconstruct the black box and it's no fun anymore.

In the librarian approach, you are always in control of what's going on. You're choosing small, well-documented libraries for each individual task in your project. You tend to favor "knowing what's going on" over "things happening automagically". If a library that you've chosen no longer fits your needs, you simply replace it with a new one or use both. Your choice, you're free.

## The Frame-Workers Do Real Business

> The amount of time [developers] spend trying to "learn" into the custom code you produced is time I don't get to task them with solving real business problems.   
-- Jim O'Flaherty 

Contrary to what some might expect, the frame-workers are not a bunch of kids who chase every single shiny thing out there on the field. Instead, they go for the framework so that they can focus on the real business instead of reinventing the wheel for the millionth time.

Fun or not, doable or not, most of us are not hired to solve technical problems that were already solved a lot of times by a lot of people. We are hired to solve actual, business problems and we should put as much focus towards that as possible. Choosing libraries, coding bits of your own and trying to make it all work together is a waste of time if there's a framework doing all that out of the box.

This argument goes even further. If you're skilled enough, the time and money wasted to code it up can be marginal, but the maintenance and learning costs won't be, for sure! If a system is to be maintained for many years, by many different teams, the cost of learning how the non-framework setup work can be significant. And every single bug that arises in our own mix of technical solutions is an unnecessary cost that should not be underestimated.

## That Crappy System You've Seen

> Totally agree 100%. The problem comes when people don't think [...]   
-- Tim Chippington Derrick 

As one could reasonably expect, there's quite a number of people who switched tribes because of their past experiences. As Tim Chippington Derrick and Jim O'Flaherty (again!) both nicely concluded, crappiness and un-maintainability of output solutions is not an inherent characteristic of any of the approaches. Rather, it's all on people who naively pick one route or the other without giving much thought to the trade-offs.

I truly agree and can relate to that conclusion. Over my relatively short programming career, I already had a chance to work on a project that suffered from both ineffective framework usage and developers trying to implement things on their own at the same time. The result? You wouldn't want to see that.

To conclude this point, whether you're currently struggling with a weird configuration of external frameworks or maintaining a bunch of poorly design in-house solutions, it's not the tools to be blamed -- it's the people.

## Everything is a Framework, LIAR!

> Jetty IS a framework!   
-- David Buschman 

There are two more points that were mentioned in the comments that I totally don't agree with and I'd like to explain why. The first is the notion that if you're not using a framework provided by an external party, you're always building one of your own in the codebase. The second is that almost any tool we're using is a framework and therefore talking about framework-less programming is pointless/stupid/whatever.

### What Is a Framework?

Before I target each of the points directly, I think it's worth establishing a common definition of a framework. I won't go so far as to provide anything of my own. Instead, I'll paste a comment from Mileta Cekovic, which nobody seemed to argue against:

> Framework? It does what it says: puts my work into a frame.   
-- Mileta Cekovic 

It's easy to see how things commonly referred to as framework fit this definition. Scrum, for instance, takes your work over a product and puts into nice frames called Backlog Items, Sprints, Daily Stand-ups and so on. A good example, a bit closer to the topic of the post, would be the Spring Framework. It takes your project and puts it into a frame of beans, their lifecycle, AOP, and so on.

### A Framework for Thinking About Frameworks

With the definition in place, we need to understand one more thing about frameworks if we are to have a productive discussion i.e. we need to consider them in context. This statement implies two distinct, but related things.

Firstly, if I am in the context of writing _some _application in _some _language, then I can talk about JVM being a potential framework for the solution. On the other hand, if I am talking about a _concrete _application written in _Java_, then talking about JVM being a framework makes no sense. JVM is a given here.

Secondly, we need to consider _how_ we're using a given tool. If I'm using Spring to construct a complete object graph and run my application, then I'm really using Spring as a framework. If I import Spring to use a bunch of utility methods or to trick it into providing me a single configurated class instance to support a larger whole built with other tools, then Spring is not used as a framework here, it's used as a library.

### Back to the Discussion

With this little digression of mine, we can finally talk about the points raised during the discussion. As the definition provided in the very same discussion suggests, the degree to which you're building a framework of your own (when you're not using one already) depends on how much you frame your further work. So, if you design a set of primitives upon which the rest of the application is later built, then yes, you're creating a framework and it can be considered a waste. On the other hand, if all you do is abstract the needs of your application using interfaces and then implement that using libraries, then it's surely not a framework. That's just (good) design.

As for the other point and all the funny-haha comments related to the fact that I used Jetty on JVM instead of plain assembler and claimed not to use frameworks, that's all a matter of context. In the context of my post, JVM and Kotlin were indeed taken as a given, so the whole discussion was on another level of abstraction. When it comes to Jetty and Servlets, it's important to notice that I did not submit myself to the frame it provides. I did not structure my application around their abstractions/primitives. Instead, I used them as an easy way to implement a single one of my very own interfaces, without the rest of the application knowing anything about it. Therefore, I'd be far from saying that Jetty or Servlets framed my work in any way.

## Final Thoughts

Thanks everyone for a civilized, active discussion under my last post. The number of comments produced in a short time, combined with a diversity of opinions, convince me that the argument between the librarians and the frame-workers is far from settled. On the contrary, it might never be clearly settled, as the topic involves a big human factor and requires a careful balance of trade-offs, which is to be performed for every project separately. Finally, if anyone even reached this far in the text, which group are you in? Are you a free, reasonable librarian or a business focused, pragmatic frame-worker?

CA App Experience Analytics, a whole new level of visibility. [Learn more.](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D322361143%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D322361143%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Opinions expressed by DZone contributors are their own.
