# Design Patterns — Coming Full Circle, Part Two

_Captured: 2016-03-23 at 15:14 from [medium.com](https://medium.com/swlh/design-patterns-coming-full-circle-part-two-ced2c69e4724)_

![](https://cdn-images-1.medium.com/max/2000/1*jCJClUq_h15C9j0XOWZ5iw.png)

_This is the second of a two-part series related to design patterns in architecture, software engineering, and our work at Flux. You can check out Part 1 here:__[ Architecture Inspires Software: Design Patterns_](https://medium.com/@flux/design-patterns-coming-full-circle-d8292e261dc6#.kv1aoix04)

Today, designers and architects around the world are methodically, steadily, and admirably grinding out solutions to very real and important problems associated with meeting the needs of an increasingly crowded, resource depleted planet.

At their core, the vast majority of modern building design projects share more similarities than they do differences. Here at Flux, we wondered how much more progress could be made if design firms and architects around the world were able to spend less time solving the same problems over and over again and more time focused on addressing the truly unique aspects of each project. Specifically:

What if we were able harness the collective wisdom and knowledge of the global AEC community?

What might our world look like if the AEC industry were to embrace the notion of design patterns?

#### **_Part_** **_Two: _The Flux Patterns**

As a software engineer, I am constantly on the lookout for patterns in the world around me. It gives me a little thrill when I discover a pattern that exists between two seemingly disparate scenarios in my day-to-day life.

For example, I recently noticed a pattern that draws from one of my favorite pastimes -- skiing at Lake Tahoe -- and an activity I despise -- driving to Lake Tahoe.

During a ride on the chairlift, I looked down and observed that the skiers all tended to pass each other on the left; just as they would if they were driving a car.

It occurred to me that whether we are speeding down the highway in a Subaru or hurtling down a mountain with two planks strapped to our feet, people (whether they are aware of it or not) tend to follow the same pattern when passing each other -- on the left.

**Observing. Listening. Learning.**

Patterns abound in the world around us -- in nature, human behavior, music, politics, urban planning and yes, in software design. Any lover of patterns almost certainly is very observant because identifying patterns comes down to exactly that -- listening, watching, and being attuned to what's going on around us.

At Flux, we are very observant. In particular, we are good listeners. As a company focused on developing solutions for the AEC industry, we've spent a tremendous amount of time meeting with and listening to a wide variety of building industry professionals, including computational designers, architects, engineers and general contractors.

Interestingly, as we spent more time listening to the concerns and frustrations of each group, a clear set of common pain points began to form. We have realized that although their daily tasks and responsibilities appear on the surface to be very different, at a very fundamental level, the problems that each face are actually very similar.

The learning obtained from these meetings -- and the shared pain points that we have uncovered -- are what drives our work here at Flux. So, inspired by the work of [Christopher Alexander and the Gang of Four](https://medium.com/@flux/design-patterns-coming-full-circle-d8292e261dc6#.kv1aoix04), here's brief look at the "Flux Patterns" we have identified as common pain points for the AEC industry.

#### Pattern #1: Embrace Heterogeneous Tools.

_Problem:_ No single tool can do it all.

_Pattern Opportunity: Embrace the use of heterogeneous tools._

> _"It slices, it dices. It makes julienne fries! But wait! There's more…." (Ronco Veg-o-Matic)_

![](https://cdn-images-1.medium.com/max/1200/1*cAUG2o-IXMaWPbdd7S0bMg.jpeg)

> _Veg-o-Matic and derivatives_

Inherently, we know that the best way to get a job done is by using the right tool for the job. Any cook will tell you that they would much rather have a high quality chef's knife, sturdy spatula, and mandoline slicer in their kitchen rather than a seemingly catch-all kitchen appliance. (Sorry, Veg-O-Matic.)

In the same way, design teams should be empowered to use the best tool for the task at hand -- not settle for something that someone else thinks is probably _good enough_.

On any building project, designers rely on dozens of purpose-specific tools. Unfortunately, very few of these tools do a particularly good job of communicating with each other. This hurts productivity and is a major source of frustration throughout the industry.

Rather than forcing designers to select a smaller number of tools or try to coerce their tools into doing things they aren't particularly well-suited for, industry professionals should focus their energy on finding a way for tools to communicate better.

This concept is at the heart of Flux's work. By developing plugins for the most popular design tools and creating an open C# and JavaScript SDK, Flux is providing a conduit for information sharing.

![](https://cdn-images-1.medium.com/max/800/1*_2YpljD72Qx0eSdd85lAqw.png)

#### Pattern #2: Exchange Data, Not Files.

_Problem:_ Most tools share data by importing and exporting entire files.

_Pattern Opportunity: Exchange data, not files._

Rather than sharing whole files, tools should be able to extract only the relevant data needed for the specific job. Treat each piece of data as an atomic object, decoupled from everything else in the file. Files from one tool nearly always contain extraneous information that is irrelevant for another tool. The process of importing and exporting files also loses fidelity.

![](https://cdn-images-1.medium.com/max/800/1*1xTHRHTrs7N7aTUYZCQOLQ.png)

> _Extract only the data that is relevant_

#### Pattern #3 Fresh Data is the Best Data.

_Problem:_ The "model" of a building project is typically composed of multiple files from different programs, from different dates and times, from different teams. As a result, versioning headaches are common, and it is incredibly difficult to keep track of what the original 'source of truth' was.

_Pattern Opportunity: Fresh data is the best data._

Instead of exchanging and piecing together information from multiple static files, shift towards exchanging dynamic data in real time. Keeping track of the latest information and identifying the 'source of truth' becomes a much simpler process.

Atomic data sent to a central repository can be accessed by everyone on the project team and becomes the universal source of truth for the project.

#### Pattern #4: Transform to Fit

_Problem:_ Due to the heterogeneous nature of the design tool landscape, the same concept is often represented in different ways according to the language of that tool. i.e. the concept of 'wall' is represented differently in Revit than in it is in IFC or GBXML.

_Pattern Opportunity: Transform to Fit_

In software engineering, when data is sent in one format and needs to be consumed in another, a typical approach is to build an object that identifies and then adapts the incoming data into the appropriate format for consumption.

This is referred to as the _'adapter pattern'_ and is used to create either a 1-to-1 or a 1-to-many adaption. Here at Flux, we've developed a graphical programming environment called the Flow to transform incoming data into other various formats using a set of utility functions provided in operating environment.

While it's true that a square peg might not (initially) fit into a round hole, it can be transformed using the right tool to whittle down the edges and make it round. The Flow is an ever-growing toolbox for software developers to make the same type of transformations to their data.

#### **The Road Ahead.**

Have you recognized a pattern in your own work or the work of your colleagues? How many times did you see it before you recognized it as a pattern? Have other people observed the same thing?

Developing a set of patterns, whether for design or for process, is necessarily an iterative and a collaborative effort. Your ideas, input, and feedback are all critical, and we hope you join us in these explorations!

[Learn more about our interoperability tools on our homepage](https://flux.io/), and[ sign up](https://flux.io/signup/) to try Flux on your own project.

Then, tell us about the patterns that _you_ discover.

_-- Jen Carlile, Co-founder, Software Engineer, Flux.io_
