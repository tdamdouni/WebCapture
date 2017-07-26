# Java Design Pattern: Builder

_Captured: 2015-11-21 at 12:42 from [www.programcreek.com](http://www.programcreek.com/2013/02/java-design-pattern-builder/)_

The key feature of Builder pattern is that it involves a step-by-step process to build something, i.e., every produce will follow the same _process _ even though each step is different.

In the following example, we can define a drink builder called StarbucksBuilder which will build a Starbucks drink. StarbucksBuilder has several steps to build a Starbucks drink, such as buildSize() and buildDrink(). And finally return the drink built.

**1\. Builder Design Pattern Class Diagram**

![builder-design-pattern](http://www.programcreek.com/wp-content/uploads/2013/02/builder-design-pattern.png)

> _2. Builder Design Pattern Java Code Example_
    
    
    package designpatterns.builder;
     
    // produce to be built
    class Starbucks {
    	private String size;
    	private String drink;
     
    	public void setSize(String size) {
    		this.size = size;
    	}
     
    	public void setDrink(String drink) {
    		this.drink = drink;
    	}
    }
     
    //abstract builder
    abstract class StarbucksBuilder {
    	protected Starbucks starbucks;
     
    	public Starbucks getStarbucks() {
    		return starbucks;
    	}
     
    	public void createStarbucks() {
    		starbucks = new Starbucks();
    		System.out.println("a drink is created");
    	}
     
    	public abstract void buildSize();
    	public abstract void buildDrink();
    }
     
    // Concrete Builder to build tea
    class TeaBuilder extends StarbucksBuilder {
    	public void buildSize() {
    		starbucks.setSize("large");
    		System.out.println("build large size");
    	}
     
    	public void buildDrink() {
    		starbucks.setDrink("tea");
    		System.out.println("build tea");
    	}
     
    }
     
    // Concrete builder to build coffee
    class CoffeeBuilder extends StarbucksBuilder {
    	public void buildSize() {
    		starbucks.setSize("medium");
    		System.out.println("build medium size");
    	}
     
    	public void buildDrink() {
    		starbucks.setDrink("coffee");
    		System.out.println("build coffee");
    	}
    }
     
    //director to encapsulate the builder
    class Waiter {
    	private StarbucksBuilder starbucksBuilder;
     
    	public void setStarbucksBuilder(StarbucksBuilder builder) {
    		starbucksBuilder = builder;
    	}
     
    	public Starbucks getstarbucksDrink() {
    		return starbucksBuilder.getStarbucks();
    	}
     
    	public void constructStarbucks() {
    		starbucksBuilder.createStarbucks();
    		starbucksBuilder.buildDrink();
    		starbucksBuilder.buildSize();
    	}
    }
     
    //customer
    public class Customer {
    	public static void main(String[] args) {
    		Waiter waiter = new Waiter();
    		StarbucksBuilder coffeeBuilder = new CoffeeBuilder();
     
    		//Alternatively you can use tea builder to build a tea
    		//StarbucksBuilder teaBuilder = new TeaBuilder();
     
    		waiter.setStarbucksBuilder(coffeeBuilder);
    		waiter.constructStarbucks();
     
    		//get the drink built
    		Starbucks drink = waiter.getstarbucksDrink();
     
    	}
    }

**3\. Real Usage of Builder Design Pattern**

Builder pattern has been used in a lot of libraries. However, there is a common mistake here. Consider the following example of StringBuilder which is a class from Java standard library. Does it utilize the Builder pattern?
    
    
    StringBuilder strBuilder= new StringBuilder();
    strBuilder.append("one");
    strBuilder.append("two");
    strBuilder.append("three");
    String str= strBuilder.toString();

In Java standard library, StringBuilder extends AbstractStringBuilder.

The append() method is one step of the process, just like a step in our Starbucks example. The toString() method is another and it is the last step. However, the difference here is that there is no waiter in the picture. The Waiter class plays the director role in the picture of the Builder pattern. Since there is no such role, it is not a Builder pattern.

Of course, this is not the only reason. You can compare with the class diagram at the beginning and find out another reason.

**4\. Difference between Builder and Factory**

Builder pattern is used when there are many steps to create an object. Factory pattern is used when the factory can easily create the entire object within one method call.
