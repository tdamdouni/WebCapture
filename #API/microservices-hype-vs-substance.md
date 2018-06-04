# Microservices: Hype vs. Substance

_Captured: 2018-04-26 at 07:19 from [dzone.com](https://dzone.com/articles/microservices-hype-vs-substance?edition=376196&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=microservices%202018-04-25)_

[Sysdig](https://dzone.com/go?i=278430&u=https%3A%2F%2Fsysdig.com%2F%3FUTM_Source%3DContent_Syndication%26UTM_SFDC_Campaign%3D701f1000001cgkm%26UTM_Offer%3DSysdig-website%26UTM_Campaign%3D%26UTM_Medium%3Dpre-roll%26UTM_Content%3DDzone-microservices-zone%26UTM_Term%3D%26UTM_Creativeid%3D) is the container intelligence company. The only unified platform for monitoring, security, and troubleshooting in a microservices-friendly architecture.

The purpose of microservices is to facilitate the process of building and maintaining applications. As opposed to the conventional style of building applications, utilization of microservices means that each element of the application can be developed separately. As a result, teams can work faster than they would if they had to manage one large project, and developers have more options when it comes to choosing programming languages and frameworks that would be the most appropriate for the individual components of the application.

One of the earliest implementers of microservices is a popular American entertainment company Netflix. With many enterprises following suit, it is worth discussing and examining the hype surrounding this technology and measuring it to its real substance, ie the real benefits it provides.

## Agility vs Complexity

Since the process of building microservices based applications and their components is shorter than with monolith applications, there is more [agility](https://jaxenter.com/most-important-benefit-microservices-is-agility-129472.html) and probability of introducing new versions of a service in a shorter period of time. However, the process of deployment is more complex than with conventional monolith applications as different components may be implemented with the use of different tools.

## Reliability vs Failure Response Strategy

Failure of a given microservice affects solely this individual service while the rest of the components might be able to operate normally. A failure in a conventional monolith application may affect the performance of all its functionalities. The problem is, however, that without close monitoring it might be difficult or even impossible to establish the source of failure with multiple microservices being implemented. That is why each microservice needs to have a separate monitoring configuration.

## Testing: Easier or More Challenging?

As each microservice is built in isolation, theoretically testing should be made easier. However, due to the asynchronicity of microservices, creating and implementing manual and automated tests may turn out to be more challenging than in the case of monolith applications.

## No Central Log Monitoring

Since each microservice generates a log and the log messages are distributed across multiple hosts, there needs to be a good logging strategy to manage issues that might appear anywhere in the application.

## Management: Easier or More Complex?

As each team is responsible for the development of separate components, the work becomes divided between smaller teams and, simply put, gets done faster. However, it can be more challenging to manage a variety of different components of the [infrastructure](http://ottawa-it-services.ca/how-can-you-standardize-your-it-infrastructure/) and new tools must be implemented to handle this complexity.

## Improved Scalability

While monolith applications can only be scaled vertically, microservices based applications can be also scaled horizontally. If there is an increase in demand for one of the application components, scaling only this particular part of infrastructure is possible rather than impacting the whole application.

## More Flexibility vs Higher Costs

While developers working with microservices can utilize a variety of languages, frameworks and modern technologies, this diversity results in overall higher costs of application maintenance.

## More Independence vs Slower Performance

Each component of the microservice architecture can be changed or replaced without affecting the functioning of the other elements. On the other hand, each component consumes resources, and the burden on servers is greater than with monolithic applications. This increase of resource usage may cause the application to run slower and could require the use of additional servers. If the application takes too much time to respond, users will most likely exit it before it starts running.

## Business-Friendly

Since the use of microservices allows for dividing a large project into smaller, easily manageable tasks, services can be changed and updated according to the specific needs of a given business.

## Polyglot in Nature

As mentioned already, each module can have its own language, framework, database and other tools which suit a given component best. Each team is responsible for their part of the project which gives them more extensive knowledge in their particular component and better familiarity with the code of their choice.

## Conclusion

The implementation of microservices has its range of advantages and challenges as well. How you approach the solutions provided by microservices may depend on your project's specifications. If you value flexibility and independence, then utilizing microservices infrastructure can be the right choice for you. The solutions provided by microservices offer also more opportunities of adjusting the needs of a specific business client which might be a crucial benefit to you and your team. With the right strategy and a plan for testing, monitoring and management you can learn how to take advantage of the freedom microservices solutions have to offer.

[Download our white paper:](https://dzone.com/go?i=278431&u=https%3A%2F%2Fgo.sysdig.com%2FSysdig-Architecture%3FUTM_Source%3DContent_Syndication%26UTM_SFDC_Campaign%3D701f1000001cgkm%26UTM_Offer%3Dsysdig-architecture%26UTM_Campaign%3D%26UTM_Medium%3Dtext-link%26UTM_Content%3DDzone-microservices-zone%26UTM_Term%3D%26UTM_Creativeid%3D) The Architecture of the Sysdig Container Intelligence Platform. Built for microservices and containers for monitoring, security, troubleshooting
