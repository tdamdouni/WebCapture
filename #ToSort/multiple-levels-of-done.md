# Multiple Levels of Done

_Captured: 2017-02-10 at 18:38 from [www.mountaingoatsoftware.com](https://www.mountaingoatsoftware.com/blog/multiple-levels-of-done?utm_content=bufferd69f3&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

![](https://www.mountaingoatsoftware.com/uploads/blog/multiple-levels-of-done_quote.jpg)

_The following was originally published in Mike Cohn's monthly newsletter. If you like what you're reading, sign up to have this content delivered to your inbox weeks before it's posted on the blog, [here](https://www.mountaingoatsoftware.com/email-tips)._

Having a "definition of done" has become a near-standard thing for Scrum teams. The definition of done (often called a "DoD") establishes what must be true of each product backlog item for that item to be done.

A typical DoD would be something similar to:

  * The code is well written. (That is, we're happy with it and don't feel like it immediately needs to be rewritten.)
  * The code is checked in. (Kind of an "of course" statement, but still worth calling out.)
  * The code was either pair programmed or peer reviewed.
  * The code comes with tests at [all appropriate levels](https://www.mountaingoatsoftware.com/blog/the-forgotten-layer-of-the-test-automation-pyramid). (That is, unit, service and user interface.)
  * The feature the code implements has been documented in any end-user documentation such as manuals or help systems.

Many teams will improve their Definition of Done over time. For example, a team using the example above might not be able to do so much automated testing when first starting out. But, hopefully, they would add that to their definition of done over time.

All this is sufficient for the vast majority of teams. But I've worked on a few projects whose teams benefitted from having _multiple_ definitions of done. A team takes a product backlog item to definition of done Level 1 in a first sprint, to definition of done Level 2 in a subsequent sprint, and so on.

I am most definitely not saying they code something in a first sprint and test it in a second sprint. "Done" still means tested, but it may mean tested to different--but appropriate--levels. Let's look an example.

## An Example from a Game Studio

One thing I've really enjoyed in working with game studios is that they understand that not all work will make it into the finished game. Sometimes, for example, a game team experiments with a new character trying to make the character fun. If they can't, the character isn't added to the game.

So it would be extremely wasteful for a game team to have a definition of done requiring all art to be perfect, all audio be recorded, and refresh rates be high when they are merely trying to decide if a new character is fun. The team should do _just_ _enough_ to answer that question.

In a number of game studios, this has led to a four-level definition of done:

**Done, Level 1 (D1)** means the new feature works and decisions can be made. For animation, this was often "the character is animated in a white room." It's "shippable" to friendly users (often internal) who can comment on whether the new functionality meets its objective.

**D2:** The thing is integrated into the game and users can play it / interact with it.

**D3:** The feature is truly shippable. It's good enough to include in a major public release. The team may not want to release it yet--they may first want to improve the frame rate, add some polygons, brighten colors, and so on. But the feature could be shipped with this feature in this state if necessary.

**D4: **The feature is tuned, polished, and everyone loves it. There's nothing the team would change. A typical public release will include a mix of D4 and D3 items. There will always be areas the team wants to go back to and further improve. But, time intrudes and they ship the product. So D3 is totally shippable. You're not embarrassed by D3 and only your hardest core users will notice the ways it could be better. D4 rocks.

## Are Multiple Definitions of Done Right for You?

Very likely not. Most teams do quite well with a single definition of done. But the ideas above extend beyond just game development. I've used the same approach in a variety of other application domains, notably hardware development. In that case, the teams involved were developing dozens of new gadgets for an integrated suite of home automation products.

They used these definitions:

**D1: **The new hardware works on a test bench in the office.

**D2:** The new hardware is integrated with the other products in the suite.

**D3:** The new hardware is installed and running in at least one model house used for this type of beta testing.

**D4:** The product is fully ready for sale (e.g., it meets all requirements for UL approval).

Within this company, there were dozens of components in development at all times, and some components could be found at each level of doneness. For example, a product to raise and lower window shades could be in testing at the model home, while a newer component to open and close doors had just been started and was only working on a test bench of one developer.

Most projects will never need this. If you do think it's appropriate for you, before trying it, really be sure you're not using the technique as an excuse to skip things like testing.

Each level should exist as a way of making decisions about the product. A good test of that is to see if some features are dropped at each level. It is a good sign, for example, that sometimes a feature reaches a certain doneness level, and the product owner decides the feature is no longer wanted due to perhaps its cost or delivery time.
