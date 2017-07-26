# The Power of Open/Closed Principle

_Captured: 2017-02-19 at 21:21 from [dzone.com](https://dzone.com/articles/the-power-of-openclosed-principle?oid=twitter&utm_content=buffer43d5f&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

Continuing [our journey](https://dzone.com/articles/single-responsibility-principle-explained) through **SOLID **principles with Ben and Tony, we're now looking to unleash the power of the **Open/Closed Principle **(and generate an infinite number of reports)!

## Tony's New Reports

Tony comes to you to ask for a new report with some usage statistics that nobody cares about. You carefully ask him about every little detail and then provide an estimate: **3 weeks! **You can see it in his eyes; how his animal spirit is awakening! How can sending one more email per day with some simple statistics that you can get right from your database take 3 weeks?!

You try to explain that it requires changes in the whole reporting module, and there's a huge risk of breaking something, but that doesn't work. The estimate is way too big and, by the way, your colleague Darek says that he could do it in 1 week. How come? Does he have superpowers?!

You hired the best-looking lady in the office as a private investigator to reach out to Darek and find out his secret to adding new reports so quickly. It turned out that Darek has a list! A list of ALL the damn files that you'd have to modify to add the report. A powerlist!

## Open/Closed Principle

The section above is based on a true story. The situation in which you have to modify a lot of files to add a new feature is a classic violation of the **Open/Closed Principle**:

> Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.

If we were to adhere to this rule, there would be no files to modify in order to add a new feature or those files would be limited to some configuration/factory methods. You're no longer changing any code, you're only adding stuff. Think about it. No more tedious copy-pasting, no more accidentally breaking stuff, no more having to remember which files to modify, just **adding new code** -- this is the **real power!**

## Applying OCP

Applying the principle should be pretty straightforward. There's no magic spells or formulas. All you need is four keywords: abstract, extends, interface, and implements . You find the places that require a change:

Then you extract proper abstractions:

Then, you implement each of your features using these abstractions in separate source files:

The interfaces or base classes are the ones being both open and closed - they're open to be derived from and closed for modifying their content. If you're having trouble with weird inheritance trees or choosing the right names, check out **design patterns** - the problem that you're trying to solve has probably been solved by someone else already. Easy!

But if it's all so simple, then…

## What's the Problem?!

The real challenge in implementing the **Open/Closed Principle** lies in choosing the places to close (as in "closed for modification"). What would be the next new feature added to Tony's reporting? Another report? Maybe adding a new column? Maybe sending different variations of the report to different people? Maybe using another file format for the report? Maybe, maybe, maybe.

The truth is, we don't know the future. However hard we try, most of the times "the business" finds a way to surprise us -- tasks us with something that we didn't anticipate. How shall we choose the abstractions then? What should we make configurable? How generic should our systems be? These are all valid questions without direct answers. If you try to use a lot of design patterns left and right, supplied by a ton of abstractions, there's a huge chance that your code will be an unreadable piece of crap, instead of a nicely open/closed solution.

How do we decide then? What are the heuristics?

  * Product backlog: if the new feature is already present in the backlog, there's a huge chance it will be implemented one day. Therefore, if we're working with the potentially affected code, we might prepare it for the upcoming feature.
  * Previous features: I'd call this "closing by refactoring". While implementing new features, whenever you notice that a place is vulnerable to modifications, you close it, so that the problem doesn't occur ever again. (I conciously apply only this one)
  * Experience (or "gut feelings"): people say that with experience, your gut will help you apply **OCP **effectively

Here's what Uncle Bob says about applying the rule:

> Since closure cannot be complete, it must be strategic. That is, the designer must choose the kinds of changes against which to close his design. This takes a certain amount of prescience derived from experience. The experienced designer knows the users and the industry well enough to judge the probability of different kinds of changes. He then makes sure that the open-closed principle is invoked for the most probable changes.

## Final Thoughts

I already mentioned that I consciously apply **OCP** only during refactorings. In the end, it's all about being able to provide enough business value in a timeframe that satisfies both sides. If the necessity to change multiple files slows down development, then the power of the principle is right there, for us. If we're as efficient with a simple if or, heaven forbid, a switch statement, then why bother?

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).

### Like This Article? Read More From DZone
