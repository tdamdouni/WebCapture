### [current community](//stackoverflow.com)

  * [chat](http://chat.stackoverflow.com)

[

Stack Overflow ](//stackoverflow.com)

  * [

Meta Stack Overflow ](http://meta.stackoverflow.com)

  * [

Stack Overflow Careers ](//careers.stackoverflow.com?utm_source=stackoverflow.com&utm_medium=site-ui&utm_campaign=multicollider)

###  your communities 

[Sign up](https://stackoverflow.com/users/signup?ssrc=site_switcher&returnurl=http%3a%2f%2fstackoverflow.com%2fquestions%2f1673841%2fexamples-of-gof-design-patterns-in-javas-core-libraries) or [log in](https://stackoverflow.com/users/login?ssrc=site_switcher&returnurl=http%3a%2f%2fstackoverflow.com%2fquestions%2f1673841%2fexamples-of-gof-design-patterns-in-javas-core-libraries) to customize your list. 

### [more stack exchange communities](//stackexchange.com/sites)

[company blog](http://blog.stackoverflow.com)

[ Stack Exchange ](//stackexchange.com) Inbox Reputation and Badges

[sign up](https://stackoverflow.com/users/signup?ssrc=head&returnurl=http%3a%2f%2fstackoverflow.com%2fquestions%2f1673841%2fexamples-of-gof-design-patterns-in-javas-core-libraries) [log in](https://stackoverflow.com/users/login?ssrc=head&returnurl=http%3a%2f%2fstackoverflow.com%2fquestions%2f1673841%2fexamples-of-gof-design-patterns-in-javas-core-libraries) [tour](/tour) help 

  * [ Tour  Start here for a quick overview of the site  ](/tour)
  * [ Help Center  Detailed answers to any questions you might have  ](/help)
  * [ Meta  Discuss the workings and policies of this site  ](//meta.stackoverflow.com)

[stack overflow careers](//careers.stackoverflow.com?utm_source=stackoverflow.com&utm_medium=site-ui&utm_campaign=anon-topbar)

  

[ Stack Overflow ](/)

  * [Questions](/questions)
  * [Tags](/tags)
  * [Users](/users)
  * [Badges](/help/badges)
  * [Unanswered](/unanswered)
  * [Ask Question](/questions/ask)

[Sign up](/users/signup?ssrc=hero&returnurl=http%3a%2f%2fstackoverflow.com%2fquestions%2f1673841%2fexamples-of-gof-design-patterns-in-javas-core-libraries) ×

Stack Overflow is a community of 4.7 million programmers, just like you, helping each other. Join them; it only takes a minute: 

# [Examples of GoF Design Patterns in Java's core libraries](/questions/1673841/examples-of-gof-design-patterns-in-javas-core-libraries)

up vote 673 down vote favorite

**2357**

I am learning GoF Java Design Patterns and I want to see some real life examples of them. What are some good examples of these Design Patterns in Java's core libraries?

[java](/questions/tagged/java) [oop](/questions/tagged/oop) [design-patterns](/questions/tagged/design-patterns) [java-api](/questions/tagged/java-api)

[share](/q/1673841)

[edited Apr 11 at 3:40](/posts/1673841/revisions)

  

community wiki 

  

[ 16 revs, 7 users 56%  
[unj2](/users/82368) ](/posts/1673841/revisions)

##  **locked** by [Shog9](/users/811/shog9)♦ Apr 11 at 3:39

This question's answers are a collaborative effort: if you see something that can be improved, just edit the answer to improve it! _No additional answers can be added here_

comments disabled on deleted / locked posts / reviews | 

##  7 Answers 7

[active](/questions/1673841/examples-of-gof-design-patterns-in-javas-core-libraries?answertab=active#tab-top) [oldest](/questions/1673841/examples-of-gof-design-patterns-in-javas-core-libraries?answertab=oldest#tab-top) [votes](/questions/1673841/examples-of-gof-design-patterns-in-javas-core-libraries?answertab=votes#tab-top)

up vote 1805 down vote accepted

+250

You can find an overview of a lot of design patterns in [Wikipedia](http://en.wikipedia.org/wiki/Design_pattern_%28computer_science%29#Classification_and_list). It also mentions which patterns are mentioned by GoF. I'll sum them up here and try to assign as much as possible pattern implementations found in both the Java SE and Java EE API's.

* * *

## [Creational patterns](http://en.wikipedia.org/wiki/Creational_pattern)

### [Abstract factory](http://en.wikipedia.org/wiki/Abstract_factory_pattern) (recognizeable by creational methods returning the factory itself which in turn can be used to create another abstract/interface type)

  * `[javax.xml.parsers.DocumentBuilderFactory#newInstance()`](http://docs.oracle.com/javase/6/docs/api/javax/xml/parsers/DocumentBuilderFactory.html#newInstance%28%29)
  * `[javax.xml.transform.TransformerFactory#newInstance()`](http://docs.oracle.com/javase/6/docs/api/javax/xml/transform/TransformerFactory.html#newInstance%28%29)
  * `[javax.xml.xpath.XPathFactory#newInstance()`](http://docs.oracle.com/javase/6/docs/api/javax/xml/xpath/XPathFactory.html#newInstance%28%29)

### [Builder](http://en.wikipedia.org/wiki/Builder_pattern) (recognizeable by creational methods returning the instance itself)

  * `[java.lang.StringBuilder#append()`](http://docs.oracle.com/javase/6/docs/api/java/lang/StringBuilder.html#append%28boolean%29) (unsynchronized)
  * `[java.lang.StringBuffer#append()`](http://docs.oracle.com/javase/6/docs/api/java/lang/StringBuffer.html#append%28boolean%29) (synchronized)
  * `[java.nio.ByteBuffer#put()`](http://docs.oracle.com/javase/6/docs/api/java/nio/ByteBuffer.html#put%28byte%29) (also on `[CharBuffer`](http://docs.oracle.com/javase/6/docs/api/java/nio/CharBuffer.html#put%28char%29), `[ShortBuffer`](http://docs.oracle.com/javase/6/docs/api/java/nio/ShortBuffer.html#put%28short%29), `[IntBuffer`](http://docs.oracle.com/javase/6/docs/api/java/nio/IntBuffer.html#put%28int%29), `[LongBuffer`](http://docs.oracle.com/javase/6/docs/api/java/nio/LongBuffer.html#put%28long%29), `[FloatBuffer`](http://docs.oracle.com/javase/6/docs/api/java/nio/FloatBuffer.html#put%28float%29) and `[DoubleBuffer`](http://docs.oracle.com/javase/6/docs/api/java/nio/DoubleBuffer.html#put%28double%29))
  * `[javax.swing.GroupLayout.Group#addComponent()`](http://docs.oracle.com/javase/6/docs/api/javax/swing/GroupLayout.Group.html#addComponent%28java.awt.Component%29)
  * All implementations of `[java.lang.Appendable`](http://docs.oracle.com/javase/6/docs/api/java/lang/Appendable.html)

### [Factory method](http://en.wikipedia.org/wiki/Factory_method_pattern) (recognizeable by creational methods returning an implementation of an abstract/interface type)

  * `[java.util.Calendar#getInstance()`](http://docs.oracle.com/javase/6/docs/api/java/util/Calendar.html#getInstance%28%29)
  * `[java.util.ResourceBundle#getBundle()`](http://docs.oracle.com/javase/6/docs/api/java/util/ResourceBundle.html#getBundle%28java.lang.String%29)
  * `[java.text.NumberFormat#getInstance()`](http://docs.oracle.com/javase/6/docs/api/java/text/NumberFormat.html#getInstance%28%29)
  * `[java.nio.charset.Charset#forName()`](http://docs.oracle.com/javase/6/docs/api/java/nio/charset/Charset.html#forName%28java.lang.String%29)
  * `[java.net.URLStreamHandlerFactory#createURLStreamHandler(String)`](http://docs.oracle.com/javase/6/docs/api/java/net/URLStreamHandlerFactory.html) (Returns singleton object per protocol)

### [Prototype](http://en.wikipedia.org/wiki/Prototype_pattern) (recognizeable by creational methods returning a _different_ instance of itself with the same properties)

  * `[java.lang.Object#clone()`](http://docs.oracle.com/javase/6/docs/api/java/lang/Object.html#clone%28%29) (the class has to implement `[java.lang.Cloneable`](http://docs.oracle.com/javase/6/docs/api/java/lang/Cloneable.html))

### [Singleton](http://en.wikipedia.org/wiki/Singleton_pattern) (recognizeable by creational methods returning the _same_ instance (usually of itself) everytime)

  * `[java.lang.Runtime#getRuntime()`](http://docs.oracle.com/javase/6/docs/api/java/lang/Runtime.html#getRuntime%28%29)
  * `[java.awt.Desktop#getDesktop()`](http://docs.oracle.com/javase/6/docs/api/java/awt/Desktop.html#getDesktop%28%29)
  * `[java.lang.System#getSecurityManager()`](http://docs.oracle.com/javase/6/docs/api/java/lang/System.html#getSecurityManager%28%29)
* * *

## [Structural patterns](http://en.wikipedia.org/wiki/Structural_pattern)

### [Adapter](http://en.wikipedia.org/wiki/Adapter_pattern) (recognizeable by creational methods taking an instance of _different_ abstract/interface type and returning an implementation of own/another abstract/interface type which _decorates/overrides_ the given instance)

  * `[java.util.Arrays#asList()`](http://docs.oracle.com/javase/6/docs/api/java/util/Arrays.html#asList%28T...%29)
  * `[java.io.InputStreamReader(InputStream)`](http://docs.oracle.com/javase/6/docs/api/java/io/InputStreamReader.html#InputStreamReader%28java.io.InputStream%29) (returns a `Reader`)
  * `[java.io.OutputStreamWriter(OutputStream)`](http://docs.oracle.com/javase/6/docs/api/java/io/OutputStreamWriter.html#OutputStreamWriter%28java.io.OutputStream%29) (returns a `Writer`)
  * `[javax.xml.bind.annotation.adapters.XmlAdapter#marshal()`](http://docs.oracle.com/javase/6/docs/api/javax/xml/bind/annotation/adapters/XmlAdapter.html#marshal%28BoundType%29) and `[#unmarshal()`](http://docs.oracle.com/javase/6/docs/api/javax/xml/bind/annotation/adapters/XmlAdapter.html#unmarshal%28ValueType%29)

### [Bridge](http://en.wikipedia.org/wiki/Bridge_pattern) (recognizeable by creational methods taking an instance of _different_ abstract/interface type and returning an implementation of own abstract/interface type which _delegates/uses_ the given instance)

  * None comes to mind yet. A fictive example would be `new LinkedHashMap(LinkedHashSet<K>, List<V>)` which returns an unmodifiable linked map which doesn't clone the items, but _uses_ them. The `[java.util.Collections#newSetFromMap()`](http://docs.oracle.com/javase/6/docs/api/java/util/Collections.html#newSetFromMap%28java.util.Map%29) and `[singletonXXX()`](http://docs.oracle.com/javase/6/docs/api/java/util/Collections.html#singleton%28T%29) methods however comes close.

### [Composite](http://en.wikipedia.org/wiki/Composite_pattern) (recognizeable by behavioral methods taking an instance of _same_ abstract/interface type into a tree structure)

  * `[java.awt.Container#add(Component)`](http://docs.oracle.com/javase/6/docs/api/java/awt/Container.html#add%28java.awt.Component%29) (practically all over Swing thus)
  * `[javax.faces.component.UIComponent#getChildren()`](http://docs.oracle.com/javaee/6/api/javax/faces/component/UIComponent.html#getChildren%28%29) (practically all over JSF UI thus)

### [Decorator](http://en.wikipedia.org/wiki/Decorator_pattern) (recognizeable by creational methods taking an instance of _same_ abstract/interface type which adds additional behaviour)

  * All subclasses of `[java.io.InputStream`](http://docs.oracle.com/javase/6/docs/api/java/io/InputStream.html), `[OutputStream`](http://docs.oracle.com/javase/6/docs/api/java/io/OutputStream.html), `[Reader`](http://docs.oracle.com/javase/6/docs/api/java/io/Reader.html) and `[Writer`](http://docs.oracle.com/javase/6/docs/api/java/io/Writer.html) have a constructor taking an instance of same type.
  * `[java.util.Collections`](http://docs.oracle.com/javase/6/docs/api/java/util/Collections.html), the `[checkedXXX()`](http://docs.oracle.com/javase/6/docs/api/java/util/Collections.html#checkedCollection%28java.util.Collection,%20java.lang.Class%29), `[synchronizedXXX()`](http://docs.oracle.com/javase/6/docs/api/java/util/Collections.html#synchronizedCollection%28java.util.Collection%29) and `[unmodifiableXXX()`](http://docs.oracle.com/javase/6/docs/api/java/util/Collections.html#unmodifiableCollection%28java.util.Collection%29) methods.
  * `[javax.servlet.http.HttpServletRequestWrapper`](http://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpServletRequestWrapper.html) and `[HttpServletResponseWrapper`](http://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpServletResponseWrapper.html)

### [Facade](http://en.wikipedia.org/wiki/Facade_pattern) (recognizeable by behavioral methods which internally uses instances of _different_ independent abstract/interface types)

  * `[javax.faces.context.FacesContext`](http://docs.oracle.com/javaee/6/api/javax/faces/context/FacesContext.html), it internally uses among others the abstract/interface types `[LifeCycle`](http://docs.oracle.com/javaee/6/api/javax/faces/lifecycle/Lifecycle.html), `[ViewHandler`](http://docs.oracle.com/javaee/6/api/javax/faces/application/ViewHandler.html), `[NavigationHandler`](http://docs.oracle.com/javaee/6/api/javax/faces/application/NavigationHandler.html) and many more without that the enduser has to worry about it (which are however overrideable by injection).
  * `[javax.faces.context.ExternalContext`](http://docs.oracle.com/javaee/6/api/javax/faces/context/ExternalContext.html), which internally uses `[ServletContext`](http://docs.oracle.com/javaee/6/api/javax/servlet/ServletContext.html), `[HttpSession`](http://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpSession.html), `[HttpServletRequest`](http://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpServletRequest.html), `[HttpServletResponse`](http://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpServletResponse.html), etc.

### [Flyweight](http://en.wikipedia.org/wiki/Flyweight_pattern) (recognizeable by creational methods returning a cached instance, a bit the "multiton" idea)

  * `[java.lang.Integer#valueOf(int)`](http://docs.oracle.com/javase/6/docs/api/java/lang/Integer.html#valueOf%28int%29) (also on `[Boolean`](http://docs.oracle.com/javase/6/docs/api/java/lang/Boolean.html#valueOf%28boolean%29), `[Byte`](http://docs.oracle.com/javase/6/docs/api/java/lang/Byte.html#valueOf%28byte%29), `[Character`](http://docs.oracle.com/javase/6/docs/api/java/lang/Character.html#valueOf%28char%29), `[Short`](http://docs.oracle.com/javase/6/docs/api/java/lang/Short.html#valueOf%28short%29), `[Long`](http://docs.oracle.com/javase/6/docs/api/java/lang/Long.html#valueOf%28long%29) and `[BigDecimal`](https://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html#valueOf-long-int-))

### [Proxy](http://en.wikipedia.org/wiki/Proxy_pattern) (recognizeable by creational methods which returns an implementation of given abstract/interface type which in turn _delegates/uses_ a _different_ implementation of given abstract/interface type)

  * `[java.lang.reflect.Proxy`](http://docs.oracle.com/javase/6/docs/api/java/lang/reflect/Proxy.html)
  * `[java.rmi.*`](http://docs.oracle.com/javase/6/docs/api/java/rmi/package-summary.html), the whole API actually.

The Wikipedia example is IMHO a bit poor, lazy loading has actually completely nothing to do with the proxy pattern at all.

* * *

## [Behavioral patterns](http://en.wikipedia.org/wiki/Behavioral_pattern)

### [Chain of responsibility](http://en.wikipedia.org/wiki/Chain_of_responsibility_pattern) (recognizeable by behavioral methods which (indirectly) invokes the same method in _another_ implementation of _same_ abstract/interface type in a queue)

  * `[java.util.logging.Logger#log()`](http://docs.oracle.com/javase/6/docs/api/java/util/logging/Logger.html#log%28java.util.logging.Level,%20java.lang.String%29)
  * `[javax.servlet.Filter#doFilter()`](http://docs.oracle.com/javaee/6/api/javax/servlet/Filter.html#doFilter%28javax.servlet.ServletRequest,%20javax.servlet.ServletResponse,%20javax.servlet.FilterChain%29)

### [Command](http://en.wikipedia.org/wiki/Command_pattern) (recognizeable by behavioral methods in an abstract/interface type which invokes a method in an implementation of a _different_ abstract/interface type which has been _encapsulated_ by the command implementation during its creation)

  * All implementations of `[java.lang.Runnable`](http://docs.oracle.com/javase/6/docs/api/java/lang/Runnable.html)
  * All implementations of `[javax.swing.Action`](http://docs.oracle.com/javase/6/docs/api/javax/swing/Action.html)

### [Interpreter](http://en.wikipedia.org/wiki/Interpreter_pattern) (recognizeable by behavioral methods returning a _structurally_ different instance/type of the given instance/type; note that parsing/formatting is not part of the pattern, determining the pattern and how to apply it is)

  * `[java.util.Pattern`](http://docs.oracle.com/javase/6/docs/api/java/util/regex/Pattern.html)
  * `[java.text.Normalizer`](http://docs.oracle.com/javase/6/docs/api/java/text/Normalizer.html)
  * All subclasses of `[java.text.Format`](http://docs.oracle.com/javase/6/docs/api/java/text/Format.html)
  * All subclasses of `[javax.el.ELResolver`](http://docs.oracle.com/javaee/6/api/javax/el/ELResolver.html)

### [Iterator](http://en.wikipedia.org/wiki/Iterator_pattern) (recognizeable by behavioral methods sequentially returning instances of a _different_ type from a queue)

  * All implementations of `[java.util.Iterator`](http://docs.oracle.com/javase/6/docs/api/java/util/Iterator.html) (thus among others also `[java.util.Scanner`](http://docs.oracle.com/javase/6/docs/api/java/util/Scanner.html)!).
  * All implementations of `[java.util.Enumeration`](http://docs.oracle.com/javase/6/docs/api/java/util/Enumeration.html)

### [Mediator](http://en.wikipedia.org/wiki/Mediator_pattern) (recognizeable by behavioral methods taking an instance of different abstract/interface type (usually using the command pattern) which delegates/uses the given instance)

  * `[java.util.Timer`](http://docs.oracle.com/javase/6/docs/api/java/util/Timer.html) (all `scheduleXXX()` methods)
  * `[java.util.concurrent.Executor#execute()`](http://docs.oracle.com/javase/6/docs/api/java/util/concurrent/Executor.html#execute%28java.lang.Runnable%29)
  * `[java.util.concurrent.ExecutorService`](http://docs.oracle.com/javase/6/docs/api/java/util/concurrent/ExecutorService.html) (the `invokeXXX()` and `submit()` methods)
  * `[java.util.concurrent.ScheduledExecutorService`](http://docs.oracle.com/javase/6/docs/api/java/util/concurrent/ScheduledExecutorService.html) (all `scheduleXXX()` methods)
  * `[java.lang.reflect.Method#invoke()`](http://docs.oracle.com/javase/6/docs/api/java/lang/reflect/Method.html#invoke%28java.lang.Object,%20java.lang.Object...%29)

### [Memento](http://en.wikipedia.org/wiki/Memento_pattern) (recognizeable by behavioral methods which internally changes the state of the _whole_ instance)

  * `[java.util.Date`](http://docs.oracle.com/javase/6/docs/api/java/util/Date.html) (the setter methods do that, `Date` is internally represented by a `long` value)
  * All implementations of `[java.io.Serializable`](http://docs.oracle.com/javase/6/docs/api/java/io/Serializable.html)
  * All implementations of `[javax.faces.component.StateHolder`](http://docs.oracle.com/javaee/6/api/javax/faces/component/StateHolder.html)

### [Observer (or Publish/Subscribe)](http://en.wikipedia.org/wiki/Observer_pattern) (recognizeable by behavioral methods which invokes a method on an instance of _another_ abstract/interface type, depending on own state)

  * `[java.util.Observer`](http://docs.oracle.com/javase/6/docs/api/java/util/Observer.html)/`[java.util.Observable`](http://docs.oracle.com/javase/6/docs/api/java/util/Observable.html) (rarely used in real world though)
  * All implementations of `[java.util.EventListener`](http://docs.oracle.com/javase/6/docs/api/java/util/EventListener.html) (practically all over Swing thus)
  * `[javax.servlet.http.HttpSessionBindingListener`](http://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpSessionBindingListener.html)
  * `[javax.servlet.http.HttpSessionAttributeListener`](http://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpSessionAttributeListener.html)
  * `[javax.faces.event.PhaseListener`](http://docs.oracle.com/javaee/6/api/javax/faces/event/PhaseListener.html)

### [State](http://en.wikipedia.org/wiki/State_pattern) (recognizeable by behavioral methods which changes its behaviour depending on the instance's state which can be controlled externally)

  * `[javax.faces.lifecycle.LifeCycle#execute()`](http://docs.oracle.com/javaee/6/api/javax/faces/lifecycle/Lifecycle.html#execute%28javax.faces.context.FacesContext%29) (controlled by `[FacesServlet`](http://docs.oracle.com/javaee/6/api/javax/faces/webapp/FacesServlet.html), the behaviour is dependent on current phase (state) of JSF lifecycle)

### [Strategy](http://en.wikipedia.org/wiki/Strategy_pattern) (recognizeable by behavioral methods in an abstract/interface type which invokes a method in an implementation of a _different_ abstract/interface type which has been _passed-in_ as method argument into the strategy implementation)

  * `[java.util.Comparator#compare()`](http://docs.oracle.com/javase/6/docs/api/java/util/Comparator.html#compare%28T,%20T%29), executed by among others `Collections#sort()`.
  * `[javax.servlet.http.HttpServlet`](http://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpServlet.html), the `service()` and all `doXXX()` methods take `HttpServletRequest` and `HttpServletResponse` and the implementor has to process them (and not to get hold of them as instance variables!).
  * `[javax.servlet.Filter#doFilter()`](http://docs.oracle.com/javaee/6/api/javax/servlet/Filter.html#doFilter%28javax.servlet.ServletRequest,%20javax.servlet.ServletResponse,%20javax.servlet.FilterChain%29)

### [Template method](http://en.wikipedia.org/wiki/Template_method_pattern) (recognizeable by behavioral methods which already have a "default" behaviour definied by an abstract type)

  * All non-abstract methods of `[java.io.InputStream`](http://docs.oracle.com/javase/6/docs/api/java/io/InputStream.html), `[java.io.OutputStream`](http://docs.oracle.com/javase/6/docs/api/java/io/OutputStream.html), `[java.io.Reader`](http://docs.oracle.com/javase/6/docs/api/java/io/Reader.html) and `[java.io.Writer`](http://docs.oracle.com/javase/6/docs/api/java/io/Writer.html).
  * All non-abstract methods of `[java.util.AbstractList`](http://docs.oracle.com/javase/6/docs/api/java/util/AbstractList.html), `[java.util.AbstractSet`](http://docs.oracle.com/javase/6/docs/api/java/util/AbstractSet.html) and `[java.util.AbstractMap`](http://docs.oracle.com/javase/6/docs/api/java/util/AbstractMap.html).
  * `[javax.servlet.http.HttpServlet`](http://docs.oracle.com/javaee/6/api/javax/servlet/http/HttpServlet.html), all the `doXXX()` methods by default sends a HTTP 405 "Method Not Allowed" error to the response. You're free to implement none or any of them.

### [Visitor](http://en.wikipedia.org/wiki/Visitor_pattern) (recognizeable by two _different_ abstract/interface types which has methods definied which takes each the _other_ abstract/interface type; the one actually calls the method of the other and the other executes the desired strategy on it)

  * `[javax.lang.model.element.AnnotationValue`](http://docs.oracle.com/javase/6/docs/api/javax/lang/model/element/AnnotationValue.html) and `[AnnotationValueVisitor`](http://docs.oracle.com/javase/6/docs/api/javax/lang/model/element/AnnotationValueVisitor.html)
  * `[javax.lang.model.element.Element`](http://docs.oracle.com/javase/6/docs/api/javax/lang/model/element/Element.html) and `[ElementVisitor`](http://docs.oracle.com/javase/6/docs/api/javax/lang/model/element/ElementVisitor.html)
  * `[javax.lang.model.type.TypeMirror`](http://docs.oracle.com/javase/6/docs/api/javax/lang/model/type/TypeMirror.html) and `[TypeVisitor`](http://docs.oracle.com/javase/6/docs/api/javax/lang/model/type/TypeVisitor.html)
  * `[java.nio.file.FileVisitor`](http://docs.oracle.com/javase/7/docs/api/java/nio/file/FileVisitor.html) and `[SimpleFileVisitor`](http://docs.oracle.com/javase/7/docs/api/java/nio/file/SimpleFileVisitor.html)

[share](/a/2707195)

[edited Sep 25 at 15:47](/posts/2707195/revisions)

  

community wiki 

  

[ 30 revs, 8 users 79%  
[BalusC](/users/157882) ](/posts/2707195/revisions)

3

 

impressive.. :) +1. `javax.lang.model.element` defines visitors ;) I'm not quite sure whether `doXXX` and `doFilter` are "strategies". - [Bozho](/users/203907/bozho) Apr 26 '10 at 13:14

2

 

This related blog post just appeared [briandupreez.net/2010/11/design-patterns-in-jdk.html](http://www.briandupreez.net/2010/11/design-patterns-in-jdk.html) - [Bozho](/users/203907/bozho) Nov 23 '10 at 19:09

4

 

The mentioned builders e.g. StrinbgBuilder are all not an example for the Builder-Pattern. It is a very common mistake however to consider them as builders (so you are not really to blame ^_^) - [Angel O'Sphere](/users/358562/angel-osphere) May 25 '11 at 13:41

7

 

@BalusC: Object.toString() can hardly be considered to be a factory method; the class relationship is right but the intention is wrong. It's hard to draw the line of course, but any method creating and returning another object can't be called a factory method. Maybe you can say that purpose of toString isn't to create a string but the return info about the receiver, therefore it is not a factory method. - [Lii](/users/452775/lii) Oct 20 '12 at 15:40

11

 

@BalusC, I have a question to ask you. Did you read the **WHOLE** source code of Java and JSF? - [Tapas Bose](/users/576758/tapas-bose) Jan 9 '13 at 21:39

 |  show **11** more comments

up vote 58 down vote

  1. Observer pattern throughout whole swing (`Observable`, `Observer`)
  2. MVC also in swing
  3. Adapter pattern: InputStreamReader and OutputStreamWriter NOTE: `ContainerAdapter`, `ComponentAdapter`, `FocusAdapter`, `KeyAdapter`, `MouseAdapter` are _not_ adapters; they are actually Null Objects. Poor naming choice by Sun.
  4. Decorator pattern (`BufferedInputStream` can decorate other streams such as `FilterInputStream`)
  5. AbstractFactory Pattern for the AWT Toolkit and the Swing pluggable look-and-feel classes
  6. `java.lang.Runtime#getRuntime()` is Singleton
  7. `ButtonGroup` for Mediator pattern
  8. `Action`, `AbstractAction` may be used for different visual represntations to execute same code -> Command pattern
  9. Interned Strings or CellRender in JTable for Flyweight Pattern (Also think about various pools - Thread pools, connection pools, EJB object pools - Flyweight is really about management of shared resources)
  10. The Java 1.0 event model is an example of Chain of Responsibility, as are Servlet Filters.
  11. Iterator pattern in Collections Framework
  12. Nested containers in AWT/Swing use the Composite pattern
  13. Layout Managers in AWT/Swing are an example of Strategy

and many more I guess

[share](/a/1673862)

[edited Oct 5 '12 at 3:00](/posts/1673862/revisions)

  

community wiki 

  

[ 7 revs, 3 users 69%  
[jitter](/users/122428) ](/posts/1673862/revisions)

28

 

java.lang.Math (6th one) is not singleton, you don't have an instance to start with, everything is static. That's not singleton - [Ion Todirel](/users/90843/ion-todirel) Apr 25 '10 at 5:11

  
 

Thanks for the tip on MouseAdapter. I found this exaplanation: [stackoverflow.com/questions/9244185/…](http://stackoverflow.com/questions/9244185/why-is-mouseadapter-an-adapter) - [Lincoln](/users/1178043/lincoln) May 20 at 14:24

add a comment | 

up vote 31 down vote

  1. **Flyweight** is used with some values of Byte, Short, Integer, Long and String.
  2. **Facade** is used in many place but the most obvious is Scripting interfaces.
  3. **Singleton** \- java.lang.Runtime comes to mind.
  4. **Abstract Factory** \- Also Scripting and JDBC API.
  5. **Command** \- TextComponent's Undo/Redo.
  6. **Interpreter** \- RegEx (java.util.regex._) and SQL (java.sql._) API.
  7. **Prototype** \- Not 100% sure if this count, but I thinkg `clone()` method can be used for this purpose.

[share](/a/1673964)

[edited Nov 4 '09 at 14:16](/posts/1673964/revisions)

  

community wiki 

  

[ 2 revs  
[NawaMan](/users/176180) ](/posts/1673964/revisions)

7

 

You're correct about Prototype - [Scott Stanchfield](/users/12541/scott-stanchfield) Nov 4 '09 at 18:49

  
 

Concerning **Flyweight** pattern: it could be different Layout Managers from `java.awt` and `java.swing` packages. Indeed, they share almost identical intrinsic attributes and extrinsic attributes are different UI components that they lay out in UI form. - [Vitaly](/users/5195810/vitaly) Oct 23 at 16:48

add a comment | 

up vote 21 down vote

RMI is based on Proxy.

Should be possible to cite one for most of the 23 patterns in GoF:

  1. Abstract Factory: java.sql interfaces all get their concrete implementations from JDBC JAR when driver is registered.
  2. Builder: java.lang.StringBuilder.
  3. Factory Method: XML factories, among others.
  4. Prototype: Maybe clone(), but I'm not sure I'm buying that.
  5. Singleton: java.lang.System
  6. Adapter: Adapter classes in java.awt.event, e.g., WindowAdapter.
  7. Bridge: Collection classes in java.util. List implemented by ArrayList.
  8. Composite: java.awt. java.awt.Component + java.awt.Container
  9. Decorator: All over the java.io package.
  10. Facade: [ExternalContext](http://docs.oracle.com/javaee/6/api/javax/faces/context/ExternalContext.html) behaves as a facade for performing cookie, session scope and similar operations.
  11. Flyweight: Integer, Character, etc.
  12. Proxy: java.rmi package
  13. Chain of Responsibility: Servlet filters
  14. Command: Swing menu items
  15. Interpreter: No directly in JDK, but JavaCC certainly uses this.
  16. Iterator: java.util.Iterator interface; can't be clearer than that.
  17. Mediator: JMS?
  18. Memento: 
  19. Observer: java.util.Observer/Observable (badly done, though)
  20. State: 
  21. Strategy: 
  22. Template: 
  23. Visitor: 

I can't think of examples in Java for 10 out of the 23, but I'll see if I can do better tomorrow. That's what edit is for.

[share](/a/1677958)

[edited Sep 29 '12 at 10:24](/posts/1677958/revisions)

  

community wiki 

  

[ 4 revs, 3 users 85%  
[duffymo](/users/37213) ](/posts/1677958/revisions)

add a comment | 

up vote 20 down vote

The Abstract Factory pattern is used in various places. E.g., DatagramSocketImplFactory, PreferencesFactory. There are many more---search the Javadoc for interfaces which have the word "Factory" in their name.

Also there are quite a few instances of the Factory pattern, too.

[share](/a/1673906)

answered [Nov 4 '09 at 13:59](/posts/1673906/revisions)

  

community wiki 

  

[ uckelman ](/posts/1673906/revisions)

add a comment | 

up vote 13 down vote

Even though I'm sort of a broken clock with this one, Java XML API uses Factory a lot. I mean just look at this:

    
    
    Document doc = DocumentBuilderFactory.newInstance().newDocumentBuilder().parse(source);
    String title = XPathFactory.newInstance().newXPath().evaluate("//title", doc);
    

...and so on and so forth.

Additionally various Buffers (StringBuffer, ByteBuffer, StringBuilder) use Builder.

[share](/a/1673950)

answered [Nov 4 '09 at 14:07](/posts/1673950/revisions)

  

community wiki 

  

[ Esko ](/posts/1673950/revisions)

add a comment | 

up vote 12 down vote

  * [Factory method](http://www.oodesign.com/factory-method-pattern.html)

java.util.Collection#Iterator is a good example of a Factory Method. Depending on the concrete subclass of Collection you use, it will create an Iterator implementation. Because both the Factory superclass (Collection) and the Iterator created are interfaces, it is sometimes confused with AbstractFactory. Most of the examples for AbstractFactory in the the accepted answer (BalusC) are examples of [Factory](http://www.oodesign.com/factory-pattern.html), a simplified version of Factory Method, which is not part of the original GoF patterns. In Facory the Factory class hierarchy is collapsed and the factory uses other means to choose the product to be returned.

  * Abstract Factory

An abstract factory has multiple factory methods, each creating a different product. The products produced by one factory are intended to be used together (your printer and cartridges better be from the same (abstract) factory). As mentioned in answers above the families of AWT GUI components, differing from platform to platform, are an example of this (although its implementation differs from the structure described in Gof).

[share](/a/6080919)

[edited May 22 '11 at 8:44](/posts/6080919/revisions)

  

community wiki 

  

[ 3 revs  
[Catweazle](/users/451797) ](/posts/6080919/revisions)

add a comment | 

##  Not the answer you're looking for? Browse other questions tagged [java](/questions/tagged/java) [oop](/questions/tagged/oop) [design-patterns](/questions/tagged/design-patterns) [java-api](/questions/tagged/java-api) or [ask your own question](/questions/ask). 

asked

**6 years ago**

viewed

**307385 times**

active

**[1 month ago](?lastactivity)**

Upcoming Events 

* * *

[2015 Community Moderator Election](http://stackoverflow.com/election)

ends in 3 days

  

#### Linked

[

15

](/q/3649754) [Examples of Design Patterns used in JDK](/questions/3649754/examples-of-design-patterns-used-in-jdk)

[

2

](/q/14831606) [what is Gang of Four design pattern](/questions/14831606/what-is-gang-of-four-design-pattern)

[

1

](/q/7172155) [Is the factory design pattern used in a Java API?](/questions/7172155/is-the-factory-design-pattern-used-in-a-java-api)

[

0

](/q/7500954) [Java Design Patterns Examples](/questions/7500954/java-design-patterns-examples)

[

1

](/q/3494581) [Design patterns illustrated by Java SE/EE APIs?](/questions/3494581/design-patterns-illustrated-by-java-se-ee-apis)

[

1

](/q/16754265) [KeyAdapter inner class… What exactly is Java doing here?](/questions/16754265/keyadapter-inner-class-what-exactly-is-java-doing-here)

[

0

](/q/22377782) [Pattern examples in Java Development Kit](/questions/22377782/pattern-examples-in-java-development-kit)

[

435

](/q/70689) [What is an efficient way to implement a singleton pattern in Java?](/questions/70689/what-is-an-efficient-way-to-implement-a-singleton-pattern-in-java)

[

253

](/q/3541077) [Design Patterns web based applications](/questions/3541077/design-patterns-web-based-applications)

[

88

](/q/2707401) [Please help me understand the "Decorator Pattern" with a real world example.](/questions/2707401/please-help-me-understand-the-decorator-pattern-with-a-real-world-example)

[see more linked questions…](/questions/linked/1673841)

#### Related

[

81 

](/q/244706)[Learning/Implementing Design Patterns (For Newbies)](/questions/244706/learning-implementing-design-patterns-for-newbies)

[

652 

](/q/327955)[Does Functional Programming Replace GoF Design Patterns?](/questions/327955/does-functional-programming-replace-gof-design-patterns)

[

10 

](/q/2829106)[disadvantages of builder design pattern](/questions/2829106/disadvantages-of-builder-design-pattern)

[

2 

](/q/3384726)[C# GOF Pattern Examples](/questions/3384726/c-sharp-gof-pattern-examples)

[

253 

](/q/3541077)[Design Patterns web based applications](/questions/3541077/design-patterns-web-based-applications)

[

-3 

](/q/6366847)[Examples of Design Patterns used in FOSS](/questions/6366847/examples-of-design-patterns-used-in-foss)

[

2 

](/q/7420766)[Connection between GoF Design Patterns and SOLID](/questions/7420766/connection-between-gof-design-patterns-and-solid)

[

2 

](/q/9484708)[Examples of GoF design patterns in .net](/questions/9484708/examples-of-gof-design-patterns-in-net)

[

34 

](/q/17012159)[Which GoF Design pattern will be changed or influenced by the introduction of lambdas in Java8?](/questions/17012159/which-gof-design-pattern-will-be-changed-or-influenced-by-the-introduction-of-la)

[

-1 

](/q/22097049)[GoF design pattern detection](/questions/22097049/gof-design-pattern-detection)

####  [ Hot Network Questions ](//stackexchange.com/questions?tab=hot)

  * [ What can a human offer an intelligent badger-like animal for trade? ](http://worldbuilding.stackexchange.com/questions/30050/what-can-a-human-offer-an-intelligent-badger-like-animal-for-trade)
  * [ How to add tactics and maneuvering into space warfare ](http://worldbuilding.stackexchange.com/questions/30074/how-to-add-tactics-and-maneuvering-into-space-warfare)
  * [ Is it unprofessional to leave a job early as a trainee? ](http://workplace.stackexchange.com/questions/58067/is-it-unprofessional-to-leave-a-job-early-as-a-trainee)
  * [ How to compress game frame by frame animation to a minimum on disk ](http://gamedev.stackexchange.com/questions/111633/how-to-compress-game-frame-by-frame-animation-to-a-minimum-on-disk)
  * [ Who is the sleepiest of them all? ](http://codegolf.stackexchange.com/questions/64369/who-is-the-sleepiest-of-them-all)
  * [ Ignorance and the arising of dukkha ](http://buddhism.stackexchange.com/questions/12692/ignorance-and-the-arising-of-dukkha)
  * [ List of symbols marked [[EXPERIMENTAL]] in the documentation ](http://mathematica.stackexchange.com/questions/100058/list-of-symbols-marked-experimental-in-the-documentation)
  * [ What is Kant's effect on modern culture, beyond philosophy? ](http://philosophy.stackexchange.com/questions/29795/what-is-kants-effect-on-modern-culture-beyond-philosophy)
  * [ What is the prefix "\c@" mean in build log? ](http://tex.stackexchange.com/questions/279290/what-is-the-prefix-c-mean-in-build-log)
  * [ Will ISIS attacks hurt my PhD application as a Muslim? ](http://academia.stackexchange.com/questions/58293/will-isis-attacks-hurt-my-phd-application-as-a-muslim)
  * [ Why do we not use the definite article in "Where can I find the room 401?" ](http://ell.stackexchange.com/questions/73709/why-do-we-not-use-the-definite-article-in-where-can-i-find-the-room-401)
  * [ What happens if a language other than English is used over the radio? ](http://aviation.stackexchange.com/questions/22983/what-happens-if-a-language-other-than-english-is-used-over-the-radio)
  * [ Statistics concept to explain why you're less likely to flip the same number of heads as tails, as the number of flips increases? ](http://stats.stackexchange.com/questions/182488/statistics-concept-to-explain-why-youre-less-likely-to-flip-the-same-number-of)
  * [ Add semicolon at the end of code line programmatically ](http://mathematica.stackexchange.com/questions/100057/add-semicolon-at-the-end-of-code-line-programmatically)
  * [ How did file identify this particular file? ](http://unix.stackexchange.com/questions/244502/how-did-file-identify-this-particular-file)
  * [ How can an uneducated but rational person differentiate between science and religion? ](http://philosophy.stackexchange.com/questions/29755/how-can-an-uneducated-but-rational-person-differentiate-between-science-and-reli)
  * [ When using an axiom scheme, are we implicitly using a choice principle? ](http://math.stackexchange.com/questions/1538911/when-using-an-axiom-scheme-are-we-implicitly-using-a-choice-principle)
  * [ Will it damage my rain gear to store it in a compression sack? ](http://outdoors.stackexchange.com/questions/9902/will-it-damage-my-rain-gear-to-store-it-in-a-compression-sack)
  * [ How to handle distortion at the poles of a UV sphere? ](http://blender.stackexchange.com/questions/41885/how-to-handle-distortion-at-the-poles-of-a-uv-sphere)
  * [ How do i kill process running on port 80 ](http://unix.stackexchange.com/questions/244531/how-do-i-kill-process-running-on-port-80)
  * [ What does the term "tanker" mean when used in regards to a passenger airliner? ](http://aviation.stackexchange.com/questions/23039/what-does-the-term-tanker-mean-when-used-in-regards-to-a-passenger-airliner)
  * [ A single word for 'regularly visited place' ](http://english.stackexchange.com/questions/288018/a-single-word-for-regularly-visited-place)
  * [ Separate a list into even-indexed and odd-indexed parts ](http://codegolf.stackexchange.com/questions/64315/separate-a-list-into-even-indexed-and-odd-indexed-parts)
  * [ Are there ever any animals featured that aren't Pokemon? ](http://anime.stackexchange.com/questions/27455/are-there-ever-any-animals-featured-that-arent-pok%c3%a9mon)

more hot questions 

![](/posts/1673841/ivc/c907)

lang-java

[tour](/tour) [help](/help) [blog](http://blog.stackoverflow.com?blb=1) [chat](http://chat.stackoverflow.com) [data](http://data.stackexchange.com) [legal](http://stackexchange.com/legal) [privacy policy](http://stackexchange.com/legal/privacy-policy) [work here](http://stackexchange.com/work-here) [advertising info](http://stackexchange.com/mediakit) mobile **[contact us](/contact)** **[feedback](http://meta.stackoverflow.com)**

Technology  Life / Arts  Culture / Recreation  Science  Other 

  1. [Stack Overflow](//stackoverflow.com)
  2. [Server Fault](//serverfault.com)
  3. [Super User](//superuser.com)
  4. [Web Applications](//webapps.stackexchange.com)
  5. [Ask Ubuntu](//askubuntu.com)
  6. [Webmasters](//webmasters.stackexchange.com)
  7. [Game Development](//gamedev.stackexchange.com)
  8. [TeX - LaTeX](//tex.stackexchange.com)
  1. [Programmers](//programmers.stackexchange.com)
  2. [Unix & Linux](//unix.stackexchange.com)
  3. [Ask Different (Apple)](//apple.stackexchange.com)
  4. [WordPress Development](//wordpress.stackexchange.com)
  5. [Geographic Information Systems](//gis.stackexchange.com)
  6. [Electrical Engineering](//electronics.stackexchange.com)
  7. [Android Enthusiasts](//android.stackexchange.com)
  8. [Information Security](//security.stackexchange.com)
  1. [Database Administrators](//dba.stackexchange.com)
  2. [Drupal Answers](//drupal.stackexchange.com)
  3. [SharePoint](//sharepoint.stackexchange.com)
  4. [User Experience](//ux.stackexchange.com)
  5. [Mathematica](//mathematica.stackexchange.com)
  6. [Salesforce](//salesforce.stackexchange.com)
  7. [ExpressionEngine® Answers](//expressionengine.stackexchange.com)
  8. [ more (13) ](http://stackexchange.com/sites#technology)
  1. [Photography](//photo.stackexchange.com)
  2. [Science Fiction & Fantasy](//scifi.stackexchange.com)
  3. [Graphic Design](//graphicdesign.stackexchange.com)
  4. [Movies & TV](//movies.stackexchange.com)
  5. [Seasoned Advice (cooking)](//cooking.stackexchange.com)
  6. [Home Improvement](//diy.stackexchange.com)
  7. [Personal Finance & Money](//money.stackexchange.com)
  8. [Academia](//academia.stackexchange.com)
  9. [ more (9) ](http://stackexchange.com/sites#lifearts)
  1. [English Language & Usage](//english.stackexchange.com)
  2. [Skeptics](//skeptics.stackexchange.com)
  3. [Mi Yodeya (Judaism)](//judaism.stackexchange.com)
  4. [Travel](//travel.stackexchange.com)
  5. [Christianity](//christianity.stackexchange.com)
  6. [Arqade (gaming)](//gaming.stackexchange.com)
  7. [Bicycles](//bicycles.stackexchange.com)
  8. [Role-playing Games](//rpg.stackexchange.com)
  9. [ more (21) ](http://stackexchange.com/sites#culturerecreation)
  1. [Mathematics](//math.stackexchange.com)
  2. [Cross Validated (stats)](//stats.stackexchange.com)
  3. [Theoretical Computer Science](//cstheory.stackexchange.com)
  4. [Physics](//physics.stackexchange.com)
  5. [MathOverflow](//mathoverflow.net)
  6. [Chemistry](//chemistry.stackexchange.com)
  7. [Biology](//biology.stackexchange.com)
  8. [ more (5) ](http://stackexchange.com/sites#science)
  1. [Stack Apps](//stackapps.com)
  2. [Meta Stack Exchange](//meta.stackexchange.com)
  3. [Area 51](//area51.stackexchange.com)
  4. [Stack Overflow Careers](//careers.stackoverflow.com)

site design / logo (C) 2015 Stack Exchange Inc; user contributions licensed under [cc by-sa 3.0](http://creativecommons.org/licenses/by-sa/3.0/) with [attribution required](http://blog.stackoverflow.com/2009/06/attribution-required/)

rev 2015.11.20.3010 

Stack Overflow works best with JavaScript enabled![](http://pixel.quantserve.com/pixel/p-c1rF4kxgLUzNc.gif))
