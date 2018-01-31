# OOP Concept for Beginners: What Is Abstraction?

_Captured: 2017-12-20 at 11:41 from [dzone.com](https://dzone.com/articles/oop-concept-for-beginners-what-is-abstraction?edition=347096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-19)_

Try [Okta](https://dzone.com/go?i=247339&u=https%3A%2F%2Fdeveloper.okta.com%2Fsignup%2F%3Futm_campaign%3DSyndication%25253EGlobal%25253Edeveloper-trial-sep-14-FY18Q3%26utm_medium%3Dpre-text%26utm_source%3Ddzone-java-zone-all-developer) to add social login, MFA, and OpenID Connect support to your Java app in minutes. Create a [free developer account](https://dzone.com/go?i=247339&u=https%3A%2F%2Fdeveloper.okta.com%2Fsignup%2F%3Futm_campaign%3DSyndication%25253EGlobal%25253Edeveloper-trial-sep-14-FY18Q3%26utm_medium%3Dpre-text%26utm_source%3Ddzone-java-zone-all-developer) today and never build auth again.

Abstraction is one of the [key concepts](https://stackify.com/oops-concepts-in-java/) of object-oriented programming (OOP) languages. Its main goal is to handle complexity by hiding unnecessary details from the user. That enables the user to implement more complex logic on top of the provided abstraction without understanding or even thinking about all the hidden complexity.

That's a very generic concept that's not limited to object-oriented programming. You can find it everywhere in the real world.

## Abstraction in the Real World

I'm a coffee addict. So, when I wake up in the morning, I go into my kitchen, switch on the coffee machine and make coffee. Sound familiar?

Making coffee with a coffee machine is a good example of abstraction.

You need to know how to use your coffee machine to make coffee. You need to provide water and coffee beans, switch it on and select the kind of coffee you want to get.

The thing you don't need to know is how the coffee machine is working internally to brew a fresh cup of delicious coffee. You don't need to know the ideal temperature of the water or the amount of ground coffee you need to use.

Someone else worried about that and created a coffee machine that now acts as an abstraction and hides all these details. You just interact with a simple interface that doesn't require any knowledge about the internal implementation.

You can use the same concept in object-oriented programming languages like Java.

## Abstraction in OOP

Objects in an OOP language provide an abstraction that hides the internal implementation details. Similar to the coffee machine in your kitchen, you just need to know which methods of the object are available to call and which input parameters are needed to trigger a specific operation. But you don't need to understand how this method is implemented and which kinds of actions it has to perform to create the expected result.

Let's implement the coffee machine example in Java. You do the same in any other object-oriented programming language. The syntax might be a little bit different, but the general concept is the same.

### Use Abstraction to Implement a Coffee Machine

Modern coffee machines have become pretty complex. Depending on your choice of coffee, they decide which of the available coffee beans to use and how to grind them. They also use the right amount of water and heat it to the required temperature to brew a huge cup of filter coffee or a small and strong espresso.

### Implementing the _CoffeeMachine_ Abstraction

Using the concept of abstraction, you can hide all these decisions and processing steps within your _CoffeeMachine_ class. If you want to keep it as simple as possible, you just need a constructor method that takes a _Map _of _CoffeeBean_ objects to create a new _CoffeeMachine_ object and a _brewCoffee_ method that expects your _CoffeeSelection_ and returns a _Coffee_ object.

You can clone the source of the example project at https://github.com/thjanssen/Stackify-OopAbstraction.
    
    
            System.out.println(“Making coffee ...”);

_CoffeeSelection_ is a simple enum providing a set of predefined values for the different kinds of coffees.

And the classes _CoffeeBean_ and _Coffee_ are simple POJOs (plain old Java objects) that only store a set of attributes without providing any logic.

### Using the _CoffeeMachine_ Abstraction

Using the _CoffeeMachine_ class is almost as easy as making your morning coffee. You just need to prepare a _Map _of the available _CoffeeBean_s, instantiate a new _CoffeeMachine _object, and call the _brewCoffee _method with your preferred _CoffeeSelection_.
    
    
    import org.thoughts.on.java.coffee.CoffeeException;
    
    
            Map<CoffeeSelection, CoffeeBean> beans = new HashMap<CoffeeSelection, CoffeeBean>();

You can see in this example that the abstraction provided by the _CoffeeMachine _class hides all the details of the brewing process. That makes it easy to use and allows each developer to focus on a specific class.

If you implement the _CoffeeMachine_, you don't need to worry about any external tasks, like providing cups, accepting orders or serving the coffee. Someone else will work on that. Your job is to create a _CoffeeMachine_ that makes good coffee.

And if you implement a client that uses the _CoffeeMachine_, you don't need to know anything about its internal processes. Someone else already implemented it so that you can rely on its abstraction to use it within your application or system.

That makes the implementation of a complex application a lot easier. And this concept is not limited to the public methods of your class. Each system, component, class, and method provides a different level of abstraction. You can use that on all levels of your system to implement software that's highly reusable and easy to understand.

### Not Limited to the Client API

Let's dive a little bit deeper into the coffee machine project and take a look at the constructor method of the _CoffeeMachine_ class.
    
    
            this.configMap = new HashMap<CoffeeSelection, Configuration>();
    
    
            this.configMap.put(CoffeeSelection.ESPRESSO, new Configuration(8, 28));
    
    
            this.configMap.put(CoffeeSelection.FILTER_COFFEE, new Configuration(30, 480));

As you can see in the code snippet, the constructor not only stores the provided _Map_ of available _CoffeeBeans_ in an internal property, it also initializes an internal _Map _that stores the configuration required to brew the different kinds of coffees and instantiates a _Grinder_ and a _BrewingUnit_ object.

![As you can see in the code snippet, the constructor not only stores the provided Map of available CoffeeBeans in an internal property, it also initializes an internal Map that stores the configuration required to brew the different kinds of coffees and instantiates a Grinder and a BrewingUnit object.](https://stackify.com/wp-content/uploads/2017/11/class-diagram2-png-1024x506.png)

> _Constructor code snippet_

All these steps are not visible to the caller of the constructor method. The developer most likely doesn't even know that the _Grinder_ or _BrewingUnit_ class exists. That's another example of the abstraction that the _CoffeeMachine_ class provides.

### Each Class Provides Its Own Abstraction

The classes _Grinder _and _BrewingUnit _provide abstractions on their own. The _Grinder _abstracts the complexity of grinding the coffee and _BrewingUnit _hides the details of the brewing process.

That makes the implementation of the _CoffeeMachine _class a lot easier. You can implement the _brewCoffee_method without knowing any details about the grinding or brewing process. You just need to know how to instantiate the 2 classes and call the _grind_ and _brew_ methods.

### Different Abstraction Levels Within the Same Class

In this example, I took the abstraction one step further and implemented 3 methods to brew the different kinds of coffee. The _brewCoffee _method, which gets called by the client, just evaluates the provided _CoffeeSelection _and calls another method that brews the specified kind of coffee.

The _brewFilterCoffee_ and _brewEspresso_ methods abstract the specific operations required to brew the coffee.

I defined both methods as private because I just want to provide an additional, internal level of abstraction. That not only makes the implementation of the _brewCoffee _method a lot easier, it also improves the reusability of the code.

You could, for example, reuse the _brewEspresso _method when you want to support the _CoffeeSelection.CAPPUCCINO_. You would then just need to implement the required operations to heat the milk, call the _brewEspresso _method to get an espresso, and add it to the milk.

## Summary

Abstraction is a general concept which you can find in the real world as well as in OOP languages. Any objects in the real world, like your coffee machine, or classes in your current software project, that hide internal details provide an abstraction.

These abstractions make it a lot easier to handle complexity by splitting them into smaller parts. In the best case, you can use them without understanding how they provide the functionality. And that not only helps you to split the complexity of your next software project into manageable parts, it also enables you every morning to brew a fresh cup of amazing coffee while you're still half asleep.

Build and launch faster with Okta's user management API. Register today for the [free forever developer edition](https://dzone.com/go?i=226224&u=https%3A%2F%2Fdeveloper.okta.com%2Fsignup%2F%3Futm_campaign%3DSyndication%253EGlobal%253Edeveloper-trial-FY18Q2%26utm_medium%3Dpost-text%26utm_source%3Ddzone-java-zone-all-developer)!
