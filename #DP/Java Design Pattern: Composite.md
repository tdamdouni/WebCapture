# Java Design Pattern: Composite

_Captured: 2015-11-21 at 12:59 from [www.programcreek.com](http://www.programcreek.com/2013/02/java-design-pattern-composite/)_

Composite pattern is relatively simple, but it has been used in many designs, such as SWT, eclipse workspace, etc. It basically produce a hierarchical tree which can be accessed by using a uniform method.

**Class Diagram **

![composite-design-pattern](http://www.programcreek.com/wp-content/uploads/2013/02/composite-design-pattern.png)

> _The following code implements the following tree structure._

![Composite-design-pattern-2](http://www.programcreek.com/wp-content/uploads/2013/02/Composite-design-pattern-2.png)

**Java Code **
    
    
    import java.util.List;
    import java.util.ArrayList;
     
    //Component
    interface Component {
        public void show();
    }
     
    //Composite
    class Composite implements Component {
     
        private List<Component> childComponents = new ArrayList<Component>();
     
        public void add(Component component) {
        	childComponents.add(component);
        }
     
        public void remove(Component component) {
        	childComponents.remove(component);
        }
     
    	@Override
    	public void show() {
    		for (Component component : childComponents) {
            	component.show();
            }
    	}
    }
     
    //leaf
    class Leaf implements Component {
    	String name;
    	public Leaf(String s){
    		name = s;
    	}
        public void show() {
            System.out.println(name);
        }
    }
     
     
    public class CompositeTest {
     
        public static void main(String[] args) {
            Leaf leaf1 = new Leaf("1");
            Leaf leaf2 = new Leaf("2");
            Leaf leaf3 = new Leaf("3");
            Leaf leaf4 = new Leaf("4");
            Leaf leaf5 = new Leaf("5");
     
            Composite composite1 = new Composite();
            composite1.add(leaf1);
            composite1.add(leaf2);
     
            Composite composite2 = new Composite();        
            composite2.add(leaf3);
            composite2.add(leaf4);
            composite2.add(leaf5);
     
            composite1.add(composite2);
            composite1.show();
        }
    }

Category >> [Design Patterns Stories](http://www.programcreek.com/category/design-patterns/)

If you want to post syntax highlighted code and let me or someone else review it, please put the code inside <pre><code> and </code></pre> tags.   
For example:
    
    
    <pre><code> 
    String foo = "bar";
    </code></pre>
    
