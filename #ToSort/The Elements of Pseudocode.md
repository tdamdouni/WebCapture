# The Elements of Pseudocode

_Captured: 2015-10-14 at 23:15 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/the-elements-of-pseudocode)_

## The Elements of Pseudocode

![Logical Thinking](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/logical_thinking_small.jpg)

> _Logical Thinking_

In this lesson we'll cover the foundational elements of pseudocoding and coding. We'll start referring to your batches of pseudocode as either a "program" or a "script" (or, later, a "module").

### Sequence

The first assumption is that the program runs from top to bottom in a continuous sequence. Think of it like a recipe.
    
    
    Step 1
    Step 2
    ...
    Step N
    

### Selection (Flow Control)

There are going to be points in the program where you will want to divert the flow based on some sort of condition. In that case, just like in English, you'll use an **IF** statement to tell it where to go if one thing is true and then an **ELSE** to tell it what to do if the condition is not met. People don't always use "Else" in daily English anymore but it's the same as "Otherwise".

You can also choose between multiple options by combining the two into one **ELSE IF**. Here's an example which you may be familiar with if you've been to an amusement park (where they only allow children above certain heights to ride the roller coasters):
    
    
    PROGRAM CheckChildHeightBeforeEntry
        IF the child is taller than 4 feet
            give the child a high-five
            Allow the child to enter the ride
        ELSE IF the child is between 3'10" and 4 feet tall
            IF the parents give permission
                Allow the child to enter the ride
            ELSE
                Prevent the child from entering the ride
            END
        ELSE
            Prevent the child from entering the ride
        END
    END
    

In the example above, we used indentation to show you where one batch of instructions ends and the next part of our expression begins. We also use "END" to show when each IF statement has finished (even though it's redudnant with the indentation). We've also decided to capitalize all the important keywords like "IF" to make them easier to see. And we wrapped the whole thing in the words **PROGRAM** and **END** to identify the boundaries of the script.

The point isn't to stick with an exact style -- it's to be as clear as possible so the reader knows what's going on.

Here's the same example with some slightly more formal syntax:
    
    
    PROGRAM CheckChildHeightBeforeEntry
        IF(the child is taller than 4 feet) THEN
            Give the child a high-five;
            Allow the child to enter the ride;
        ELSE IF(the child is between 3'10" and 4 feet tall) THEN
            IF(the parents give permission) THEN
                Allow the child to enter the ride;
            ELSE
                Prevent the child from entering the ride;
        ELSE
            Prevent the child from entering the ride;
        END
    END
    

### Iteration (aka Looping)

Imagine that you need to perform the same set of instructions many times, relying on feedback from each time to decide whether you're ready to finish yet. The most common way to do that is by using the words **WHILE** and **DO** and also specifying a condition. As long as the condition is true, you will keep looping back through your code. Once it's done, the program continues executing as normal.

Let's say you want to fill in a hole:
    
    
    PROGRAM FillInAHole
        WHILE(the hole is not full) DO
            Get a shovel full of dirt
            Empty the shovel onto the hole
        END
        Relax with an ice cold lemonade
    END
    

There are a few different ways of writing iterators which will show up again when you start learning code, for instance just saying **TIMES**:
    
    
    PROGRAM ThreeCheers
        Print "Three Cheers!"
        3 TIMES DO
            Print "Hip Hip Hooray!"
        END
    END
    

Or, maybe you want to iterate through each item in a batch of things. A good keyword for that would be **EACH**, and you would just have to specify which bunch of things to iterate through:
    
    
    PROGRAM CleanTheFridge
        for EACH item in the fridge DO
            IF(the item is rotten) THEN
                throw away the item
            ELSE
                put the item back in the fridge
            END
        END
        Make Dinner
    END
    

### Said Another Way

**Check out the below presentation from Damian Gordon about pseudocoding:**

### Wrapping Up

That's really it for the basic stuff -- now you can solve all kinds of logic problems or programming challenges or recipes for life's tasks. The answers rarely require anything more sophisticated than a procedure with conditionals and looping. In the coming lessons we'll cover a few other principles that will help you tackle the more complex problems, but you're ready to take on all kinds of challenges now.

If you're (un)lucky, you might even start thinking procedurally about all the tasks you do in your daily life and writing them down in the form of conditional statements and iterations. Just don't get stuck in an infinite loop doing so!

![infinite road](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/infinite_road_small.jpg)

> _infinite road_
