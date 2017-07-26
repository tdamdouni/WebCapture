# Java Design Pattern: Template Method

_Captured: 2015-11-21 at 13:20 from [www.programcreek.com](http://www.programcreek.com/2012/08/java-design-pattern-template-method/)_

The Template Method design pattern defines the workflow for achieving a specific operation. It allows the subclasses to modify certain steps without changing the workflow's structure.

The following example shows how Template Method pattern works.

**Class diagram**

![template-method-pattern-class-diagram](http://www.programcreek.com/wp-content/uploads/2012/08/template-method-pattern-class-diagram.jpg)

**Java Code**

Vehicle.java defines a vehicle and hot it works
    
    
    package com.programcreek.designpatterns.templatemethod;
     
    abstract public class Vehicle {
    	//set to protected so that subclass can access
    	protected boolean status;
     
    	abstract void start();
    	abstract void run();
    	abstract void stop();
     
    	public void testYourVehicle(){
    		start();
    		if(this.status){
    			run();
    			stop();
    		}	
    	}
    }

Car.java subclass Vehicle and defines concrete methods
    
    
    package com.programcreek.designpatterns.templatemethod;
     
    public class Car extends Vehicle {
     
    	@Override
    	void start() {
    		this.status = true;
    	}
     
    	@Override
    	void run() {
    		System.out.println("Run fast!");
     
    	}
     
    	@Override
    	void stop() {
    		System.out.println("Car stop!");
    	}
    }

Truck.java subclass Vehicle and defines concrete methods
    
    
    package com.programcreek.designpatterns.templatemethod;
     
    public class Truck extends Vehicle {
     
    	@Override
    	void start() {
    		this.status = true;
    	}
     
    	@Override
    	void run() {
    		System.out.println("Run slowly!");
    	}
     
    	@Override
    	void stop() {
    		System.out.println("Truck stop!");
     
    	}
    }

The testVehicle method only accept a Vehicle, it does not care if it is a car or truck, because they will work in the same way. This is an example of program to interface(P2I).
    
    
    import com.programcreek.designpatterns.templatemethod.Car;
    import com.programcreek.designpatterns.templatemethod.Truck;
    import com.programcreek.designpatterns.templatemethod.Vehicle;
     
    public class Main {
    	public static void main(String args[]){
    		Car car = new Car();
    		testVehicle(car);
     
    		Truck truck = new Truck();
    		testVehicle(truck);
    	}
     
    	public static void testVehicle(Vehicle v){
    		v.testYourVehicle();
    	}
    }

**Real usage of Template Method Pattern**

This pattern is used in Spring framework's Data Access Object(DAO). org.springframework.jdbc.core.JdbcTemplate class has all the common repeated code blocks related with JDBC workflow, such as update, query, execute, etc.

Category >> [Design Patterns Stories](http://www.programcreek.com/category/design-patterns/)

If you want to post syntax highlighted code and let me or someone else review it, please put the code inside <pre><code> and </code></pre> tags.   
For example:
    
    
    <pre><code> 
    String foo = "bar";
    </code></pre>
    
