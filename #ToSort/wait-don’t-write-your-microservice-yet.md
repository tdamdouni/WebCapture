# Wait! Don’t Write Your Microservice…Yet

_Captured: 2017-04-26 at 14:12 from [dzone.com](https://dzone.com/articles/wait-dont-write-your-microservice-yet?edition=292912&utm_source=weekly%20digest&utm_medium=email&utm_campaign=wd%202017-04-26)_

### Don't rush splitting your systems into microservices. Carve out microservices as the bounded contexts become more apparent; it will save you time and money.

Today's data climate is fast-paced and it's not slowing down. [Here's why your current integration solution is not enough.](https://dzone.com/go?i=188126&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fdata-inspired-future-e-guide%2F%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%25252520-%25252520Data-Inspired%25252520Future%26utm_source%3DDZONE) Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=188126&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fdata-inspired-future-e-guide%2F%3Futm_campaign%3DDZONE%26utm_medium%3DE-guide%25252520-%25252520Data-Inspired%25252520Future%26utm_source%3DDZONE)

Day one, we were super excited to start a new project for a huge financial institution. They seemed to know the domain and as Knoldus we understood the technology. The stakeholders were excited about the [Reactive Paradigm](http://www.reactivemanifesto.org/) and the client architects were all stoked up the way there would be microservices which would allow them all the benefits that other companies had been harping about. We had proposed [Lagom](https://www.lagomframework.com/) and it was taken well.

We had an overview of the domain and we had a set of domain experts assigned to us who would be product owners on different tracks that we would work on. Great, that does seem like a perfect start. But when things are too good to be true…probably they are.

The lead architect (LA) asks me, "So how much logs would each microservice generate?" I am like…what? And he explains, "Since we are going to build it with microservices, I need to understand the logging needs so that I can size the disks."

I am like, "I don't know…uh…mmm."

LA: "But, we explained the domain to you so I thought this would be easy! Ok, how many microservices would we have?"

I respond, "I don't know! … yet." And now the LA is losing it on me. I could go on how the conversation evolved, or rather degraded, but I would rather talk about how we finally managed to convince the stakeholders that this thought process is incorrect.

Whenever we start a new project, we start building a MONOLITH. Yes, you heard me. That is how we start. When you are starting a product, you know too little about how the intercommunication between teams, subdomains, and bounded contexts would work out. Once we have the monolith and we identify the submodules and the play between them, it is relatively trivial to break it down into microservices. The only things to remember is to design a monolith carefully, paying attention to modularity, especially at the API boundaries and data storage. If this is done right, it is simple to shift to microservices. Once we have the well-done monolith, it is easy to carve out and logically package subparts of the monolith as a microservice.

![Screenshot from 2017-04-19 23-58-40](https://knoldus.files.wordpress.com/2017/04/screenshot-from-2017-04-19-23-58-40.png)

You could, of course, argue about the benefits of getting to microservices directly: once we have a monolith, it cannot be broken down into microservices easily. We cannot start with smaller teams which can work on their own parts and what not. But, for the teams to work on their own parts, your bounded contexts should be very well defined, which is almost never true. The boundaries and the contexts become clear(er) once we have the system reasonably in place. I would even counter-argue that a lot of times, you would want to peel off a part of the system into a microservice much later when you get feedback from production data.

In our example, one of the services which generated PDF reports for the day's trades was bundled along with the reporting service. Over a period, we realized that this service was hit a lot and especially during the closing hours or the first hour after closing. Other reports did not follow the same behavior. We separated out the PDF service as its own microservice which could expand to 2x servers on peak load. The report service continued to work the way it was.

So, the summary is that however hard you may try, you would almost always fail at separating out the microservices when you begin the project. In fact, the cost of badly carved out bounded contexts and microservices would be much higher than beginning with a monolith and breaking it down as and when needed.

You might be interested in this post as well: "[And you thought you were doing microservices](https://blog.knoldus.com/2016/05/08/and-you-thought-you-were-doing-microservices/)."

[Is iPaaS solving the right problems?](https://dzone.com/go?i=171134&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-ipaas-plus-e-guide%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DeGuide%252520-%252520iPaaS%252520vs%252520iPaaS%252520%252520) Not knowing the fundamental difference between iPaaS and iPaaS+ could cost you down the road. Brought to you in partnership with [Liaison Technologies.](https://dzone.com/go?i=171134&u=https%3A%2F%2Fwww.liaison.com%2Fresources%2Fipaas-vs-ipaas-plus-e-guide%2F%3Futm_campaign%3DDZONE%26utm_source%3DDZONE%26utm_medium%3DeGuide%252520-%252520iPaaS%252520vs%252520iPaaS%252520%252520)
