# The Confusing World of Object-Oriented Programming, Explained as an RPG

_Captured: 2015-11-04 at 23:21 from [lifehacker.com](http://lifehacker.com/object-oriented-programming-explained-with-a-role-playi-1740569072?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+lifehacker%2Ffull+%28Lifehacker%29)_

![The Confusing World of Object-Oriented Programming, Explained as an RPG](http://i.kinja-img.com/gawker-media/image/upload/s--RDbkv9xp--/c_scale,fl_progressive,q_80,w_800/1504463010743894824.png)

Object-oriented programming (or OOP) is an abstract concept, often hard to grasp when you're new to programming. The "Invent with Python" blog offers an awesome analogy that makes OOP more understandable if you've ever played a RPG-style video game like World of Warcraft or Dungeons & Dragons.

Let's say you're creating your own game. You'll need to represent all the characters (heroes and monsters), their stats (health and magic points), inventory items, and so on--and also account for health damage your characters take, inventory going up or down, and other status changes. Defining each thing with variables (e.g., `monster1Name = 'Goblin'`, `monster2Name = 'Dragon'`) and using lists or a list of dictionaries gets quickly out of hand and makes the code more complex (and bug-prone) than it needs to be. E.g.: `monsters = [{'name': 'Goblin', 'health': 20, 'magic points': 0, 'inventory': {'gold': 12, 'dagger': 1}}, {'name': 'Dragon', 'health': 300, 'magic points': 200, 'inventory': {'gold': 890, 'magic amulet': 1}}]`

That's where OOP and its classes and methods come in:

> **Classes are the blueprints for a new data type in your program.** Object-oriented programming provides a new approach for modeling the armor, monsters, etc. much better than a hodge-podge of lists and dictionaries, even though OOP concepts it take some getting used to.
> 
> In fact, since the hero will have all the same features of monsters (health, inventory, etc.) we can just have a generic `LivingThing` class that the hero and monsters share. 

You define the LivingThing class once and then can quickly and easily create new monsters from it. You could update the LivingThing class to, say, now track your RPG character's hunger just by adding one line of code--instead of having to update every object individually. As explained in [a different laundry analogy](http://lifehacker.com/learn-key-computer-science-concepts-with-these-everyday-1699474241), objects encapsulate complexity.

Check out Al Sweigart's post below for the full RPG-meets-OOP example. Whether you want to create your own RPG game or another kind of program, this explanation is a lot more interesting to read than most OOP tutorials.

[Why is Object-Oriented Programming Useful? (With a Role Playing Game Example)](http://inventwithpython.com/blog/2014/12/02/why-is-object-oriented-programming-useful-with-an-role-playing-game-example/) | The "Invent with Python" Blog
