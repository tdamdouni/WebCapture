# Name Things Well

_Captured: 2017-10-10 at 20:20 from [dzone.com](https://dzone.com/articles/name-things-well?edition=329552&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-10)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

I've said that the five code qualities we've been discussing are quantifiable. That is, we can create more of them if we want. Let's discuss how to do this.

The one code quality I'd like to focus on is [cohesion](https://dzone.com/articles/quality-code-is-cohesive). To me, it makes the most sense and I can easily see when my code is cohesive and when it isn't. The number one way I do this is to ask myself if I can come up with a good name for it. If I can come up with a good name for something then I've scoped it correctly. I've defined its place in the world. I've said what it does so its intention is clear.

To non-software developers, the act of naming something may seem mundane or even trivial, but to professional software developers, we know that the greater part of developing software is all about coming up with really good names. After all, everything gets named in code: data and behavior.

Naming is how we imbue the system with knowledge. It's how we communicate what we're doing in our code to other developers. Names should be active and say plainly what the code does. I like using long names for things so I can clearly articulate what it is. In every IDE I've worked in in the last ten years, you just have to type the name in once and the next time you need to refer to the name it will autocomplete after a few keystrokes. Today, with most compilers, names can be up to 256 characters and I like to use as many as I feel I need to so I can express the intention behind what it represents.

Invariably I find that if I'm having trouble naming something that one or more of the code qualities are missing, especially cohesion, and that tells me to break things down into simpler entities.

I try to include domain terms in the names I use, and I try to exclude software jargon as much as possible. I know it's a lofty goal that I can't fully achieve but I like to keep my code as readable as possible to non-developers.

My wife is not a developer. She's a filmmaker. If she can read through some code I've written and get a general sense of what's going on and what it's all about then I'm pretty satisfied it's clear. But if she's completely confused, I'll take the time to rewrite the code so it's more understandable rather than pepper it with comments.

In fact, every time I see a what comment that describes what the code is doing, I find I can usually replace it with a method call and give that method a meaningful name. This is far more valuable than a comment. It makes the code itself expressive.

I have been chastised before for telling programmers to "write uncommented code." But many lines of comments in code are either a nuisance or are downright misleading, and everyone would be better off if it didn't exist. If you want to write a lot of comments then do it with your check-ins in version control where it could be more useful to say what you did.

One thing I find that's interesting as a design pattern developer is that I often end up with rather generic names for things. For example, the polymorphic method in a strategy pattern might be called process and the class name may represent how the strategy is processed. Since I use design patterns a lot, I often end up with generic method names, but I'm fine with that.

I like my methods to create observable behaviors in the system and I like to name my methods to reveal what observable behavior will happen when the method is invoked.

I also like naming things for how I use them. I find I do this a lot when I write automated tests. Doing test first development, I think about how I'm going to call a behavior before I think about how I'm going to implement that behavior. That's a really important, fundamental approach of good software development because it allows me to define what I want to do before I start focusing on how to do it.

I talked a lot about encapsulation in the past and one of the ways I define encapsulation is by hiding implementation details and only revealing what a service does. This involves more than just defining method parameters and return values. The method's name is also important. Names imply behavior and we want to imply the right behaviors with as few presuppositions on implementation details as possible. In other words, we want to name things for what they do, not how they do it.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
