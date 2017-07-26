# Why is Object-Oriented Programming Useful? (With a Role Playing Game Example)

_Captured: 2015-11-04 at 23:22 from [inventwithpython.com](http://inventwithpython.com/blog/2014/12/02/why-is-object-oriented-programming-useful-with-an-role-playing-game-example/)_

This blog post is those still new to programming and have probably heard about "object-oriented programming", "OOP", "classes", "inheritance/encapsulation/polymorphism", and other computer science terms but still don't get what exactly OOP is used for. In this post I'll explain _why_ OOP is used and how it makes coding easier. This post uses Python 3 code, but the concepts apply to any programming language.

There are two key non-OOP concepts to understand right off the bat:

  1. **Duplicate code is a Bad Thing.**
  2. **Code will always be changed.**

Aside from small "throw-away" programs that are written for some single task and only run once, you'll almost always need to update your code to either **fix bugs** or **add new features**. A large part of writing good software is writing software that is readable and easy to change.

If you have copy/pasted code in your program, changing it requires making the same change to multiple places in your program. This is problematic. If you miss applying the change to some places, you'll fail to fix the bug everywhere or implement the new feature inconsistently. _Duplicate code is a Bad Thing._ Having duplicate code in your program is setting yourself up for bugs and headache.

Functions let you get rid of duplicate code. You write the code in a function once, and just call the function everywhere your program needs that code run. Updating the function's code updates it everywhere the function is called automatically. Just as functions makes updating code easier, using object-oriented programming techniques also organizes your code to make changes easier. _And code will always be changed._

**The Role Playing Game Example**

Most OOP tutorials stink. They have "Car" classes with "Honk" methods and other examples that are unrelatable to the actual programs that new coders write or have used before. So this blog will use an RPG-style video game (think World of Warcraft, Pokemon, or Dungeons & Dragons). We're used to thinking of things in these games as a collection of integers and strings. Check out all the numbers on this Diablo status screen or D & D character sheet:

![](http://inventwithpython.com/blogstatic/oop_stats1.jpg?27f655)

![](http://inventwithpython.com/blogstatic/oop_stats2.jpg?27f655)

Taking out the graphics from these RPG video games, the characters, armor, and other objects are just a bunch of integer or string values in variables. Without using object-oriented concepts, you could implement these things in Python code like this:

name = 'Elsa' health = 50 magicPoints = 80 inventory = {'gold': 40, 'healing potion': 2, 'key': 1} print('The hero %s has %s health.' % (name, health))

The above variable names are pretty generic. To add monsters in this program, you'll need to rename the player character's variables and make new ones for the monsters:

heroName = 'Elsa' heroHealth = 50 heroMagicPoints = 80 heroInventory = {'gold': 40, 'healing potion': 2, 'key': 1} monsterName = 'Goblin' monsterHealth = 20 monsterMagicPoints = 0 monsterInventory = {'gold': 12, 'dagger': 1} print('The hero %s has %s health.' % (heroName, heroHealth))

But of course you'll want to have more than one monster, but then you'll have variables like `monster1Name`, `monster2Name`, etc. That's a poor way to code, so maybe you'll make the monster variables into lists:

monsterName = ['Goblin', 'Dragon', 'Goblin'] monsterHealth = [20, 300, 18] monsterMagicPoints = [0, 200, 0] monsterInventory = [{'gold': 12, 'dagger': 1}, {'gold': 890, 'magic amulet': 1}, {'gold': 15, 'dagger': 1}]

Then you could just have the first goblin's stats be the values at index `0` in the lists, the dragon's stats are at index `1`, and the other goblin's stats are at index `2`. This way you could have multiple monsters contained in these variables.

But this kind of code easily leads to bugs. If your lists get out of sync, the program will no longer work correctly. Say the player vanquishes the goblin at index `0` and the program calls a vanquishMonster() function. But the function has a bug and deletes the values from all the lists except (accidentally) `monsterInventory`:

def vanquishMonster(monsterIndex): del monsterName[monsterIndex] del monsterHealth[monsterIndex] del monsterMagicPoints[monsterIndex] # Note there is no del for monsterInventory vanquishMonster(0)

The monster lists end up looking like:

monsterName = ['Dragon', 'Goblin'] monsterHealth = [300, 18] monsterMagicPoints = [200, 0] monsterInventory = [{'gold': 12, 'dagger': 1}, {'gold': 890, 'magic amulet': 1}, {'gold': 15, 'dagger': 1}]

Now it looks like the dragon's inventory is the same as the old goblin's inventory. And the second goblin now has the inventory the dragon had. _This is quickly getting out of hand._ The problem is that you have _one_ monster's data spread out over multiple variables. You could fix this by putting a single monster's data into a dictionary, and then have a list of dictionaries:

monsters = [{'name': 'Goblin', 'health': 20, 'magic points': 0, 'inventory': {'gold': 12, 'dagger': 1}}, {'name': 'Dragon', 'health': 300, 'magic points': 200, 'inventory': {'gold': 890, 'magic amulet': 1}}, {'name': 'Goblin', 'health': 18, 'magic points': 0, 'inventory': {'gold': 15, 'dagger': 1}}]

G'ah. This code is getting complex. For example, the inventory of a monster is a dictionary-in-a-dictionary-in-a-list. What if things like spells or inventory items also have their own attributes and need to be dictionaries? What if an inventory item could be a sack, which itself contains other inventory items? This monsters dictionary would get intense.

This is something that object-oriented programming can solve by creating a new data type.

**Creating Classes**

**Classes are the blueprints for a new data type in your program.** Object-oriented programming provides a new approach for modeling the armor, monsters, etc. much better than a hodge-podge of lists and dictionaries, even though OOP concepts it take some getting used to.

In fact, since the hero will have all the same features of monsters (health, inventory, etc.) we can just have a generic `LivingThing` class that the hero and monsters share. Your code can be changed to look like this:

class LivingThing(): def __init__(self, name, health, magicPoints, inventory): self.name = name self.health = health self.magicPoints = magicPoints self.inventory = inventory # Create the LivingThing object for the hero. hero = LivingThing('Elsa', 50, 80, {}) monsters = [] monsters.append(LivingThing('Goblin', 20, 0, {'gold': 12, 'dagger': 1})) monsters.append(LivingThing('Dragon', 300, 200, {'gold': 890, 'magic amulet': 1})) print('The hero %s has %s health.' % (hero.name, hero.health))

Hey look, using classes has already cut down our code in half since we can use the same code for both player characters and monsters.

In the above code you are defining a new data type/class (pedantics aside, but the two terms are basically the same. See also: [Stack Overflow - What's the difference between a type and a class?](https://stackoverflow.com/questions/468145/what-is-the-difference-between-type-and-class)) called `LivingThing`. You can have `LivingThing` values/objects (again, two terms for basically the same thing) just like you can have integer values, string values, or boolean values.

Some Python-specific details about the above code:

class LivingThing():

The above is a `class` statement that defines a new class, just like `def` statements define a new function. The class's name is `LivingThing`.

def __init__(self, name, health, magicPoints, inventory):

The above defines a method for the `LivingThing` class. **"Method"** is just the name used for functions that belong to a class. (See also: [Stack Overflow - What is the difference between a method and a function?](https://stackoverflow.com/questions/155609/what-is-the-difference-between-a-method-and-a-function))

This particular method is special. The name `__init__()` is used for the "constructor function" (also called a "constructor method", or "constructor" or "ctor" for short) for the class. While a class is a blue print for a new data type, you still need to create values of this data type in order to have something that you can store in variables or pass to functions.

When called, the constructor creates the new object, runs the code in the constructor, and returns the new object. This is what the `hero = LivingThing('Elsa', 50, 80, {})` line is. No matter what the class name is, the constructor is always named `__init__`.

If a class has no `__init__()` method, Python supplies a generic constructor method for your class that doesn't do anything. But the `__init__()` method is a good place for code that does the initial setup of a new object.

In Python, the first parameter for methods `self`. The `self` parameter is used to create member variables, explained next.

The body of the constructor function is this:

self.name = name self.health = health self.magicPoints = magicPoints self.inventory = inventory

This seems a bit repetitive, but what this code does is create member variables for the object being created by the constructor. Member variables will begin with `self.` to show that they are member variables belonging to the object, and not just regular local variables in the method.

**Calling the Constructor**

# Create the LivingThing object for the hero. hero = LivingThing('Elsa', 50, 80, {}) monsters = [LivingThing('Goblin', 20, 0, {'gold': 12, 'dagger': 1}), LivingThing('Dragon', 300, 200, {'gold': 890, 'magic amulet': 1}), LivingThing('Goblin', 18, 0, {'gold': 15, 'dagger': 1})] print('The hero %s has %s health.' % (hero.name, hero.health))

The constructor call in Python will just look like a function call using the the class's name. So `LivingThing()` is the call to the `LivingThing` class's `__init__()` constructor. The above `LivingThing('Elsa', 50, 80, {})` call creates a new `LivingThing` object is created and stored in the `hero` variable. The above code also creates `LivingThing` objects for the three monsters and stores them in the `monsters` list.

And here's where we begin to see the benefits of object-oriented programming. If another programmer is reading your code, when they see the `LivingThing()` call they know they can just look for "class LivingThing" and find out the details of everything they need to know about what a `LivingThing` is.

But an even bigger benefit comes when you try to update your `LivingThing` class.

**Updating Classes** Say you wanted to add "hunger" levels to your RPG. If a hero or monster has a `hunger` level of `0`, they are not at all hungry. But if their `hunger` level is above `100`, then they take damage and their `health` value decreases each day. You could change your `__init__()` method to this:

def __init__(self, name, health, magicPoints, inventory): self.name = name self.health = health self.magicPoints = magicPoints self.inventory = inventory self.hunger = 0 # all living things start with hunger level 0

Without changing _any_ other line of code, _every_ `LivingThing` object in your game now has a hunger level! You don't have to worry about some `LivingThing` objects having the `hunger` member variable and some not: the very definition of what a `LivingThing` is has been updated.

You also don't have to change any of the constructor calls since you didn't add a new hunger level parameter to the `__init__()` method. That's because `0` is a good common-sense default value for a new `LivingThing` object's hunger level. If you do add a new parameter to `__init__()` for the hunger levels, you'll have to update all the code that calls the constructor. But this is true for any function anyway.

If your RPG has a lot of default values for things, you can avoid a lot of "boilerplate" code by using classes with a constructor that sets the default for you.

**Methods**

Methods are useful for running code that affect the object itself. For example, you could just have code that changes the health of a LivingThing object directly:

hero = LivingThing('Elsa', 50, {}) hero.health -= 10 # Elsa takes 10 points of damage

But this isn't a very robust way to handle taking damage. Lots of other game logic needs to be checked whenever something takes damage. For example, say you want to check if a character dies each time they take damage. You would need code like this:

hero = LivingThing('Elsa', 50, {}) hero.health -= 10 # Elsa takes 10 points of damage if hero.health < 0: print(hero.name + ' has died!')

The problem with the above approach is that you would need that check everywhere your code decreases the health of a `LivingThing` object. But duplicating code is a Bad Thing. The non-OOP way to prevent duplicate code would be to put it in a function:

def takeDamage(livingThingObject, dmgAmount): livingThingObject.health = self.health - dmgAmount if livingThingObject.health < 0: print(livingThingObject.name + ' is dead!') hero = LivingThing('Elsa', 50, {}) takeDamage(hero, 10) # Elsa takes 10 points of damage

This is a better solution because any updates to `takeDamage()` (such as factoring in armor, protective spells, bonuses, etc.) just have to be added to the `takeDamage()` function.

However, the downside is that when your program grows in size, it's easy for `takeDamage()` to get lost in among them. It isn't so clear that `takeDamage()` is related to the `LivingThing` class. If you have hundreds of functions in your program, it will be hard to figure out which ones are related to the `LivingThing` class.

The solution is to turn this function into a `LivingThing` method:

class LivingThing(): # ...other code in the class... def takeDamage(self, dmgAmount): self.health = self.health - dmgAmount if self.health == 0: print(self.name + ' is dead!') # ...other code in the class... hero = LivingThing('Elsa', 50, {}) hero.takeDamage(10) # Elsa takes 10 points of damage

Once your program has many classes, each with many methods and member variables, you will begin to see how OOP can help organize your programs to be more manageable.

**Public and Private Methods**

Methods and member variables can be marked as public or private. Public methods can be called and public member variables can be set by any code, inside or outside of the class. Private methods can be called and private member variables can be set only by code inside the object's own class.

In some languages such as Java, this "can be called/set" is strictly enforced by the compiler. In Python, there's no such concept as "private" and "public". All methods and member variables are "public". However, the convention is that if a method name begins with an underscore, it is marked as private. This is why you'll see methods such as `_takeDamage()`. Nothing prevents you from writing code that calls private methods or set private member variables from outside the object's class, but you've been fairly warned not to do that.

The reason for having this public/private distinction is to set expectations for how the class interacts with outside code. (See also: [Stack Overflow - Why "private" methods in the object oriented?](https://stackoverflow.com/questions/2620699/why-private-methods-in-the-object-oriented)) The programmer of the class expects that other people won't write code that calls the private methods or sets the private member variables.

For example, the `takeDamage()` method factors in checking for death if health falls below 0. You may want to add all sorts of other checks in the code. Things like armor, agility, and protective spells could factor in to reduce the damage taken. The `LivingThing` object might be wearing an enchanted cape that _heals_ them by adding the damage amount to their `health` instead of subtracting. All of this game logic can go in the `takeDamage()` method.

But all of OOP organizing is for nothing if you accidentally put this code in there:

class LivingThing(): # ...code in the class... hero = LivingThing('Elsa', 50, {}) # ...some more code... if someCondition: hero.health -= 50

That `hero.health -= 50` will subtract 50 points of health, without taking into any consideration what armor Elsa is wearing, if she has protective spells, or is wearing that enchanted healing cape. This code bluntly decrements `health` by `50`.

It's easy to forget about the `takeDamage()` method and accidentally write code like this. This doesn't check if the `hero` object's `health` member variable has dropped below `0`. The program continues as though Elsa is alive even if she has negative health! This is a bug we can avoid with public/private members and methods.

If you rename the `health` member variable to `_health` and mark it private, then it's easy to catch this bug when you write it:

hero = LivingThing('Elsa', 50, {}) # ...some more code... if someCondition: hero._health -= 50 # WAIT! This code is outside the hero object's class but modifying a private member variable! This must be a bug!

In a language like Java where the compiler enforces private/public access, it would be impossible to write a program that illegally accesses a private member or method. Object-oriented programming helps prevent these kinds of bugs.

**Inheritance**

Using the LivingThing class for dragons is nice, but dragons have a lot of other qualities in addition to the ones provided by `LivingThing`. So you want to create a new `Dragon` class that will have member variables like `airSpeed` and `breathType` (which can be string such as `'fire'`, `'blizzard'`, `'lightning'`, `'poison gas'`, etc).

Since `Dragon` objects will also have `health`, `magicPoints`, `inventory`, and all the other things that `LivingThing` objects have, you _could_ just create a new `Dragon` class and copy/paste all the code from your `LivingThing` class. But this would result in duplicate code, which is a Bad Thing.

Instead, make a `Dragon` class that is a **subclass** of the `LivingThing` class:

class LivingThing(): # ...other code in the class... class Dragon(LivingThing): # ...Dragon-specific code in the class...

This is effectively saying, "A `Dragon` is the same as a `LivingThing`, with some additional methods and member variables". When you create a `Dragon` object, it will automatically have all the same methods and member variables as `LivingThing` (saving us from duplicating the code). But it could also have dragon-specific methods and member variables to it. Further, any code that deals with a `LivingThing` object can automatically handle a `Dragon` object because `Dragon` objects already have the `LivingThing` members and methods. This principle is called **subtype polymorphism**.

In practice, inheritance is easy to abuse though. You must be certain that any conceivable change or update you make to the `LivingThing` class would also be something you would want the `Dragon` class _and every other subclass of `LivingThing`_ to also have. This might not always be so straightforward.

For example, what if you created `Monster` and `Hero` subclasses of the `LivingThing` class, and then created `FlyingMonster` and `MagicalMonster` subclasses from `Monster`. Would the new `Dragon` class be a subclass of `FlyingMonster` or `MagicalMonster`? Or maybe just its own subclass of `Monster`?

This is where inheritance and OOP start to get tricky and religious arguments over the "correct" way to design classes come about. I want to keep this blog post short and simple, so I'll leave these topics as exercises for the reader to look into. (See also [Stack Overflow - Prefer composition over inheritance?](https://stackoverflow.com/questions/49002/prefer-composition-over-inheritance) and [Wikipedia - Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance))

**Summary**

I hate programming tutorials for beginners that start with object-oriented programming. OOP is a very abstract concept. Until have some experience and are writing large programs, you won't understand why using classes and objects makes programming easier. Instead, the neophyte is left with a steep learning curve to climb and no idea why they're climbing it. I hope the RPG example has at least given you a glimpse as to why OOP can be helpful. There is MUCH more to OOP. If you want to learn more, try googling for "[python object oriented design"](https://www.google.com/search?q=python%20object%20oriented%20design) or "[python design patterns"](https://www.google.com/search?q=python+design+patterns).

If you are still confused by OOP concepts, feel free to write programs without classes. You don't **need** them and they can result in over-engineered code. But once you have some coding experience under your belt, the benefits of object-oriented programming will become apparent. Good luck!
