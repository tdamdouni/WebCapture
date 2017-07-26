# Java Design Pattern: State

_Captured: 2015-11-21 at 13:17 from [www.programcreek.com](http://www.programcreek.com/2011/07/java-design-pattern-state/)_

State Design Pattern is mainly for changing state at run-time.

**State pattern story**

People can live with different financial status. They can be rich or they can be poor. The two states - rich and poor - can be converted to each other from time to time. The idea behind the example: people normally work harder when they are poor and play more when they are rich. What they do depends on the state in which they are living. The state can be changed based on their actions, otherwise, the society is not fair.

**State pattern class diagram **

Here is the class diagram. You can compare this with [strategy pattern](http://www.programcreek.com/2011/01/a-java-example-of-strategy-design-pattern/) to get better understanding of the difference.

![state-pattern-class-diagram](http://www.programcreek.com/wp-content/uploads/2011/07/state-pattern-class-diagram.jpg)

**State pattern Java code**

The Java example below shows how State pattern works.

State classes.
    
    
    package com.programcreek.designpatterns.state;
     
    interface State {
    	public void saySomething(StateContext sc);
    }
     
    class Rich implements State{
    	@Override
    	public void saySomething(StateContext sc) {
    		System.out.println("I'm rick currently, and play a lot.");
    		sc.changeState(new Poor());
    	}
    }
     
    class Poor implements State{
    	@Override
    	public void saySomething(StateContext sc) {
    		System.out.println("I'm poor currently, and spend much time working.");
    		sc.changeState(new Rich());
    	}
    }

StateContext class
    
    
    package com.programcreek.designpatterns.state;
     
    public class StateContext {
    	private State currentState;
     
    	public StateContext(){
    		currentState = new Poor();
    	}
     
    	public void changeState(State newState){
    		this.currentState = newState;
    	}
     
    	public void saySomething(){
    		this.currentState.saySomething(this);
    	}
    }

Main class for testing
    
    
    import com.programcreek.designpatterns.*;
     
    public class Main {
    	public static void main(String args[]){
    		StateContext sc = new StateContext();
    		sc.saySomething();
    		sc.saySomething();
    		sc.saySomething();
    		sc.saySomething();
    	}
    }

Result:
    
    
    I'm poor currently, and spend much time working. 
    I'm rick currently, and play a lot.
    I'm poor currently, and spend much time working. 
    I'm rick currently, and play a lot.
    
