# Java Design Pattern: Decorator – Decorate your girlfriend

_Captured: 2015-11-21 at 13:00 from [www.programcreek.com](http://www.programcreek.com/2012/05/java-design-pattern-decorator-decorate-your-girlfriend/)_

Decorator pattern adds additional features to an existing object dynamically. In this post, I will use a simple example - decorate your girlfriend - to illustrate how decorator pattern works.

**1\. Decorator Pattern Story**

Let's assume you are looking for a girlfriend. There are girls from different countries such as America, China, Japan, France, etc. They may have different personalities and hobbies. In a dating web like eharmony.com, if each type of girl is an individual Java class, there would be thousands of classes. That is a serious problem called _class explosion_. Moreover, this design is not extensible. Whenever there is a new girl type, a new class needs to be created.

Let's change the design, and let each hobby/personality becomes a decorator which can be dynamically applied to a girl.

**2\. Class Diagram**

![java-design-pattern-decorator](http://www.programcreek.com/wp-content/uploads/2012/05/java-design-pattern-decorator-650x626.jpeg)

Girl is the abstract class at the top level, we have girls from different countries. With a GirlDecorator class, we can decorator each girl with any feature by adding a new decorator.

**3\. Decorator pattern Java code**

Girl.java
    
    
    public abstract class Girl {
    	String description = "no particular";
     
    	public String getDescription(){
    		return description;
    	}
    }

AmericanGirl.java
    
    
    public class AmericanGirl extends Girl {
    	public AmericanGirl(){
    		description = "+American";
    	}
    }

EuropeanGirl.java
    
    
    public class EuropeanGirl extends Girl {
    	public EuropeanGirl() {
    		description = "+European";
    	}
    }

GirlDecorator.java

Science.java
    
    
    public class Science extends GirlDecorator {
     
    	private Girl girl;
     
    	public Science(Girl g) {
    		girl = g;
    	}
     
    	@Override
    	public String getDescription() {
    		return girl.getDescription() + "+Like Science";
    	}
     
    	public void caltulateStuff() {
    		System.out.println("scientific calculation!");
    	}
    }

We can add more method like "Dance()" to each decorator without any limitations.

Art.java
    
    
    public class Art extends GirlDecorator {
     
    	private Girl girl;
     
    	public Art(Girl g) {
    		girl = g;
    	}
     
    	@Override
    	public String getDescription() {
    		return girl.getDescription() + "+Like Art";
    	}
     
    	public void draw() {
    		System.out.println("draw pictures!");
    	}
    }

Main.java
    
    
    package designpatterns.decorator;
     
    public class Main {
     
    	public static void main(String[] args) {
    		Girl g1 = new AmericanGirl();
    		System.out.println(g1.getDescription());
     
    		Science g2 = new Science(g1);
    		System.out.println(g2.getDescription());
     
    		Art g3 = new Art(g2);
    		System.out.println(g3.getDescription());
    	}
    }

Output:

+American  
+American+Like Science  
+American+Like Science+Like Art

We can also do something like this:

**4\. Decorator Pattern Used in Java Stand Library**

A typical usage of Decorator pattern is Java IO classes.

Here is a simple example - BufferedReader decorates InputStreamReader.

InputStreamReader(InputStream in) - bridge from byte streams to character streams. InputSteamReader reads bytes and translates them into characters using the specified character encoding.

BufferedReader(Reader in) - read text from a character stream and buffer characters in order to provide efficient reading methods(e.g., readLine())
