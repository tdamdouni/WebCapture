# Java Design Pattern: Singleton

_Captured: 2015-11-21 at 12:39 from [www.programcreek.com](http://www.programcreek.com/2011/07/java-design-pattern-singleton/)_

Singleton pattern is one of the most commonly used patterns in Java. It is used to control the number of objects created by preventing external instantiation and modification. This concept can be generalized to systems that operate more efficiently when only one object exists, or that restrict the instantiation to a certain number of objects, such as:

  1. private constructor - no other class can instantiate a new object.
  2. private reference - no external modification.
  3. public static method is the only place that can get an object.

**The Story for Singleton**

Here is a simple use case. A country can have only one president. So whenever a president is needed, the only president should be returned instead of creating a new one. The `getPresident()` method will make sure there is always only one president created.

**Class Diagram and Code**

![singleton](http://www.programcreek.com/wp-content/uploads/2011/07/singleton.jpg)

Eager Mode:
    
    
    public class AmericaPresident {
    	private static final AmericaPresident thePresident = new AmericaPresident();
     
    	private AmericaPresident() {}
     
    	public static AmericaPresident getPresident() {
    		return thePresident;
    	}
    }

`thePresident` is declared as `final`, so it will always contain the same object reference.

Lazy Mode:
    
    
    public class AmericaPresident {
    	private static AmericaPresident thePresident;
     
    	private AmericaPresident() {}
     
    	public static AmericaPresident getPresident() {
    		if (thePresident == null) {
    			thePresident = new AmericaPresident();
    		}
    		return thePresident;
    	}
    }

**Singleton Pattern Used in Java Stand Library**

`java.lang.Runtime#getRuntime()` is a frequently used method from Java standard library. `getRunTime()` returns the runtime object associated with the current Java application.
    
    
    class Runtime {
    	private static Runtime currentRuntime = new Runtime();
     
    	public static Runtime getRuntime() {
    		return currentRuntime;
    	}
     
    	private Runtime() {}
     
    	//... 
    }

Here is a simple example of using `getRunTime()`. It reads a webpage on a Windows system.
    
    
    Process p = Runtime.getRuntime().exec(
    		"C:/windows/system32/ping.exe programcreek.com");
    //get process input stream and put it to buffered reader
    BufferedReader input = new BufferedReader(new InputStreamReader(
    		p.getInputStream()));
     
    String line;
    while ((line = input.readLine()) != null) {
    	System.out.println(line);
    }
     
    input.close();

Output:
    
    
    Pinging programcreek.com [198.71.49.96] with 32 bytes of data:
    Reply from 198.71.49.96: bytes=32 time=53ms TTL=47
    Reply from 198.71.49.96: bytes=32 time=53ms TTL=47
    Reply from 198.71.49.96: bytes=32 time=52ms TTL=47
    Reply from 198.71.49.96: bytes=32 time=53ms TTL=47
    
    Ping statistics for 198.71.49.96:
        Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
    Approximate round trip times in milli-seconds:
        Minimum = 52ms, Maximum = 53ms, Average = 52ms
    

**Another Implementation of Singleton Pattern**

As private constructor doesn't protect from instantiation via reflection, Joshua Bloch (Effective Java) proposes a better implementation of Singleton. If you are not familiar with Enum, [here](http://docs.oracle.com/javase/tutorial/java/javaOO/enum.html) is a good example from Oracle.
    
    
    public enum AmericaPresident{
    	INSTANCE;
     
    	public static void doSomething(){
    		//do something
    	}
    }

* Thanks to Dan's comment.
