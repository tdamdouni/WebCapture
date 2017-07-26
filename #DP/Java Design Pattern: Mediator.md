# Java Design Pattern: Mediator

_Captured: 2015-11-21 at 13:24 from [www.programcreek.com](http://www.programcreek.com/2013/02/java-design-pattern-mediator/)_

Mediator design pattern is used to collaborate a set of colleagues. Those colleagues do not communicate with each other directly, but through the mediator.

In the example below, Colleague A want to talk, and Colleague B wants to fight. When they do some action(i.e., doSomething()), they invoke mediator to do that.

** Mediator Class Diagram**

![mediator-design-pattern](http://www.programcreek.com/wp-content/uploads/2013/02/mediator-design-pattern.png)

**Mediator Java Code**
    
    
    package designpatterns.mediator;
     
    interface IMediator {
    	public void fight();
    	public void talk();
    	public void registerA(ColleagueA a);
    	public void registerB(ColleagueB a);
    }
     
    //concrete mediator
    class ConcreteMediator implements IMediator{
     
    	ColleagueA talk;
    	ColleagueB fight;
     
    	public void registerA(ColleagueA a){
    		talk = a;
    	}
     
    	public void registerB(ColleagueB b){
    		fight = b;
    	}
     
    	public void fight(){
    		System.out.println("Mediator is fighting");
    		//let the fight colleague do some stuff
    	}
     
    	public void talk(){
    		System.out.println("Mediator is talking");
    		//let the talk colleague do some stuff
    	}
    }
     
    abstract class Colleague {
    	IMediator mediator;
    	public abstract void doSomething();
    }
     
    //concrete colleague
    class ColleagueA extends Colleague {
     
    	public ColleagueA(IMediator mediator) {
    		this.mediator = mediator;
    	}
     
    	@Override
    	public void doSomething() {
    		this.mediator.talk();
    		this.mediator.registerA(this);
    	}
    }
     
    //concrete colleague
    class ColleagueB extends Colleague {
    	public ColleagueB(IMediator mediator) {
    		this.mediator = mediator;
    		this.mediator.registerB(this);
    	}
     
    	@Override
    	public void doSomething() {
    		this.mediator.fight();
    	}
    }
     
    public class MediatorTest {
    	public static void main(String[] args) {
    		IMediator mediator = new ConcreteMediator();
     
    		ColleagueA talkColleague = new ColleagueA(mediator);
    		ColleagueB fightColleague = new ColleagueB(mediator);
     
    		talkColleague.doSomething();
    		fightColleague.doSomething();
    	}
    }

Among other behavioral pattern, Observer is the most similar pattern with Mediator. You can read Observer pattern to compare the difference.

Category >> [Design Patterns Stories](http://www.programcreek.com/category/design-patterns/)

If you want to post syntax highlighted code and let me or someone else review it, please put the code inside <pre><code> and </code></pre> tags.   
For example:
    
    
    <pre><code> 
    String foo = "bar";
    </code></pre>
    
