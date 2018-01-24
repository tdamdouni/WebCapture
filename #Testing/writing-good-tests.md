# Writing Good Tests

_Captured: 2017-11-28 at 13:45 from [dzone.com](https://dzone.com/articles/writing-good-tests?edition=338993&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202017-11-28)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

As Misko Hevery, the author of AngularJS, says in his outstanding Google Tech Talk series " [Clean Code Talks](https://www.youtube.com/playlist?list=PL693EFD059797C21E)," most developers assume they know how to write a good test but they don't.

Knowing how to write a good test is paramount to being successful with TDD. Tests must be unique, expressive, and independent - easier said than done.

Doing TDD correctly is a discipline. It takes a deep understanding of a large body of knowledge as well as a lot of experience doing it. You can't learn TDD from a 500-word blog post any more than you can learn brain surgery from one. It takes dedication, time, and practice.

I'm hooked on TDD but I guess I was predisposed to that since I've written automated test programs from the very start of my career as a developer and throughout the past three decades.

As I grow older my memory fades. This happens to all of us, although I didn't believe it would happen to me when I was younger. Fortunately, wisdom replaces energy.

I lean on TDD to help me manage all those details I need to manage when I code. I rely on instant feedback from my builds to tell me if what I just did was a good thing or a bad thing. And with that kind of instant feedback, I make the connection between what I just did and how it affects my code.

Stimulus and response have to go together in order for an association to be made. If Pavlov rang the bell then fed his dogs an hour later they'd never make the connection. That's why we don't make the connection between the bugs we write when they're found, weeks later, by QA.

But good unit tests help us make this connection by giving us immediate feedback whenever we make a change to the system. They also help us articulate the behavior we want to create and then validate that that behavior is working as expected.

Writing implementation independent tests by asserting against acceptance criteria or known behaviors gives us the freedom to change the implementation later without breaking our tests. Most developers weren't taught how to do this, but writing good tests are central to success with TDD. Writing a test for every public method often drives us to write implementation-dependent tests, which can break when we refactor code.

Good tests are extremely valuable because they help you build out behaviors in ways that make sense and they support you in refactoring your code later. But in order for tests to have these amazing benefits and more they must be good tests. They must be unique, at the right level of abstraction, based on acceptance criteria, and be implementation independent.

I have discussed some of the major pitfalls to doing TDD in my book, _[Beyond Legacy Code: Nine Practices to Extend the Life (and Value) of Your Software](http://BeyondLegacyCode.com)_, as well as on [my blog](http://ToBeAgile.com/blog). I also teach [classes for professional software developers](https://tobeagile.com/training-home/). Where you get experience doing TDD correctly you can see the benefits for yourself.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
