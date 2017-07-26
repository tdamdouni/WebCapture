# Agile Is The New Waterfall

_Captured: 2015-10-14 at 23:39 from [medium.com](https://medium.com/@ayasin/agile-is-the-new-waterfall-f7baef5d026d)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*HumuLoReTLPXVf-UymZj6g.jpeg?q=20)![](https://cdn-images-1.medium.com/max/800/1*HumuLoReTLPXVf-UymZj6g.jpeg)

You've been lied to by the same people that have always lied to you.

Agile is terrible. Scrum is worse.

Before I begin, let me get Agile's [straw man](https://en.wikipedia.org/wiki/Straw_man) out of the way: No sane person advocates for Waterfall. Repeat, there are zero sane Waterfall advocates. That said, every argument that Agile adherents make against their opponents could easily be made by those imaginary Waterfall adherents they fear so much with a slight change in wording.

Agile has become everything that waterfall was to developers and worse. It is a wolf in sheep's clothing and I'm going to expose it here today.

#### The Agile promise

> "full of sound and fury, signifying nothing" -- Shakespeare, MacBeth

Agile promised us engineer driven development. It was a shining deliverance from the dystopia of Waterfall where every important decision was being made immutable outside the hands of engineers. If you read the Agile manifesto it says as much. It values individuals, working software, collaboration, and rolling with the punches. These are awesome ideals. We would be included in requirements, we could give feedback. Changes would happen, it would be no one's fault and no one would be working weekends to keep up with them. We would have input at every level and most importantly WE would be the drivers of technical decisions. There would be jellybeans and lollipops. I mean who would argue against jellybeans and lollipops? Unfortunately for the vast majority of us, we got lollipoops and jellybeans from "Bertie Botts Every Flavour Beans" with every flavor but barf removed.

#### Agile is a hammer

Hammers are great tools and have their place. There is one place where Agile works: If you're a consulting company who needs to do a rapid prototype for a client that doesn't really know what they want. In this instance Agile works out IF you are billing on a time and materials basis. You just throw stuff together as quickly as possible because you know it's mostly trash anyway. No matter what crazy idea the client comes up with, you schedule it, explain the cost and do it if they're good with it. The client is happy, the consulting company is getting paid, eventually the project gets done. Win win (though the win is heavily in favor of the consulting company).

#### You are the nail

One thing to note above is that the consulting company is in no way in charge of anything. They're grunt workers dealing with "business driven development".

The core of waterfall and agile share this idea of "business driven development", and it is in this that they are the same bag of bad in different wrappers.

#### The reality of Agile: Waterfall 2.0

The reality of Agile is that you still have immutable decisions made by business people with no real understanding of technology. Those decisions are then forced on to developers. The end result is the same as Waterfall, only the names have changed.

Unfortunately, with little or no documentation, now the developer is accountable for the outcome while having little or no authority to create a winning one. This responsibility without authority makes Agile even more toxic than Waterfall.

> "Authority, when first detecting chaos at its heels, will entertain the vilest schemes to save its orderly facade." -- Alan Moore, V for Vendetta

The addition of the daily "scrum" ensures that anyone who is perceived to be working too slowly (whether this is true or not) is immediately highlighted. This type of "boiler room" atmosphere may work great for a few, but for most it is a source of significant stress and ultimately lower productivity. This pressure encourages developers to not think about the future, but rather just slap something together today that just barely functions. This is so prevalent in Agile that "tech debt" seems like a fundamental pillar of the process. If you're a startup that plans to be out of business in 6 months, this isn't really a problem. If you want to be around for a while, you better practice what you learned in shop class : "measure twice, cut once". In software, this means considering the bigger picture before you start slapping down lines of code.

#### Story points, the metrics of Agile

Even in measuring Agile fails. It uses a unitless measure called "story points". Unfortunately these are arbitrarily assigned, and then managers attempt to discern "velocity" from them. The problem is that teams aren't all that stable, and you need lots of data points. If your sprints last 2 weeks, you can get a maximum of 26 data points for a year, but often with team churn you really get 10 or less (insufficient data to draw conclusions from). Imagine sampling the temperature 10 times from April to August to determine what you should be wearing in December.

Worse still, story points almost always turn into "units of time" in the minds of those in charge. These units are then used to compare teams or force teams to explain why their "velocity" dropped, even though the numbers began as arbitrary unitless values and so can't be compared in this manner.

#### You're doing Agile wrong

Armies of "Agile consulting"companies have sprung up to convince you that you need help doing Agile. Your project failed; it's not Agile, it's you. You just did it wrong, and you would have won by doing it right (a [No True Scotsman](https://en.wikipedia.org/wiki/No_true_Scotsman) fallacy for those interested). Agile coaches, certified scrum masters, 2 day agile training courses, etc all have a vested interest in keeping the lie going. Why do you need coaches, masters and training for 4 basic ideas in the manifesto? Spoiler: You don't. You DO, however, need them to force waterfall into this new package.

#### So what should we do?

> "Happy families are all alike; every unhappy family is unhappy in its own way." -- Tolstoy, Anna Karenina

The inverse of what Tolstoy said about families is true for processes. All successful processes are unique. You can't read a book and go through it's 12 steps to build great software any more than you can read a book, go through it's 12 steps and come up with the next big thing. You have to figure it out for your situation. Here's where I'd start:

**Get rid of everything.**

Get rid of your scrum master, your product owner, your Agile coach, and fire the Agile consultancy that's going to make you more Agile. Now that you have a blank slate you can start to figure out what makes sense for YOU.

**Bring in the bare minimum amount of process.**

Maybe that's a board of app ideas, maybe it's a list of features currently being worked on just so you can figure out if there are going to be conflicts, etc. Whatever that minimum set is for you, start there.

**Get involved.**

When a feature goes from a "brainstorming" stage(which may include crazy ideas like "give users a ride to the ISS if they sign up 4 friends") to a "refinement" stage, get everyone involved. By this I don't mean just the dev managers, I mean everyone, soup to nuts, that will be involved with the feature. Don't discuss how long it will take. Discuss the merits of the feature, how it could be implemented, etc. These discussions should be vigorous and disruptive (this doesn't mean be unprofessional). These matter. Alot. If you exclude anyone, exclude managers. This creates an ACTUAL engineering driven culture.

**Only add processes that reduce significant actual risk.**

Create process to help reduce a particular risk IF you can answer yes to one of these three questions:

  1. Did an actual problem occur that was systemic and not just a one off? _Example: Sally and Bob both repeatedly started working on the same feature, and don't figure it out for 2 days because there's no way for them to do so._
  2. Is risk of a problem occurring very high? _Example: drives crash often enough that if your source isn't checked into source control for a month, there's a real risk of significant loss._
  3. Would a problem have catastrophic consequences? _Example: if a wing falls off a plane in flight, it's game over for everyone on board._

If the honest answer to all these questions is No, then you're wasting time with that part of the process.

**Ship it when it's ready, not before, not after.**

Let engineers do their work, think things through and write 15 lines of code instead of 150. Use code reviews, testing, etc. The cost of shipping the wrong thing is much higher than the cost of slipping arbitrary deadlines to ship the right thing.

#### Wait, now I'm agile

Yes, now you're lowercase a agile, not uppercase a Agile. There's a huge difference as I hope you've now seen. You have the minimum process that works for you and one that allows you to efficiently get stuff that matters done. Every minute you were previously spending on process that isn't part of your new minimum core is now recovered for productive work. Last, but not least, you now (hopefully) have an engineering driven organization.

**Go win**.

#### My current project

A company I co-founded, [June](https://joinjune.com), recently launched. June is a platform where IT professionals can get paid by recruiters to hear about opportunities. Opportunity sound good? Pursue it. Not a great one? No problem. You get paid either way. You can read about [how and why this works in detail here](https://medium.com/swlh/what-i-learned-from-nearly-a-year-of-working-with-recruiters-and-what-i-did-about-it-1cc1c59a7492) and apply to join at [joinjune.com](https://joinjune.com).

#### About Me

I'm Amir Yasin, the CTO and Co-Founder of [June](http://joinjune.com/). Get Paid to speak with the best IT recruiters in the world.

I'm a polyglot developer deeply interested in high performance, scalability, software architecture and generally solving hard problems. You can [follow me on Medium](https://medium.com/@ayasin) where I blog about software engineering, [follow me on Twitter](https://twitter.com/ayasin) where I occasionally say interesting things, or check out [my contributions to the FOSS community on GitHub](https://github.com/ayasin).

**If you enjoyed this post, I'd really appreciate a recommend (just click the heart below)**.
