# Java Design Pattern: Factory

_Captured: 2015-11-21 at 12:40 from [www.programcreek.com](http://www.programcreek.com/2013/02/java-design-pattern-factory/)_

**1\. The story for Factory pattern**

Factory design pattern is used for creating an object based on different parameters. The example below is about creating human in a factory. If we ask the factory for a boy, the factory will produce a boy; if we ask for a girl, the factory will produce a girl. Based on different parameters, the factory produce different stuff.

**2\. Factory pattern class diagram**

![factory-design-pattern](http://www.programcreek.com/wp-content/uploads/2013/02/factory-design-pattern.png)

> _3. Factory pattern Java code_
    
    
    interface Human {
    	public void Talk();
    	public void Walk();
    }
     
     
    class Boy implements Human{
    	@Override
    	public void Talk() {
    		System.out.println("Boy is talking...");		
    	}
     
    	@Override
    	public void Walk() {
    		System.out.println("Boy is walking...");
    	}
    }
     
    class Girl implements Human{
     
    	@Override
    	public void Talk() {
    		System.out.println("Girl is talking...");	
    	}
     
    	@Override
    	public void Walk() {
    		System.out.println("Girl is walking...");
    	}
    }
     
    public class HumanFactory {
    	public static Human createHuman(String m){
    		Human p = null;
    		if(m.equals("boy")){
    			p = new Boy();
    		}else if(m.equals("girl")){
    			p = new Girl();
    		}
     
    		return p;
    	}
    }

**4\. Factory design pattern used in Java standard library**

Based on different parameter, getInstance() returns a different instance of Calendar.
    
    
    java.util.Calendar - getInstance()
    java.util.Calendar - getInstance(TimeZone zone)
    java.util.Calendar - getInstance(Locale aLocale)
    java.util.Calendar - getInstance(TimeZone zone, Locale aLocale)
    java.text.NumberFormat - getInstance()
    java.text.NumberFormat - getInstance(Locale inLocale)
    

You can view the source code of [Calendar](http://www.javased.com/index.php?source_dir=openjdk-7/java/util/Calendar.java#getInstance-Locale-aLocale) and [NumberFormat](http://www.javased.com/index.php?source_dir=openjdk-7/java/text/NumberFormat.java) in [javased.com](http://www.javased.com/?action=source-search).
