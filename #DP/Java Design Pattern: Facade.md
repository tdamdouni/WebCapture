# Java Design Pattern: Facade

_Captured: 2015-11-21 at 13:05 from [www.programcreek.com](http://www.programcreek.com/2013/02/java-design-pattern-facade/)_

Facade design pattern hides complexity of a task and provides a simple interface. A very good example is the startup of a computer. When a computer starts up, it involves the work of cpu, memory, hard drive, etc. To make it easy to use for users, we can add a facade which wrap the complexity of the task, and provide one simple interface instead.

**1\. Facade Pattern Class Diagram **

![facade-design-pattern](http://www.programcreek.com/wp-content/uploads/2013/02/facade-design-pattern1.png)

> _2. Java Facade Pattern Example_
    
    
    //the components of a computer
     
    class CPU {
        public void processData() { }
    }
     
    class Memory {
        public void load() { }
    }
     
    class HardDrive {
        public void readdata() { }
    }
     
    /* Facade */
    class Computer {
        private CPU cpu;
        private Memory memory;
        private HardDrive hardDrive;
     
        public Computer() {
            this.cpu = new CPU();
            this.memory = new Memory();
            this.hardDrive = new HardDrive();
        }
     
        public void run() {
            cpu.processData();
            memory.load();
            hardDrive.readdata();
        }
    }
     
     
    class User {
        public static void main(String[] args) {
            Computer computer = new Computer();
            computer.run();
        }
    }

**3\. Example in Real Project **

In javax.faces.context, ExternalContext internally uses ServletContext, HttpSession, HttpServletRequest, HttpServletResponse, etc. It allows the Faces API to be unaware of the nature of its containing application environment.

This example is based on Facade design pattern in Wiki, so the credit is given to Wiki.

Reference:  
1\. [ExternalContext](http://docs.oracle.com/javaee/6/api/javax/faces/context/ExternalContext.html)  
2\. [Wiki Facade](http://en.wikipedia.org/wiki/Facade_pattern)
