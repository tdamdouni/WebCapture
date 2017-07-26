# The Nine States of Design

_Captured: 2015-11-13 at 10:00 from [medium.com](https://medium.com/swlh/the-nine-states-of-design-5bfe9b3d6d85)_

Modern UI teams are designing components first; Interfaces are merely the thoughtful composition of components. This leaves an often glaring hole for users on "the unhappy path" -- The places where users may, intentionally or not, stray from your idealized flow. As we learn to craft systems rather than pages, we must invest effort into shaping these often missed states of design and create with a component lifecycle that can support everyone. Here's the lifecycle as I see it:

#### States

  1. **Nothing**

What happens _before_ your component does anything? Maybe it's the first time a user sees it. Maybe it's not activated yet. Essentially, the component exists but hasn't _started_.

![](https://cdn-images-1.medium.com/freeze/max/30/1*LNyqFzjiRNkqw186I2_YtQ.png?q=20)![](https://cdn-images-1.medium.com/max/800/1*LNyqFzjiRNkqw186I2_YtQ.png)

> _Jonas Treub makes sure framer gets you up to speed._

2\. **Loading**

The dreaded state. In a perfect world, no one would ever see this; Alas, here we find ourselves. There are plenty of ways to keep your loading state subtle and unobtrusive. Facebook does a pretty good job of this:

![](https://cdn-images-1.medium.com/max/800/1*TpIehvczESpOJD7yQ3HF2g.gif)

> _Facebook uses a "dummy post" rather than a traditional loading spinner._

3\. **None**

Your component has initialized, but it's empty. No data. No Items. Now may be a good time to get the user to act ("Do this thing!"), or to reward them ("Good job, everything is taken care of").

4\. **One**

You have some data. On an input, this may be after the first keystroke. In a list, it might be when you have one item (or one left).

5\. **Some**

This is usually what you think of first. What is the ideal state for this component? Your data is loaded, you have input, and the user is familiar with it.

6\. **Too many**

Woah there! The user has overdone it in some way. Too many results (maybe you paginate them now), too many characters (maybe ellipses?), and so on.

7\. **Incorrect**

Something is not right about the component. An error has occurred.

8\. **Correct**

Good to go! This item has had its needs satisfied.

9\. **Done**

The user's correct input has been received by the application. They don't have to worry about it anymore.

![](https://cdn-images-1.medium.com/max/800/1*r6NdBjvStCqOWe4orT7bNQ.gif)

> _Igor Chebotarev gives some positive feedback._
