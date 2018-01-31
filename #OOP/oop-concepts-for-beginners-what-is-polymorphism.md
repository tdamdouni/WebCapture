# OOP Concepts for Beginners: What Is Polymorphism

_Captured: 2018-01-02 at 04:29 from [dzone.com](https://dzone.com/articles/oop-concepts-for-beginners-what-is-polymorphism?edition=347148&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-01)_

The word polymorphism is used in various contexts and describes situations in which something occurs in several different forms. In computer science, it describes the concept that objects of different types can be accessed through the same interface. Each type can provide its own, independent implementation of this interface. It is one of the [core concepts of object-oriented programming (OOP)](https://stackify.com/oops-concepts-in-java/).

If you're wondering if an object is polymorphic, you can perform a simple test. If the object successfully passes multiple is-a or [instanceof](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/op2.html) tests, it's polymorphic. As I've described in my post about [inheritance](https://stackify.com/oop-concept-inheritance/), all Java classes extend the class _Object_. Due to this, all objects in Java are polymorphic because they pass at least two instanceof checks.

## **Different Types of Polymorphism**

Java supports 2 types of polymorphism:

  * static or compile-time
  * dynamic

### **Static Polymorphism**

Java, like many other object-oriented programming languages, allows you to implement multiple methods within the same class that use the same name but a different set of parameters. That is called [method overloading](https://docs.oracle.com/javase/tutorial/java/javaOO/methods.html) and represents a static form of polymorphism.

The parameter sets have to differ in at least one of the following three criteria:

  * They need to have a different number of parameters, e.g. one method accepts 2 and another one 3 parameters.
  * The types of the parameters need to be different, e.g. one method accepts a _String_ and another one a _Long._
  * They need to expect the parameters in a different order, e.g. one method accepts a _String_ and a _Long_ and another one accepts a _Long_ and a _String_. This kind of overloading is not recommended because it makes the API difficult to understand.

In most cases, each of these overloaded methods provides a different but very similar functionality.

Due to the different sets of parameters, each method has a different [signature](https://www.thoughtco.com/method-signature-2034235). That allows the compiler to identify which method has to be called and to bind it to the method call. This approach is called static binding or static polymorphism.

Let's take a look at an example.

#### **A Simple Example for Static Polymorphism**

I use the same CoffeeMachine project as I used in the previous posts of this series. You can clone it at https://github.com/thjanssen/Stackify-OopInheritance.

The _BasicCoffeeMachine_ class implements two methods with the name _brewCoffee_. The first one accepts one parameter of type _CoffeeSelection_. The other method accepts two parameters, a _CoffeeSelection_, and an _int_.
    
    
        public List brewCoffee(CoffeeSelection selection, int number) throws CoffeeException {
    
    
            for (int i=0; i<number; i++) {

Now when you call one of these methods, the provided set of parameters identifies the method which has to be called.

In the following code snippet, I call the method only with a _CoffeeSelection_ object. At compile time, the Java compiler binds this method call to the _brewCoffee(CoffeeSelection selection)_ method.

If I change this code and call the _brewCoffee_ method with a _CoffeeSelection_ object and an _int_, the compiler binds the method call to the other _brewCoffee(CoffeeSelection selection, int number)_ method.

### **Dynamic Polymorphism**

This form of polymorphism doesn't allow the compiler to determine the executed method. The [JVM](https://en.wikipedia.org/wiki/Java_virtual_machine) needs to do that at runtime.

Within an [inheritance hierarchy](https://stackify.com/oop-concept-inheritance/), a subclass can override a method of its superclass. That enables the developer of the subclass to customize or completely replace the behavior of that method.

It also creates a form of polymorphism. Both methods, implemented by the super- and subclass, share the same name and parameters but provide different functionality.

Let's take a look at another example from the CoffeeMachine project.

#### **Method Overriding in an Inheritance Hierarchy**

The _BasicCoffeeMachine_ class is the superclass of the _PremiumCoffeeMachine_ class.

![](https://stackify.com/wp-content/uploads/2017/12/word-image-13.png)

Both classes provide an implementation of the _brewCoffee(CoffeeSelection selection)_ method.
    
    
            this.configMap.put(CoffeeSelection.FILTER_COFFEE, new Configuration(30, 480));
    
    
        public List brewCoffee(CoffeeSelection selection, int number) throws CoffeeException {
    
    
            for (int i=0; i<number; i++) {
    
    
                throw new CoffeeException("CoffeeSelection ["+selection+"] not supported!");
    
    
            GroundCoffee groundCoffee = this.grinder.grind(this.beans.get(CoffeeSelection.FILTER_COFFEE), config.getQuantityCoffee());
    
    
            return this.brewingUnit.brew(CoffeeSelection.FILTER_COFFEE, groundCoffee, config.getQuantityWater());
    
    
        public void addBeans(CoffeeSelection selection, CoffeeBean newBeans) throws CoffeeException {
    
    
                    existingBeans.setQuantity(existingBeans.getQuantity() + newBeans.getQuantity());
    
    
                this.beans.put(selection, newBeans);

If you read the post about the [OOP concept inheritance](https://stackify.com/oop-concept-inheritance/), you already know the two implementations of the _brewCoffee_ method. The _BasicCoffeeMachine_ only supports the _CoffeeSelection.FILTER_COFFEE_. The _brewCoffee _method of the _PremiumCoffeeMachine_ class adds support for _CoffeeSelection.ESPRESSO_. If it gets called with any other _CoffeeSelection_, it uses the keyword _super_ to delegate the call to the superclass.

#### **Late Binding**

When you want to use such an inheritance hierarchy in your project, you need to be able to answer the following question: which method will the JVM call?

That can only be answered at runtime because it depends on the object on which the method gets called. The type of the reference, which you can see in your code, is irrelevant. You need to distinguish three general scenarios:

  1. Your object is of the type of the superclass and gets referenced as the superclass. So, in the example of this post, a _BasicCoffeeMachine_ object gets referenced as a _BasicCoffeeMachine_.
  2. Your object is of the type of the subclass and gets referenced as the subclass. In the example of this post, a _PremiumCoffeeMachine_ object gets referenced as a _PremiumCoffeeMachine_.
  3. Your object is of the type of the subclass and gets referenced as the superclass. In the CoffeeMachine example, a _PremiumCoffeeMachine_ object gets referenced as a _BasicCoffeeMachine_.

#### **Superclass Referenced as the Superclass**

The first scenario is pretty simple. When you instantiate a _BasicCoffeeMachine_ object and store it in a variable of type _BasicCoffeeMachine_, the JVM will call the _brewCoffee_ method on the _BasicCoffeeMachine_ class. So, you can only brew a _CoffeeSelection.FILTER_COFFEE_.

#### **Subclass Referenced as the Subclass**

The second scenario is similar. But this time, I instantiate a _PremiumCoffeeMachine_ and reference it as a _PremiumCoffeeMachine_. In this case, the JVM calls the _brewCoffee_ method of the _PremiumCoffeeMachine_class, which adds support for _CoffeeSelection.ESPRESSO_.

#### **Subclass Referenced as the Superclass**

This is the most interesting scenario and the main reason why I explain dynamic polymorphism in such details.

When you instantiate a _PremiumCoffeeMachine_ object and assign it to the _BasicCoffeeMachine coffeeMachine_ variable, it still is a _PremiumCoffeeMachine_ object. It just looks like a BasicCoffeeMachine.

The compiler doesn't see that in the code, and you can only use the methods provided by the _BasicCoffeeMachine_ class. But if you call the _brewCoffee_ method on the _coffeeMachine_ variable, the JVM knows that it is an object of type _PremiumCoffeeMachine_ and executes the overridden method. This is called late binding.

## **Summary**

Polymorphism is one of the core concepts in OOP languages. It describes the concept that different classes can be used with the same interface. Each of these classes can provide its own implementation of the interface.

Java supports two kinds of polymorphism. You can overload a method with different sets of parameters. This is called static polymorphism because the compiler statically binds the method call to a specific method.

Within an inheritance hierarchy, a subclass can override a method of its superclass. If you instantiate the subclass, the JVM will always call the overridden method, even if you cast the subclass to its superclass. That is called dynamic polymorphism.
