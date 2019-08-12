# Breaking Down the Monolith: Microservices vs. Self-Contained Systems

_Captured: 2018-09-14 at 07:03 from [dzone.com](https://dzone.com/articles/breaking-down-a-monolithic-software-a-case-for-mic?edition=396191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-09-13)_

The new [Gartner Critical Capabilities report](https://dzone.com/go?i=299475&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921) explains how APIs and microservices enable digital leaders to deliver better B2B, open banking and mobile projects.

Today's IT publications and discussions are full of such words as digital transformation, bimodal IT, continuous development, and agility. It is hardly debatable that in this light, **monolithic architectures and monolithic applications** should become a thing of the past sooner or later -preferably, sooner, of course. And indeed, IT departments are encouraged to move away from their monoliths for a number of perfectly sensible and understandable reasons: complicated maintenance, too many dependencies, difficult testing and deployment (a monolith can only be deployed as a whole). Monoliths are like a Bermuda Triangle for any agile IT initiatives.

Rather more often than not, it is suggested to replace monoliths with **microservices**.

Microservices is nowadays a term that is often used to refer to both microservices per se and to a specific architectural style that is based on microservices.

The [concept is rather easy](http://martinfowler.com/microservices/), it's about **building an application consisting of many small services that can be independently deployed and maintained, and don't have any dependencies, but rather communicate with each other through lightweight mechanisms and lack a centralized infrastructure**. It is even possible to write these small (micro-) services each in its own language.

![Microservices-Architecture](http://www.elastic.io/wp-content/uploads/2016/06/Microservices-01-1.jpg)

Their benefits are undoubted, too: they easily allow for continuous deployment, and certain parts of an application can be changed, debugged, or even replaced quickly and without affecting the rest. With microservices, you absolutely cannot break an application: if something goes wrong, it will go wrong only within its own microspace, while the rest of the application will continue working as before.

However, as it usually is with shiny pictures of a perfect future outcome vs. sobering facts of reality, moving from a monolith to microservices is sometimes easier said than done.

Recently, I went to the SEACON conference in Hamburg (a very recommendable small conference for IT people in a fabulous location, by the way), where I sat in a presentation "A Rocky Road from Monoliths in the Direction of Microservices" by [Bjorn Kimminich](https://de.linkedin.com/in/bkimminich/en) from [Kuehne + Nagel](http://www.kn-portal.com/).

The name of the presentation, if you read it carefully, actually already says a lot: "in the direction," but not "to." Indeed, Bjorn showed that it proves to make no sense to break down a complex monolith into microservices. He was also very kind to allow me to write about his story in our blog, and so here I am, sharing with you another way of moving away from monoliths, the way successfully implemented at Kuehne + Nagel.

## Meet the Monolith KN Login

Kuehne + Nagel is a global transportation and logistics company founded in Germany and now based in Switzerland. One of its probably most valuable products is a supply chain management tool called KN Login, which was built entirely internally.

KN Login is a highly complex software application that manages a massive number of different things. Just to name a few, it helps keep track of your products, and by "products" I mean huge containers and such; it streamlines operations and helps better manage your assets; it ensures proactive control to help you maintain your supply chain integrity and efficiency; it improves communication and collaboration with your supply chain partners; it even helps track if containers with your products are exposed to optimal environmental conditions, and if not - warns the responsible staff. In a nutshell, it is responsible for quite a few processes and operations.

KN Login has been continuously developed since 2007 and by now it contains over 1.500.000 lines of code, with over 200 developers in total having been working on it. Moreover, it is built with a variety of languages: initially, it was written with a self-made Java Web Framework, which is deeply embedded in the monolith's architecture and is, therefore, impossible to replace. At the same time, the IT team at Kuehne + Nagel now recommend using an open source framework like Spring whenever possible instead. In addition to that, it uses multiple UI technologies to address the requirements and needs of different business units. All in all, KN Login is a mix of JSP, jQuery, Swing/ ULC, GWT/GXT. And it has a monolithic underlying database, which is used for operations, visibility and reporting.

Like any other monolithic application, KN Login wasn't so complex back at the beginning (and probably wasn't expected to become so), but - again like any other monolithic application - it grew over time into a million [LOC](https://en.wikipedia.org/wiki/Source_lines_of_code) burden.

Now, with such a variety of code lines, languages and people working on it, it is quite easy to "break" the application. All you need to do is to use a wrong class in a wrong piece of code. Maintaining such a complex software is a challenge even for the experienced IT, let alone for people who are new in the team. At the same time, KN Login is involved in an unimaginable number of processes and steps, and this puts a huge responsibility on its implementers and maintainers.

## On the Road to Moving Away From the Monolith

The question that IT at Kuehne + Nagel asked themselves was how to make the software less heavyweight and easier to maintain. In fact, Bjorn Kimminich shared in his presentation a few very valuable tips, which I, in turn, am sharing with you. So:

  1. First important thing to do right now is **STOP adding even more stuff to the monolith**, no matter how badly business units want to have cool new features for certain modules, or add modules they desperately need, or make it even more interactive and user-friendly. The only thing that should be carried out is just fixes and smallest changes.
  2. **Find the so-called seams in your monolith**. These are basically certain components in the software body that are more loosely coupled than others. Ideally, these are even certain modules that would contain several components, though this is easier said than done. Of course, again, ideally, you should be able to identify even entire modules that can be then eventually cut out of the monolith. But this certainly depends on the complexity of a software and how many modules/product clusters it has.
  3. **Realize that most of your seams are just wishful thinking**, because the transitive dependency is so complex that it has all the right to be called a dependency hell. In other words, components are so dependent on each other, that it is nearly impossible to separate them.![Monolith's dependency hell](http://www.elastic.io/wp-content/uploads/2016/06/Monolith-01.jpg)

  4. **Try to "desiccate" the monolith over time in spite of #3 through future new projects that, hopefully, will cover parts of some of the monolith's functionality**. In order to do this, watch for seemingly low-hanging fruits, e.g. components to which business units wish to add more advanced features. After these new projects go live, you can "turn off" the corresponding components in the monolith since they are now practically replaced through the new projects.
  5. **Moving to Microservices might be too much of a drastic step, especially when you have such complex monolithic software** like KN Login. The "[Grand Redesign](https://www.amazon.de/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882/ref=sr_1_4?ie=UTF8&qid=1465204606&sr=8-4&keywords=Robert+C.+Martin)" approach that is usually advocated for in cases of moving to microservices from monolith simply cannot work here - you cannot take everything apart to build it anew. Besides, with 1.500.000 lines of code you would easily end up with several thousands of microservices, which wouldn't really make the whole matter any more transparent and manageable.

But if turning to microservices is not the best way of breaking down a complex monolithic software, with what other options IT is left there?

## Self-Contained Systems (SCS) Might Be the Answer

Generally, the [concept of self-contained systems (SCS)](http://scs-architecture.org/) is very close to that of microservices: you take monolithic software and break it down into many smaller independent parts. But unlike with microservices, you break it down into autonomous, replaceable web applications.

The main decisive difference between the two is, however, that SCS are typically larger than microservices and within a software, there will be considerably fewer SCS than microservices. Another [notable difference](http://scs-architecture.org/vs-ms.html) is that SCS typically also have autonomous UI, business logic and data storage each, which makes them highly flexible in terms of customization. The preferred integration of SCS units should happen at the UI-level, though API-level integration is also practiced. All this allows one to build SCS units using different languages and even different databases, helping solve real specific problems.

Thus, self-contained systems help avoid the "Grand Redesign" and instead move to a more agile version of a software in small, manageable steps which would minimize the risk of failure. And indeed, Kuehne + Nagel chose this architecture approach for their eCommerce platform [KN Freightnet](http://www.kn-portal.com/airfreight/kn_freightnet_for_airfreight/kn_freightnet_overview/).

**KN Freightnet** was a new project for offering a logistics eCommerce platform, where small customers can ask for quotes and do bookings in an easy and well-guided way. The quoting part was already present in KN Login. KN Freightnet basically duplicated this feature, thus becoming the pilot project for dissecting the monolith in the way that Kuehne + Nagel outlined this process: Duplicate the "low-hanging fruit" outside the monolith, create an independent software around it and switch off the duplicated component in the KN Login when it's entirely safe to do so.

![Creating first self-contained systems units](http://www.elastic.io/wp-content/uploads/2016/06/Creating-first-SCS-01-1.jpg)

Initially, KN FreightNet was only offering the quoting functionality for Airfreight. Later, Seafreight and Overland also got interested in an eCommerce presence. But instead of putting their requirements into the existing application, new SCS units for each mode of transport were created, along with some additional SCS units for cross-cutting concerns or very special functionality like the Product Transit Time Simulator, making it a total of 10 modules, or speaking in SCS terms, a total of 10 autonomous web applications, each with its own UI.

Even though it took the Kuehne + Nagel IT team whole 4 years only for KN Freightnet software to arrive at its current stage, the SCS approach was and is, according to Bjorn, the only viable way for implementing a complex application that would otherwise end up as a monolithic software - again. Currently, the IT team at Kuehne + Nagel is working on separating other modules from KN Login.

**The End. Almost.**

## Bye-Bye Microservices, Welcome Self-Contained Systems? Well, Maybe Not So Fast…

The example provided by Kuehne + Nagel may implicate that the options for breaking down a monolithic software are either opting for microservices or self-contained systems. Yet one sentence uttered by Bjorn Kimminich almost nonchalantly at the end of his presentation made me search for a wider perspective; he said, namely, that who knows, maybe they will go for microservices after SCS.

And indeed, I encountered another exciting use case shared by [Otto](https://www.otto.de/unternehmen/en/index.php), a huge online retailer from Germany. If microservices is your topic, you absolutely need to read [this article completely](https://dev.otto.de/2015/09/30/on-monoliths-and-microservices/), however, here is what caught my attention most:

Just like Kuehne + Nagel, Otto had a monolithic software that grew over time in its complexity significantly. And just like Kuehne + Nagel, Otto decided to break it down into self-contained systems, or as they called them, **"verticals"**. Yet over past few years, more verticals came to life, while others were becoming more and more complex. And so, Otto decided to take a step even further and dissect verticals into microservices. For deeper technical details and more important, achieved benefits, have a look at [their article on why they chose microservices](https://dev.otto.de/2016/03/20/why-microservices/).

![Breaking Self-Contained Systems down into microservices](http://www.elastic.io/wp-content/uploads/2016/06/Breaking-SCS-into-m-services-01.jpg)

What's more interesting here, though, is that self-contained systems might be a perfect intermediary step between a complex monolith and microservices.

## In a Nutshell

Kudos to you if you have diligently read this article from start to finish. But if you didn't manage it completely, here are some key points you can take with you:

  1. A **monolithic software is bound to become a pain in the neck in every possible way**, but probably most importantly, in its maintenance. So, even if it just a proof of concept, avoid starting with a monolith.

  2. **If you already have a complex monolith**, you might want to start thinking about how to break it down. And if you do so, even if your long-term goal is microservices architecture, **you might want to start with self-contained systems first** (SCS).

  3. **Look for new projects that would duplicate and subsequently replace certain functionality in your monolith,** e.g. for modules within the monolith which business units want to extend or retarget. At the same time, make sure you don't add any more feature to your monolith. But be prepared that you won't be able to move to a more agile version of your software overnight - it might take years, but it's worth it.

  4. **Even self-contained systems can become too big and bulky over time**. This is when you can start thinking about breaking those down too, this time into **microservices**. 

_I'd like to finish the article with a big Thank You to Bjorn Kimminich for allowing me to cover his use case in a great detail, referring to his [presentation](http://kuehne-nagel.github.io/monolith-to-microservices/#/1). If it were not for your consent, the article would have been less than half so fun to write. Also, thank you for taking a look at the final draft and correcting a few pieces of information I happened to have misinterpreted._

The new [Gartner Critical Capabilities for Full Lifecycle API Management report](https://dzone.com/go?i=299476&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921) shows how CA Technologies helps digital leaders with their B2B, open banking, and mobile initiatives. [Get your copy from CA Technologies.](https://dzone.com/go?i=299476&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921)
