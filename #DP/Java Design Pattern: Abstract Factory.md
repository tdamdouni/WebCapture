# Java Design Pattern: Abstract Factory

_Captured: 2015-11-21 at 12:41 from [www.programcreek.com](http://www.programcreek.com/2013/02/java-design-pattern-abstract-factory/)_

Abstract Factory pattern adds another layer of abstraction for Factory pattern. If we compare Abstract Factory with Factory, it is pretty obvious that a new layer of abstraction is added. Abstract Factory is a super-factory which creates other factories. We can call it "Factory of factories".

**Abstract Factory class diagram**

![abstract-factory-design-pattern](http://www.programcreek.com/wp-content/uploads/2013/02/abstract-factory-design-pattern.png)

**Abstract Factory Java code**
    
    
    interface CPU {
        void process();
    }
     
    interface CPUFactory {
    	CPU produceCPU();
    }
     
    class AMDFactory implements CPUFactory {
        public CPU produceCPU() {
            return new AMDCPU();
        }
    }
     
    class IntelFactory implements CPUFactory {
        public CPU produceCPU() {
            return new IntelCPU();
        }
    }
     
    class AMDCPU implements CPU {
        public void process() {
            System.out.println("AMD is processing...");
        }
    }
     
    class IntelCPU implements CPU {
        public void process() {
            System.out.println("Intel is processing...");
        }
    }
     
    class Computer {
    	CPU cpu;
     
        public Computer(CPUFactory factory) {
        	cpu = factory.produceCPU();
            cpu.process();
        }
    }
     
    public class Client {
        public static void main(String[] args) {
            new Computer(createSpecificFactory());
        }
     
        public static CPUFactory createSpecificFactory() {
            int sys = 0; // based on specific requirement
            if (sys == 0) 
            	return new AMDFactory();
            else 
            	return new IntelFactory();
        }
    }

**Real use example**

Actually, this is a very important concept of modern frameworks. [Here ](http://stackoverflow.com/questions/1993397/abstract-factory-pattern-on-top-of-ioc/1994455#1994455)is a question about this.
