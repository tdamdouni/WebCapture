# Encapsulation and Testability

_Captured: 2017-11-09 at 20:11 from [dzone.com](https://dzone.com/articles/encapsulation-and-testability?edition=334857&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-09)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Poorly encapsulated software is hard to test because without clear boundaries, what we actually test becomes significantly larger than what we need to test. This makes our tests run slower and it also makes them brittle so our tests are harder to maintain.

When code is unencapsulated, it can be hard to lock down behaviors in a system that we want to test. This can get so bad that we may not even be able to use a programmatic interface and must resort instead to simulating the user interacting with the system.

Manual testing or even automating user input to drive testing is a bad idea. It's far too high level and it ties your tests to your user interface, making them brittle. It's far better to provide a programmatic interface that can be used to test code.

Unit testing is the first type of testing we should think of because it's the simplest and also the most cost-effective.

Find problems early, or better yet, set up the system so we just can't make mistakes. Encapsulation is like that. Encapsulation is a promise that a boundary is created and that nothing will penetrate that boundary. We can define an object that has public parts and private parts. The public parts can be accessed by anything or anyone but the private parts are internal, nothing on the outside can access the private information or behavior inside.

This guarantee in software languages allows us to create software that is both reliable and secure. Of course, by convention, instance data that an object holds should be marked private so that no other object can access it directly. If outside objects do need access to that data then we will provide public getters and setters.

We may, for example, want to serialize access to a particular resource so we're granting access to only one request at a time, or we may want to just keep track of the requestors, or keep account of them, or whatever. The object that holds the state gets to decide - and that's the point of object-oriented programming. We want objects to encapsulate their own state and be in charge of it, that is to say, to contain the behaviors that access that state, which is the next code quality that we'll be talking about: [assertiveness](https://dzone.com/articles/quality-code-is-assertive).

Testable code tends to be well-encapsulated. It hides implementation details and can validate if that behavior is correct. Testable code is code that can be tested at the unit level. When code is built with tests in this way there's less need for other kinds of tests. A lot of the QA testing, scenario testing, and other types of non-automated testing can go away. We're then left with a suite of tests that have all the characteristics we need: they run fast, they give the right level of feedback, and they support refactoring - all good qualities in a test base.

Unit tests run fast because we're only testing what we need to. If the tests were written well and written to be unique, unit tests also provide the right level of feedback.

And finally, when they're written to test behaviors rather than implementations, unit tests support refactoring. If we test behaviors and then refactor the code so we're changing the design but not changing the behaviors our tests shouldn't break.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
