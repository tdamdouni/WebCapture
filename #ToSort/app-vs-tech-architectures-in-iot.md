# App vs. Tech Architectures in IoT

_Captured: 2017-04-19 at 08:46 from [dzone.com](https://dzone.com/articles/app-v-tech-in-iot)_

When we talk about architecture, we usually don't know what we're talking about.

Not that we don't know the design we're discussing or the way we want to organize the technology in a system. No, this we usually have a good handle on -- the problem is that we don't really have a rigorous definition of what _architecture _really is.

There's a few different kinds of architecture that are accepted today -- application, technology, and data architecture. Technology and data architecture are pretty easy to differentiate, in that one deals with the technological design of a system, and the other the organization of the data in the system. Certainly related, but relatively easy to differentiate.

But what about this application architecture thing?

Application architecture (I frequently refer to it as systems architecture too) addresses how the specific functionality of the system is going to be partitioned. This is in many ways a functional design, rather than a technical design, and avoids touching on technology topics as much as possible. You may not be able to completely avoid technology in your application architecture, and the technology you have available may very well influence your functional design a bit, but you should try to keep them as decoupled as possible. The application architecture is longer lived than technology architecture usually, and you should be able to plug different technologies into your application architecture as needed. Overall, you need both, but it's important to understand what the differences between the two are. The best way to understand the differences is via an example.

Let's pretend that we're building a smart thermostat, a really simple one. This thermostat needs to handle two different setpoints, be remotely programmable, and use wifi networks. We'll focus on the software in this system rather than the hardware used for simplicity.

Functionally, we have an input from a thermocouple and an output to a heater. We will also support input from an external service that allows us to remotely program the device.

![Image title](https://dzone.com/storage/temp/4984715-app-arch.png)

We'll call our new thermostat the Ultra TStat-1000, as it will surely dominate the market. So from an application perspective. we can organize the system like we see above. We have to save some data, specifically the set points, and we'll do that in a data repository. We also have some process logic, to manage the actuation of the heater based on those programmed set points and information from sensors. The set points themselves are read from an external source, over an attached Wifi network. This is the application architecture - we have defined the system functionally, but we haven't mapped any specific technology into the device.

![Image title](https://dzone.com/storage/temp/4984723-canvas-2.png)

Once we've defined the application, we can begin to look at specific technology. Here, I've labeled the functional components with technology stereotypes. Specifically, we'll use files for data storage, an embedded Linux OS, and we'll encode the process logic in C as a daemon process. We'll furthermore use driver software to read from the sensors and control the heater, and we'll communicate with external services using REST and JSON over HTTPS.

Now that we've defined our application architecture separately from our technology architecture, we can substitute specific technologies for others as long as they still address our application needs. For example, we could replace our file-based storage with a small database, or REST/JSON with protocol buffers. And we can do this without affecting the overall functionality of the system.

Application and technology architectures are really distinct things -- and understanding how they differ will make you a better architect and designer.
