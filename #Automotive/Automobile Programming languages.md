# Automobile Programming languages

_Captured: 2015-06-07 at 23:25 from [stackoverflow.com](http://stackoverflow.com/questions/1044271/automobile-programming-languages)_

Electronics in the automotive industry are usually based on embedded microcontrollers. As such, the programming languages are usually C, C++, and assembly. In some cases, a higher-level language such as ladder-logic is used to describe the actual control logic.

Modern automobiles have several separate computer systems, each designed to control a specific aspect of the vehicle's operation. There is usually one controller for the engine, one for the transmission, one for the dashboard electronics, one for the ABS braking system, traction control, etc.

Each of these control modules has a set of inputs and outputs. The engine controller, for example, reads many sensors including coolant temperature, engine speed, oxygen intake, throttle position, and so on. And, based on these inputs, it makes decisions about fuelling for the engine. In hybrid vehicles and electric-only vehicles, the engine control system is, of course, entirely different. There is still a controller, but instead of just making decisions about fuelling, it can make decisions about when to engage the electric motors vs the gas engine, how much power to apply to each electric motor, etc.

The various control modules are connected together using an in-vehicle network. There are many different ways of implementing this network, but one of the most common is CAN (Controller Area Network). The network allows individual control modules to send and receive information from other modules at high speed while the vehicle is in operation.

**update:** Here are some links for further reading:

[CAN systems](http://www.aa1car.com/library/can_systems.htm) from AA1Car.com  
[The Hybrid Bible](http://www.carbibles.com/hybrids_bible.html) from CarBibles.com  
[Sensors Make Cars Smarter](http://www.designnews.com/article/13464-Sensors_make_cars_smarter.php) \- an article from Design News

**update:** Here is a recent article on the subject which may be of interest:

[This Car Runs On Code](http://news.discovery.com/tech/toyota-recall-software-code.html) \- an article from Discovery.com
