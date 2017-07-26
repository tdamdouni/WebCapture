# Builder Pattern

_Captured: 2015-10-20 at 23:05 from [davidcorne.com](http://davidcorne.com/2013/01/21/builder-pattern/#more-680)_

## The Purpose

The idea behind the builder pattern is to abstract away the construction of an object so that many implementations can use the same builder. This separates the construction logic of the desired class from it's representation.

## The Pattern

Here is a general UML diagram for this

![](https://raw.github.com/davidcorne/Design-Patterns-In-Python/master/Images/UML/Builder_general.png)

So the object you are interested in creating is the class Product in this scenario. The class which you call to deal with this is the Director.

The Director keeps a member which implements the Builder interface and calls this in it's create() method. This member is one of the ConcreteBuilder classes and has the logic needed for the creation of the specific Product you want.

This abstracts the logic needed to create different types of Product. The Product may also be an interface and each ConcreteBuilder may return a different type.

The Builder is typically set either with a function, where the Director class is responsible for the logic of the ConcreteBuilder creation, or by passing a ConcreteBuilder directly to the Director.

## An Example Usage

This will use the example of building different types of vehicles. The code for this example is all contained in [this file](https://github.com/davidcorne/Design-Patterns-In-Python/blob/master/Structural/Builder.py).

The Product here is a Vehicle which is defined as the following class.

67891011121314151617181920212223242526
`#==============================================================================``class` `Vehicle(``object``):``def` `__init__(``self``, type_name):``self``.``type` `=` `type_name``self``.wheels ``=` `None``self``.doors ``=` `None``self``.seats ``=` `None``def` `view(``self``):``print``(``"This vehicle is a "` `+``self``.``type` `+``" with; "` `+``str``(``self``.wheels) ``+``" wheels, "` `+``str``(``self``.doors) ``+``" doors, and "` `+``str``(``self``.seats) ``+``" seats."``)`

So different Vehicles can have different names, numbers of wheels doors and seats. The method view() will print a summery of what the Vehicle is.

The construction of instances of Vehicle will be handles by the ConcreteBuilder classes. These should derive from a Builder interface (abstract class) so here is the base class VehicleBuilder.

282930313233343536373839404142434445
`#==============================================================================``class` `VehicleBuilder(``object``):``"""``An abstract builder class, for concrete builders to be derived from.``"""``__metadata__ ``=` `abc.ABCMeta``@abc``.abstractmethod``def` `make_wheels(``self``):``raise``@abc``.abstractmethod``def` `make_doors(``self``):``raise``@abc``.abstractmethod``def` `make_seats(``self``):``raise`

This uses the [abc](http://docs.python.org/2/library/abc.html) module just like the first version of PrimeFinder in my [strategy pattern](http://davidcorne.com/2013/01/21/strategy-pattern/) post.

So with this Builder there are three functions for setting up the Vehicle. For the ConcreteBuilders there is a CarBuilder and a BikeBuilder, both of which inherit from VehicleBuilder. Here are the implementations of these classes.

4748495051525354555657585960616263646566676869707172737475
`#==============================================================================``class` `CarBuilder(VehicleBuilder):``def` `__init__(``self``):``self``.vehicle ``=` `Vehicle(``"Car "``)``def` `make_wheels(``self``):``self``.vehicle.wheels ``=` `4``def` `make_doors(``self``):``self``.vehicle.doors ``=` `3``def` `make_seats(``self``):``self``.vehicle.seats ``=` `5``#==============================================================================``class` `BikeBuilder(VehicleBuilder):``def` `__init__(``self``):``self``.vehicle ``=` `Vehicle(``"Bike"``)``def` `make_wheels(``self``):``self``.vehicle.wheels ``=` `2``def` `make_doors(``self``):``self``.vehicle.doors ``=` `0``def` `make_seats(``self``):``self``.vehicle.seats ``=` `2`

The only logic in these is the creation of the vehicle object and setting the properties on it. Now to use these we need a Director class to call. For this example the Director is called VehicleManufacturer.

77787980818283848586878889909192939495
`#==============================================================================``class` `VehicleManufacturer(``object``):``"""``The director class, this will keep a concrete builder.``"""``def` `__init__(``self``):``self``.builder ``=` `None``def` `create(``self``):``""" ``Creates and returns a Vehicle using self.builder``Precondition: not self.builder is None``"""``assert` `not` `self``.builder ``is` `None``, ``"No defined builder"``self``.builder.make_wheels()``self``.builder.make_doors()``self``.builder.make_seats()``return` `self``.builder.vehicle`

VehicleManufacturer has a create() function which contains the calling code used with the Builder. However as you can see from the docstring and the code this has a precondition of self.builder being set. This means that if you have not given the Director a ConcreteBuilder to use, it cannot create a Vehicle.

So this class is called like so.

12345678910
`#==============================================================================``if` `(__name__ ``=``=` `"__main__"``):``manufacturer ``=` `VehicleManufacturer()``manufacturer.builder ``=` `CarBuilder()``car ``=` `manufacturer.create()``car.view()``manufacturer.builder ``=` `BikeBuilder()``bike ``=` `manufacturer.create()``bike.view()`

The calling code uses one VehicleManufacturer to build both a car and a bike. The output of this code is given below.

The specific UML for this example is this.

![](https://raw.github.com/davidcorne/Design-Patterns-In-Python/master/Images/UML/Builder_specific.png)

> _Specific Builder Pattern_

All of the code for the design patterns can be found [here](https://github.com/davidcorne/Design-Patterns-In-Python).  
Thanks for reading.
