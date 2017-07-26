# Java Design Pattern: Adapter

_Captured: 2015-11-21 at 12:57 from [www.programcreek.com](http://www.programcreek.com/2011/09/java-design-pattern-adapter/)_

Adapter pattern is frequently used in modern Java frameworks.

It comes into place when you want to use an existing class, and its interface does not match the one you need, or you want to create a reusable class that cooperates with unrelated classes with incompatible interfaces.

**1\. Adapter pattern story**

The Adapter idea can be demonstrated with the following simple example. The purpose of the sample problem is to adapt an orange as an apple.

![Java Adapter Design Pattern](http://www.programcreek.com/wp-content/uploads/2011/09/SimpleAdapter.jpg)

From the lower diagram, the adapter contains an instance of Orange, and extends Apple. It seems to be that after an Orange object gets a adapter skin, it acts like an Apple object now.

**2\. Adapter class diagram**

![adapter-pattern-class-diagram](http://www.programcreek.com/wp-content/uploads/2011/09/adapter-pattern-class-diagram.jpg)

> _3. Adapter pattern Java code_
    
    
    class Apple {
    	public void getAColor(String str) {
    		System.out.println("Apple color is: " + str);
    	}
    }
     
    class Orange {
    	public void getOColor(String str) {
    		System.out.println("Orange color is: " + str);
    	}
    }
     
    class AppleAdapter extends Apple {
    	private Orange orange;
     
    	public AppleAdapter(Orange orange) {
    		this.orange = orange;
    	}
     
    	public void getAColor(String str) {
    		orange.getOColor(str);
    	}
    }
     
    public class TestAdapter {
    	public static void main(String[] args) {
    		Apple apple1 = new Apple();
    		Apple apple2 = new Apple();
    		apple1.getAColor("green");
     
    		Orange orange = new Orange();
     
    		AppleAdapter aa = new AppleAdapter(orange);
    		aa.getAColor("red");
    	}
     
    }

Indeed, this probably is the simplest idea about adapter pattern. A double-way adapter may be used more often. To make a double-channel adapter, adapter requires to implements two interfaces and contains the two instances. It is still a simple idea.

**4\. Adapter Pattern used in Java SDK**

java.io.InputStreamReader(InputStream) (returns a Reader)  
java.io.OutputStreamWriter(OutputStream) (returns a Writer)

In a real large framework, the idea may not be very apparent. E.g. How the Adapter idea is used in Eclipse is not so easy to discover. [This](http://www.programcreek.com/2011/09/adapters-in-eclipse/) is a post towards how it is used in Eclipse Runtime.
