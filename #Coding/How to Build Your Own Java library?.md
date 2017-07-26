# How to Build Your Own Java library?

_Captured: 2015-11-22 at 14:16 from [www.programcreek.com](http://www.programcreek.com/2011/07/build-a-java-library-for-yourself/)_

Code reuse is one of the most important factors in software development. It is a VERY good idea to put frequently-used functions together and build a library for yourself. Whenever some method is used, just simply make a method invocation. For Java, it's straightforward to manage such a library. Here a simple example in Eclipse. The library will contain only one "add" method for demo purpose.

Step 1: Create a "Java Project" named as "MyMath", and a simple "add" method under "Simple" class.

Package structure is as follows:

![](http://www.programcreek.com/wp-content/uploads/2011/07/1.png)

Simple.java
    
    
    public class Simple {
    	public static int add(int a, int b){
    		return a+b;
    	}
    }

Step 2: Export as a .jar file.

Right Click the project and select "export", a window is show as follows.

![](http://www.programcreek.com/wp-content/uploads/2011/07/java-export-jar-2-300x269.png)

> _Following the wizard, to get the .jar file._

Step 3: Use the jar file.

Right click the target project, and select "Build Path"->"Add External Archives"->following wizard to add the jar file.

Now you can make a simple method call.
    
    
    public class Main {
    	public static void main(String[] args) {
    		System.out.println(Simple.add(1, 2));
    	}
    }

Last, but not the least, the library should be constantly updated and optimized. Documentation is important. If the library is not documented well, you may totally forget a function you programmed a year ago. Proper package names should be used to indicate the function of classes and methods. For example, you can name first layer of the packages by following the package names of standard Java library: programcreek.util, programcreek.io, programcreek.math, programcreek.text, etc. You domain specific knowledge then can be used in the next level. In addition, always do enough research first and make sure there is no implements of what you want to do before you start program anything. Libraries from industry utilizes the power of thousands of smart developers.
