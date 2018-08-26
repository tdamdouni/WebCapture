# Design Patterns Explained: Adapter Pattern With Code Examples

_Captured: 2018-05-28 at 16:49 from [dzone.com](https://dzone.com/articles/design-patterns-explained-adapter-pattern-with-cod?edition=379196&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-05-27)_

Design patterns provide a reliable and easy way to follow [proven design principles](https://stackify.com/solid-design-principles/) and to write well-structured and maintainable code. One of the popular and often used patterns in object-oriented software development is the adapter pattern. It follows Robert C. Martin's [Dependency Inversion Principle](https://stackify.com/dependency-inversion-principle/) and enables you to reuse an existing class even so it doesn't implement an expected interface.

If you do some research on the adapter pattern, you will find two different versions of it:

  1. The class adapter pattern that implements the adapter using [inheritance](https://stackify.com/oop-concept-inheritance/).
  2. The object adapter pattern that uses [composition](https://stackify.com/oop-concepts-composition/) to reference an instance of the wrapped class within the adapter.

You are probably aware of all the discussions about [inheritance vs. composition](https://www.thoughtworks.com/de/insights/blog/composition-vs-inheritance-how-choose). Composition provides more flexibility and avoids unexpected side-effect when you need to change existing code. Due to this, the object adapter pattern is by far the more popular approach and the one I will focus on in this article.

## The Adapter Pattern

The general idea of an adapter in software development is identical to the one in the physical world. If you have been to different countries, you probably recognized that a lot of them are using [differently shaped power sockets](https://www.power-plugs-sockets.com/). Quite often, they are shaped in a way that the plug of your electrical device doesn't fit. So, how do you connect the charger of your mobile phone or laptop to these power sockets?

The answer is simple. You get an adapter which you can put into the power socket and then you put your plug into the other end of the adapter. The adapter changes the form of your plug so that you can use it with the power socket. In that example and in most other situations, the adapter doesn't provide any additional functionality. It just enables you to connect your plug to the power socket.

The Adapter Pattern applies the same idea to object-oriented programming by introducing an additional adapter class between an [interface](https://docs.oracle.com/javase/tutorial/java/concepts/interface.html) and an existing class.

![](https://stackify.com/wp-content/uploads/2018/05/adapter-pattern-concept-18941.png)

The adapter class implements the expected interface and keeps a reference to an object of the class you want to reuse. The methods defined by the interface call one or more methods on the referenced object and return a value of the expected type. By doing that, the adapter class fulfills the expected contract by implementing the interface and enables you to reuse existing, incompatible implementations.

Let's apply the pattern to an example.

## Brewing coffee using the Adapter Pattern

I like to start my morning with a fresh cup of coffee. The only issue is that I need to get out of bed and prepare the coffee before I can drink it. It would be much better if it would be automatically prepared when my alarm rings. So, let's build a small app for it.

### An App to Brew a Coffee

The _FilterCoffeeApp_ does exactly that. It expects an implementation of the _FilterCoffeeMachine_ interface as a constructor parameter and uses it in the _prepareCoffee_ method to brew a cup of filter coffee.

The _FilterCoffeeMachine_ interface is relatively simple. It just defines the _brewCoffee_method which you can call to make a cup of coffee.

That seems to be a good approach that enables you to use different coffee machines with your application. The only requirement is that all classes that represent a coffee machine implement the _FilterCoffeeMachine_ interface.

### A Basic Coffee Machine

The _BasicCoffeeMachine_ class implements that interface and can be used by the _FilterCoffeeApp_.
    
    
        private Map<CoffeeSelection, GroundCoffee> groundCoffee; private BrewingUnit brewingUnit;
    
    
            this.config = new Configuration(30, 480);
    
    
                    existingCoffee.setQuantity(existingCoffee.getQuantity() + newCoffee.getQuantity());

### A Premium Coffee Machine

But what happens if you get a new, more advanced coffee machine that doesn't implement the _FilterCoffeeMachine_ interface?

You can use the _Coffee brewCoffee(CoffeeSelection selection) throws CoffeeException_ method of the _PremiumCoffeeMachine_ to prepare filter coffee or espresso. As you can see, the method has the same name as the one defined by the _FilterCoffeeMachine_ interface, but the method signature is incompatible. It expects a parameter and [declares an exception](https://stackify.com/specify-handle-exceptions-java/).

The _PremiumCoffeeMachine_ represents a coffee machine, but it doesn't implement the _FilterCoffeeMachine_ interface. So, you can't use it with the _FilterCoffeeApp_.

I will not change the class so that it implements the required interface. It's oftentimes not possible to change existing classes because they are implemented by a different team or the classes are used in other projects which don't contain the required interface. I also don't want to change the _FilterCoffeeMachine_ interface. The _BasicCoffeeMachine_ implements that interface and I would need to change that class whenever I change the interface. In these situations, it's better to apply the adapter pattern.

### Implementing the Adapter

By introducing an adapter class, that implements the _FilterCoffeeMachine_ interface and wraps the _PremiumCoffeeMachine_ class, you enable your _FilterCoffeeApp_ to use the coffee machine.

![](https://stackify.com/wp-content/uploads/2018/05/adapter-pattern-example-18928.png)

> _For this example, the adapter class needs to fulfill two tasks:_

  1. It has to provide an implementation of the _FilterCoffeeMachine_ interface.
  2. The _brewCoffee_ method needs to bridge the gap between the _brewCoffee_method defined by the interface and the _brewCoffee_ method implemented by the _PremiumCoffeeMachine_ class.

The interface and the existing class are not too different. That makes the implementation of the adapter class relatively simple.

As you can see in the code snippet, the _FilterCoffeeAdapter_ class implements the _FilterCoffeeMachine_ interface and expects a _PremiumCoffeeMachine_ object as a constructor parameter. It keeps that object in a private field so that it can use it in the _brewCoffee_ method.

The implementation of the _brewCoffee_ method is the critical and for most adapter classes, the most difficult part. In this case, the _PremiumCoffeeMachine_ class provides a method that you can call to perform the task. But it's more flexible and requires a _CoffeeSelection_ enum value to define which kind of coffee it shall produce.

The method of the _PremiumCoffeeMachine_ class throws a _CoffeeException_ if it gets called with a _CoffeeSelection_ value different than _FILTER_COFFEE_ and _ESPRESSO_. The _brewCoffee_ method of the _FilterCoffeeMachine_ interface doesn't declare this exception and you need to handle it within the method implementation.

In this example, there is no perfect way to do that. You can either write a log message and return null, as I did in the code snippet, or you can [throw a ](https://stackify.com/specify-handle-exceptions-java/)_[RuntimeException](https://stackify.com/specify-handle-exceptions-java/)_.

In your application, you might have better ways to handle the exception. You might be able to perform a retry or to trigger a different business operation. This would make your application more robust and improve the implementation of your adapter.

## Summary

The Adapter Pattern is an often-used pattern in object-oriented programming languages. Similar to adapters in the physical world, you implement a class that bridges the gap between an expected interface and an existing class. That enables you to reuse an existing class that doesn't implement a required interface and to use the functionality of multiple classes, that would otherwise be incompatible.

One advantage of the Adapter Pattern is that you don't need to change the existing class or interface. By introducing a new class, which acts as an adapter between the interface and the class, you avoid any changes to the existing code. That limits the scope of your changes to your software component and avoids any changes and side-effects in other components or applications.

The Adapter Pattern provides an implementation of the Dependency Inversion design principle. If you're not already familiar with it, I recommend reading about the different SOLID design principles. I wrote a series of articles explaining all five of them:
