# Java Design Pattern: Observer

_Captured: 2015-11-21 at 13:12 from [www.programcreek.com](http://www.programcreek.com/2011/01/an-java-example-of-observer-pattern/)_

In brief, Observer Pattern = publisher + subscriber.

Observer pattern has been used in GUI action listener. [Swing GUI example](http://www.programcreek.com/2009/01/the-steps-involved-in-building-a-swing-gui-application/) shows how action listener works like an observer.

The following is a typical example about head hunter. There are two roles in this diagram - HeadHunter and JobSeeker. Job seekers subscribe to a head hunter, and head hunter notifies job seekers when there is a new job opportunity.

**Class Diagram**

![](http://www.programcreek.com/wp-content/uploads/2011/01/observer-pattern.gif)

> _[observer pattern](http://www.programcreek.com/wp-content/uploads/2011/01/observer-pattern.gif)_

**Java Code**

Subject interface.
    
    
    public interface Subject {
    	public void registerObserver(Observer o);
    	public void removeObserver(Observer o);
    	public void notifyAllObservers();
    }

Observer interface.
    
    
    public interface Observer {
    	public void update(Subject s);
    }

HeadHunter class implements Subject.
    
    
    import java.util.ArrayList;
     
    public class HeadHunter implements Subject{
     
    	//define a list of users, such as Mike, Bill, etc.
    	private ArrayList<Observer> userList;
    	private ArrayList<String> jobs;
     
    	public HeadHunter(){
    		userList = new ArrayList<Observer>();
    		jobs = new ArrayList<String>();
    	}
     
    	@Override
    	public void registerObserver(Observer o) {
    		userList.add(o);
    	}
     
    	@Override
    	public void removeObserver(Observer o) {}
     
    	@Override
    	public void notifyAllObservers() {
    		for(Observer o: userList){
    			o.update(this);
    		}
    	}
     
    	public void addJob(String job) {
    		this.jobs.add(job);
    		notifyAllObservers();
    	}
     
    	public ArrayList<String> getJobs() {
    		return jobs;
    	}
     
    	public String toString(){
    		return jobs.toString();
    	}
    }

JobSeeker is an observer.
    
    
    public class JobSeeker implements Observer {
     
    	private String name;
     
    	public JobSeeker(String name){
    		this.name = name;
    	}
    	@Override
    	public void update(Subject s) {
    		System.out.println(this.name + " got notified!");
    		//print job list
    		System.out.println(s);
    	}
    }

Start Point.
    
    
    public class Main {
     
    	public static void main(String[] args) {
    		HeadHunter hh = new HeadHunter();
    		hh.registerObserver(new JobSeeker("Mike"));
    		hh.registerObserver(new JobSeeker("Chris"));
    		hh.registerObserver(new JobSeeker("Jeff"));
     
    		//Each time, a new job is added, all registered job seekers will get noticed.
    		hh.addJob("Google Job");
    		hh.addJob("Yahoo Job");
    	}
    }

**Observer pattern in JDK**

java.util.EventListener

Category >> [Design Patterns Stories](http://www.programcreek.com/category/design-patterns/)

If you want to post syntax highlighted code and let me or someone else review it, please put the code inside <pre><code> and </code></pre> tags.   
For example:
    
    
    <pre><code> 
    String foo = "bar";
    </code></pre>
    
