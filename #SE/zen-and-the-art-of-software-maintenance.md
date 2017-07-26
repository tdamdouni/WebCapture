# Zen and the Art of Software Maintenance

_Captured: 2017-05-04 at 22:14 from [dzone.com](https://dzone.com/articles/zen-and-the-art-of-software-maintenance)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

On April 24, 2017, Robert M. Pirsig, author of [Zen and the Art of Motorcycle Maintenance](http://amzn.to/2oWYEGY), died - one of the best books I have ever read. In this post, we'll have a quick look at how his book might be useful for software developers without giving away too many spoilers.

## The Chase for Quality

In the book, the main character describes how his past self chased the understanding of quality. The problem started with the most basic question: _what is quality really?_ Can you define _quality_ without resorting to synonyms like _perfection_ or _virtue_? Is quality objective or subjective? If it's objective, then how come there's no instrument to measure it yet? If, on the contrary, quality is subjective, then why does it matter so much and how come most people can agree about the quality of certain things?

Obviously, this problem can be easily moved into the software world. How do we define software quality? How do we know whether a piece of software is of high quality? How do we _make_ such software? These are all valid questions, especially for those of you that care about the job you're doing and the software you produce.

The answer seems to lie in the word that I've just used: _care_. In a sense, quality and excellence are not what defines an object; these are what cause the object to be in the first place. If you _care_ about them when building the product, then you're building them _in_ the product. If you read the fantastic [Clean Code](http://amzn.to/2pzkUdF) book, this point of view should resemble the one from James Coplien's foreword:

> Quality is the result of a million selfless acts of care--not just of any great method that descends from the heavens. 

## Form and Function

In some parts of the book, although not as many as the title might suggest, the main character talks about how the motorcycle is built and how to maintain it. He goes on for a while about the parts that the motorcycle consists of and how these parts are built from other parts and so on. This is an important description of what makes up the motorcycle, but it's not sufficient. In a perfect world, it might be even enough to build a motorcycle, but would you be able to maintain it? Would you be able to really tell anyone _how _it works? Not really. You'd just know the _what_, the _form _of the motorcycle, but not the _how_.

The _how _of the motorcycle is also referred to as the _function_ of each of its parts. Although to some it might be of little interest, it could actually be considered more important than the _form_. Imagine that a part of the motorcycle broke on the road. If you know it's _function_, then perhaps you know you can get to the nearest mechanic without it. Or you can replace it with something that you carry in your backpack until you get a better replacement. If you know just the _form_ and a part breaks, then either you have that exact part with you or you're screwed.

These concepts, although maybe understood a little deeper, lie at the roots of the [DCI architecture](http://tidyjava.com/dci-architecture-visionary/). The dumb data classes are the system's _form._ The primary goal of their existence is to describe _what the system is_. The roles that are then dynamically assigned to these classes are descriptions of _what the system does_ - its underlying _function_. These two descriptions are related, i.e. they can work together as a system, but are, at the same time, separate. Since a system's use case is described by the _function_ rather than its _form,_ and the roles are dynamically assignable, the system becomes very flexible, i.e. you can easily replace parts as long as they are suitable to perform certain _functions_.

You can find more about the all interesting DCI architecture in another great book: [Lean Architecture for Agile Software Development](http://amzn.to/2p0kxFQ).

## Gumption Traps

"Zen and the Art of Motorcycle Maintenance" is not only the title of the book but also a concept coined by the main character's current self. One of its most important parts is gumption towards the motorcycle maintenance. To preserve gumption, one must avoid what the character calls the _gumption traps_. Simply put, these are all the things that could disturb you and drag your mind and enthusiasm away from the motorcycle and the problem at hand.

Gumption traps can be divided into two main categories: setbacks and hang-ups. The former are all the external factors that work against your gumption, e.g. you have to do the job all over again because you forgot to put in some part, or you are simply missing the part that you need to finish your job. The latter are more internal factors like boredom or impatience. If you're willing to do a good job at motorcycle maintenance, you need to have exactly the opposite: interest and patience. If you currently don't, maybe it's time for a break.

Software developers obviously have a plethora of gumption traps to fall into. The most common setback is obviously a changing or clarifying requirement. If it means that you will have to rework everything you did in the past weeks or months then, well, here your gumption goes away. The second most common setback that I know of would be the company's processes. Emails, meetings, approvals, tickets, escalations - for a newbie in the field, it seems like everyone around wants you to do anything but programming. As for hang-ups, these are no different than in the motorcycle maintenance field. Everyone gets bored from time to time when tasked with one of these repeatable, my company-forces-me-to-do-it type of things. And obviously, everyone gets impatient from time to time, when things do not work out as we expected.

The topic of gumption is very interesting, but there's only so many words one can fit in a single article that people will then actually read. If I got you interested in the gumption traps and fighting them then [Zen and the Art of Motorcycle Maintenance](http://amzn.to/2oWYEGY) and [The Clean Coder](http://amzn.to/2qo4gMh) books are for you.

## Final Words

As already stated in the first paragraph, _Zen and the Art of Motorcycle Maintenance_ is one of the best books that I have ever read. As it often happens with quality literature, the topic does not necessarily have to be of in your area of expertise and you can still find a ton of wisdom and useful advice in there. Therefore, set aside some time every day and read, read, read. It will make you a better programmer and a wiser person.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
