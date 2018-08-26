# Programming BS: Spaghetti Code

_Captured: 2018-03-16 at 13:18 from [dzone.com](https://dzone.com/articles/programming-bs-spaghetti-code?edition=368203&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-03-16)_

Container Monitoring and Management eBook: [Read about the new realities of containerization.](https://dzone.com/go?i=274432&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fcontainer-monitoring-and-management.html%3Fcid%3DNA-DSP-APM-AEJ-000195-00001663-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_eb1-container-monitoring-mgmt-articlepreroll%26mrm%3D)

There is no excuse for having a spaghetti code project. A project can fit a reasonable schedule, satsify unforseeable requests, be well architected, and well written without ever being spaghetti code at any point. On a scale of 1 to 10 where 10 is perfect, a project can hover around 7-9 throughout its lifetime and still meet demands.

Spaghetti code is BS!

## **A Bad Example**

When I first joined my second employer, I discovered fairly quickly the project had a landmine quality about it--I just never knew for sure when fixing a bug for a certain screen, what other seemingly completely unrelated screen would blow up as a result of my fix. Within two months of being there, I discovered the testers were doing 40 hours of testing for every single code change, even if it was just one line! If I recall correctly, there were three full time testers for three full time developers. Did you see the several problems the business was experiencing in this paragraph?

After two months, I did some analysis on why the code was so awful. I decided to present my findings to the manager in ordinary human speak, not geek speak, as I was quite sure he had never written a line of code. At this point, I had two years and two months of industry experience, and really didn't want to do this, but felt I had to. The code was holding the company back, and they needed to deal with it. I did it as politely as I could figure out how to do, without blaming anyone. Essentially, I made a business case.

About two months later, the company hired a new chief architect. They didn't have anyone by the title before, and this was an additional hire, not a replacement. He said fairly quickly the code was crap, and started working on the details of a rewrite.

## **A Good Example**

Fortunately, I worked on a project for 5 years--from inception until a rewrite started--and it was never spaghetti code. I would say, "It'll take X amount of time to make the required changes," and almost always take X or less time to do it, where X was never purposely over-inflated by a Scottie-like factor of four. So did others. The project was never perfect, but hovered around 80% or so of perfect. Anybody could read everyone else's code, and work on it as needed. I never knew what new random thing somebody would want in the project. One week was all database work, another was all reporting, another was all web services.

I felt at the end of it that if that project, a multi-tenancy system using a portal server (something most JEE programmers are not familiar with), with its complexity (including a rather strange way of using SQL to emulate a document database, because they didn't exist yet) could manage to never be spaghetti code, then any project should be able to do so.

Guess what? This project was the very project led by the chief architect I mentioned in the bad example, at that same company.

## Why Do We Have Spaghetti Code?

There are multiple reasons code can become spaghetti code, here are some that come to mind:

  * Not learning architecture in university

  * No recognizable architectural pattern ever being applied (eg, MVC, MVVM, MVP, Actor, etc)

  * Nobody never raises the state of the software as an issue to management

  * People tend to follow the herd

  * Wanting to clear the bug queue rather than refactor

  * Stateful rather than stateless code

  * Reusing code rather than duplicating code

Notice that only the last two things are purely technical programming considerations.

When I went to university, I never took a course on architecture, because either there wasn't one, or I didn't think it was interesting enough (after all, I didn't acquire a degree JUST to get a job). No employer has ever asked me any architecture question beyond, "What does MVC stand for?", as if knowing an acronym implies sufficient wisdom and experience of a topic. I suspect a lot of other programmers would say the same.

If you never take the time to learn an architecture, it's not surprising if you wind up creating something that is a spaghetti monster--in fact, it's a virtual guarantee of such a result. I don't know why people can work for years on a project and never point out to management that the code is terrible, but I have seen this multiple times at multiple companies, where nobody even really seems to care.

Following the herd isn't all bad--if a project has good architectural leadership that does not allow code to go sideways, then others will simply follow that expectation. But if a project is terrible and nobody seems to care, then others who join the project will likely just continue the path of "doing whatever it takes to get it to work". So as long as a team can start with a good design and keep up the expectation of writing good code, the project should remain in a good state. This mirrors the physical world, where up front design work is done first by a small number of people, followed by construction by a larger number of people. It also mirrors the physical world in that construction companies who don't care construct things poorly, and vice-versa.

## Statefulness and the Reuse of Code

Every spaghetti project I've seen has some kind of bad statefulness. Typically, it manifests in one or both of two ways (often they are combined): encapsulation, and call chains.

Encapsulation can be done in a good way, but sometimes the logic is just so obtuse that it is nearly impossible to follow without running a debugging session and stepping through the code. There's not much point in making a "black box" of data and behaviour if only God unserstands the black box operation.

Sometimes method A calls method B which calls method C, etc., down to method J. These kind of deep call chains often have two problems:

  1. Method J needs a new parameter, but would have to be passed down from A through I first

  2. Simply declaring the new parameter on A through I isn't sufficient, as you discover that some parts of the code start at method B, while yet others start at method D, and those other call chains don't necessarily have any way of acquiring the parameter value needed.

If you think about the above, there is a "clever" form of code reuse happening here, where an attempt is made to write less code by sharing parts of the call chain across unrelated business processes. A related example would be a myriad of includes in your UI (such as JSP includes) where unrelated screens share fragments of included template logic.

This kind of code sharing has been the bane of my existence on more than one project. It is better to copy code than to try to share it like this.

## Don't Be Clever, Make Silos

In my experience, "clever" code is invariably code that is hard to reason about or understand, hard to debug, hard to fix or extend--just plain hard to work with period. The cleverness generally involves around some way of reducing the number of statements at the expense of being understandable to another human. If others have a hard time understanding it, then what's the point? It's better to write more code when more statements offer easier understanding, and be concise only when writing more statements would just increase the code size with no benefit to understandability. Striking this balance is a matter of experience and persistently trying to find the bowl of porridge that's just right.

One way to keep the disparate parts of a project disentangled is to use separate silos. Say you have a CustomerAddress and a WarehouseAddress. At first blush, these objects are very similar--a CustomerAddress has one address line while a WarehouseAddress has three, only the CustomerAddress has a type (mailing, billing, physical). It's tempting to use the same database table, the same UI code, the same business logic.

But this is a proverbial slippery slope. Usually, the objects in question will become more divergent over time, leading to ever more complex logic at every stage trying to handle these two different objects as if they were the same. There is often a seemingly endless amount of stuffing these two supposedly round pegs in holes that have an annoying propensity towards squareness.

A better idea is to just start right off with a separate database table, separate UI screen, separate business logic. If the CustomerAddress is already developed, then a good start for WarehouseAddress is to copy the CustomerAddress silo of data and logic, and then modify it as needed. Now the two can diverge as much as needed, and there is no "cleverness" in any shared logic trying to handle the two, because there is no shared logic in the first place.

Another benefit is that perhaps at some point, the CustomerAddress is thrown away entirely in favour of a different approach. In such an event, it is simple to know exactly what code to throw away, without impacting the WarehouseAddress, and without having any code laying around that nobody is really sure whether or not it is still needed.

Effectively, we take the Single Responsiblity Principle to the level of a silo, that completely handles one object on its own. In some cases, there may be multiple ways of using the same object. For example, perhaps in a mult-tenant system each tenant has their own validations on the CustomerAddress. The separate validations can still remain within the same overall silo, as long as they are also seperated, such as a seperate class for each one. In other words, silos can contain silos as needed.

## **Conclusion**

Learn architecture. You should have an hour here and there where for legitimate reasons you don't have much work to do; use them to create a small project with some architectural pattern like MVC. No, MVC is not a Maven dependency! It is something you practice, like walking and breathing, that you cannot "get an app for."

If you're working on a project that is clearly spaghetti code, do your company a favour and bring this up with management. Spaghetti code increases the project cost with extra development time, testing, etc. It can even inflate the team size. The client will probably figure out at some point they are paying too much for what they are getting, that they are paying more money for less value.

It's ok if you have to introduce a hack to reach a deadline, but **really do** fix that hack in short order, like the next two weeks. Don't let it just sit around. Put this in the project schedule and manage it just like everything else. Have some rule about not introducing new hacks when a small upper limit number of hacks already exist (like 3) until one of them is fixed first.

Write understandable code, not clever code. Learn to use Single Responsiblity Silos. Anybody can follow the tips laid out in this article to avoid spaghetti code. There are of course other causes for spaghetti code, I am writing from my own experience, but I have no doubt there are some equally simple things that can be done to avoid them also. It's a matter of analyzing what is wrong with the code well enough to describe it in human speak to a non-programmer, then come up with some ways to fix it, and to avoid it again in the future.

Take the Chaos Out of Container Monitoring. [View the webcast on-demand!](https://dzone.com/go?i=274433&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcompany%2Fevents%2Fwebcasts%2Fapplication-performance-monitoring-and-management.html%3Fcommid%3D286663%26cid%3DNA-DSP-APM-AEJ-000195-00001663-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_webcast1-apm-taming-chaos-articlepostroll%26mrm%3D)
