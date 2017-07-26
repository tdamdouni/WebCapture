# Pathologies of Inquisitive Code

_Captured: 2017-07-07 at 06:52 from [dzone.com](https://dzone.com/articles/pathologies-of-inquisitive-code?edition=306234&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-06)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Objects that are not assertive are by default inquisitive. They are either inquisitive or they are mute. They don't interact with the outside word at all. If an object interacts with other objects, the real question with regard to assertiveness is, "Who's in charge?"

One object can delegate a task to another object but still be in charge of that task and therefore still be assertive. It's when an object gives up its control of a task - when it doesn't have access to the resources it needs to fulfill its tasks - that it has to become inquisitive.

Inquisitive code is poorly performant. If you look at a sequence diagram, which is one of the 14 UML diagrams, you'll see that the sequence of calls for inquisitive code is more involved than the sequence of calls for assertive code. This is because inquisitive code has to access other objects through their public interface in order to access their private state, which it needs in order to accomplish its tasks. When one object makes repeated calls to other objects to access its state, it can degrade performance even as it unnecessarily increases complexity, making the code more difficult to read and understand. Business rules are then spread out across multiple objects and it becomes harder to define boundaries for objects when the objects themselves become less and less well-defined.

The very essence of what an object is depends upon its responsibilities. Inquisitive objects end up being poorly defined, which distorts the overall object model and makes it difficult to figure out where other responsibilities belong in a system.

Martin Fowler describes some of the "code smells" related to inquisitive code with funny and memorable names such as, "feature envy" where one object is constantly accessing the features of another object that should be part of the responsibilities of the calling object, and therefore part of the calling object. He also uses the term, "inappropriate intimacy" for inquisitive code because when one object calls into other objects in this way, it often becomes bound to those other objects' implementation. This kind of interdependence drives the cost of change up because when one piece of code is changed the dependent pieces break and must also be changed to be kept in sync.

When code is assertive instead of inquisitive, all the behavior is in one place so it's far easier to read and understand.

Code that is inquisitive also has encapsulation issues because the state and behavior that it should possess is somewhere else and often the state that needs to be shared between these behaviors in separate objects is better left private.

All of these issues are bad but as we start to scale up, writing multi-threaded issues and multi-user systems, these issues become paramount. Inquisitive code is more difficult to make multi-threaded and to run on high availability servers. If high performance is important then writing assertive code is also important.

In a lot of ways, inquisitive code is a holdover from procedural programming. Procedural programs can be inquisitive. They can take a global perspective. But in object-oriented programs, we want to create behaviors through the interaction of objects rather than using explicit logic because it's more maintainable and extendable to do it this way.

Assertive code supports this, inquisitive code doesn't.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
