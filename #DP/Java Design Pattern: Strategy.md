# Java Design Pattern: Strategy

_Captured: 2015-11-21 at 13:19 from [www.programcreek.com](http://www.programcreek.com/2011/01/a-java-example-of-strategy-design-pattern/)_

Strategy pattern is also called policy pattern.

Here is a story about Strategy pattern. Suppose Mike sometimes speeds when driving, but he doesn't always do that. He may be stopped by a police officer. It's possible that the police is very nice, who would let him go without any ticket or with a simple warning. (Let call this kind of police "NicePolice".) Also it's possible that he may be caught by a hard police and gets a ticket. (Let's call this kind of police "HardPolice".) He doesn't know what kind of police would stop him, until he actually gets caught, that is, run-time. This is the whole point of Strategy pattern.

**Strategy Pattern Class Diagram**

![strategy-pattern-class-diagram](http://www.programcreek.com/wp-content/uploads/2011/01/strategy-pattern-class-diagram.jpg)

**Strategy Pattern Java Code**

Define a interface Strategy, which has one method processSpeeding()

Now we have two kinds of police officers.
    
    
    public class HardPolice implements Strategy{
    	@Override
    	public void processSpeeding(int speed) {
    		System.out.println("Your speed is "+ speed+ ", and should get a ticket!");
    	}
    }

Define a situation in which a police officer will be involved to process speeding.
    
    
    public class Situation {
    	private Strategy strategy;
     
    	public Situation(Strategy strategy){
    		this.strategy = strategy;
    	}
     
    	public void handleByPolice(int speed){
    		this.strategy.processSpeeding(speed);
    	}
    }

Finally, try the result.
    
    
    public class Main {
    	public static void main(String args[]){
    		HardPolice hp = new HardPolice();
    		NicePolice ep = new NicePolice();
     
    		// In situation 1, a hard officer is met
                    // In situation 2, a nice officer is met
    		Situation s1 = new Situation(hp);
    		Situation s2 = new Situation(ep);
     
    		//the result based on the kind of police officer.
    		s1.handleByPolice(10);
    		s2.handleByPolice(10);        
    	}
    }

Output is:
    
    
    Your speed is 10, and should get a ticket!
    This is your first time, be sure don't do it again!
    

You can compare this pattern with[ State pattern](http://www.programcreek.com/2011/07/java-design-pattern-state/) which is very similar. The major difference is that State pattern involves changing the behavior of an object when the state of the object changes while Strategy pattern is mainly about using different algorithm at different situation.

**Strategy Pattern in JDK**

1). Java.util.Collections#sort(List list, Comparator < ? super T > c)  
2). java.util.Arrays#sort(T[], Comparator < ? super T > c)

The sort method use different Comparator in different situations. To know more about this method, check out [Deep Understanding of Arrays.sort()](http://www.programcreek.com/2013/11/arrays-sort-comparator/).

You may also want to check out [The Difference between Comparator and Comparable](http://www.programcreek.com/2011/12/examples-to-demonstrate-comparable-vs-comparator-in-java/).
