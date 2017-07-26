# Java Design Pattern: Iterator

_Captured: 2015-11-21 at 13:24 from [www.programcreek.com](http://www.programcreek.com/2013/02/java-design-pattern-iterator/)_

Iterator pattern is used to iterate through a collection of objects. It is a commonly used pattern, you probably have used it before. Whenever you sees something like hasNext() and next(), it is probably a iterator pattern. For example, you may iterate through a list of database query record.

**Iterator Pattern Class Diagram**

![iterator-design-pattern](http://www.programcreek.com/wp-content/uploads/2013/02/iterator-design-pattern.jpg)

**Iterator Pattern Java Code**
    
    
    interface IIterator{
    	public boolean hasNext();
    	public Object next();
    }
     
    interface IContainer{
    	public IIterator createIterator();
    }
     
    class RecordCollection implements IContainer{
    	private String recordArray[] = {"first","second","third","fourth","fifth"};
     
    	public IIterator createIterator(){
    		RecordIterator iterator = new RecordIterator();
    		return iterator;
    	}
     
    	private class RecordIterator implements IIterator{
    		private int index;
     
    		public boolean hasNext(){
    			if (index < recordArray.length)
    				return true;
    			else
    				return false;
    		}
     
    		public Object next(){
    			if (this.hasNext())
    				return recordArray[index++];
    			else
    				return null;
    		}
    	}
    }
     
    public class TestIterator {
    	public static void main(String[] args) {
    		RecordCollection recordCollection = new RecordCollection();
    		IIterator iter = recordCollection.createIterator();
     
    		while(iter.hasNext()){
    			System.out.println(iter.next());
    		}	
    	}
    }

**Iterator Pattern used in JDK**

In java.util package, the Iterator interface is defined as follows:
    
    
    public interface Iterator<E> {
        boolean hasNext();
        E next();
        void remove();
    }

Then there are class that can create an Iterator, e.g., TreeSet#iterator(), HashSet#iterator(), etc.

Category >> [Design Patterns Stories](http://www.programcreek.com/category/design-patterns/)

If you want to post syntax highlighted code and let me or someone else review it, please put the code inside <pre><code> and </code></pre> tags.   
For example:
    
    
    <pre><code> 
    String foo = "bar";
    </code></pre>
    
