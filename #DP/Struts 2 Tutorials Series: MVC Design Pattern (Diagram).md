# Struts 2 Tutorials Series: MVC Design Pattern (Diagram)

_Captured: 2015-11-21 at 13:09 from [www.programcreek.com](http://www.programcreek.com/2011/08/struts-2-tutorials-mvc-design-pattern/)_

_Struts 2_ follows the_ Model-View-Controller(MVC)_ design patterns. The diagram below demonstrates how _Struts 2_ framework implements MVC components.

  * Action - model
  * Result - view
  * FilterDispatcher - controller

**The role each module plays**

_Controller_'s job is to map incoming HTTP requests to actions. Those mapping are defined by using XML-based configuration(struts.xml) or Java annotations.

_Model_ in Struts 2 is actions. Each action is defined and implemented by following the framework defined contract(e.g. consist an execute() method). Model component consists the data storage and business logic. Each action is an encapsulation of requests and is placed ValueStack.

_View_ is the presentation component of MVC pattern. In spire of common JSP files, other techniques such as tilts, velocity, freemaker, etc. can be combined to provide a flexible presentation layer.

**Interactions among each MVC module**

![Struts2 MVC Architecture](http://www.programcreek.com/wp-content/uploads/2011/08/Struts2MVC-600x367.jpg)

MVC pattern is the most obvious pattern in Struts 2. You can read the[ design pattern stories](http://www.programcreek.com/java-design-patterns-in-stories/) page and know other patterns.
