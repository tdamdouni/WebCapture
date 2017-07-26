# The Pragmatics of TDD

_Captured: 2015-10-17 at 21:51 from [blog.8thlight.com](http://blog.8thlight.com/uncle-bob/2013/03/06/ThePragmaticsOfTDD.html)_

So my last blog: [The Startup Trap](http://blog.8thlight.com/uncle-bob/2013/03/05/TheStartUpTrap.html) raised quite a ruckus. Amidst the various shouts of agreement and support, there was also a group who vehemently disagreed. I'm not going to summarize all their disagreements here, since I've already used up my quota of curse words for the month. But one of those disagreements struck me as something I should address.

It's the old argument of pragmatism vs. dogmatism. In essence, the complaint was that I was being too dogmatic. That TDD might be great in some cases, but in others it might have too high a cost. So you have to be pragmatic and choose wisely.

At first this sounds perfectly reasonable. After all, pragmatism is a good thing, right? I mean, if you knew that TDD was going to make you miss your deadline; and that you could make the deadline by dropping it; you'd drop it, right?

Right. No question. And, in fact, there are times when that's exactly the right course of action. The purpose of this blog is to lay out those times when _I_ think TDD is too expensive.

But before I do I want to make a point. TDD is a discipline for programmers like double-entry bookkeeping is for accountants or sterile procedure is for surgeons. Are there times when accountants don't use double-entry bookkeeping? Are there times when surgeons don't use sterile procedure?

The answer is yes in both cases. I rather doubt that accountants use double-entry bookkeeping when they balance their personal checkbooks, or when checking the total on a restaurant bill. I could be proven wrong about the former, after all, I used double-entry bookkeeping for years when balancing my checkbook. But I eventually grew to realize that the effort wasn't worth the risk. As for the latter, I think we'd all agree that double-entry bookkeeping is overkill for a restaurant bill.

As for surgeons and sterile procedure: I had a lipoma removed from my arm several years ago. My wife, an RN, observed the procedure. It was done under local in the doctors office. As the doctor was preparing I heard her question the doctor about the fact that he wasn't using sterile procedure. He replied that for an operation of this size "clean procedure" was adequate. She and I accepted that statement; and the doctor completed the operation.

A couple of days later, the incision became inflamed and painful. One of the sutures had become infected, and they had to reopen the incision and clean it out. I don't know if this was because of "clean procedure" but from now on I will insist that the doctors who work on me use sterile procedure and not "clean procedure".

Still, the point is valid. There are times when TDD is too costly, and a lower discipline should be used instead. I hope my stories have convinced you that those times are rare corner cases, and that the pragmatism meme should not be used to thwart your disciplines just because they seem inconvenient.

### The Pragmatics

So, when do I _not_ practice TDD?

  * I don't write tests for getters and setters. Doing so is usually foolish. Those getters and setters _will_ be indirectly tested by the tests of the other methods; so there's no point in testing them directly.

  * I don't write tests for member variables. They too will be tested indirectly. 

  * I don't write tests for one line functions or functions that are obviously trivial. Again, they'll be tested indirectly.

  * I don't write tests for GUIs. GUIs require _fiddling_. You have to nudge them into place by changing a font size here, an RGB value there, an XY position here, a field width there. Doing that test-first is silly and wasteful. 

    * However, I make sure that any significant processing in the GUI code is removed into modules that are testable. I don't allow significant code to go untested. So my GUI code is little more than glue and wires that pull data into place on the screen. (See articles on MVVM or Model View Presenter)
  * In general I don't write tests for any code that I have to "fiddle" into place by trial and error. But I separate that "fiddling" code from code that I am surer of and can write tests for. 

    * I have, upon occasion, fiddled code into place and then written tests after the fact.
    * I have also, upon occasion, deleted the code once "fiddled" and re-written it test-first.  

    * Which of these you choose is a judgement call.  

  * A few months ago I wrote an entire 100 line program without any tests. (GASP!)

    * The program was a one-shot. It was used once and then discarded it. (It was for a special effect in one of my videos).
    * The program was all about the screen. In essence it was a pure GUI app. So I had to _fiddle_ the whole thing into place.
    * I wrote it in Clojure, and so I had the REPL! I could run the growing program from the REPL, and I could _see_ the results of every line of code I wrote instantly. It wasn't TDD, it was EDD (Eye Driven Development).  

  * I usually don't write tests for frameworks, databases, web-servers, or other third-party software that is supposed to work. I mock these things out, and test _my_ code, not theirs.

    * Of course I sometimes _do_ test the third-party code if: 
      * I think it's broken.
      * The results are fast and predictable enough that a Mock would be overkill.

### It's not _all_ Dogma.

This list isn't complete. I'm sure I'll think of some other times that I don't write tests; but the spirit of this list ought to be evident. Pragmatics _do_ come into play when doing TDD; it's not all dogma.

However, I respect the dogma; there is a reason for it. Pragmatics can sometimes override; but: _I will not write any significant production code without making every effort to use TDD._

Robert Martin (Uncle Bob) is a Master Craftsman. He's an award-winning author, renowned speaker, and has been an uber software geek since 1970.
