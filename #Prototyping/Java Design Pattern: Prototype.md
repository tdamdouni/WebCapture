# Java Design Pattern: Prototype

_Captured: 2015-11-21 at 12:42 from [www.programcreek.com](http://www.programcreek.com/2013/02/java-design-pattern-prototype/)_

Prototype design pattern is used when very similar objects frequently are required. Prototype pattern clones objects and set the changed feature. This way less resources are consumed. Think about why less resources are consumed?

**1\. Prototype Pattern Class Diagram**

![prototype-pattern-class-diagram](http://www.programcreek.com/wp-content/uploads/2013/02/prototype-pattern-class-diagram.png)

**2\. Prototype Pattern Java Example**
    
    
    package designpatterns.prototype;
     
    //prototype
    interface Prototype {
        void setSize(int x);
        void printSize();
     }
     
    // a concrete class
    class A implements Prototype, Cloneable {
        private int size;
     
        public A(int x) {
            this.size = x;
        }
     
        @Override
        public void setSize(int x) {
            this.size = x;
        }
     
        @Override
        public void printSize() {
            System.out.println("Size: " + size);
        }
     
     
        @Override
        public A clone() throws CloneNotSupportedException {
            return (A) super.clone();
        }
    }
     
    //when we need a large number of similar objects
    public class PrototypeTest {
        public static void main(String args[]) throws CloneNotSupportedException {
            A a = new A(1);
     
            for (int i = 2; i < 10; i++) {
                Prototype temp = a.clone();
                temp.setSize(i);
                temp.printSize();
            }
        }
    }

**3\. Prototype Design Pattern Used in Java Standard Library**

java.lang.Object - clone()

Category >> [Design Patterns Stories](http://www.programcreek.com/category/design-patterns/)

If you want to post syntax highlighted code and let me or someone else review it, please put the code inside <pre><code> and </code></pre> tags.   
For example:
    
    
    <pre><code> 
    String foo = "bar";
    </code></pre>
    
