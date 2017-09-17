# Can a Drone Carry a Full-Grown Human in a Hammock?

_Captured: 2017-09-10 at 19:26 from [www.wired.com](https://www.wired.com/story/can-a-drone-carry-a-full-grown-human-in-a-hammock/)_

I have many jobs, but one of my favorite is finding crazy stuff on the internet and using physics to see if it is [real or fake](https://www.wired.com/2014/10/physics-fake-videos/). In this case we have a video that shows a drone carrying a human in a hammock. I'll go ahead and say it--this is probably fake.

### The Physics of Drones

You can't tell if the video is real or fake without first understanding the basics of drone flight. In particular, we need to look at the physics of what makes a drone hover. When you think of a drone, most people picture one of these remote controlled vehicles with four or more rotors (a quadcopter). Technically, a drone could have any even number of rotors instead of just four ([you need an even number in order to easily maneuver](https://www.wired.com/2017/05/the-physics-of-drones/)). There are fixed wing drones, too--but those aren't very popular.

Let's focus on the rotor-based drones, though. Their key to lift is their rotors' thrust: A rotor's main job is to take air from above the aircraft and push it down at some speed. Let's imagine that in some short time interval, the rotor takes a cylinder of air above (that was initially at rest) and gives it some final velocity moving down.

This mass of air depends on both the air's density and the size of the rotors. Bigger rotors means a greater mass of air. Since the air gets pushed down with some velocity, it increases in momentum--momentum being mass multiplied by velocity. According to the momentum principle, you need a force to change an object's momentum. So, there is a force pushing down on this air in order to "throw" it down. Since forces are an interaction between two objects, the rotors pushing down on the air means the air pushes up on the rotors. If this upward pushing force is equal to the weight of the drone, then it will hover. It's simple physics made complicated.

In the end, the total rotor area is very important. For a given drone weight, you could either make a larger rotor (or more rotors) and push the air down at a slow speed, or you could make a small rotor and push the air down at a fast speed. It would seem like you could use any size rotor you like--but that's not practically true.

Clearly you need a particular force in order to hover. But it's more than just the force that matters--it's also about power. Here I am using the physics definition of power, which is the rate that energy is used. Yes, it takes energy to increase the speed of this air. The air starts from rest above the rotors but then has kinetic energy below. This energy depends on the mass and the velocity of the air. I'll skip all the details and just share this expression for the power needed to hover based on fundamental ideas such as momentum and energy.

In this expression, the power (P) depends on the density of air (ρ), the rotor area (A) and the air speed (v). If the aircraft is hovering, then there is a relationship between area and air speed such that I can calculate the power needed to hover. OK, I admit that this expression might seem crazy since I really don't know much about helicopters and aerodynamics of flying things. However, I _do_ have access to [Wikipedia](http://www.wikipedia.org) which lists lots of different helicopters that should be able to hover. It also lists the rotor size, the engine power, and the weight. That means I can calculate the theoretical power based on my fundamental physics principles as well as the listed power. Here is what I get.

What does this graph say? It says that there is indeed a relationship between the calculated power and the listed power. It says that my power calculation isn't completely bogus. So let's use it.

### How Much Can a Drone Lift?

Theoretically, a drone could lift any amount no matter what size rotor it has. But on a practical level, there are two limitations. First, the maximum air speed is probably around 40 m/s (based on my calculations for the [physics of the S.H.I.E.L.D. Helicarrier](https://www.wired.com/2012/07/could-s-h-i-e-l-d-helicarrier-fly/)). Second, if the drone had a power of something crazy like 1,000 Watts, it wouldn't be able to fly very long.

Using my Google-fu, it seems like the drone in this video might be a [DJI-S800](https://www.dji.com/spreading-wings-s800/spec). From the quadcopter's diagram, I get a rotor radius of 0.188 meters for a total rotor area (6 rotors) of 0.67 m2. Assuming a total drone plus human mass of 70 kg I can first calculate the required thrust speed in order to hover. With these values I get 43 m/s--that seems plausible. Now for the power, I get 14.8 kilowatts ([you can see my calculations here](https://trinket.io/glowscript/40efa2b719). A power of 14.8 kilowatts is sort of crazy high. A normal-sized house could probably get by with less than 3 kilowatts. Just saying.

Notice if you replace the human with a dummy that has a mass of only 5 kg, then the power drops to 280 Watts--that's much more reasonable. The video seems to obviously be a dummy instead of a human, but the other alternative would a completely digital drone added onto a real video. But in the end, it's fairly easy to crunch the power numbers for different masses since I used a Python program for the calculations. [Plain calculators are dumb](https://www.wired.com/story/ditch-that-fancy-scientific-calculator/).

### Maybe This Drone is Real

Here is one more drone with a human (but not in a hammock). This one is probably real.

What's the difference between the hammock drone and this one--other than the hammock? Yes, this second human flying drone has a _much_ larger rotor area. I'm not going to calculate it, but I wouldn't be surprised if it was around 4 m2. A larger rotor area means lower thrust speed which means a lower power consumption. In fact, if I change my calculation above to include this rotor area, I get a thrust speed of 16.9 m/s and a power of 5.8 kilowatts. Yes, that's still a large power--but it's significantly lower than the hammock drone. Bigger rotors are better.

Gadgets

DJI's latest batch of quadcopters lets users get sky-high while capturing hi-definition photography and video. Take a look under the hood of DJI's Phantom 2 Vision+ and Inspire 1 to see how the technology and advanced features are allowing for a bird's eye view that was previously reserved for, well, birds.
