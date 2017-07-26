# Java Design Pattern: Memento

_Captured: 2015-11-21 at 13:25 from [www.programcreek.com](http://www.programcreek.com/2013/02/java-design-pattern-memento/)_

In future, time travel will be invented. Memento is the key to time travel. Basically, what it does is to allow an object to go back to a state.

In the following example, You can time travel to any era for your Life, and You can restore to a previous era you have been to.

**Memento Design Pattern Class Diagram**

![memento design pattern](http://www.programcreek.com/wp-content/uploads/2013/02/memento.png)

> _Memento Design Pattern Java Code_
    
    
    package designpatterns.memento;
    import java.util.List;
    import java.util.ArrayList;
    class Life {
        private String time;
     
        public void set(String time) {
            System.out.println("Setting time to " + time);
            this.time = time;
        }
     
        public Memento saveToMemento() {
            System.out.println("Saving time to Memento");
            return new Memento(time);
        }
     
        public void restoreFromMemento(Memento memento) {
        	time = memento.getSavedTime();
            System.out.println("Time restored from Memento: " + time);
        }
     
        public static class Memento {
            private final String time;
     
            public Memento(String timeToSave) {
            	time = timeToSave;
            }
     
            public String getSavedTime() {
                return time;
            }
        }
    }
     
    public class You {
        public static void main(String[] args) {
            List<Life.Memento> savedTimes = new ArrayList<Life.Memento>();
     
            Life life = new Life();
     
            //time travel and record the eras
            life.set("2000 B.C.");
            savedTimes.add(life.saveToMemento());
            life.set("2000 A.D.");
            savedTimes.add(life.saveToMemento());
            life.set("3000 A.D.");
            savedTimes.add(life.saveToMemento());
            life.set("4000 A.D.");
     
            life.restoreFromMemento(savedTimes.get(0));   
     
        }
    }

Category >> [Design Patterns Stories](http://www.programcreek.com/category/design-patterns/)

If you want to post syntax highlighted code and let me or someone else review it, please put the code inside <pre><code> and </code></pre> tags.   
For example:
    
    
    <pre><code> 
    String foo = "bar";
    </code></pre>
    
