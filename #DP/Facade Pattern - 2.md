# Facade Pattern

_Captured: 2016-11-18 at 12:20 from [davidcorne.com](https://davidcorne.com/2013/01/07/facade-pattern/#more-583)_

The facade pattern is used to make one object with a simple interface represent a complicated system. The problem often occurs in programming where you have a series of interconnected classes where the functions must be called in a certain order or have complicated interdependencies.

This pattern is to give a standard interface to such a system, so you don't have to rely on reading how you call the system in one of the files or look at example usage.

##  The Pattern 

Here is a [UML](http://en.wikipedia.org/wiki/Unified_Modeling_Language) diagram representing the pattern.

![](https://i2.wp.com/www.dofactory.com/Patterns/Diagrams/facade.gif)

> _UML for Facade pattern_

UML is a very useful tool however I have not used a lot yet. It provides a (mostly) standardised way of representing system structure for object oriented programming. I intend to use a UML diagram to represent each pattern in this series, I will explain them so hopefully you don't need to know UML to follow what's going on.

This is a nice and simple UML diagram with the following elements; the facade box represents a class, the boxes in the subsystem box could be any object such as a class or a function and the lines between them indicate some relationship.

This shows that the pattern is just one class which groups together a lot of other objects and uses them in some way.

##  An Example Usage

Here is an implementation of this in python. For this example I am using a car. As this is a small example I will not create a whole complex sub-system, just a few classes.

Here are the three classes which make up the sub-system; Engine, StarterMotor and Battery.

678910111213141516171819202122232425262728293031323334
`#==============================================================================``class` `Engine(``object``):``def` `__init__(``self``):``# how much the motor is spinning in revs per minute``self``.spin ``=` `0``def` `start(``self``, spin):``if` `(spin > ``2000``):``self``.spin ``=` `spin ``/``/` `15``#==============================================================================``class` `StarterMotor(``object``):``def` `__init__(``self``):``# how much the starter motor is spinning in revs per minute``self``.spin ``=` `0``def` `start(``self``, charge):``# if there is enough power then spin fast``if` `(charge > ``50``):``self``.spin ``=` `2500``#==============================================================================``class` `Battery(``object``):``def` `__init__(``self``):``# % charged, starts flat``self``.charge ``=` `0`

So now we need our facade object which will work as a common interface for the car.

36373839404142434445464748495051525354555657585960
`#==============================================================================``class` `Car(``object``):``# the facade object that deals with the battery, engine and starter motor.``def` `__init__(``self``):``self``.battery ``=` `Battery()``self``.starter ``=` `StarterMotor()``self``.engine ``=` `Engine()``def` `turn_key(``self``):``# use the battery to turn the starter motor``self``.starter.start(``self``.battery.charge)``# use the starter motor to spin the engine``self``.engine.start(``self``.starter.spin)``# if the engine is spinning the car is started``if` `(``self``.engine.spin > ``0``):``print``(``"Engine Started."``)``else``:``print``(``"Engine Not Started."``)``def` `jump(``self``):``self``.battery.charge ``=` `100``print``(``"Jumped"``)`

This enables the user of Car to use the system as it was intended to be used. I include this at the bottom of the python module so that on running it makes a car, tries to start it, then jumps it to start it.

`#==============================================================================``if` `(__name__ ``=``=` `"__main__"``):``corsa ``=` `Car()``corsa.turn_key()``corsa.jump()``corsa.turn_key()`

The output of this program is the following;

That is a simple example of the facade design pattern. The code for this is on my GitHub [here](https://github.com/davidcorne/Design-Patterns-In-Python/blob/master/Structural/Facade.py).

All of the code for this series can be found in [this repository](https://github.com/davidcorne/Design-Patterns-In-Python).
