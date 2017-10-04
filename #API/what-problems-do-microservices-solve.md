# What Problems Do Microservices Solve?

_Captured: 2017-09-21 at 13:47 from [dzone.com](https://dzone.com/articles/what-problems-do-microservices-solve-1?edition=325527&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202017-09-21)_

Share, secure, distribute, control, and monetize your APIs with the platform built with performance, time-to-value, and growth in mind. [Free 90-day trial](https://dzone.com/go?i=231226&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Ftechnologies%2Fjboss-middleware%2F3scale%2Fget-started%3Fsc_cid%3D701f2000000h30LAAQ) of 3Scale by Red Hat

_Editorial note: I originally wrote this post for the TechTown blog. You can [check out the original here, at their site](http://techtowntraining.com/resources/blog/what-problems-do-microservices-solve)._

Do you find that certain industry buzzwords set your teeth on edge? If so, I assure you that you have company. Buzzwords permeate every professional space, but it seems that tech really knows how to attract them. Internet of things. The cloud. Big data. DevOps. Agile and lean. And yes, microservices.

![](https://www.daedtech.com/wp-content/uploads/2015/06/LikeABoss.jpg)

Because of our industry's propensity for buzzwords, [Gartner created something it calls the hype cycle](http://www.gartner.com/technology/research/methodologies/hype-cycle.jsp). It helps their readers and clients evaluate how much attention to pay to emergent ideas. They can then separate vague fluff from ideas that have arrived to stay. And let's be honest - it's also a funny, cathartic concept.

If you've tired of hearing the term microservices, I can understand that. As of 2016, [Gartner put it at the peak of inflated expectations](https://www.gartner.com/doc/3371727/hype-cycle-application-services-). This means that the term had achieved maximum saturation a year ago, and our collective fatigue will drive it into the trough of disillusionment.

And yet the concept retains value. Once the hype fades and it makes its way toward the plateau of productivity, you'll want to understand when, how, and why to use it. So in a nod toward pragmatism, I'm going to talk about microservices in terms of the problems that they solve.

## First, What Are Microservices?

Before going any further, let me offer a specific definition. After all, relying on vague, hand-waving definitions is the main culprit in buzzword fatigue. I certainly don't want to contribute to that.

Industry thought leader [Martin Fowler offers a detailed treatment of the subject](https://martinfowler.com/articles/microservices.html): "In short, the microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms, often an HTTP resource API. These services are built around business capabilities and independently deployable by fully automated deployment machinery."

Now, understand something. The architectural trade-off here is nothing new. In essence, it describes centralizing intelligence versus distributing it. With a so-called monolith, clients have it easy. They call the monolith, which handles all details internally. When you distribute intelligence, on the other hand, clients have more burden to figure out how to compose calls and interactions.

The relative uniqueness of the microservices movement comes from taking that tradeoff and layering atop it delivery mechanisms and the concept of atomic business value. Organizations touting _valuable _ microservices architectures tend to offer them up over HTTP and providing functionality that stands neatly alone. (I make the distinction of valuable architectures since I see a lot of shops just call whatever they happen to deliver a microservices architecture.)

For example, a company may offer a customer onboarding microservice. It can stand alone to create new customers. But clients of this service, internal and external, may use it to compose larger, more feature-rich pieces of functionality.

So, having defined the architectural style, let's talk about the problems it solves.

## Microservices Allow Skill Set Flexibility

Imagine an organization with a large, monolithic website. This sprawling entity serves as the company's entire public interface on the internet.

Now imagine staffing this organization. The app dev group probably consists of many teams, divided up by functional areas of the application. Maybe it has the order processing team and the administration team. You get the idea.

Historically, such a company would staff a department with dozens or hundreds of people. And all of those people would have similar technical backgrounds. While this might not seem remarkable, it does put significant constraints on hiring, staffing, and training. Life gets much easier if you can just hire good people and let them use their chosen tech stacks.

Splitting your organization's architecture into microservices allows you to do exactly that. The microservices approach results in much looser coupling among technical components. This, in turn, gives individual teams more technical flexibility.

## Microservices Help Developers With Efficiency

Now that you have developers on fewer coupled teams, you can realize additional efficiency. To understand how, consider the traditional organization with its sprawling web app.

Usually, the sprawling web app involves many teams working in collaboration on one giant codebase. They may not all pull the entire codebase onto their development machines. But then again, they might. And even if they don't, they feel some pain for it. Other teams might break them with their code commits. And everyone shares a common, long-running build.

With microservices, you get true separation among the teams. They each have their own, much smaller codebases. Builds are snappy, and all facets of development are more manageable at smaller scales. This can mean some enormous windfalls in productivity.

## Easy, Less Risky Deployments

Part and parcel with the ease of smaller scale comes the ease of deployment. Think of deploying a large-scale web application. You do extensive testing and risk assessment. Then you offer advanced notification, sometimes weeks ahead of time.

When the time comes (always a Friday evening), you take everything offline. You deploy as quickly as possible, and then you scramble to do all of the smoke testing. Once the outage window passes and nothing is obviously on fire, you start to breathe a little easier. But only after some days of non-issues do you feel at ease.

This is life for deploying a monolith. After all, deploying anything requires deploying everything. So even small tweaks to tangential functionality carries a major risk.

Microservices architectures flip the script on this. Instead of deploying everything, you can deploy only a small segment of your offering. This lowers risk, particularly when you have low priority fixes to obscure components.

## Runtime Resiliency

Speaking of risk minimization, let's think about what happens after deployment. In the world of the monolith, all of the company's functionality runs as a big conceptual ball on a server.

This means that malfunctioning components can create global problems. For example, let's say that some relatively unimportant module springs a memory leak. Over the course of time, this can lead to negative consequences across the board. The behavior of the entire site may slow to a crawl. Or maybe the leak even crashes the web server, taking everything temporarily offline.

With microservices, you avoid this risk. A misbehaving service still presents a problem. But you can address it individually. And if it's not mission critical, you even have the flexibility not to prioritize a fix.

The flexibility extends beyond just isolating problems, too. Even when everything is going well, you have levers to pull. Scaling individual services up and down to accommodate load fluctuations becomes possible in a way that'd be unheard of with monoliths. You have a fleet of small boats to arrange, rather than a single battleship.

## Application Lifecycle Flexibility

I'll offer one last problem that microservices address. And this one spans the entire lifetime of your codebases.

When you have a single application of large scope, you tend to live it for years. When new technologies emerge, you _migrate_ toward using them, time-permitting. But your application tends to resist this. It builds up cruft and the dreaded pockets of legacy code. It has technical debt.

But microservices applications resist these problems. While I won't go so far as to call them disposable, I will say that they require _far_ less commitment. If you want to migrate to a new technology, you can retire an old service and write a new one. By having many tiny codebases, you become less attached to any one individually. And this makes painful strategic decisions about the code come with a lot less risk.

## No Silver Bullets

I've made the microservices architecture seem pretty appealing in this post. That's to be expected. After all, I've written about the problems that they solve.

But this is not to say that microservice architectures don't have drawbacks. They do. Like any architectural decision, this one involves tradeoffs. Distributing intelligence makes things simpler and more flexible at the component level. But it also distributes the complexity, encourages fragmentation, and opens the door to over-engineering.

Microservices architecture is worth understanding. Behind the hype and buzzword status, genuine benefits exist. You'd do well to avail yourself of them, but make sure you do so with eyes wide open.

Explore the core elements of owning an API strategy and best practices for effective API programs. [Download](https://dzone.com/go?i=231227&u=https%3A%2F%2Fengage.redhat.com%2F3scale-api-owners-s-201706160312%3Fsc_cid%3D701f2000000h30LAAQ) the API Owner's Manual, brought to you by 3Scale by Red Hat
