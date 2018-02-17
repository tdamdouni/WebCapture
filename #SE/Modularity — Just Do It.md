# Modularity — Just Do It

_Captured: 2016-05-20 at 17:05 from [medium.com](https://medium.com/@PieceDigital/modularity-just-do-it-ab4dd2dd20f9#.h9o3399nd)_

![](https://cdn-images-1.medium.com/max/800/0*ndB7JpFsdSnq5ole.jpg)

> _JUST… DO IT! MAKE YOUR APP MAINTAINABLE!_

> What's so great about modularity?

There are several great benefits to designing your application in a modular fashion. For some these points will be obvious, but for others (especially new coders) the benefits may not be so apparent in the beginning. I mean, what could go wrong with throwing everything into one file?

Nothing, as far as logic and functionality is concerned, but here are some reasons that modular design is a far superior design:

  * **Separation of concerns.**
  * **Unit testing.**
  * **Readability.**
  * **DRY-ness.**
  * **Re-usability.**

Unless the function is an IIFE or something that initiates an application, your functions shouldn't be massive. I'm guilty of doing this myself so I know what it's like. Having been working to improve on this issue, I think I'm in a good position now to say that it's bad idea. I can't quantify any specific LOC, or even a range as that will differ depending on your project. But ultimately having small functions that do one or two things and do it/them well is ideal. This points ties in well with everything else that follows.

### **Unit testing**

It's impossible to test something that you can't touch. If all of your logic is wrapped up into one function how can you test it? All of the data and logic inside of it is private (unless it's returned data but that still leaves things complicated).

With modularity this would be no problem. With your logic separated into separate modules and functions unit testing becomes much more possible. Now you can make sure that all components are working as intended automatically with tests, rather than manually trying out every feature multiple ways.

### **Readability**

Having tons of code in one place becomes hard to read over time. The less code there is in one place, the easier it is to read and reason with. Ergo it's easier to maintain, and the documentation becomes easier to write as well. Pretty simple.

### **DRY-ness/Re-usability**

These were going to be separate sections but they tie into each other so closely.

Having your code be modular means that it can be reused. If it's reusable then it's DRY code. DRY code is good code. If you can avoid repeated code, do it. It's better in the long run for, you guessed it, maintainability! Pretty simple. :D

> Sounds complicated…

It's not, I swear! It may seem easier in the beginning to just put everything in one place. I suppose it is when you're just getting started with coding. That's what I did. But in the long run modularity will make your projects much easier to maintain, test, document, and read.

I'm currently in the process of developing a web app, [which I'll be documenting here](https://medium.com/@PieceDigital/phase-1-planning-the-web-development-process-4f6d3db36503#.79wjlyjgm), or you can just [watch my Github repo](https://github.com/piecedigital/cashulator). I have plenty of documentation up already that you can read.

I hope you enjoyed reading this, and most importantly I hope it helped you. :)

_I'm a self-taught web developer from Virginia, USA.  
My stack is so MERN.  
I like JavaScript stuff.  
My website is __[here_](http://piecedigital.net)_.  
My Twitter is __[here_](http://twitter.com/piecedigital)_.  
My Github is __[here_](http://github.com/piecedigital)_.  
Follow me for more tech stuff 'n' whatnot._
