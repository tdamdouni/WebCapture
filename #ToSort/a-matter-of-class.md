# A Matter of Class

_Captured: 2017-06-06 at 09:44 from [dzone.com](https://dzone.com/articles/a-matter-of-class?edition=304122&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-05)_

Get Your Apps to Customers 5X Faster with [RAD Studio](https://dzone.com/go?i=219226&u=https%3A%2F%2Fwww.embarcadero.com%2Fproducts%2Frad-studio%3Futm_source%3DDzone%26utm_medium%3DOnlineDisplay%26utm_campaign%3DRadStudioDzone%26utm_content%3DPreRollText)

Introduced by the ECMAScript 2015 specifications, the _class_ construct has become part of the official JavaScript syntax. This construct has been enthusiastically welcomed by many developers. Indeed, it has been considered a sign of the formalization of various attempts to simulate classes, inheritance, and other object-oriented features offered for several years by many libraries, such as [Prototype](http://prototypejs.org/), [ExtJS](https://www.sencha.com/products/extjs/), [Dojo](https://dojotoolkit.org/), [Backbone](http://backbonejs.org/), [Ember](http://emberjs.com/), and others. TypeScript itself was born with the aim of bringing class-based object-oriented programming to the JavaScript language. However, the _class_ construct may lead to serious misconceptions about the object-oriented nature of JavaScript. Let's analyze why.

## **A Convenient Construct**

Using the _class_ construct is very handy. Just take a look at the following code to define the _Animal_ class:
    
    
        console.log(this.name + ‘ makes a noise.’);

Now let's compare it with the equivalent ECMAScript 5 code:

The _class_ construct provides a much more compact code. It appears self-contained and familiar to people who have a traditional object-oriented programming background.

The convenience of this construct becomes even more noticeable when we use inheritance, as we can see by analyzing the following code where the _Snake _and _Horse_ classes are defined by deriving from _Animal_:
    
    
        console.log(this.name + ‘ hisses.’);
    
    
        console.log(this.name + ‘ whinnies.’);

Let's consider now the respective definitions with the dear old ECMAScript 5:
    
    
      Animal.apply(this, [name, 0]);
    
    
      console.log(this.name + ‘ hisses.’);
    
    
      Animal.apply(this, [name, 4]);
    
    
      console.log(this.name + ‘ whinnies.’);

The convenience of using the _class_ construct seems clear: in addition to a smaller number of statements, we get a greater readability and a similarity to the syntax of most object-oriented programming languages. Anyway, regardless of the definition used, in both cases, we will use the classes and constructor functions in the same way:
    
    
    console.log(kaa.legsNumber);    //0
    
    
    console.log(fury.legsNumber);   //4

This ensures the maximum interoperability between the old and the new approach.

## **Not Everyone Is Happy**

Despite its convenience, however, not all developers are so excited about the introduction of the _class_ construct. It looks familiar to most programmers and gives the illusion of using a class-based object-oriented programming language such as Java and C#.

But that is the whole point: it is an illusion, a dangerous illusion. Contrary to what might seem, ECMAScript 2015 specifications have not introduced **the concept of class** in JavaScript. JavaScript is, and remains, a prototype-based object-oriented programming language, even with the _class_ construct.

The introduction of this construct in JavaScript syntax seems to extend the chain of errors that characterized the definition of this language: from the choice of the name itself, that has caused (and still causes) a bit of confusion with Java, to the use of the _new_ keyword to create objects, [actively contested by Douglas Crockford](http://javascript.crockford.com/prototypal.html).

The main effect of these choices is that programmers are misguided in the real understanding of the language and are led to blame it because its behavior is not what is expected.

## **Is it a Real Class?**

But what is the difference between the _class_ construct in class-based languages and the one in JavaScript? As we said, JavaScript is still a prototype-based language, so the _class_ construct is just **syntactic sugar** for creating constructor functions in a more compact way. If we try to get the type of a class, we will find that it is not but a function:

The definition of _Animal_, _Snake_, and _Horse,_ by using the _class_ construct, has the same effect of its definition by using the old ECMAScript 5-style code. Objects are not created by referencing a class, but by referencing a prototype, that is another object, as usual in JavaScript. This means that we can dynamically change the structure of our objects without involving its original class. For example, we can write the following code:

We add a couple of wings to our _Horse_ object, and it continues to be a horse. That's perfectly legal in JavaScript, but it is very difficult to implement and to understand in a class-based world.

Even worse, we can overturn the whole structure of our _Horse_ object as follows:
    
    
      console.log(this.name + ‘ hisses.’);

We have redefined the structure of a _Horse_ as if it were a _Snake_, but it still remains an instance of the _Horse_ class. That's out of any definition of class, not only in the context of programming languages but also in philosophy and set theory contexts.

For example, from a mathematical point of view, a class is a collection of objects that can be unambiguously defined by one or more properties that all its member share. Clearly, since _fury_ and _furySnake_ share no properties, they cannot belong to the same (conceptual) class. Also, from a class-based object-oriented point of view, the two objects can't belong to the same class.

## **Conclusion**

Maybe the choice of a name other than _class_ would have sounded strange to developers coming from languages like Java, C#, and C++, but it would have created fewer illusions and disappointments.

In any case, now the die is cast. The important thing is that the JavaScript developer is aware of what _class_ really means. You have been warned.

[Try RAD Studio for FREE!](https://dzone.com/go?i=219227&u=https%3A%2F%2Fwww.embarcadero.com%2Fproducts%2Frad-studio%3Futm_source%3DDzone%26utm_medium%3DOnlineDisplay%26utm_campaign%3DRadStudioDzone%26utm_content%3DPostRollText) It's the fastest way to develop cross-platform Native Apps with flexible Cloud services and broad IoT connectivity. [Start Your Trial Today!](https://dzone.com/go?i=219227&u=https%3A%2F%2Fwww.embarcadero.com%2Fproducts%2Frad-studio%3Futm_source%3DDzone%26utm_medium%3DOnlineDisplay%26utm_campaign%3DRadStudioDzone%26utm_content%3DPostRollText)
