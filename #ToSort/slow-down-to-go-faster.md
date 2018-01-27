# Slow Down to Go Faster

_Captured: 2018-01-27 at 22:42 from [dzone.com](https://dzone.com/articles/slow-down-to-go-faster?edition=359093&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-27)_

**[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). **

I know it seems like a paradox but often we have to slow down in order improve our productivity. We need to step back and look at what we're doing and see if we can find more effective ways to meet our goals.

A [NIST study](http://www.cse.psu.edu/~gxt29/bug/localCopies/nistReport.pdf) showed that over 80% of software developers' time is spent undoing the things they did in the first 20% of their time on the project. Developing software is fraught with inefficiencies from the process of writing down then interpreting requirements for the separation of coding from testing and the enormous amount of time lost when debugging software.

Clearly, there must be better ways of constructing software than the way most people are doing it, and there are, but some of the techniques are not commonly known.

Extreme Programming (XP) has been promoting emergent design and test-first development since the early 2000s, and those of us who apply these practices well have been seeing their value and have been reaping great rewards. But this is a complex field and just following the practices of Extreme Programming doesn't guarantee success. Writing software involves many skills and building it well involves even more skills.

I'm an advocate for test-first development because I find it helps me go faster by slowing me down.

Test-first makes me first think about the interface I want to create and then build a strong contract around that interface. Building strong contracts around interfaces is an important skill for good software architecture, and TDD has me focus on this as one of the first things I do when building a system. I like that.

Another thing that TDD does to help slow me down is that it concretizes abstract requirements by giving me examples of the behaviors I want to create. This is a pretty different way of thinking about building software than most of us were trained.

In the past, if I wanted to handle image compression, for example, I would go off and build an image compression library. It would involve weeks of design and planning and then even more weeks of coding until I could get enough of the system to compile that I could actually test it at some level--and this may be several months into a project. In many ways, I'm flying blind. I get no feedback from my tools until my code compiles and runs.

By contrast, building a system incrementally using test-first development and by specification by example means you always have a working version of the system and you're building it interactively. All the tools you have, including your compiler and all the unit tests you've written, are constantly running to support you and tell you when you make mistakes. This is a far more preferable way of building software because it's safer.

Which brings me to the best way to slow down and that is to have a fast build.

Having a fast build is central to doing Extreme Programming effectively. If you have a slow build then you probably have technical debt that has to be paid off in order for your system to run more efficiently, in which case it also pays to slow down and pay off your debt so that system runs efficiently.

Understanding design options and principles also help me to slow down because I know that it's often trivial to refactor code from one design to another design. I don't have to feel rushed into committing to any particular design when I'm building a system because I know that as I learn more I can refactor it fairly easily.

With techniques that allow me to build systems a piece at a time, allowing the design to emerge, I find that the quality of my work increases significantly. Emergent design does work--when we pay attention to some fundamental principles that make code more testable and straightforward to work with.

**Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). **
