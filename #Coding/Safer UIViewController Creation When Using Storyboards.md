# Safer UIViewController Creation When Using Storyboards

_Captured: 2015-12-03 at 19:37 from [medium.com](https://medium.com/ios-os-x-development/safer-uiviewcontroller-creation-when-using-storyboards-1915ac2b2c80#.4ort8bvh6)_

The [initializer-based](https://medium.com/ios-os-x-development/dependency-injection-in-swift-a959c6eee0ab#.fcvipcvia) dependency injection is likely the safest way of [creating view controllers](https://medium.com/ios-os-x-development/dependency-injection-in-view-controllers-9fd7d2c77e55#.8marr7fn8). However, it is not compatible with storyboards because controllers are created by the framework and dependencies can only be injected in properties. If the storyboards are still required, how can the risk of getting not fully configured controllers be minimized?

Restrict the view controller creation to one place, whose single responsibility is the creation of objects. The common design pattern called [Abstract Factory](https://en.wikipedia.org/wiki/Abstract_factory_pattern) can be applied here.

When using a factory, the view controller dependencies that have to be injected as properties reach the view controller via two paths:

  * The long-lived view controller dependencies become factory dependencies. They are first passed to the factory in its initializer and then to the view controller properties after the object construction.
  * The short-lived dependencies are passed to the factory creation methods as parameters.

### Example

The _PhotoDetailViewController_ has two dependencies: a photo and a context. The long-lived context becomes a factory dependency. The short-lived photo becomes a factory method parameter.

Now all clients that need to create _PhotoDetailViewController_ instances won't forget to pass a photo and a context to them.

### Testability

Even if the view controllers are created in one place without a factory, the above-mentioned technique can improve the testability. Imagine a routing object responsible for the navigation from one screen to another. _Wireframe _from the [VIPER](http://mutualmobile.github.io/blog/2013/12/04/viper-introduction/) architecture could be taken as an example.

By injecting an abstract factory into the _Wireframe_, it becomes trivial to test if the _Wireframe_ creates the proper view controllers.

Because the _ViewControllerFactory_ is a protocol, a spy implementing it can be injected instead of the _StoryboardViewControllerFactory_ for testing the _Wireframe._

### Conclusion

When the initializer-based dependency injection can't be accomplished, like with storyboards, the next-best alternative for setting dependencies is the property-based injection. To minimize the risk of working with not fully configured objects, the view controller creation should be constrained within one place. Code testability can be further improved by implementing the central creation point using the Abstract Factory pattern.
