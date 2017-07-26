# Waterfall model probably the most costly mistake in the world

_Captured: 2016-12-10 at 02:11 from [valueatwork.se](http://valueatwork.se/waterfall-model-probably-the-most-costly-mistake-in-the-world/?lang=en)_

![Waterfall model probably the most costly mistake in the world](http://valueatwork.se/innehall/uploads/2013/05/Realwaterfall-300x300_c.gif)

If you would guess how the worlds most used project model was developed. Would your guess be:

  * a) A group of researchers developed waterfall model and proposed it as the best option of existing methods
  * b) A group of practicioners innovated a method that became the most widely used model
  * c) A person copied a picture of a method that he understood and could explain and put it into a standards document

You might have guessed that neither a nor b are **correct** answers?

What happened was that [Winston Royce](http://en.wikipedia.org/wiki/Winston_W._Royce) wrote a recommendation about how large complex software projects should structure their process based on his experiences from NASA. Royce published the article in 1970 in [IEEE PROCEEDINGS WESCON](http://www.cs.umd.edu/class/spring2003/cmsc838p/Process/waterfall.pdf). Royce starts by describing for the reader a basic model of a development process that only has two main parts **Analysis and Development,** this would work for small routines and procedures but will not work for large complex systems. To deliver large systems there is a higher need to coordination and discovery that is needed which means many more activities are needed **System Requirements => Software Requirements => Analysis => Program Design => Coding => Testing**. Those activities became the wellknown waterfall model. Nowhere in the paper does Royce call that for the waterfall model , he even states that this way of developing software should not be done:

> **_"I believe in this concept, but the implementation described above is risky and invites failure." -Royce_**

What Royce recommends is detailed on the pages after the "waterfall model" in his paper and describes an iterative development process that relies heavily on prototyping before the "real" product is crafted. His final model is crafted to develop knowledge as quickly as possible and allow for fast iteration when we gain knowledge. (See picture below for the model that Royce rekommended).

![Royce SDLC model](http://www.valueatwork.se/innehall/uploads/2013/04/Realwaterfall-300x184.gif)

> _The sw development model recommended by Royce_

Royce paper and his ideas are not that spread or discussed until Department of Defence realizes that they need to standardise deliveries to the US defence forces and starts work on [MIL-STD-2167](http://www.product-lifecycle-management.com/download/DOD-STD-2167A.pdf). The MIL STD comes out 1985 and it requires that software development process is controlled by a process based on picture 2 from Royce paper. Thus the waterfall model is born and becomes the standard that all organizations must comply with if they want to deliver software to the US defence forces. Adoption of the waterfall model explodes and with this many models are created that build on the waterfall model. (V-model in Germany …)

Actually it does not take a long before the US DoD updates MIL-STD-2167 to recommend a more iterative or evolutionary model but it is too late for the rest of the world the model has gone viral. Thousands upon thousands of companies use the waterfall model or help other companies to implement it. It's interesting that today DoD recommends a iterative and incremential model for governing software development ([Read more](https://learn.dau.mil/CourseWare/46_5/images/dodi5000_2.pdf)).

One of the principal authors of MIL-STD-2167 has gone out and said that he did not have any experience of iterative or evoluationary development thats why recommeded a simpler model from Royce paper. When I was working in Washington DC I did hear second hand that he called it the biggest mistake in his entire career. I have not been able to find the interview where he says it so that is unsubstiated, see it as a interesting anecdote.

## Why did the waterfall model go viral?

There was a lack of easily understandable methodlogies to govern software development and almost every organization used their own way and their own terms for what is done when. Basically there was a vacuum and the waterfall model came in right time. The waterfall model is easy to understand -** as long as we finalize all of the work we can go to next stage and do our work there - The idea behind waterfall is so simple and superfically "logically sound" it basically creates its own gravitational pull.**

It is the simplistic part of the waterfall model that causes it to fail. Today we all know about Innovation processes, paths knowledge discovery takes and the need to iterate and that value flow is dependent on meeting Littles Law. But if you did not know any of that then the waterfall idea is very seductive and superficialy logically sound.

## Is waterfall really used today?

A model that experts did not support and it was removed from the standard where is was published - surely we are more knowledgable today and use better methods. Unfortunately - there are a lot of sharp and smart people that use it and actually you can still find research papers refering to Royce as the founder and advocate of the waterfall model. If you pick up project management books that are not from the Agile sphere I bet that you find some form of waterfall model described and prescribed. It has even been cemented as the Stage-Gate model by Robert Cooper that was a collegue of Royce at TRW. (more about stage gate model in a future write up)

Many project managers actually continue setting up projects accordingly to the waterfall model even if they are supposed to use iterative models like RUP  
The assumption behind waterfall model is that we can know all of the critical factors up front so we can do Big-Design-Up-Front (BDUF) and then continue but can we do that in the real world? Lets look at the surrounding world our projects operate in and use the [Cynefin ](http://en.wikipedia.org/wiki/Cynefin)Model by Dave Snowden to help explain it.

![Cynefin Model](http://www.valueatwork.se/innehall/uploads/2013/04/2011_cynefin-model-Ic-300x238.png)

> _Cynefin model by Dave Snowden_

If our projects can operate in varioius environments as described by the Cynefin model in the picture to the left then if the project is in the **Simple** environment. This is an environment where our surroundings are controllable and standardized we know what variabilities we have in our work and our knowledge is rich in this area. Then the waterfall model would probably work quite well and be efficient. This type of environment exists in manufacturing with few system level actors or maintenance work of an existing system.

As soon as we move to new product development that needs innovation to create value in the marketplace then we are in the areas of Complicated or Complex. Our knowledge of the domain is inperfect, we might not know how the state of art thing we create is going to behave in a complex system environment. We might not know exactly which combination of factors are important to the end users or customers so that we can capture the value in the market. We might not know how we are going to manufacture the product or service. All products and services that provide market value rely on some degree on innovation and this means we operate in the complex or complicated dimensions. If we would produce same product we did three years ago our customers would not buy it regardless how we motivate our decision to stick with something that is simple to create.

There are a lot of examples in the IT world in how we craft systems that end up causing a lot of problems. (Read [Javla Skitsystem (Damn crap system)](http://javlaskitsystem.se/) by Jonas Soderstrom and [amazon_link id="0672326140″ target="_blank" ]The Inmates are Running the Asylum: Why High-tech Products Drive Us Crazy and How to Restore the Sanity[/amazon_link] by Alan Cooper)

There is a consensus between researchers and practicioners that the core idea behind product development and new product development is to build domain knowledge fast and a lot of different methods are utilized to make that happen. There is a need to do both top-down and bottom-up work which iterates quickly to find risks and build knowledge and allow for course corrections. It is only possible work accordingly to state of art methods if your overall system allows it. In some cases the project control system creates articificial restrictions that hamper the effectiveness and efficiency of the project.

## Good things with the waterfall model - do they exist?

When discussing projects the following arguments are usually the main factors for using waterfall or stage gate:

  * We need a structure that explains how far we have progressed and what our current status is. I.e. Once we have passed Gate/phase x then we know that the following has been done ….
  * We need a mechanism to close down projects in our portfolio. Meaning that we need to reevaluate our business need and business case from a holistic perspective and we might need to close a project and give the resources to another project.
  * We need some mechanism to manage the financing of the projects. For each gate or phase we release more finances to the project.

All of the above mentioned things are valid needs, no doubt about it. No company operates without good control over their finances and how they are used.

### How does super agile and lean startups handle these questions?

I met [Bill Aulet (@BillAulet)](http://entrepreneurship.mit.edu/faculty/bill-aulet) (MIT Specialist and lecturer of Entrepreneurship ) at MITEDP this spring and got a view of how startups operate from the perspective of startups, venture capitalists and angel financiers. Even fastmoving startups must have rock solid control of their finances and must be able to explain to their financiers how far they have progressed in the commercialization of the idea they have, It is even so that some VC companies state that: "If a company uses waterfall or traditional stage gate processes we do not finance it or we bring in our own experts to change the way they work" . Or the in the words of Product Development Expert Eleine Chen (@chenelaine) "Waterfall? Nobody uses waterfall anymore, the costs are too high". Just to clarify her context for the comment was startup scene around Boston, she is well aware that waterfall is still used around the world.

> If your company is in market that has status quo and none of the competitors improve their product delivery process nor their innovation process then you will probably not need to improve. But for all other companies if you do not improve on both counts you will be roadkill

In summary startups have same need to keep their stakeholders and financiers updated with current status and understand which projects, subprojects or experiments should continue or be canceled. But the startups does not handle this through use of waterfall model in product development and gates for startups differs from how we normally see or use Stage-Gate. More about this in a later write up.

## Problems with waterfallmodell

It is possible to run any project accordingly to the waterfall model as long as you do not mind that it costs more and takes longer than alternatives. (if you operate in the complex and complicated dimensions)  
Often we notice first when we come closer to the deadline that we will run over time and budget - It is interesting to ask why is that a prevelent mode in waterfall projects?

The main dynamics behind the big problem with waterfall model is that it makes quality of the process and the product invisible this causes severe ripple effects where large amounts of rework must be done due to errors in requirements, specifications, designs and development.

### Two main operating modes of waterfall projects

1) If the amount of people and time is enough to absorbe both unexpected and unseen variation of the **Work to be Done** and **Identified Rework** then the project will deliver although to an higher cost than a iterative project. At the end of the projects timeplan the only remaining lever a project manager has to operate on is Quality. Often the steering group will authorize an exception from the launch quality criteria and start a project to clean up quality problems that will be discovered in production.  
2) If the variation of the **Work to be Done** and **Identified Rework** cannot be absorbed by the project schedule and the number of people working then it is really easy for the project to spiral out of control. Usually it starts by working overtime and bringing more people into the project both of these actions are well meaning but will cause further deterioration of quality and more rework.  
The main culprit is lack of feedback on many levels that would allow for learning, improving and proper steering of the project.

> Ignoring crucial feedback in your product development process is like driving through a city using a timeschedule of when to break and accelerate and not looking to see what happens on the street. If you are driving in a one street village you can succeed but I would not recommend that approach in Stockholm. - Rolf

Let us analyse the most common arguments for using the waterfall model .

  1. **We need a structure that explains to our stakeholders what our status is. **What happens is that the steeringgroups cannot determine if the requirements or specifications are complete enough to provide a good base for development to start. Most common is that the early phases get accepted with maybe a comment or two that some requirements are the incomplete and must be completed within a fixed timelimit. I propose an experiement - take your own organization if you run Stage-Gate or waterfall projects and investigate in how many cases a unsuccessful project was already flagged in the requirements or specification phase. It is more common that waterfall projects suffer from 90% syndrome, i.e. "we are almost done". So as a status mechanism there is a lot of improvement potential.
  2. **We need a method to prune our project portfolio.** If we have a strategic decision to take about resources then that decision should be taken as soon as possible and not to wait for a Gate or Phase review. If it is a question about the project not providing expected financial or market benefits then the early phases most often will not provide enough knowledge about the cost of the latter phases waterfall model in it self fails as a good mechanism here. If the case is that the surrounding world changes so that the market no longer needs the product then the project should be closed down asap and not wait for a gate or phase review.
  3. **We need a mechanism for financing of the project**. Meaning that we want to balance project risk. I.e. we provide more finances to the project that is on track to deliver to the market. The reasoning is the same as in bullet point 1. We do not know for sure how much rework and quality issues we have and what the final cost will be before we start testing. There are numerous examples from vehicle and airplane industry where complex projects overshoot the budget and timeschedule with 300-400%.

##  The secret behind 300-400% improvement - drop the waterfall method

In Systems Thinking it is normally regarded that the greatest leverage point exists when we change our views about the world, when our mental models about how the world works changes we can almost at once see different ways of solving a problem which was deadlocked earlier.

You will never know how much work has actually be done nor the quality of the endresult or your process quality by creating documents and reviewing them. You need to investigate the endproduct and its behaviour. To do this your development effort should be pulled by Integration events over the project lifecycle.

Integration events as pull-events is the main difference but there are other methods that will build knowledge faster than waterfall method. One such method is Set-based development and while it has not really gotten traction in the software development camp yet it is coming. Set based development is to build knowledge up front by creating and designing multiple solution/design alternatives from the start (remember we know the least when we start our project and this method will allow us to keep some important design options open until we have gained enough knowledge to decide). Then you find quick and fast ways of closing down alternatives and each intergration event will close further alternatives.

One of the largest european banks used set based design to develop one of their more innovative services and it was crucial to the market success that followed.

In Sweden it is within the industry sector where these methods are used in companies like; Scania, Volvo, Ericsson and that is thanks to the Lean Product Development (LDP) movement in Sweden. On the software side the Agile camp has done a lot to move away from waterfall but when it comes to portfolio and program management and knowledge building for improved innovation and performance there is a lot to learn from the LPD movement.

## Try it out yourself - Simulate

You can test and experiment to see the dynamics and the results in going from a waterfall lifecycle model to an iterative model. I have published a simulator that builds on research done by System Dynamics scientists at MIT. The simulation model has been validated enough so it was used in US courts to determine how responsibility should be divided between the vendor and the customer for some of the largest defence projects that overran the budget. Recently the model is used by a technology company to start, monitor and manage projects differently with extremely good results (1.3 Billion US $ in savings thanks to a more fact based approach of running projects) I mention all of this so you have some background information about the simulation before you use it.

This is a good showcase of the advanced simulations we use in our project dynamics, improvement and systems thinking classes. Please note that you cannot use the simulator to determine exactly what results your company would get since I have locked down a lot of the parameters it can be used to learn about the dynamics and the relative sizes of changes to results when structure of working is changed.

You only need to change one variable when you run the simulation, keep everything else as default values. To discover what effect integration events would have on a project we will change "**Maximum Time To Discover rework**" this symbolizes that we have iterations with same lenght as Maximum Time to Discover Rework is set to. (i.e we do requirements, design, specification, development and testing within that space of time)

![Project Setup for simulation](http://www.valueatwork.se/innehall/uploads/2013/04/ProjectSetup-300x171.gif)

> _Step 1 - Project Setup Only change "Time to Discover Rework"_

![Step 2 - Dashboard run the project and check results](http://www.valueatwork.se/innehall/uploads/2013/04/Dashboard-300x172.gif)

> _Step 2 - Dashboard run the project and check results_

Run the experiment with these three cases;

  1. Max Time to Discover rework = 12 manader (Symbolizes waterfall case)
  2. Max Time to Discover rework = 6 manader (We use integration events to discover our progress and quality)
  3. Max Time to Discover rework = 3 manader (We have even more frequent integration events)

If you do want to know what the results are without running the simulations you can find them in the table below.

Scenario Time to discover rework Cost Time to Finish

Waterfall
12 months
953
88 months

Integration pull events 6mo
6 months
565
55 months

Integration pull events 3mo
3 months
318
34 months

As far as I know it Integration Events for large complex projects comes from Harley Davidson. Harley Davidson made an inprovement journey, from a Time to Market of +72 Months (Pure waterfall in 2001) to a Time To Market of 28 months (Frequent Integration events by 2006). There is an excellent book by Dantar Oosterwal that describes the journey that Harley Davidson made and how they used systems thinking to accelerate their improvement journey.  
[amazon_enhanced asin="0814413781″ /]

_With this simulation I wanted to show the effect of integration events, in a real situation a project that discovers they are going to be late will take action but is is not those dynamics we try to show and understand here. _

##  New thoughts

My hope is that you have discovered that there is alternatives to Waterfall and Stage Gate regardless of what industry sector you work in . That you know know that the waterfall model contributes in a best case to an unecessary waste of money and time and in a worst case scenario a huge quality problems combined with going over the budget with hundreds to thousands of percent. Before all I hope you continue to think about why and how things work as they do in your organisation and in others - that is a good way to gain deeper knowledge. Sometimes we have gotten incorrect and faulty information that we base our mental models on and if we can spot those mistakes our actions will be more successful in the future.  
The waterfall model became a meme in the software industry even though numerous experts have spoken and acted against it but the underlying mental model has often not changed when project managers versed in the waterfall method started using iterative and incremental models like RUP and others. Today Agile models are mainstream but still there are a lot of controversy and positioning. Situation is quite interesting since everyone basically wants to help the organisation to succeed with the projects, nobody plays this game to lose. In some cases the stalemate comes from the fact that the discussion has transformed to a conflict of values and the discussion is sometimes far removed from the facts or the facts are perceived differently. What we need is a deeper understanding of project dynamics so that we can discuss and understand the applicability of principles, rules and guidelines.

## Cost of waterfall in Sweden = 4479 Billion SEK

Lets do a simple thought experiment. The picture below shows the Swedish Gross National Product development from 2000 to 2012 from Swedish Ekonomifakta (Portal about official Swedish economics data). Ekonomifakta calculated that between 10%-20% of the GNP is invested in projects.

This calculation is only done to show the magnitude of the problem so it is simplified a lot.  
Lets say that 20% of GNP is invested in projects each year from 2000 to 2011.  
All projects are waterfall projects or limited by stage gates.  
All projects can be executed with one third of the budget of a waterfall project

Then out of total project investments between 2000-2011 we waste 4479 Billion SEK compared to a reachable optimum state. Simplistic but interesting to think about the improvement potential.
    
    
    (Note: In real life some projects will not be able to realize such benefits due to other constraining factors and it would take several iterations of projects before enough innovation was made to capture the potential value. This though experiment is more to show the magnitude of unrealized potential)
