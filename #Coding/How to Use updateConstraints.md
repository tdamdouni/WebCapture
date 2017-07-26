# How to Use updateConstraints

_Captured: 2015-09-01 at 00:24 from [oleb.net](http://oleb.net/blog/2015/08/how-to-use-updateconstraints/)_

Ever since the `updateConstraints()` method got added to `UIView` when auto layout was introduced, I have asked myself what it, and its sibling `updateViewConstraints()` on `UIViewController`, is good for. I always found these methods awkward to implement.

This is what [the documentation](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIView_Class/#//apple_ref/occ/instm/UIView/updateConstraints) has to say (emphasis mine):

> Custom views that set up constraints themselves should do so by overriding this method. _When your custom view notes that a change has been made to the view that invalidates one of its constraints, it should immediately remove that constraint, and then call `setNeedsUpdateConstraints` to note that constraints need to be updated._ Before layout is performed, your implementation of `updateConstraints` will be invoked, allowing you to verify that all necessary constraints for your content are in place at a time when your custom view's properties are not changing.

Sounds simple enough: whenever you need to change your layout, invalidate it. Then wait for the system to call `updateConstraints()` in the next layout pass, which is your chance to make the necessary changes to your layout constraints. In practice this approach doesn't work so well, however:

  1. You're not starting with a clean slate on every execution of `updateConstraints()`. Your view will already have some constraints, and in most cases you only need to modify some of them. This means the typical `updateConstraints()` implementation would be littered with if statements to check if a particular constraint already exists.

  2. Your view doesn't necessarily own all of its constraints. Other views in the view hierarchy may have added constraints to your view, so your code cannot make assumptions about the contents of the `constraints` array. This means you'll have to keep track of all the constraints you may need to modify in separate properties, anyway.

  3. Changes to constraints are usually made in response to events. If you follow the advice in the documentation, your event handling code would need to call `setNeedsUpdateConstraints()` after updating some internal state. This means the code that modifies the layout (in `updateConstraints()`) is in a different place than the code that triggers the change, which can make the logic harder to follow.

(On the other hand, littering your class with imperative layout modification code in various places can be unclear too. A [pure functional approach to layout](https://facebook.github.io/react-native/) where a view's full layout is declared in a single place and recomputed from scratch on every frame would probably be best, but isn't trivial to do with good performance in UIKit.)

So should you use `updateConstraints()` as suggested in the documentation? In this year's [Mysteries of Auto Layout (Part 2) WWDC session](https://developer.apple.com/videos/wwdc/2015/?id=219), Apple gives different advice:

> Really, all this is is a way for views to have a chance to make changes to constraints just in time for the next layout pass, but it's often not actually needed.
> 
> All of your initial constraint setup should ideally happen inside Interface Builder. Or if you really find that you need to allocate your constraints programmatically, some place like `viewDidLoad` is much better. `updateConstraints` is really just for work that needs to be repeated periodically.
> 
> Also, it's pretty straightforward to just change constraints when you find the need to do that; whereas, if you take that logic apart from the other code that's related to it and you move it into a separate method that gets executed at a later time, your code becomes a lot harder to follow, so it will be harder for you to maintain, it will be a lot harder for other people to understand.
> 
> So when would you need to use `updateConstraints`? Well, it boils down to performance. If you find that just changing your constraints in place is too slow, then update constraints might be able to help you out. It turns out that changing a constraint inside `updateConstraints` is actually faster than changing a constraint at other times. The reason for that is because the engine is able to treat all the constraint changes that happen in this pass as a batch.

There you have it. Don't use `updateConstraints()` for the initial setup of your view. Use it for best performance when you need to add, modify, or delete lots of constraints within a single layout pass. If performance is not a problem, updating your constraints directly in place is often easier.
