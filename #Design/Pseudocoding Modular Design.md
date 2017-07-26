# Pseudocoding Modular Design

_Captured: 2015-10-14 at 23:19 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/pseudocoding-modular-design)_

##  Apply what you've just learned by pseudocoding a modular solution to a classic problem. 

## Assignment: Pseudocoding a More Complex Design with Modularity

Over the last several lessons, you've learned all about how to use modularity to break down a problem. You even picked up some tips on how to make your modules perform better. In this assignment, you'll be asked to take apart a more complicated problem and pseudocode up the design for its solution.

To do this, you _could_ simply jam all the code into one long script but it would be an instance of one giant "god" module so you know that's a bad idea. Practice thinking of each subtask as a separate module.

The goal for this exercise is NOT to rigorously apply all the SOLID principles (and you can't do this anyway with the simple pseudocode you've learned). We instead want you to think in terms of modules and to recognize when the problem needs to be separated into them.

### The Elevator

![Elevator keypad](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/elevator_keypad_small.jpg)

> _Elevator keypad_

You live in a 25 story building with one elevator. The central microcontroller got eaten by rats and the building manager has asked you to code up the elevator's operating procedure until he can get a new one. You figure you'll have to learn to actually code soon but you first want to think things through and pseudocode your design.

#### Elevator Details

The basic elevator machinery is completely dumb (it doesn't do anything it's not told to do) but is capable of interpreting and executing the commands:

  * "open elevator door"
  * "close elevator door"
  * "go up full speed"
  * "go down full speed"
  * "slow down"
  * "stop"

...and it accepts user input in the form of:

  * floor buttons inside the elevator
  * door open and close buttons inside the elevator
  * up and down call buttons on each floor

...and it has sensors for:

  * if a human is in the door closing path
  * if it is currently at a floor (instead of in-between floors)

...and it has a few quirky requirements:

  * it must "slow down" at least 1 floor before it stops.
  * there is a small chance that it actually stops between floors by accident (it's an old elevator)

#### The Task

Your job is to design a properly working elevator. It should stop on each floor it is physically able to during a given trip to pick up whoever is going the same direction. Additionally, make sure that no one is:

  1. smashed into the ground
  2. pushed through the roof
  3. squished by the doors
  4. let off in between floors
  5. stuck going the wrong direction (unless they choose not to exit)

This will be good practice thinking about all the edge cases and scenarios that a user can do.

The point isn't to follow any strict guidelines of syntax but rather to focus on getting the logic of the problem figured out and then organizing it into modules that accomplish the sub-tasks that are required.

Think about:

  * Using a loop around everything to keep your pseudocode (and elevator) running. 
  * Writing everything in one giant mess to start with and then refactoring it to break apart the modules so it feels less cluttered and messy.

### Use Modules!

This exercise is large enough that you will need to break your code up into modules. Remember the SOLID lessons -- modules should only have one major purpose. For this exercise, you can use other modules by simply calling their name in plain english and writing them out as separate programs down below your main program. They could be groups of procedural instructions like "slow down the elevator if necessary", which runs the "ReachedADestinationFloor?" program.
    
    
    PROGRAM Elevator:
        # other code
        slow down the elevator if necessary
        # other code
    END
    
    # other code
    
    PROGRAM SlowDownIfNecessary
        IF we are traveling up at full speed
            IF we are only 1 floor away from the lowest destination floor
                slow down
            END
        ELSE IF we are traveling down at full speed
            IF we are only 1 floor away from the highest destination floor
                slow down
            END
        END
    END
    

You have everything you need to design your elevator. Up, up and away!

###  Next Lesson: Turning a New Feature into Agile Stories and Pseudocode 

[ Onward! ](http://www.vikingcodeschool.com/software-engineering-basics/turning-a-new-feature-into-agile-stories-and-pseudocode) [ or go to previous lesson... ](http://www.vikingcodeschool.com/software-engineering-basics/solid-design-principles)
