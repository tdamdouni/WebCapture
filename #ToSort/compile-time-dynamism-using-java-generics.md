# Compile Time Dynamism Using Java Generics

_Captured: 2017-04-19 at 21:37 from [dzone.com](https://dzone.com/articles/compile-time-dynamism-using-java-generics)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

This article describes the use of generics for compile-time dynamism and its usage for client related type-safety. Usually, the most important aspect during sub-classing is how the override is done to achieve class-specific functionality, though with the use of the same method parameters. In certain scenarios, you might need to use class-specific parameters. Coupled with this, the overridden methods might use a parameter that itself is the super class of these class-specific parameters. An example of this is methods that are exposed through some public API and then overridden in concrete implementation classes.

## Context of Use

The description of the usage in this article is that of a very frequently occurring scenario that many of you might have faced and devised a similar solution for. The usage is explained with a simple example from the Vehicle Rental system.

![](http://www.codeguru.com/images/article/14463/generic_ord_sample.jpg)

> _Figure 1: Object Relationship Diagram_

Here, the main rental service class, _RentVehicleManager_, could be either an interface or an abstract class. _RentCarManager_ and _RentBikeManager_ subclass from _RentVehicleManager_ and override its methods with their own functionality. The implementation solutions that might have been feasible in this scenario are:

  1. Using the 'Factory' pattern to create Manager Classes.
  2. Use a common hierarchy for parameters, with strict checking in methods.
  3. Usage of a common hierarchy along with generics.

Option 1 does provide a good solution for the instance generation of related classes but does not provide any method object parameter-related generality.

For a solution using option 2, as shown in Figure 2, every overridden method will now need to include strict checking at the start of the method to see whether the argument it actually received is of the type that was expected for this class.

![](http://www.codeguru.com/images/article/14463/generic_cd_option2.jpg)

> _Figure 2: Class Diagram (Using Option 2)_

The interface, in this case, would look like this:
    
    
    package com.sumithp.codeguru.nongeneric.vehicle;
    
    import com.sumithp.codeguru.vehicle.domain.Vehicle;
    
    public interface RentVehicleMgr {
    
       public void rentOut(Vehicle vehicle);
       public void checkIn(Vehicle vehicle);
       public void diagnose(Vehicle vehicle);
       public void repair(Vehicle vehicle);
    }

A typical implementation for the Bike Rental in the case of Option 2 is shown here:
    
    
    package com.sumithp.codeguru.nongeneric.vehicle;
    
    import com.sumithp.codeguru.vehicle.domain.Vehicle;
    
    public class RentBikeMgrImpl implements RentVehicleMgr {
    
       // If we don't use Vehicle as the parameter here, the clients
       // will not be able to use a generalized interface to call our
       // methods.
    
       public void rentOut(Vehicle vehicle) {
          // if (vehicle instanceof bike)
             // Renting Out Related DB Operations
       }
    
       public void checkIn(Vehicle vehicle) {
          // if (vehicle instanceof bike)
             // Vehicle Check In Related DB Operations
       }
    
       public void diagnose(Vehicle vehicle) {
          // if (vehicle instanceof bike)
             // Self Diagnose functionality of a vehicle
             // Print diagnosis
       }
    
       public void repair(Vehicle vehicle) {
          // if (vehicle instanceof bike)
             // Perform pre-defined repair
             // Print repair details
       }
    }

Option 3 is the most complete and viable alternative because the usage is more coherent by exposing the methods in a single class, each using their implementation along with their own generic variable. Take a closer look at this solution.

## Common Hierarchy Using Java Generics

The use of Generics is greatly enhanced by the 'Type Erasure' property. This implies that there is only compile time checking, beyond which the Generic Variables are erased and no runtime verification exists. This also has certain disadvantages, such as not being completely safe to be used with third-party code (or with internal code that does not use generics).

The simple change that was made to Option 2 was that a new generic variable was added to each of the classes in the hierarchy. At the top level, _RentVehicleManager_ was declared to use any generic variable of the type that _extends_ _Vehicle_. A sample of the same is shown here:
    
    
    package com.sumithp.codeguru.generic.vehicle;
    
    import com.sumithp.codeguru.vehicle.domain.Vehicle;
    
    public interface RentVehicleMgr< T extends Vehicle > {
    
       public void rentOut(T vehicle);
       public void checkIn(T vehicle);
       public void diagnose(T vehicle);
       public void repair(T vehicle);
    }

The classes inheriting from _RentVehicleManager_, in other words, _ RentBikeManager_ and _RentCarManager_ were modified to start using a generic variable of their own type. Implementation for the Car Rental would look like:
    
    
    package com.sumithp.codeguru.generic.vehicle;
    
    import com.sumithp.codeguru.vehicle.domain.Car;
    
    public class RentCarMgrImpl implements RentVehicleMgr< Car > {
    
       // Can use Car as parameter here, as well as allow
       // clients to have a generalized interface
    
       public void rentOut(Car car) {
          // Renting Out Related DB Operations
       }
    
       public void checkIn(Car car) {
          // Vehicle Check In Related DB Operations
       }
    
       public void diagnose(Car car) {
          // Self Diagnose functionality of a vehicle
          // Print diagnosis
       }
    
       public void repair(Car car) {
          // Perform pre-defined repair
          // Print repair details
       }
    }

This would mean that any client invocation of methods on the specific type of Manager now would require its own specific Vehicle Type object to invoke the method. This would enable the Manager implementor to do away with any strict checking in the methods. Also, when making modifications to any of the methods from these subclasses, one does not have to worry about including instanceof checks.

The client code is cleaner and safer. A typical implementation would look like the following:
    
    
    package com.sumithp.codeguru.generic.vehicle.client;
    
    import com.sumithp.codeguru.generic.vehicle.RentBikeMgrImpl;
    import com.sumithp.codeguru.generic.vehicle.RentCarMgrImpl;
    import com.sumithp.codeguru.generic.vehicle.RentVehicleMgr;
    import com.sumithp.codeguru.vehicle.domain.Bike;
    import com.sumithp.codeguru.vehicle.domain.Car;
    
    public class RentGenericVehicleClient {
    
       public void rentBike() {
    
          // You want only one interface to handle all rentals
          RentVehicleMgr< Bike > rentVehicleMgr;
    
          rentVehicleMgr = new RentBikeMgrImpl();
    
          Bike bike = new Bike(104,"TWO",true,150);
          rentVehicleMgr.rentOut(bike);
    
          /*
           * Client cannot do this:
           *
           * Vehicle vehicle = new Car(104,"FOUR",true,"PETROL");
           * rentVehicleMgr.rentOut(vehicle);
           *
           * Even if there are no instanceof checks, all is well!
           * Client is absolutely clear on what he needs to do.
           *
           */
       }
    
       public void rentCar() {
    
          // You want only one interface to handle all rentals
          RentVehicleMgr< Car > rentVehicleMgr;
    
          rentVehicleMgr = new RentCarMgrImpl();
    
          Car car = new Car(104,"FOUR",true,"PETROL");
          rentVehicleMgr.rentOut(car);
    
          /*
           * Client cannot do the following as shown for rentBike():
           *
           * Vehicle vehicle = new Bike(104,"TWO",true,150);
           * rentVehicleMgr.rentOut(vehicle);
           *
           * Even if there are no instanceof checks, all is well!
           * Client is absolutely clear on what he needs to do.
           *
           */
       }
    }

This sort of design will definitely lead to an easier-to-maintain, easier-to-code, and--more importantly--an easier to understand implementation. These advantages are not only for the service or functionality implementors but also for consumers of the service.

## Conclusion

The usage of Generics in this article is useful for dynamic inheritance, although only to achieve compile-time dynamism. As already mentioned, at runtime, the generic variable will be removed from these classes.

[Download Modern Java EE Design Patterns](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035): Building Scalable Architecture for Sustainable Enterprise Development. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035).

### Like This Article? Read More From DZone
