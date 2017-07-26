# 10 Tips on How to Be a Great Programmer

_Captured: 2017-05-10 at 22:03 from [dzone.com](https://dzone.com/articles/10-tips-on-how-to-be-a-great-programmer?edition=298048&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-10)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

I was recently asked in an interview about my opinion on how to be a great programmer. That's an interesting question, and I think we can all be great programmers, regardless of our talent, if we follow a couple of rules that - I believe - should be common sense. In fact, these rules don't all apply to programmers only, but to any professional.

Not everything in this list is meant to be taken entirely serious, some things are just my opinion and yours may vary, and not all descriptions of programmer personalities match real-world situations I may have encountered, so if in doubt, please do not take offense. I didn't mean _you :)_

Here they are:

### 1\. Learn How to Ask Questions

There are essentially these types of programmers asking questions:

  * **The perfectionist**: Especially when asking a question about some open source tool, they may have already debugged through the code and found the real cause of their problem. But even if not, the perfectionist will write an introduction to the problem, steps to reproduce, potentially a suggested workaround, and as I said, potentially a suggested fix. In fact, the perfectionist doesn't have questions. Only answers.
  * **The chatterbox**: This person will not really ask questions. Rather, they arrange their thoughts publicly and occasionally put a rhetorical question mark here and there. What may appear to be a question is really just a stream of thoughts and if you wait with the answer, they may either find the answer themselves or ask the real question in email number 37. Or not. Or maybe, if we try it this way. You know what? It turned out that the requirement is completely wrong, I solved it with some other technique. Oh, actually, I changed libraries entirely. Hehe. No more questions.
  * **The slacker**: [Here's the code](http://brokenlink/). What's wrong? Help, please.
  * **The manager**: For this type, time is money. The questions must be short and the answers ASAP. There's something ironic about this approach, because by keeping the questions short (read: incomplete, not concise), most often, a lot of important details are missing, which only leads to requests for details. Then, the manager (naturally being disappointed because the reply is not an answer but a new question) will send, yet again, a short message and demand an answer with even more urgency. This can go back and forth for quite a while. In the end, it may take 1-2 weeks until what could've been the answer will actually be answered.
  * **The complainer**: This person doesn't ask questions. They complain. Until the question goes away. Perhaps. If it doesn't all the better. More reasons to complain.

By now, it should be clear that a well-prepared question (concise, simple, short, yet with enough details) will yield much better answers. If you know what exactly you want to learn with your question, chances are, you'll get exactly what you wanted.

### 2\. Learn How to Avoid Asking Questions

In fact, mostly, it's better to try to avoid asking questions. Perhaps you can figure it out yourself? Not always, of course. Many things, you simply cannot know and by asking a domain expert, you'll find the quickest and most efficient path to success. But often, trying something yourself has these benefits:

  * You learn it the "hard way" which is the way that sticks to our memory much better - we'll remember what we've learned.
  * It's more rewarding to figure stuff out for yourself.
  * You don't create "noise." Remember the chatterbox? Unless the person you're asking the question(s) is routinely answering questions (and thus postponing their answer), they may not see through your stream of thoughts and try to answer each individual incomplete "question." That doesn't help anyone.
  * By postponing a question (for a while, at least), you can gather more relevant information that you can provide to someone who might be able to answer your question. Think of the "perfectionist." Spend more time looking for details first, then answer the question.
  * You'll get better at asking questions by training to ask good questions. And that takes a bit more time.

### 3\. Don't Leave Broken Windows

There was a very interesting article on Reddit recently about [not leaving broken windows](https://dev.to/raulavila/dont-leave-broken-windows). The essence of the article is to never compromise on quality. To never become a slacker. To never leave … broken windows. Here's a quote from the article:

> "When we take certain shortcuts to deliver something in the shortest period of time, and our code reflects how careless we've been, developers coming after us (from the same team, a future team, and even ourselves!), will reach an important conclusion: it's not important to pay enough attention to the code we produce. Little by little our application will start deteriorating in what becomes an unstoppable process."

This isn't about being a perfectionist, in fact. Sometimes, fixing broken windows can be postponed (and must be, of course). But often times, by allowing windows to break and stay broken, we're introducing a situation where no one is happy. Not us the programmers, not our customers, not our users, not our project managers. This is an attitude thing and thus at the core of being professional. How did Benjamin Franklin put it?

> "The bitterness of poor quality remains long after the sweetness of low price is forgotten."

That's true for everything. In this case, "low price" is the quick win we might get by implementing something in a sloppy way.

### 4\. Software Ought to Be Deterministic. Aim for It!

In an ideal world, everything in software is "deterministic." We'd all be functional programmers, writing side-effect free, pure functions. Like `[String.contains()`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#contains-java.lang.CharSequence-). No matter how many times you execute the following:

… the result is always the same, expected result. The universe and all its statefulness will have absolutely no impact on this computation. It's _deterministic_.

We can do that, too in our own programs, not just in standard libraries. We can try to write side-effect free, deterministic modules as often as possible. This isn't really a matter of what technology we choose. Deterministic programming can be done in any language - even if functional languages have more tools to prevent accidental side effects through more sophisticated type systems. But the example I've shown is a Java example. Object orientation permits determinism. Heck, procedural languages like PL/SQL allow for determinism. It's a requirement for a function to be deterministic if it is to be used in an index:

So again, this is a matter of discipline. You could see a side-effect procedure/method/"function" as a "broken window." Perhaps it was easier to maintain a side-effect, hoping that eventually, it can be removed. But that's usually a lie. The price will be paid later when non-determinism suddenly strikes. [And it will](https://en.wikipedia.org/wiki/Murphy%27s_law).

### 5\. Expect the Unexpected

That previous link is key. [Murphy's Law](https://en.wikipedia.org/wiki/Murphy%27s_law) is something we programmers should observe all the time. Everything can break. And it will. Come on, as software engineers, we _know_ it will break. Because our world is not deterministic, neither are the business requirements that we're implementing. We can implement tip #4 (determinism) only until it is no longer possible. From then on, we'll inevitably enter the world of non-determinism (the "real world"), where stuff will go wrong. So, aim for it. Expect the unexpected. Train your inner pessimist to foresee all kinds of things.

How to write that pessimistic code in a concise manner is another story, of course. And how to distinguish from things that _will_ fail (and need to be dealt with) from things that _might_ fail (and don't need to be dealt with), takes some practice

### 6\. Never Cargo Cult. Never Follow Dogma. Always Embrace "It Depends"

Everything you've been taught is potentially wrong. Including (or probably, _especially_) when someone really popular says it. Here's a nice quote:

> "I think at least 50% of my career has been either contributing to or unwinding one Fowler-inspired disaster or another."

Our profession is full of hypocrisy. We like to think of ourselves as mathematicians, where only the purest of ideas persist, and they're necessarily correct.

That's wrong. Our profession is built _on top_ of mathematics, but unless you go into the funky world of category theory or relational algebra (and even then, I doubt everything is "correct"), you're in the pragmatic world of real-world business requirements. And that's, quite frankly, very far from perfect. Let's look at some of the most popular programming languages out there:

  * C
  * Java
  * SQL

Do you really think that these languages resemble mathematics in the least bit? If so, let's discuss segmentation faults, Java generics, or SQL three-valued logic. These languages are platforms built by pragmatists. There is some really cool theoretical background in all of them, but ultimately, they had to do the job.

The same is true for everything built on top of languages: libraries, frameworks, [design patterns](https://blog.jooq.org/2016/07/04/how-functional-programming-will-finally-do-away-with-the-gof-patterns/), heck, even architectures. Nothing is right or wrong. Everything is a tool that was designed for some context. Think of the tool in its context. Never think of the tool as a standalone raison d'etre. We're not doing [art for art's sake](https://en.wikipedia.org/wiki/Art_for_art%27s_sake).

So, say no to unquestioned:

  * XML
  * JSON
  * Functional programming
  * Object-oriented programming
  * Design patterns
  * Microservices
  * Three-tier architectures
  * DDD
  * TDD
  * In fact: *DD
  * The list goes on...

All of these are nice tools given a certain context, but they don't always hold true. By staying curious and thinking out of the box, you'll be a better programmer and know when to use which one of these tools.

### 7\. Do It

True. There are luminaries out there who outperform everyone.

But most programmers are simply "good." Or they have the potential to be "good." How can you be a good programmer? By doing it. Great software wasn't written in a day, and popular people aren't the only heroes of our time. I've met many great programmers no one knows about, because they lead private lives, and solve the private problems of small companies.

But great programmers all have one thing in common: they just do it. They practice. They work every day to get better and better.

Want to get better at SQL? Do it! Try to write a SQL statement with some new features in them, every day. Use window functions. Grouping sets. Recursion. Partitioned outer join. The MODEL and/or MATCH_RECOGNIZE clauses. It doesn't have to ship to production every time, but the practice will be worth it.

### 8\. Focus on One Subject (in the Long Run)

There might be only a very few "good" full stack developers out there. Most full stack developers will, rather, be mediocre at everything. Sure, a small team might need only a few of them and they can cover a lot of business logic to quickly bootstrap a piece of new software. But everything will be quite sloppy and "kinda works." Perhaps that's good enough for the minimum viable product phase, but in the long run, there will be more complex problems that a full stack developer will not have the time to properly analyze (or foresee!).

Focus on one subject mostly, and get really good at that. A specialist will always be in demand as long as that specialist's niche exists, and many niches will outlive us all (hello COBOL or SQL). So, do your career a favor and do something really good, rather than many things "just ok."

### 9\. Play

While you should mostly focus on one subject, you shouldn't forget the other subjects completely. You may never be really really really good at all of SQL, scaling up, scaling out, low-level performance, CSS (who's good at that anyway!?), object orientation, requirements engineering, architecture, etc. all at once (see tip #8). It's just not possible.

But you should at least understand the essence of each of these. You should understand when SQL is the right choice (and when it isn't). When low-level performance tuning is important (and when it isn't). How CSS works in principle. The advantage of object-orientation, FP, etc.

You should spend some time playing with these (and many more) concepts and technologies to better understand why they're important. To know when to apply them, and then perhaps to find an expert to actually execute the work.

By playing around with new paradigms and technologies, you'll open up your mind to entirely different ways of thinking, and chances are, you'll be able to use that in your everyday work in one way or another.

### 10\. Keep it Simple, Stupid

Albert Einstein said:

> "Everything should be made as simple as possible, but no simpler."

No one is able to handle huge complexity. Not in software, not in any other aspect of life. Complexity is the killer of good software and thus simplicity is the enabler. Easy to understand. Hard to implement. Simplicity is something that takes _a lot_ of time and practice to recognize and produce. There are many rules you can follow, of course.

One of the simplest rules is to have methods/functions with only a few parameters. Let's look at that. Surely, the aforementioned `[String.contains()`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#contains-java.lang.CharSequence-) method qualifies. We can write `"abcde".contains("bcd")` and without reading any documentation, everyone will immediately understand what this does and why. The method does one thing and one thing only. There are no complicated context/settings/other arguments that can be passed to the method. There are no "special cases," nor any caveats.

Again, producing simplicity in a library is much easier than doing that in business logic. Can we achieve it? Perhaps. By practicing. By refactoring. But like great software, simplicity is not built in a day.

(Protip: [Conway's Law](https://en.wikipedia.org/wiki/Conway%27s_law) applies. It is utterly impossible to write good, simple software in an environment where the business is super complex. Either, you like complexity and ugly legacy, or you better get out of that business).

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
