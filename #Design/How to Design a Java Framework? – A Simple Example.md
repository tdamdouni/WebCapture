# How to Design a Java Framework? – A Simple Example

_Captured: 2015-11-22 at 14:17 from [www.programcreek.com](http://www.programcreek.com/2011/09/how-to-design-a-java-framework/)_

You may be curious about how framework works? A simple framework example will be made here to demonstrate the idea of frameworks.

**Goal of a Framework**

First of all, why do we need a framework other than just a normal library? The goal of framework is defining a process which let developers implement certain functions based on individual requirements. In other words, framework defines the skeleton and developers fill in the flash when using it.

**The Simplest Framework**

In the following example, the first 3 classes are defined as a part of framework and the 4th class is the client code of the framework.

Main.java is the entry point of the framework. This can not be changed.
    
    
    //imagine this is the entry point for a framework, it can not be changed
    public class Main {
    	public static void main(String[] args) {
    		Human h = new Human(new Walk());
    		h.doMove();		
    	}
    }

Move.java is the Hook. A hook is where developers can define / extend functions based on their own requirements.

Human.java is the Template, which reflects the idea of how the framework works.
    
    
    public class Human {
    	private Move move;
     
    	public Human(Move m){
    		this.move = m;
    	}
     
    	public void doMove(){
    		this.move.action();
    	}
    }

This simple framework allows and requires developers to extend "Move" class. Actually, in this simple framework, action() method is the only thing developers are able to change.

Inside of the implementation, different "action" can be programmed to different purpose. E.g. the example below print "5 miles per hour", of course, you can redefine it as "50 miles per hour".
    
    
    public class Walk extends Move {
     
    	@Override
    	public void action() {
    		// TODO Auto-generated method stub
    		System.out.println("5 miles per hour - it is slow!");
    	}
    }

**Conclusion **

The example here just shows how a simple Template and Hook works. A real framework is more complicated than this. Not only does it contain other relations like template-temple relation, but also very complex process about how to efficiently improve performance and programming usability.
