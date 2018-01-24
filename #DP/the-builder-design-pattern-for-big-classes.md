# The Builder Design Pattern for Big Classes

_Captured: 2018-01-13 at 10:17 from [dzone.com](https://dzone.com/articles/builder-design-pattern-for-big-classes?edition=352110&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-12)_

Learn how to troubleshoot and diagnose some of [the most common performance issues in Java today](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201131&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-top-10-java-performance-problems%2F%3Futm_source%3Dsponsorship%26utm_medium%3Dsponsorship%26utm_campaign%3Djava%2525252520zone%26utm_content%3Debook-top-10-java-performance-problems%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

As per the original definition of Builder Design Pattern, it separates the construction of a complex object from its representation so that the same construction process can create different representations. One side effect of this pattern is that we can avoid mistakes associated with the construction of an object with a constructor that takes too many arguments. For example, consider the following class:

You see the problem here. The constructor asks the developer to send the arguments in a specific order. To double the problem, all the arguments are Strings and anybody using this constructor needs to remember the order or check the documentation, if there is any present. Imagine a situation when there are more than 10 arguments. This is very cumbersome in that case.

How do we make life easier for developers who are using this class? One way could be providing a default constructor and setter methods for each of the attributes. I see a number of issues with this approach, namely:

  * What if my class should not have a default constructor, i.e. we cannot imagine an Employee having no name, department, address, phone, or mobile. One argument could be that we have a constructor with mandatory attributes. But then, if the list of mandatory attributes itself is too long, then we again end up with the problem that we want to solve. However, if the mandatory arguments are not too large in number, then we may use this approach.
  * If we are using setters, there are times when we have the Employee object created but not complete in a logical sense, i.e. we are still setting up the properties. This inconsistent state of the object may cause issues when there are multiple threads trying to access the object.

The better approach would be to use the Builder Design pattern as given in the code down below.

Before we see it, however, there are a couple of points to be noted in the implementation.

  * The constructor for the Employee class is private. This ensures that no one can create an instance using the problematic constructor. This pre-empts the urge by developers to use the constructor directly to create an instance.
  * Builder is an inner class of Employee. We need to do this, as there are no public setter methods in Employee for the reason described above, and Builder needs to have access to the private properties of Employee.
    
    
            return "Employee [id=" + id + ", name=" + name + ", department=" +
    
    
                department + ", address=" + address + ", phone=" + phone + ", mobile=" + mobile + "]";
    
    
                Employee emp = new Employee(name, department, address, phone, mobile);

The following code shows how we use this to create an instance of the Employee class:

Understand the needs and benefits around implementing [the right monitoring solution for a growing containerized market](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital). Brought to you in partnership with [AppDynamics.](https://dzone.com/go?i=201132&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Fthe-importance-of-monitoring-containers%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%2520zone%26utm_content%3Dimportance-of-monitoring-containers%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital)
