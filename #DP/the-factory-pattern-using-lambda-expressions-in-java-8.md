# The Factory Pattern Using Lambda Expressions in Java 8

_Captured: 2017-04-25 at 23:54 from [dzone.com](https://dzone.com/articles/factory-pattern-using-lambda-expression-in-java-8)_

Learn how to troubleshoot and diagnose some of [the most common performance issues in Java today](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

The factory pattern is one of the most used design patterns in Java. This type of design pattern falls under the host of creational patterns, as this pattern provides one of the best ways to create an object. The factory design pattern lets you create objects without exposing the instantiation logic to the client.

In this post, I would like to give an example of Factory pattern and then rewrite the same example using the lambda expression to be introduced in Java 8.

## Factory Pattern: An Example

I am going to create a _Shape_ interface as well as concrete classes implementing the _Shape_ interface. A factory class _ShapeFactory_ is defined as the next step.

Create an interface: _Shape.java_

Consider two implementations of this Shape interface: _Circle.java_ & _Rectangle.java_

Create a Factory to generate an object of your concrete classes based on given information.

Use the Factory to get an object of concrete class by passing an information such as type: _FactoryPatternDemo.java_

Verify the output:

## Factory Pattern: Refactor With Lambda Expressions

In Java 8, we can refer to constructors just like we refer to methods, by using  
method references. For example, here's how to refer to the Circle constructor:

Using this technique, we could rewrite the previous code by creating a Map that maps a shape  
name to its constructor:

We can now use this Map to instantiate different shapes, just as we did with the previous factory code:
    
    
      final static Map<String, Supplier<Shape>> map = new HashMap<>();
    
    
         Supplier<Shape> shape = map.get(shapeType.toUpperCase());

Use the factory to get an object of concrete class using the lambda expression: _FactoryPatternDemo.java_
    
    
         shapeFactory.get().getShape("circle").draw();
    
    
         shapeFactory.get().getShape("rectangle").draw();      

Verify the output:

This is quite a neat way to make use of a Java 8 feature to achieve the same intent as the  
factory pattern. But this technique doesn't scale very well if the factory method getShape  
needs to take multiple arguments to pass on to the Shape constructors! You'd have to provide  
a different functional interface than a simple Supplier.

Understand the needs and benefits around implementing [the right monitoring solution for a growing containerized market](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics.](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital)

### Like This Article? Read More From DZone
