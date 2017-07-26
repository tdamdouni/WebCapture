# I Am Code and So Can You

_Captured: 2015-11-18 at 17:52 from [www.wired.com](http://www.wired.com/2013/12/i-am-code-and-so-can-you/)_

The Hour of Code is simple. Just go to [code.org](http://code.org) and click the START button. Yes, it is really that simple. There are quite a few tutorials at several different levels and in several different programing languages.

But the real question is: Should everyone learn to code? Let me ask a different question: Should everyone learn algebra? For the algebra question, I am going to say "yes". Maybe you won't use algebra in everything you do. However, algebra shows up in so many places it just seems silly to never study it. The same is true for coding - it's everywhere.

In science, coding is a very useful tool. Coding is another way to approach and solve problems. You can't really get too far into science (especially physics) without using some type of code. My favorite example is the three body problem.

Before looking at the three body problem, let me show you the two body problem. Suppose I have two stars that are gravitationally interacting with each other.

![Fall 13 Sketches.key 3](http://www.wired.com/images_blogs/wiredscience/2013/12/fall_13_sketcheskey_3.jpg)

> _Fall 13 Sketches.key 3_

This is a complicated problem, there is no doubt. However, there are some tricks that we can use to solve this problem on paper. Oh, by "solve" I mean find the position of both stars at any point in the future. But what happens if I add a third object?

![Fall 13 Sketches.key 4](http://www.wired.com/images_blogs/wiredscience/2013/12/fall_13_sketcheskey_4.jpg)

> _Fall 13 Sketches.key 4_

This is the three body problem. Three objects interacting with each other. You pretty much can't solve this problem on paper. Impossible on paper, but actually not too difficult with a computer program. There are many similar examples in science. We just can't do everything we want without a little code.

## Coding Homework

One of the problems people have starting to code is finding a purpose. You can't always jump into the coolest things to calculate and maybe you aren't inspired by a "hello world" program. Here are some ideas of fairly simple things you could work on (really in whatever language you want).

**The two trains problem.** Surely you've seen a boring problem that goes something like this:

The distance from Simpleton to Atlantis is 150 kilometers. Train A leaves Simpleton heading towards Atlantis with a speed of 50 km/hr. Train B leaves Atlantis at the same time towards Simpleton with a speed of 70 km/hr. At what time and location do the two trains meet? (if you want to spice it up, say that train B leaves 20 minutes laters).

How do you make a boring problem not boring? Use a brute force technique to solve the problem. It's really not too hard. Basically, you just calculate the position of both trains every minute (or second if you want to be more accurate) and then find the time that the two trains have the same location. Problem solved. It's not even cheating.

**Make your own Angry Birds**. This one requires a little more physics, but it's not too bad. The basic idea is to write a simple code that has a bird moving across the screen just like the real game. I wouldn't worry about it colliding with anything, that is much more complicated. Of course in this case you might want to use some type of language that makes drawing things easy. I would use [VPython](http://www.vpython.org) or [glowscript](http://glowscript.org/) just because I like them. However, the [Khan Academy Computer Science module](http://www.khanacademy.org/cs) is pretty easy to use also ([here is a tutorial I wrote some time ago](www.wired.com/wiredscience/2012/08/an-introduction-to-numerical-modeling/)). A couple other options, [Scratch](http://scratch.mit.edu/) and [Processing](http://www.processing.org/).

**Use a random number to estimate Pi**. The basic idea is to generate pairs of random numbers between 0 and 1 such that each pair forms a random point in a 1 by 1 box (with coordinates x,y). Some of these numbers will have a distance from one corner of the box less than a value of 1:

Now, if you look at the ratio of points that are closer than 1 away from the corner to the all the points, you can see it would form a picture sort of like this (you don't have to have your program draw the picture but it helps to see what is going on).

![On the 8th day  god Made pi   Wired Science](http://www.wired.com/images_blogs/wiredscience/2013/12/on_the_8th_day_god_made_pi_wired_science.jpg)

> _On the 8th day god Made pi Wired Science_

These blue dots form a quarter of a circle. So, the ratio of blue dots to total dots should be the ratio of the area of a quarter of a circle to the area of a square. I can write this as:

Calculate the ratio of dots, multiply by four and BOOM - you have pi. The more dots you use, the better your estimate.
