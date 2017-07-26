# Java Design Pattern: Bridge

_Captured: 2015-11-21 at 12:58 from [www.programcreek.com](http://www.programcreek.com/2011/10/java-design-pattern-bridge/)_

In brief, Bridge Design Pattern is a two layer abstraction.

> The bridge pattern is meant to "decouple an abstraction from its implementation so that the two can vary independently". The bridge uses encapsulation, aggregation, and can use inheritance to separate responsibilities into different classes. 

**1\. Bridge pattern story**

The example of TV and Remote Control(typo in diagram) can demonstrate the two layers of abstraction. You have an interface for TV and an abstract class for remote control. As you know, it is not a good idea to make a concrete class for either of them, because other vendors may make different implementations.

![bridge design pattern](http://www.programcreek.com/wp-content/uploads/2011/10/bridge.jpg)

> _2. Bridge pattern Java code_

First define a TV interface: ITV
    
    
    public interface ITV {
    	public void on();
    	public void off();
    	public void switchChannel(int channel);
    }

Let Samsung implement ITV interface.
    
    
     
    public class SamsungTV implements ITV {
    	@Override
    	public void on() {
    		System.out.println("Samsung is turned on.");
    	}
     
    	@Override
    	public void off() {
    		System.out.println("Samsung is turned off.");
    	}
     
    	@Override
    	public void switchChannel(int channel) {
    		System.out.println("Samsung: channel - " + channel);
    	}
    }

Let Sony implement ITV interface.
    
    
    public class SonyTV implements ITV {
     
    	@Override
    	public void on() {
    		System.out.println("Sony is turned on.");
    	}
     
    	@Override
    	public void off() {
    		System.out.println("Sony is turned off.");
    	}
     
    	@Override
    	public void switchChannel(int channel) {
    		System.out.println("Sony: channel - " + channel);
    	}
    }

Remote control holds a reference to the TV.
    
    
    public abstract class AbstractRemoteControl {
    	/**
    	 * @uml.property  name="tv"
    	 * @uml.associationEnd  
    	 */
    	private ITV tv;
     
    	public AbstractRemoteControl(ITV tv){
    		this.tv = tv;
    	}
     
    	public void turnOn(){
    		tv.on();
    	}
     
    	public void turnOff(){
    		tv.off();
    	}
     
    	public void setChannel(int channel){
    		tv.switchChannel(channel);
    	}
    }

Define a concrete remote control class.
    
    
    public class LogitechRemoteControl extends AbstractRemoteControl {
     
    	public LogitechRemoteControl(ITV tv) {
    		super(tv);
    	}
     
    	public void setChannelKeyboard(int channel){
    		setChannel(channel);
    		System.out.println("Logitech use keyword to set channel.");
    	}
    }
    
    
    public class Main {
    	public static void main(String[] args){
    		ITV tv = new SonyTV();
    		LogitechRemoteControl lrc = new LogitechRemoteControl(tv);
    		lrc.setChannelKeyboard(100);	
    	}
    }

Output:

In summary, Bridget pattern allows two layers of abstraction of implementation, in this case, TV and remote control. Therefore, it gives more flexibility.

**3\. Bridge pattern in Eclipse Platform**

[Bridge pattern](http://www.programcreek.com/2013/02/eclipse-design-patterns-proxy-and-bridge-in-workspace/) is an important one used in Eclipse architecture.

Reference:

1\. Gamma, E, Helm, R, Johnson, R, Vlissides, J: Design Patterns, page 151. Addison-Wesley, 1995  
2\. [Wiki Bridge Pattern](http://en.wikipedia.org/wiki/Bridge_pattern)
