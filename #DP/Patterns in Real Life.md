# Patterns in Real Life

_Captured: 2015-11-21 at 13:33 from [www.codeproject.com](http://www.codeproject.com/Articles/29036/Patterns-in-Real-Life)_

## Introduction

In object oriented design (OO), we give clear responsibility to each object. An object is like a black box which can receive and send messages. All objects together form the complete system. Design patterns by Gang of Four introduced many general reusable solutions to commonly occurring problems in software design. I always correlate interactions between objects to real life interactions involving people and or real things. If you look around, you can see many real life examples for patterns, but played out with people instead of real objects. In this article, I will try to explain a few of these real life examples of design patterns for you.

## Who can read this article?

Any one who can read English, of course, can read this article, but the targeted audience is people with some years of software experience. You need not know any special programming language, but you must know one object oriented language. Also, you are expected to be familiar with design patterns and the terminologies used in design patterns.

## Composite pattern

In Composite pattern, you don't differentiate between a leaf and a composite. The client treats a leaf or a composite the same way. You can correlate this pattern with an organization. An organization consists of many departments. Each department consists of many projects. Each project consists of many project members. A typical organization structure is as shown below.

![organization.gif](http://www.codeproject.com/KB/architecture/patterns_in_real_life/organization.gif)

### Recursion

What makes the Composite pattern one of the most beautiful is the power of recursion. I can explain this with the same organization example. You want to find the total salary paid to all employees of the organization. It is nothing but the salary of CEO + the salary paid to all the departments. What is the salary of a department? It is the salary of the department head + the salary of all projects. What is the total salary of a project? It is the salary of the project manager + the salary of all the project members. In a nutshell, the salary of anything is the salary of self + the salary of all its sub groups.

A typical example for this in the software scenario is an XML DOM (Document Object Model) structure. A simple XML structure is shown below.

![xml.gif](http://www.codeproject.com/KB/architecture/patterns_in_real_life/xml.gif)

As you can see here, "`employees`" is a node. "`employee`" is another node which is a child of `employees`. What about `name` in `employee`? That is also a node. It is nothing but a collection of node objects. Each node can have n-number of child-nodes. If I draw a class diagram of the same, it will be like shown below.

![composite_class.gif](http://www.codeproject.com/KB/architecture/patterns_in_real_life/composite_class.gif)

If I create an object structure for the same in a system, based on the XML file input, you will have a structure which is as simple as a single object to a complex structure involving any number of objects. A typical structure is shown below:

![composite_object.gif](http://www.codeproject.com/KB/architecture/patterns_in_real_life/composite_object.gif)

To describe the advantages of the Composite pattern, I would like to take a simple organization structure as shown below. If you want to find the total number of employees in the organization, it is the sum of the root node + all its children. The calculation goes recursively, as shown below:

![recursion.gif](http://www.codeproject.com/KB/architecture/patterns_in_real_life/recursion.gif)

Another typical example of the power of recursion is GUI toolkits. For example, Java SWT (Standard Widget Toolkit). If you want to apply a theme for a dialog, you need to apply the theme for the dialog + all its child components. A child can be a composite or a widget itself. If it is a widget, there is no child for that, and the theme needs to be applied only for the widget. But if it is a composite, we need to apply the theme for all its children. Now again, a child can be a widget or a composite. The loop continues until it covers all child widgets.

Another example I can think of is the destruction of objects in C++. Take any OO language without a garbage collector. Just imagine you have a data structure like shown below. Each object has a reference only to his children and the client is aware of only the root node object. How will you destroy all the objects, leaving no memory leak? It is only a couple of lines of code that takes to destroy the complete code.

![tree.gif](http://www.codeproject.com/KB/architecture/patterns_in_real_life/tree.gif)

> _Kill a node = Kill all its children and then kill yourself._

Since the children are also of type node, the loop continues till it goes to the lowest level where there are no children.

## Observer pattern

A typical example for the Observer pattern is the conventional mail delivery system. Whenever you have a mail, the postman will come and knock at your door with the mail. Just imagine if you have to go to the post office every day and check whether there are any mails. It would have been a really inefficient system as each individual needs to go to the post office periodically. This is eliminated in real life by introducing a mail delivery mechanism.

![mailman.gif](http://www.codeproject.com/KB/architecture/patterns_in_real_life/mailman.gif)

It is the same in a GUI system as shown below. Your business logic, in this case, the cassette player, will update all the GUI components periodically, just like a post man who comes to your house with mail. It would have been inefficient for the total system to implement a periodic check by each widget to get the progress.

![standard_ui.gif](http://www.codeproject.com/KB/architecture/patterns_in_real_life/standard_ui.gif)

There are two typical models for Observer based on the way data is passed. It can be a push model or a pull model. In the push model, data is pushed along with the notification. An example for this is mail delivery, magazine subscriptions etc. In the pull model, the client will be notified about what is happening. But, it is always the responsibility of the client to check whether the relevant data is there or not. An example for this is RSS feeds. Whenever there is a change in the website, and if you have subscribed for the feed, you will get a notification. But, it is up to you to go back and see if you are interested.

## Factory Pattern and Abstract Factory pattern

Imagine you are constructing a house and you approach a carpenter for a door. You give the measurement for the door and your requirements, and he will construct a door for you. In this case, the carpenter is a factory of doors. Your specifications are inputs for the factory, and the door is the output or product from the factory.

Now, consider the same example of the door. You can go to a carpenter, or you can go to a plastic door shop or a PVC shop. All of them are door factories. Based on the situation, you decide what kind of factory you need to approach. This is like an Abstract Factory.

![factory.gif](http://www.codeproject.com/KB/architecture/patterns_in_real_life/factory.gif)

## Adapter

I think this is a self explanatory pattern. You can find many real life examples for this pattern, and the simplest, which is called by the same name, is a power adapter. You have an AC power supply and the responsibility of the adapter is to provide different types of sockets adapted to the one needed.

![adapter.gif](http://www.codeproject.com/KB/architecture/patterns_in_real_life/adapter.gif)

> _Another example for this is a translator who is translating languages spoken by one person for another person._

## Façade

Imagine you want to organize a marriage reception. You need to decorate the hall where the event is planned. You need a music band to play some music. You want to organize dinner for say 100 people, and also snack in the evening for around 50 people. If you wanted to organize such an event some 10 years back, you wanted to go to a caterer for food, a musical troop for music, and organize flowers and people to decorate them, and so and so. Some twenty years back, we needed to go to the fish market, the meat shop, the vegetable market etc., for the raw materials for the food and then organize a cook so that you have everything ready for the event. Now, life is really simpler with event managers. You just need to walk to an event manager and tell him that you need a hall decorated with flowers, dinner for 100 people, snacks for 50 people, and need a good music troop to play music while the reception is going on. You don't need to worry about anything, and they will take care of the rest. This is a typical example for Façade. You don't need to interact with many different objects for each and every activity. You will be provided a single interface which will act as a façade for many activities. This makes the life of clients much simpler.

Other examples for Façade are one stop bill payment shops, a support desk in a big organization which takes all kinds of support requests etc.

## Decorator

A decorator decorates something. An example for Decorator is a sunglass. It takes light as input, removes all harmful parts in the light, and passes it on. If you give apple as an input to a system, and if it gives orange as output, that is **not** a Decorator. Another example for this is music filtering.

A software example for Decorator is JAVA I/O. Initially, I wondered why we need to create so many objects just to do a file operation. I realized how flexible and wonderful it is after some time.

## Template

A typical example for the Template pattern is the Computer Engineering degree curriculum. It covers all the basic stuff required for a typical software engineer. He can't work as it is in an industry as he needs to fill in many gaps which are required in the specific domain. But, he will have the necessary knowledge to move to any software company after completion of the course.

## Reactor

Recently, I went to a restaurant in Bangalore. There was a female standing outside, receiving all the people entering the restaurant. She received us with a pleasant smile, then took us inside, and helped us find a table. She assigned a waiter to serve us, and then went back to the reception and waited for new clients. All she did was receive a new visitor. She is just like a web server serving multiple clients. In a typical web server, there is a thread simply waiting for requests from clients. Whenever there is a client request, it creates a separate thread and assigns that thread to handle the request. The thread will die down after serving the requests.

## Conclusion

You can find many more examples like this in our day to day life for real life design patterns. If we correlate these, we will appreciate the patterns better. Most of these real life patterns were evolved over a long period of time by brilliant people to have efficient systems in the society. If we follow this in software systems, we can create efficient software systems just like other efficient systems around you.

This article, along with any associated source code and files, is licensed under [The Code Project Open License (CPOL)](http://www.codeproject.com/info/cpol10.aspx)
