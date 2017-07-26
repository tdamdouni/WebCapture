# Design Patterns Used in Eclipse Platform

_Captured: 2015-11-21 at 13:29 from [www.programcreek.com](http://www.programcreek.com/2011/09/common-design-patterns-in-frameworks/)_

Here I summarize the design patterns used in Eclipse platform. Understanding design patterns used in Eclipse is the key for understanding Eclipse platform.

![programcreek- eclilpse platform](http://www.programcreek.com/wp-content/uploads/2011/09/programcreek-eclilpse-platform-300x181.png)

> _[programcreek- eclilpse platform](http://www.programcreek.com/wp-content/uploads/2011/09/programcreek-eclilpse-platform.png)_

Eclipse architecture has a clear layered structure. Each layer is independent to each other but interactive with each other. To better understand a framework, it is a good idea to start from a general view of the design patterns idea behind.

This is only a summary, design patterns used in each layer are illustrated.

  * Platform Runtime: Adapter([Part 1](http://www.programcreek.com/2012/01/decipher-eclipse-architecture-iadaptable-part-1-brief-introduction/),[Part 2](http://www.programcreek.com/2011/09/adapters-in-eclipse/),[Part 3](http://www.programcreek.com/2011/09/eclipse-iadaptable-example-show-properties-for-items-from-a-sample-view/)), Singleton
  * Workspace: [Proxy and Bridge](http://www.programcreek.com/2013/02/eclipse-design-patterns-proxy-and-bridge-in-workspace/), [Composite](http://www.programcreek.com/2013/02/eclipse-design-patterns-composite-in-workspace/), Observer, Visitor
  * SWT: Composite, [Strategy](http://www.programcreek.com/2013/02/eclipse-design-patterns-strategy-in-swt/), Observer
  * JFace: Strategy, Command
  * Workbench: Memento, Visual Proxy
  


**Adapter Design Pattern**

How Adapter design pattern is used in Eclipse platform? Eclipse Platform Runtime has a good example of this pattern.

First of all, Adapter design pattern has a simple idea behind - wrapping the object and making it to be compatible to another interface clients expect. You can take a look at the simplest adapter idea in my previous [post](http://www.programcreek.com/2011/09/java-design-pattern-adapter/).

How adapters are used in eclipse are slightly different and more complex. In the following example, classes and interfaces are put in one file for simplicity purpose.

The class hierarchy is shown in the diagram below.

![Eclipse IAdaptable](http://www.programcreek.com/wp-content/uploads/2011/09/EclipseAdapters1.jpg)

> _Eclipse Adapters_

When we want to go from oranges to apples, adapter comes into place. The following code shows what it does, no complex work flow from Eclipse.

PlatformAdapterManager class is totally made up, real story in eclipse is platform get adapter manager to return a proper adapter.
    
    
    public class Main {	
    	public static void main(String args[]){
    		IApple apple = new Apple();
    		IOrange orange = (IOrange)apple.getAdapter(IOrange.class);
     
    		if(orange == null){
    			System.out.println("null");
    		}else{
    			System.out.println(orange);
    		}
     
    		IPear pear = (IPear)apple.getAdapter(IPear.class);	
    		if(pear == null){
    			System.out.println("null");
    		}else{
    			System.out.println(pear);
    		}
    	}
    }

Output:  
Orange@4fe5e2c3  
Pear@23fc4bec

This is the approach of implementing the getAdapter() method in the class itself. This approach does not require registration with class, since implementation is in the getAdapter() method.

In another way that is used in Eclipse, no code changes in class are required, getAdapter method is contributed by a factory. Check out [this post](http://www.programcreek.com/2011/09/eclipse-iadaptable-example-show-properties-for-items-from-a-sample-view/) to see the real story.

References:

[corner article](http://www.eclipse.org/resources/resource.php?id=407).
