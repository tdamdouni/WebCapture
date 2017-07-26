# Using the MVVM Design Pattern in iOS

_Captured: 2017-03-12 at 20:20 from [dzone.com](https://dzone.com/articles/mvvm-in-ios?oid=twitter&utm_content=buffer0dd96&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190139&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190139&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral).

MVVM (model/view/view-model) is design pattern that helps promote a [separation of concerns](https://en.wikipedia.org/wiki/Separation_of_concerns) in software development. It is an extension of the well-known model/view/controller (MVC) pattern that is often used in user interface design.

In a traditional MVC application, a controller object is used to mediate the interaction between two other objects known as the "model" and the "view." The model is an abstract representation of data managed by the application, and the view is a visual representation of the data contained in the model. The controller notifies the view of changes to the model and updates the model in response to user input events received from the view.

MVVM expands on MVC by further decoupling the view from the controller. Instead of requiring the controller to explicitly manage the view's state, a view in an MVVM application uses [data binding](https://en.wikipedia.org/wiki/Data_binding) to be automatically updated in response to changes in a "view model" object exposed by the controller. This object adapts the data provided by the underlying model so that it can be easily consumed by the view. The additional level of indirection allows the view and controller to vary independently without the risk of breaking one or the other.

## MVC Example

For example, consider a simple custom table view cell implemented using MVC:

![](https://gkbrown.files.wordpress.com/2017/02/custom_cells.png?w=700)

The cell class might provide a set of outlets that the table view controller can use to update its state:

The controller would use the outlets to populate the cell's contents when a new cell is requested. In this example, row data is provided by dictionary instances containing `"heading"` and `"detail"` values for each cell:

However, this design creates a tight coupling between the controller and the custom cell view. Any time the view class changes, the controller must also be updated.

## MVVM Example

MVVM solves this problem by decoupling the view from the controller. Rather than exposing its implementation details via outlets, the view registers itself as an observer on the properties of the view model. Using this approach, the view and controller both become dependent on the view model, but neither is dependent on the other. As long as the view model doesn't change, either one can be modified without impact.

For example, the following markup shows a custom table view cell implemented using [MarkupKit](https://github.com/gk-brown/MarkupKit), an open-source framework for building native iOS and tvOS applications using a simple HTML-like markup language. The cell contains two labels arranged vertically in a column:

Instead of outlets, the custom cell class exposes a `content` property representing the view model. The labels' `text` properties are bound to the properties of this object:

With the bindings established, the controller can be implemented as shown below. It simply dequeues a cell and sets its `content` property to the dictionary for the corresponding row. Because they are bound to the properties of the view model, the cell's labels are automatically updated to reflect the new values. No direct manipulation of view elements is required:

## Summary

This article introduced the MVVM design pattern and provided an example of how it can be used to simplify the implementation of a custom table view cell. The complete source code for the example can be found [here](https://github.com/gk-brown/MarkupKit/tree/master/MarkupKit-iOS/MarkupKitSample).

For more information, see the MarkupKit [README](https://github.com/gk-brown/MarkupKit/blob/master/README.md).

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190140&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190140&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral).
