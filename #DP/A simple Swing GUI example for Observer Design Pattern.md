#  A simple Swing GUI example for Observer Design Pattern

_Captured: 2015-11-21 at 13:14 from [www.programcreek.com](http://www.programcreek.com/2009/01/the-steps-involved-in-building-a-swing-gui-application/)_

This example shows how to create a Swing GUI example, and explain why it is an example usage of Observer Design Pattern. 

**Complete Code**

    
    
    import java.awt.BorderLayout;
    import java.awt.event.ActionEvent;
    import java.awt.event.ActionListener;
    import javax.swing.JButton;
    import javax.swing.JFrame;
    import javax.swing.JTextArea;
     
    public class SimpleSwingExample {
     
    	public static void main(String[] args) {
    		JFrame frame = new JFrame("Frame Title");
    		final JTextArea comp = new JTextArea();
    		JButton btn = new JButton("click");
    		frame.getContentPane().add(comp, BorderLayout.CENTER);
    		frame.getContentPane().add(btn, BorderLayout.SOUTH);
     
    		btn.addActionListener(new ActionListener() {
    			public void actionPerformed(ActionEvent ae) {
    				comp.setText("Button has been clicked");
    			}
    		});
     
    		int width = 300;
    		int height = 300;
    		frame.setSize(width, height);
     
    		frame.setVisible(true);
    	}
    }

**Step-by-step explanation**

Firstly, we need a container like a Frame, a Window, or an Applet to display components like panels, buttons, text areas etc.

    
    
    JFrame frame = new JFrame("Frame Title");

Create some components such as panels, buttons, text areas etc.

    
    
    final JTextArea comp = new JTextArea();
    JButton btn = new JButton("click");

Add components to display area and arrange its layout using the LayoutManagers.

    
    
    frame.getContentPane().add(comp,BorderLayout.CENTER);
    frame.getContentPane().add(btn, BorderLayout.SOUTH);

Attach a listener to the button component. Interacting with a Component causes an Event to occur. To associate a user action with a component, attach a listener to it.

Here addActionListener method is the subject's register observer method. For a complete example of Observer design pattern, go to [Observer ](http://www.programcreek.com/2011/01/an-java-example-of-observer-pattern/)example.

    
    
    btn.addActionListener(new ActionListener(){
           public void actionPerformed(ActionEvent ae){
                 comp.setText("Button has been clicked");
           }
    });

> public interface ActionListener extends EventListener

The listener interface is for receiving action events. The class (Main, in this case) that is interested in processing an action event implements this interface, and the object created with that class is registered with a component, using the component's addActionListener method. When the action event occurs, that object's actionPerformed method is invoked.

Show the Frame.

    
    
    int width = 300;
    int height = 300;
    frame.setSize(width, height);
    frame.setVisible(true);

For# A simple Swing GUI example for Observer Design Pattern

_Captured: 2015-11-21 at 13:14 from [www.programcreek.com](http://www.programcreek.com/2009/01/the-steps-involved-in-building-a-swing-gui-application/)_

This example shows how to create a Swing GUI example, and explain why it is an example usage of Observer Design Pattern.

**Complete Code**
    
    
    import java.awt.BorderLayout;
    import java.awt.event.ActionEvent;
    import java.awt.event.ActionListener;
    import javax.swing.JButton;
    import javax.swing.JFrame;
    import javax.swing.JTextArea;
     
    public class SimpleSwingExample {
     
    	public static void main(String[] args) {
    		JFrame frame = new JFrame("Frame Title");
    		final JTextArea comp = new JTextArea();
    		JButton btn = new JButton("click");
    		frame.getContentPane().add(comp, BorderLayout.CENTER);
    		frame.getContentPane().add(btn, BorderLayout.SOUTH);
     
    		btn.addActionListener(new ActionListener() {
    			public void actionPerformed(ActionEvent ae) {
    				comp.setText("Button has been clicked");
    			}
    		});
     
    		int width = 300;
    		int height = 300;
    		frame.setSize(width, height);
     
    		frame.setVisible(true);
    	}
    }

**Step-by-step explanation**

Firstly, we need a container like a Frame, a Window, or an Applet to display components like panels, buttons, text areas etc.

Create some components such as panels, buttons, text areas etc.

Add components to display area and arrange its layout using the LayoutManagers.

Attach a listener to the button component. Interacting with a Component causes an Event to occur. To associate a user action with a component, attach a listener to it.

Here addActionListener method is the subject's register observer method. For a complete example of Observer design pattern, go to [Observer ](http://www.programcreek.com/2011/01/an-java-example-of-observer-pattern/)example.
    
    
    btn.addActionListener(new ActionListener(){
           public void actionPerformed(ActionEvent ae){
                 comp.setText("Button has been clicked");
           }
    });

> public interface ActionListener extends EventListener

The listener interface is for receiving action events. The class (Main, in this case) that is interested in processing an action event implements this interface, and the object created with that class is registered with a component, using the component's addActionListener method. When the action event occurs, that object's actionPerformed method is invoked.
