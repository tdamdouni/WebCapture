# An Object Model

_Captured: 2017-11-02 at 18:57 from [dzone.com](https://dzone.com/articles/an-object-model?edition=334828&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-02)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

If you were to draw out all the objects in your system and their relationship to each other at runtime, that would be a graphical representation of your object model.

Object-oriented programming is about modeling the behavior of entities. It is a programming paradigm that, when used correctly, helps us build resilient systems that are straightforward to understand and extend. But we gain these benefits only by correctly using the object-oriented paradigm, which involves having a domain model that reflects what's being modeled.

Designs often start out with a good domain model but then degrade over time as new features are added. Features get hacked in and new behaviors are bolted onto existing objects rather than expanding the object model to include these new classes. This distorts the object model and makes it more difficult to understand. Behaviors, and even entirely new classes, can be hiding in long methods. Pulling them out makes the code clearer and cleaner.

Object-oriented programming languages allow us to define classes and instantiate objects, but I find some developers resistant to doing that, having the false impression that creating objects is expensive and makes a system less efficient. But creating object instances are cheap, and modern runtimes are optimized for this. We should be defining classes and making objects all the time.

Any group of behaviors that converge around a set of values or state should be defined as a class. Since a class can represent anything, we can think of it in many ways, but most fundamentally as a concept that aggregates behaviors, often around a common set of instance data. For example, a savings account aggregates behaviors like deposits and withdrawals around an account balance.

Classes and objects, their runtime representations, can contain data that represents its state. They can also contain methods that represent its behaviors.

Though classes may only contain data and methods, object-oriented languages provide a rich environment for modeling anything. Classes can represent anything from tangible objects to ephemeral ideas. They can be a part of a larger whole, or they can represent the relationship between different entities.

Classes can be anything.

And there's the rub.

We have to name our classes well. If we don't create good, intention revealing names, our object model becomes distorted. If we stuff behavior into another object that belongs to its own object, the object model gets distorted. If we fail to call out classes in our domain or spread responsibilities across multiple, unrelated classes, our object model gets distorted.

When an object model gets distorted it becomes hard to read and understand. Worse still, a distorted object model will often lack flexibility precisely where flexibility is most needed.

Going against a design to special case features can often lead to maintainability issues, so we want to keep our object model robust and clear. We want it to reflect reality: the thing we're modeling. The way we do this is by calling out classes when we find them. We must actively look for classes and continue to expand our object model as our knowledge of our system expands. This is how we keep a system maintainable.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
