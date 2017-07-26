# Java Design Pattern: Flyweight

_Captured: 2015-11-21 at 13:06 from [www.programcreek.com](http://www.programcreek.com/2013/02/java-design-pattern-flyweight/)_

Flyweight pattern is used for minimizing memory usage. What it does is sharing as much data as possible with other similar objects.

**1\. Flyweight Pattern Class Diagram**

![flyweight-pattern-class-diagram](http://www.programcreek.com/wp-content/uploads/2013/02/flyweight-pattern-class-diagram.jpg)

> _2. Flyweight Pattern Java Code_
    
    
    // Flyweight object interface
    interface ICoffee {
        public void serveCoffee(CoffeeContext context);
    }
    
    
    // Concrete Flyweight object  
    class Coffee implements ICoffee {
        private final String flavor;
     
        public Coffee(String newFlavor) {
            this.flavor = newFlavor;
            System.out.println("Coffee is created! - " + flavor);
        }
     
        public String getFlavor() {
            return this.flavor;
        }
     
        public void serveCoffee(CoffeeContext context) {
            System.out.println("Serving " + flavor + " to table " + context.getTable());
        }
    }
    
    
    // A context, here is table number
    class CoffeeContext {
       private final int tableNumber;
     
       public CoffeeContext(int tableNumber) {
           this.tableNumber = tableNumber;
       }
     
       public int getTable() {
           return this.tableNumber;
       }
    }

CoffeeFactory: it only create a new coffee when necessary.
    
    
    //The FlyweightFactory!
    class CoffeeFactory {
     
        private HashMap<String, Coffee> flavors = new HashMap<String, Coffee>();
     
        public Coffee getCoffeeFlavor(String flavorName) {
            Coffee flavor = flavors.get(flavorName);
            if (flavor == null) {
                flavor = new Coffee(flavorName);
                flavors.put(flavorName, flavor);
            }
            return flavor;
        }
     
        public int getTotalCoffeeFlavorsMade() {
            return flavors.size();
        }
    }

//Waitress serving coffee
    
    
    public class Waitress {
       //coffee array
       private static Coffee[] coffees = new Coffee[20];
       //table array
       private static CoffeeContext[] tables = new CoffeeContext[20];
       private static int ordersCount = 0;
       private static CoffeeFactory coffeeFactory;
     
       public static void takeOrder(String flavorIn, int table) {
    	   coffees[ordersCount] = coffeeFactory.getCoffeeFlavor(flavorIn);
           tables[ordersCount] = new CoffeeContext(table);
           ordersCount++;
       }
     
       public static void main(String[] args) {
    	   coffeeFactory = new CoffeeFactory();
     
           takeOrder("Cappuccino", 2);
           takeOrder("Cappuccino", 2);
           takeOrder("Regular Coffee", 1);
           takeOrder("Regular Coffee", 2);
           takeOrder("Regular Coffee", 3);
           takeOrder("Regular Coffee", 4);
           takeOrder("Cappuccino", 4);
           takeOrder("Cappuccino", 5);
           takeOrder("Regular Coffee", 3);
           takeOrder("Cappuccino", 3);
     
           for (int i = 0; i < ordersCount; ++i) {
        	   coffees[i].serveCoffee(tables[i]);
           }
     
           System.out.println("\nTotal Coffee objects made: " +  coffeeFactory.getTotalCoffeeFlavorsMade());
       }
    }

Check out the output below, coffee is served to 10 tables, but only 2 coffees are created ever!
    
    
    Coffee is created! - Cappuccino
    Coffee is created! - Regular Coffee
    Serving Cappuccino to table 2
    Serving Cappuccino to table 2
    Serving Regular Coffee to table 1
    Serving Regular Coffee to table 2
    Serving Regular Coffee to table 3
    Serving Regular Coffee to table 4
    Serving Cappuccino to table 4
    Serving Cappuccino to table 5
    Serving Regular Coffee to table 3
    Serving Cappuccino to table 3
    
    Total Coffee objects made: 2
    

This example is changed based on wiki-flyweight*, it is improved to be more understandable.  
* http://en.wikipedia.org/wiki/Flyweight_pattern

Category >> [Design Patterns Stories](http://www.programcreek.com/category/design-patterns/)

If you want to post syntax highlighted code and let me or someone else review it, please put the code inside <pre><code> and </code></pre> tags.   
For example:
    
    
    <pre><code> 
    String foo = "bar";
    </code></pre>
    
