# Microservices: The Future or a Fleeting Episode?

_Captured: 2018-04-25 at 20:08 from [dzone.com](https://dzone.com/articles/microservices-the-future-or-a-fleeting-episode-log?edition=376199&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-04-25)_

[Download the How to Build (and Scale) with Microservices eBook](https://dzone.com/go?i=288421&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-how-to-build-scale-with-microservices%2F%3Futm_source%3Ddzone%26utm_medium%3Dsponsorship%25252520content%25252520syndication%26utm_campaign%3Dbumper%25252520text%25252520sponsorship%26utm_content%3Dhow%25252520to%25252520build%25252520and%25252520scale%25252520%26utm_term%3Ddzone%25252520bumper%25252520text%25252520sponsorship%26utm_budget%3Ddigital) and learn how microservices are rapidly emerging as the architecture of choice. Brought to you in partnership with[ AppDynamics](https://dzone.com/go?i=288421&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-how-to-build-scale-with-microservices%2F%3Futm_source%3Ddzone%26utm_medium%3Dsponsorship%25252520content%25252520syndication%26utm_campaign%3Dbumper%25252520text%25252520sponsorship%26utm_content%3Dhow%25252520to%25252520build%25252520and%25252520scale%25252520%26utm_term%3Ddzone%25252520bumper%25252520text%25252520sponsorship%26utm_budget%3Ddigital).

For the last three years, microservices architecture has been on the rise and many software architects have gotten carried away with this innovative approach to development. The benefits of developing a small service with one specific business purpose were too exciting and captivating to pass up. This new software architecture, which was immediately adopted by enterprise organizations who are also software leaders such as Netflix and Amazon, has shifted the way companies approach software development. It has led many other software vendors to rush into breaking down their monolith software into little pieces and rebuilding new pipelines and delivery processes required by the new software structure.

While microservices have many advantages, basing a large and complicated application on small services comes with costs. When it comes time to select an infrastructure and architecture, the high-level software design process involved requires R&D to understand the pros and cons of the different options, and how cost effective every solution is so an informed decision can be made. Yet, many organizations fail to do so and end up working with an architecture that is destructive to their software and sometimes, to the whole company. In many cases, R&D groups put the blame on the technology which begs the question: Is Microservices a good architecture or is it going to evaporate?

## Why Use Microservices?

So, we understand that with microservices, our application is going to be divided into many small parts, and we are going to have the ability to develop and maintain each and every one of them on its own - but what does it mean and why is it better? The immediate answer is flexibility. Developing a small component usually managed by one team means that the team has the authority to choose the technology they want to use for the component. As long as the technologies can supply the required APIs and meet cross-product standards-i.e. shared libraries that supply a capability, can be integrated into the deployment workflow, and comply with the monitoring, tracing, and logging principles of the software, the team's technology choices can remain their own.

Flexibility also means that features or partial features can be deployed at any time, as only one component is being upgraded at a certain time. [Rapid deployments](http://www.computerweekly.com/blog/CW-Developer-Network/When-to-use-rapid-software-application-deployment) (or RAD), which is the congenital process of Rapid Application Development, sometimes requires the deployment of parts of features which are not yet ready on certain platforms, or where the back-end implementation is complete but the front end is not, and so on. Microservices give the team the ability to upgrade one component without affecting the other.

One of the biggest challenges organizations have is the lifecycle management of software. In monolith applications, integrating all the services and components-where every change to one of them affects all the others, aligning timelines for all the teams and integrating them all into one deployment process is the holy grail many strive for, but not everyone manages to achieve this goal. Microservices architecture, by its nature, facilitates a granular software lifecycle management, allowing you to completely swap one or more features without having to lay a finger on any of its dependent systems. This eliminates the need to administer the integration of all components and allows project and release managers to focus on the software deliverables rather than on the unification of software components.

Probably the most well-known advantage of microservices architecture is scaling. Multiple copies of the same microservice can simply be deployed in order to achieve scalability and durability without affecting other services, allowing DevOps to focus on a specific service currently not functioning well or withstanding pressure. This makes it easier to respond in real-time to events such as concurrency, load, or failure of services and pinpoint issues without any effect on features that do not use the problematic microservice. Components which do not handle calls in an orderly manner can be duplicated by generating another instance of the component and creating another endpoint for the calls. There are many other advantages that microservices architecture have for software and enterprise organizations, yet microservices might not be the answer for all the problems that R&D and DevOps teams have.

## Are We Ready for Microservices?

As we mentioned earlier, many R&D groups decide to implement the microservices approach, sometimes without understanding the effects. Developing decoupled services adds complexity to the system. Adding new functionality results in a number of services having to make slight changes in the code. This means that companies have to invest time and effort in building and maintaining a simple way for engineers to run everything locally. definitely makes this task easier, but it still takes time to manage the repository and have it configured correctly for every engineer.

Testing and debugging the software is where it becomes really entangled. Writing a proper set of integration tests, on top of the tests for every component separately, requires an understanding of all the different components a given interaction might invoke, capturing all of the possible errors, and even sometimes requires a tester from outside the team to get a higher-level view of the product. In this case, the agile process is broken, as the team is no longer enclosed and is dependent on external contributors and timelines. While testing is a process that can be planned and calculated, debugging issues and understanding their root cause becomes almost impossible as many microservices are dependent on other microservices and finding the faulty one, without a strong and comprehensive tool that contains all the information of every single call between the software services, is very difficult.

Another problem that microservices-based software are more likely to encounter is slowness. Monoliths usually have nearly zero overhead when interacting with their APIs, but microservices, often running on other machines and requiring a network hop between the services, are not as fast. This structure can slow down the system considerably. This situation becomes even worse if services need to contact multiple other services synchronously in order to complete a request. Response times lengthen as they are also affected by network overhead. The same issue also affects software security. Instead of securing several components with clear restrictions to what permissions each component has, microservices requires DevOps to maintain many different hosts which complicate the configuration production environment.

Last, being able to swiftly deploy small independent units might be a great pleasure for development, but it creates an additional task for the ops teams as several applications might turn into hundreds of little microservices. Many organizations find it difficult to handle such a swarm of rapidly changing tools and have trouble building the right CD process to support this architecture.

## As Usual, It's All About Context

We now understand that microservices can improve the development process but at the same time decrease the efficiency of testing and operations. It can supply a simpler way to scale software but at the same time affect response time and performance. There's no one answer whether all software should revise their development processes and implement microservices as their architecture. Every organization, startup, mid-sized company, and even corporation should first ask the right questions and then decide on the correct approach for them. Here is a list of questions that can help locate problems that might pop up later in the development process:

  1. Can R&D handle the decoupling of services approach and sporadic and frequent releases process?

  2. Does the software require data consistency?

  3. Can testing be done at the component and integration level?

  4. Are we willing to invest time in infrastructure?

  5. Is the ops team prepared and do they have the capacity to support many microservices in production?

  6. Can the components be deployed in containers?

  7. Does the software required different SLAs for different services?

These questions are part of the process of understanding if microservices are required and if this architecture is valuable for the organization or if it will end up harming the software and the team.

## Look Before You Leap

In today's fast-paced world, organizations must stop leaping on every new buzzword and should first plan, understand the relevance of the technology, and estimate the cost of every new innovative solution they consider implementing. Even though using cutting edge technologies is sometimes considered a goal, R&D groups who want to put the new technologies into practice have to supply evidence of profitability prior to redesigning their software.

However, microservices architecture is not going to disappear as it solves many problems that enterprise organizations have.

It does seem that microservices will become less common in smaller applications and teams and will instead be developed specifically for enterprise solutions which have the ability to invest the required time and resources to handle the development, monitoring, and debugging overhead this architecture involves.

[Learn how to track microservices](https://dzone.com/go?i=286452&u=https%3A%2F%2Fwww.appdynamics.com%2Fapp-iq-platform%2Fmicroservices-iq%2F%3Futm_source%3Ddzone%26utm_medium%3Dsponsorship%26utm_campaign%3Dmicroservics%252520sponsorship%26utm_content%3Dmicroservics%252520sponsorship%26utm_term%3Ddzone%252520microservics%252520sponsorship%26utm_budget%3Ddigital) deployed in elastic infrastructure such as containers or cloud where nodes scale up and down very rapidly.
