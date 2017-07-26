# Java Design Pattern: Command

_Captured: 2015-11-21 at 13:22 from [www.programcreek.com](http://www.programcreek.com/2013/02/java-design-pattern-command/)_

Command design pattern takes an operation and its arguments and wraps them up in an object to be executed, logged, etc. In the example below, Command is an operation, its argument is a Computer, and they are wrapped in Switch.

In another perspective, Command pattern has 4 parts: command, receiver, invoker and client. In this example, Switch is the invoker, and Computer is the receiver. A concrete Command has a receiver object and invoke the receiver's method. Invoker can use different concrete command. The client determines which command to use for the receiver.

**Command Pattern Class Diagram**

![command-design-pattern](http://www.programcreek.com/wp-content/uploads/2013/02/command-design-pattern.png)

**Java Command Pattern Example**
    
    
    package designpatterns.command;
     
    import java.util.List;
    import java.util.ArrayList;
     
    /* The Command interface */
    interface Command {
       void execute();
    }
     
    // in this example, suppose you use a switch to control computer
     
    /* The Invoker class */
     class Switch { 
       private List<Command> history = new ArrayList<Command>();
     
       public Switch() {
       }
     
       public void storeAndExecute(Command command) {
          this.history.add(command); // optional, can do the execute only!
          command.execute();        
       }
    }
     
    /* The Receiver class */
     class Computer {
     
       public void shutDown() {
          System.out.println("computer is shut down");
       }
     
       public void restart() {
          System.out.println("computer is restarted");
       }
    }
     
    /* The Command for shutting down the computer*/
     class ShutDownCommand implements Command {
       private Computer computer;
     
       public ShutDownCommand(Computer computer) {
          this.computer = computer;
       }
     
       public void execute(){
          computer.shutDown();
       }
    }
     
    /* The Command for restarting the computer */
     class RestartCommand implements Command {
       private Computer computer;
     
       public RestartCommand(Computer computer) {
          this.computer = computer;
       }
     
       public void execute() {
          computer.restart();
       }
    }
     
    /* The client */
    public class TestCommand {
       public static void main(String[] args){
          Computer computer = new Computer();
          Command shutdown = new ShutDownCommand(computer);
          Command restart = new RestartCommand(computer);
     
          Switch s = new Switch();
     
          String str = "shutdown"; //get value based on real situation
     
          if(str == "shutdown"){
        	  s.storeAndExecute(shutdown);
          }else{
        	  s.storeAndExecute(restart);
          }
       }
    }

Category >> [Design Patterns Stories](http://www.programcreek.com/category/design-patterns/)

If you want to post syntax highlighted code and let me or someone else review it, please put the code inside <pre><code> and </code></pre> tags.   
For example:
    
    
    <pre><code> 
    String foo = "bar";
    </code></pre>
    
