# How BB-8 Works

_Captured: 2015-12-28 at 14:35 from [techcrunch.com](http://techcrunch.com/2015/12/22/how-bb-8-works/?sr_share=facebook#.umka58:zU3v)_

![](https://tctechcrunch2011.files.wordpress.com/2015/06/469979416.jpg?w=738)

By now, there's a pretty good chance that you've seen the new Star Wars movie -- and for those who haven't, don't worry: no spoilers here. At long last, we've got a much-needed dose of Starfighters, Rebel Alliances, Lasers, and _droids_. BB-8, the adorable successor to R2-D2, has captured hearts and minds. As lovable as it is, and even with as much life as its creators managed to instill into it, in the end… it's a super sophisticated prop. And now you're wondering: _how the heck does this thing work?_

While JJ and Co. have kept the specifics of BB-8's innards _mostly_ under wraps, we can suss out the basics. Behind that trilling orange and white sphere, BB-8 is likely a set of wheels (propelling the sphere by spinning against its inner-wall) and a magnetic mast (to hold on to and control BB-8's head). The sort of "wobbly" way BB-8 moves? It's all inherent to the design -- what might be considered a flaw if used anywhere else, here it helps to give BB-8 much of its character.

**That explanation will leave a lot of you wanting for more. Want a more detailed breakdown than that? Read on, folks.**

A lot of the analysis you see on the internet today has people treating BB-8 as two discrete operations, one each for the head and ball. However, one of the many patents filed by Disney and partner Sphero paints a different picture. [This patent,](http://docs.google.com/viewer?url=patentimages.storage.googleapis.com/pdfs/US20140345957.pdf) for a "Magnetically coupled accessory for a self-propelled device," explains how to get BB-8 to work without a separately controlled head. Combine this with Sphero's Chief Scientist Adam Wilson [telling Polygon.com ](http://www.polygon.com/2015/9/7/9272595/how-bb8-works)that the head isn't articulated independently, and you can start to paint a picture of what the internals look like.

The strongest justification for this kind of system is in watching BB-8 try to lean over. It doesn't seem to be able to maintain a constant head angle while static. This strongly implies that the head isn't articulated independently, and is consistent with the patent.

**Let's get things rolling**

The head complicates things, so let's just think about the body for now. An image from one of the patents is an extremely helpful illustration. To make things simple, let's think about this problem in two dimensions, looking only at forward and backward motion. The same principles apply to keep this stable; all that's happening when BB-8 turns is the internal assembly yawing to point in a different direction.

In a nutshell, what we've got is a sphere with wheeled mechanism inside it. The wheels are forced down against the wall of BB-8 in some way (either spring or gravity, it doesn't matter a huge deal). Rotating the wheels shifts the center of the system's mass, the bulk of which is in the wheel assembly, off of the vertical line that includes the center of the ball and the contact point with the ground. Leaning generates a moment. Do this right, and the ball moves in the direction that the wheels were shifted to. If we were to picture a mast mounted perpendicularly on top of the wheel base, the ball would move in a direction opposite to the mast.

![patentgrab_wheel](https://tctechcrunch2011.files.wordpress.com/2015/12/patentgrab_wheel.jpg?w=1024&h=743)

> _Image: United States patent application_

In broad strokes, this is similar to what it's like to get a Zorb ball moving. Being the heaviest thing in the Zorb, moving forward changes your position relative to the ball's center of mass. This, in the end, leads to rotation and forward motion. (We're not going to go over the dynamics of this problem, but reach out if you really want to know).

![zorb](https://tctechcrunch2011.files.wordpress.com/2015/12/4761405338_8ec5d50b01_o.jpg?w=1024&h=819)

> _Image: Flickr/Damian Cugley under a CC by-SA 2.0 license_

**A head for math**

That mast we talked about earlier? That's where BB-8's head goes. Since it's attached to the mast through the sphere, it makes sense that it would be attached magnetically, as the patent dictates. There are lots of ways to do this, but one that lets BB-8 bounce and still function like it does in the movie involves a set of attractive and repelling magnets. Repulsion probably keeps the head from contacting the ball, and magnetic attraction around the edges of the head keeps it from rolling off.

![bb-8-3](https://tctechcrunch2011.files.wordpress.com/2015/12/bb-8-3.png?w=1024&h=576)

> _Image: Bryce Durbin_

Earlier, we went over how to get BB-8 to move if you wanted the mast (and therefore the head) to point in the direction opposite to motion. Through most of the movie, though, you see that BB-8's head is tilted in the direction of motion. We also know that the head can't move separately. So, how does this work?

![giphy \(1\)](https://tctechcrunch2011.files.wordpress.com/2015/12/giphy-1.gif?w=560&h=315)

> _giphy (1)_

Again, BB-8's floppy motion tells a lot. Notice how before BB-8 starts moving forward full tilt, there's a brief period when it's moving with the head almost rolling backward? Applying some dynamics to the problem helps explain what's going on.

To clear things up, I don't think that this is an inverted pendulum problem, even though it's easy to draw some comparisons. However, let's pull one concept out from the typical inverted pendulum problem that you go over in school. To get the inverted pendulum's shaft pointed in the direction of motion, you first have to move the system backwards a little bit, let the shaft fall into place, and then reverse the direction of motion.

![](https://tctechcrunch2011.files.wordpress.com/2015/12/bb-8-4a_rev.png?w=2000&h=1125)

> _Image: Bryce Durbin_

Similarly, I suspect that the brief period of minimal motion when the base is moving but BB-8 as a whole isn't is doing something similar. It's likely that BB-8 gets into motion slowly (without a noticeable backward head shift). Then, by slowing the motors down, the head is allowed to roll forward. Once the head is pointing forward, you can resume the motors and get that nice full-tilt roll that's shown in the movies. Alternately, it's possible that the motors drive the mast forward, letting the ball move backwards, and then the motors maintain constant angle as BB-8 moves forward. If the mast and wheel assembly have enough inertia relative to the rest of the system, you wouldn't need more than a tiny initial motion before getting started.

All this is easier said than done, though. The control law and sensor suite running all this has to be incredibly sophisticated - making running BB-8 as much of a software problem as it is a hardware problem.

**Calibration is Key**

Since your entire operation depends on knowing the angle of offset from vertical (θ), your control system needs to be able to measure this to extreme accuracy. This is perhaps why we saw BB-8 needing to be calibrated when TechCrunch's Lucas Matney [played around](http://techcrunch.com/2015/09/03/sphero-bb8/) with a scale model toy earlier in the year. All this feeds into what you call a closed-loop control system, which maintains the angle (θ) of offset from the center at whatever value you set it as. This value is set by the software depending on how fast you want BB-8 to go.

All this being said, this system does mean the BB-8 comes with some handling restrictions. Really, it would have been simpler to just use the two-system method that other analysts predicted. I can see why the designers wouldn't have done that, though - _it's just less cool_. A lot of this is in broad strokes based on what we can get from video and patent filings. It's possible that I'm entirely wrong and BB-8 does something else_._

Featured Image: Alberto E. Rodriguez/Getty Images
