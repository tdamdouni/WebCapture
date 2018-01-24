# How Have Microservices Changed Application Development?

_Captured: 2017-10-10 at 20:18 from [dzone.com](https://dzone.com/articles/how-have-microservices-changed-application-develop?edition=329552&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-10)_

To gather insights on the state of microservices today, we spoke with 19 executives who are familiar with the current state of microservices architecture. We asked them, "What are the most important elements of microservices?" Here's what they told us:

## Speed

  * Personally, I think microservices are the embodiment of many levels of software best practices. The leading literature on microservices and hexagonal architecture emphasize that a service should be small enough to rebuild in one or two sprints. This may be a deep technical idea for an executive audience, but it has many compelling benefits - **it forces simplicity in the code, making it faster to maintain and easier to train for other developers.** It also forces good habits such as encapsulation, which creates simplicity across microservices as well as within them. Also, microservices isolate any complexity that does occur, so that if radically different databases or languages must coexist in the microservice architecture, they are gracefully contained in their own service, exposing the same sort of API contract that any other service would. Lastly, and perhaps most importantly for application modernization needs, microservices allow you to divide the map of your software ecosystem along the lines of your business units. In the emerging world of hybrid cloud architecture, it is absolutely critical that business units retain control over their infrastructure, and microservice application architecture closely aligns to this value.
  * An architectural shift is not simpler or easier because it changes the way you program. Event-driven versus push. Once you get there **it's more efficient with isolated service codes**. Serverless as a development platform makes microservices more usable. Translates to the client doing single page web apps with microservices.
  * **Faster speed to market** and realization of value with cloud scaling as a service. Also, the functionality is completely separated with formal connections via APIs. Able to integrate more services. Process changes are harder for individual teams and product managers getting the product to market since they are managing dependencies among six to 12 pieces.
  * **More frequent deployments.** Less manual testing, more automated testing. Zero downtime deployment. Easier to rollback. Greater need for automated testing and deployment.
  * **Accelerated how quickly you can get an application to market** and make modifications based on APM or consumer feedback.

## Agility

  * **Every new microservice is a new flow**: a new repository, a new set of permissions, a new machine or a new decision about where such microservice should live. The number of policies you desire for your services is the pain point: no code shared among microservices and you are soon applying the same new policy about logging, error handling, edge case management to all the microservices you have. Anyway, we started with microservices in production from day zero, and to date, we are happy enough with the development.
  * Allow legacy enterprises with monolithic apps to become **more agile** to make the digital transformation.
  * The vision to create a loosely-coupled enterprise environment has been a Holy Grail for some time. While the same theories and techniques showed promise with XML and SOAP-based web services, the implementation of microservices **better supports an agile approach to development.** The decomposition of monolithic end-to-end processes gives product and process designers and developers the flexibility to create solutions that are fit for purpose. It enables these professionals to define more discrete capabilities, allowing developers to create discrete functions - a more appropriate solution to the business problem they must solve.
  * Microservices make continuous deployment and delivery non-dependent on a single huge pipeline, and instead, can be accomplished with these much smaller components. **It allows you to make meaningful changes, often with a leaner team. **
  * Microservices architecture expect more speed. Web or mobile apps must deliver as quickly as possible today or you frustrate the end user. For Netflix and cable TV, two seconds are worth a million dollars. **More agile.** Scale for large organizations. Cloud-native. Right tooling and mindset. Changes the application development ecosystem. Teams are more collaborative because microservices are more collaborative. Have a security mindset in place from the beginning.

## Flexibility

  * It's not just an architectural style, it's also a development methodology. **Autonomy for software development teams** of three to five people (Amazon calls this "two pizza" teams) with developer, database, and designer all on the same team. Organizations will build software systems that mimic the communications pattern of the organization (Conway's Law). Microservices breaks down silos between applications and IT imposing strict organizational requirements on the team to be co-located. Symbiotic with DevOps - autonomy, decentralization, fragmentation of scale 50 to 100 microservices at a time. This increases accidental complexity. You cannot have successful microservices without DevOps in place. 
  * Easier to onboard new developers. Less overhead to deploy. **The ability to shape individual services.**
  * Microservices provide the biggest benefit to service-driven applications where the service facets require frequent change or modification. When abstracting microservices from the API definition(s) itself, this gives organizations benefit **tremendous flexibility to adapt their back end to whatever it needs to be**, without platform lock-in or other constraints found in traditional service or integration platforms. 

## Alignment

  * Conway's law: "organizations which design systems ... are constrained to produce designs which are copies of the communication structures of these organizations." **Microservices align to business objectives.** Full stack teams are aligned to customer value. Deliver business value faster. Ability to scale. See the bottlenecks and scale up as needed. Optimize hardware utilization. Must be more mindful of how to code and handle failure. Take into account latency.
  * **Deployment alignment with operations.** Change how applications are being deployed. More dynamic. How to version and update keeping the application together. Weekly releases moving concerns closer to the operations stack. Using edge services for security at scale. Orchestrate best of breed together.
  * Changes the way teams are structured. Requires greater automation. Emphasis on the adoption of more modern practices and automated testing. Decoupling enables a more functional perspective on what to develop and deliver. Instead of more traditional SOA approaches, microservices decompose by functionality, **more features and functions in alignment with organizational teams**. More flexibility to respond to the market.

## Other

  * They're a blessing and a curse. We're now running 40 to 50 microservices and each requires a JVM. It's good to decouple and containerize. It's hard to get the entire system to run on a single machine. Developers have up to 30 AWS instances. It becomes complicated to develop and hard to determine what exactly is going on in a distributed environment.

How have microservices changed application development from your perspective?

Here's who we spoke to:

  * Thomas Butt, CTO, [CardCash](https://www.cardcash.com/)
  * Matt McLarty, Vice President, API Academy, [CA Technologies](http://www.ca.com/)
  * Brian Dawson, DevOps Evangelist, [CloudBees](http://www.cloudbees.com/)
  * Lucas Vogel, Founder, [Endpoint Systems](https://www.endpointsystems.com/)
  * Job van der Voort, VP Product, [GitLab](http://www.gitlab.com/)
  * Ross Smith, Chief Architect, [PITSS America](http://www.pitss.com/)
  * Gianni Fiore, CTO, [Rebrandly](http://www.rebrandly.com/)
  * Peter Yared, CTO, [Sapho](http://www.sapho.com/)
  * Keshav Vasudevan, Product Marketing Manager, Swagger/SwaggerHub, [SmartBear](http://www.smartbear.com/)
  * Chris McFadden, V.P. Engineering and Operations, [SparkPost](http://www.sparkpost.com/)
