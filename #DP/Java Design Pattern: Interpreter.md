# Java Design Pattern: Interpreter

_Captured: 2015-11-21 at 13:23 from [www.programcreek.com](http://www.programcreek.com/2013/02/java-design-pattern-interprete/)_

Major revision in progress ... Please come back later.

Interpreter pattern is used when some context needs to be interpreted. The following example is a very simple Interpreter implementation. It interpretes letter "a" and "b" to "1" and "2".

**Class Diagram**

![interpreter pattern class diagram](http://www.programcreek.com/wp-content/uploads/2013/02/interpreter-pattern-class-diagram.jpg)

> _[interpreter pattern class diagram](http://www.programcreek.com/wp-content/uploads/2013/02/interpreter-pattern-class-diagram.jpg)_

Note that: the dependency is also shown in diagram to make the structure more understandable.

**Java Code**
    
    
     
    class Context { 
     
        private String input; 
        private String output; 
     
        public Context(String input) { 
            this.input = input; 
            this.output = "";
        } 
     
        public String getInput() { 
            return input; 
        } 
        public void setInput(String input) { 
            this.input = input; 
        } 
        public String getOutput() { 
            return output; 
        } 
        public void setOutput(String output) { 
            this.output = output; 
        } 
    }
     
    abstract class Expression {    
        public abstract void interpret(Context context); 
    }
     
    class AExpression extends Expression { 
        public void interpret(Context context) { 
            System.out.println("a expression"); 
            String input = context.getInput(); 
     
            context.setInput(input.substring(1)); 
            context.setOutput(context.getOutput()+ "1"); 
        } 
     
    }
     
    class BExpression extends Expression { 
        public void interpret(Context context) { 
            System.out.println("b expression"); 
            String input = context.getInput(); 
     
            context.setInput(input.substring(1)); 
            context.setOutput(context.getOutput()+ "2"); 
        } 
    }
     
    public class TestInterpreter {
    	 public static void main(String[] args) { 
    	        String str = "ab"; 
    	        Context context = new Context(str); 
     
    	        List<Expression> list = new ArrayList<Expression>(); 
    	        list.add(new AExpression()); 
    	        list.add(new BExpression()); 
     
    	        for(Expression ex : list) { 
    	            ex.interpret(context); 
     
    	        } 
     
    	        System.out.println(context.getOutput()); 
    	    } 
    }

**Interpreter pattern used in JDK**

java.util.Pattern

Category >> [Design Patterns Stories](http://www.programcreek.com/category/design-patterns/)

If you want to post syntax highlighted code and let me or someone else review it, please put the code inside <pre><code> and </code></pre> tags.   
For example:
    
    
    <pre><code> 
    String foo = "bar";
    </code></pre>
    
