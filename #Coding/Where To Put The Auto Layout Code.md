# Where To Put The Auto Layout Code

_Captured: 2015-09-01 at 10:52 from [swiftandpainless.com](http://swiftandpainless.com/where-to-put-the-auto-layout-code/)_

Auto Layout is kind of magic. Like a sorcerer you **tell** the elements where to position and how to behave. You don't put the elements to those positions yourself. The universe moves them because of your spells. Kind of.

But **when** should the spells be spoken? In other words when not using Interface Builder, where should the Auto Layout code go?

> Custom views that set up constraints themselves should do so by overriding this method. 

Because of this sentence I always thought Apple asks me to put the layout code in this method. But here is the problem: This method is called more than once by UIKit and adding the same constraint more than once is an error. The suggested approach I found in the Internet™ is to add a boolean to the view class and set it in updateConstraints() to make sure to only run the layout code once.

From the documentation again:

> When your custom view notes that a change has been made to the view that invalidates one of its constraints, it should immediately remove that constraint, and then call setNeedsUpdateConstraints to note that constraints need to be updated. 

This means updateConstraints() is meant to be used in the case then the constraints within a view change because of some events. For this scenario the name of the method makes much more sense.

In nearly all of my layouts the constraints are fixed. Sometimes I need to change the constant of a constraint. This can be done without removing and re-adding the constraint. (The constant of a NSLayoutConstraint is the only thing that can be changed after creation.)

Because of this, I started to put all the layout code in init(frame:). But I was not really comfortable with it because of the documentation mentioned above.

But then I heard in a session video of the WWDC this year an Apple engineer suggesting exactly that. And just yesterday I received an answer to a bug report in which I described the 'bug' that updateConstraints() isn't called. Turns out it wasn't a bug.

The Apple engineer wrote:

> In general, if the constraints will only be created once, it should be done in an initialization method (such as -init or -viewDidLoad, and so forth). Save -updateConstraints for things that are expected to change over the course of running the App. 

Nice. I love when my feeling about how code should be written is suggested by Apple.

An example of where I put my layout code can be found [here](http://swiftandpainless.com/dont-put-view-code-into-your-view-controller/).

Happy layouting!

If you enjoyed this post, then make sure you subscribe to my [feed](http://swiftandpainless.com/feed).
