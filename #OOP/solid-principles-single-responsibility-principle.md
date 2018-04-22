# SOLID Principles: Single Responsibility Principle

_Captured: 2018-04-01 at 19:38 from [dzone.com](https://dzone.com/articles/solid-principles-single-responsibility-principle?edition=371195&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-04-01)_

The single [responsibility principle](https://en.wikipedia.org/wiki/Single_responsibility_principle) is the first principle of the SOLID acronym.

> "A class should have only one reason to change."

Every module or class should have responsibility over a single part of the functionality provided by the software, and that responsibility should be entirely encapsulated by the class.

For example, imagine the scenario of navigation software. We have a position based on the direction given (north, south, west, east) the position should change.

The Position class contains values regarding the x- and y-axis position.

The direction is an enum representing the direction towards North, East, South, and West.

And at last, there is a Navigator class responsible for navigating according to the direction and position change.

In order to navigate properly, the navigator should resolve the next position based on the direction. Also, the navigator should fix the position in cases of values below 0.
    
    
                    return new Position(position.getxAxis(),position.getyAxis()+1);
    
    
                    return new Position(position.getxAxis(),position.getyAxis()-1);
    
    
                    return new Position(position.getxAxis()-1,position.getyAxis());
    
    
                    return new Position(position.getxAxis()+1,position.getyAxis());
    
    
                    position.getxAxis()<0?0:position.getxAxis(),
    
    
                    position.getyAxis()<0?0:position.getyAxis()

The problem with this approach is that if the position validity criteria change, we have to change the Navigator class. The same applies if the position movement mechanisms change. The navigator, instead of just navigating, is responsible for both resolving the next position and for fixing the new position.

An approach that does not break the single responsibility principle is to create a class that will resolve the next position and a class responsible for fixing the new position.

The NextPositionResolver class will resolve the next position based on the direction given.

The PositionRepairer class will fix the position in case of invalid x or y values.

The Navigator class will have, as dependencies, the NextPositionResolver and PositionRepairer classes in order to perform the navigation properly.

You can find the source code on [GitHub](https://github.com/gkatzioura/SolidPrinciples/tree/master/src/main/java/com/gkatzioura/solid/single). Next principle is the [open/closed ](https://egkatzioura.com/2018/02/19/solid-principles-open-closed-principle/)principle.
