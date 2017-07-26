# Turning the iPhone 6s Into a Digital Scale

_Captured: 2015-10-30 at 11:06 from [medium.com](https://medium.com/swlh/turning-the-iphone-6s-into-a-digital-scale-f2197dc2b6e7#.5cspvc8cj)_

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*3piiaM6_gCaBeyovLHhS9A.gif)

The iPhone 6s is announced and its brand new pressure sensitive hardware is unveiled. A simple but slightly vague API doc is published soon after. The question of calling the feature Force Touch or 3D Touch remains unresolved.

### September 12th, 2015

![](https://d262ilb51hltx0.cloudfront.net/freeze/max/30/1*ZDAey6AFQo9Eq-mSk9_VxA.png?q=20)![](https://d262ilb51hltx0.cloudfront.net/max/800/1*ZDAey6AFQo9Eq-mSk9_VxA.png)

My friend Chase McBride calls with a few _tech questions_ (rough translation: _startup idea_). Chase and his friend Brice Tuttle have been talking over this idea of a scale app using 3D Touch. It's the first I've heard of the idea. A quick peek through the APIs showed that we wouldn't be able to simply place anything on the screen and get a _force _value. The only App Store friendly way to get a force value would be by touching the screen with a finger and even then the force returned would be the force directly under the finger.

We're on the phone talking through this initial hurdle, when my excitement turns to concern. I start recalling other times Apple hasn't exactly been stoked on novel uses of their devices' sensors, but then I remember that despite this the App Store is speckled with creative workarounds including [a panorama app that uses vibration to rotate the phone](https://www.youtube.com/watch?v=tTMxyNyTsAY), [magnetometer-based stud finders](https://www.youtube.com/watch?v=3DYbELuz36g), [camera/flash-based heart-rate monitors](https://www.youtube.com/watch?v=bnw4_b1Rbz4), and even [Square's ubiquitous headphone-jack card reader](https://squareup.com/reader). A creative solution is waiting to be found. Creating a scale turns from impossible to a challenge.

### September 21-24th, 2015

At this point we know that the force value returned is a float in the range of 0.00 to maximumPossibleForce (with 1.00 being an average touch). We still don't know how to trigger a touch without a finger, but we have a few ideas.

I have a 5s I love, but decide if this is going to happen I need to preorder a 6s. We have roughly five days until the phone is in my hands, so what can we do in the meantime? We need to build a barebones testing app to hit the ground running and we need to come up with a way to weigh objects without touching the screen. Without that, we'll be dead in the water.

With Chase and Brice in San Francisco, and me in San Luis Obispo we hop on FaceTime to channel our inner MacGyver and brainstorm a solution. We tried foil, watch batteries, apples, carrots, coins, even salami-- at one point we had built a meat basket out of a piece of salami stuck to a jar lid with a needle as a conductive handle (pictured below). None of these solutions fit the trifecta of being convenient, common, and non-perishable.

### September 24th, 2015

#### iPhone due to arrive tomorrow

As funny as the salami basket was, blindly coding something that seemed doomed to a greasy click-bait headline was burning up my morale.

We thought through the problem again: **we needed an object that was conductive, had finger-like capacitance, formed a single finger-like touch point, was a household item, and could hold items to be weighed…**

Conductive, capacitive, common, and curved to a single-point of contact.  
**A spoon was the perfect solution we had been looking for.**

![](https://d262ilb51hltx0.cloudfront.net/max/600/1*wuHz95IHAUQQ_TLFYtko2Q.png)

### September 25th, 2015

Every car that drove by induced a mild panic attack. None of them were brown. When the UPS man finally arrived around dusk he barely made it across the street before I traded him my squiggle signature and ran back inside. 100g calibrated weight, jar of change, and digital scale all laid out in preparation, I download the test app and begin recording the force values of different number of US nickels (~5g each) on a metal spoon.

> "Dude. It's perfectly linear"

With the force values linearly correlated to weight, turning any force into a weight was going to be as simple as recording the force of known weights and creating a linear regression. It'd even be possible to use some statistics to predict how well the calibration went (there are many factors that can throw off a calibration). We opted to use coins for calibration, with a framework that made it easy to internationalize in the future.
