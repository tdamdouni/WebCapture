# Build or Buy? — The Eternal IT Question

_Captured: 2018-03-05 at 19:19 from [dzone.com](https://dzone.com/articles/build-or-buy-the-eternal-it-question?edition=366203&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-05)_

Discover when your data grows or your application performance demands increase, [MongoDB Atlas](https://dzone.com/go?i=270426&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Fgeneral%3Futm_medium%3Ddzone-synd%26utm_source%3Ddzone%26utm_content%3Dad1%26jmp%3Ddzone-ref) allows you to scale out your deployment with an automated sharding process that ensures zero application downtime.

I have been thinking a lot about the idea of "Build or Buy" in regards to systems for IT solutions. What do I mean by "Build or Buy" exactly?

### **Build**

Build an IT solution based on your team putting together the parts required. Common examples are building a custom database or storage systems for your application. These solutions are typically within the (public or private) cloud or can be hosted on-premise.

### **Buy**

Use a "as-a-Service" solution from a public cloud provider that abstracts the need for management of your IT infrastructure. You can allow the vendor to ensure the uptime and security while you focus on application development. Common examples are using services like [MongoDB's Atlas](https://www.mongodb.com/cloud/atlas) or the AWS S3 service. These are easy to begin working with because they require no capital expense and are typically ready to use in minutes. I posed the question to someone who's talked about this subject a lot lately, [Kelsey Hightower](https://twitter.com/jaydestro/status/965999841997357058), of Google.

> I advocate for both. When what's for sale does not work, then you will have no choice but to build it. Coming to that conclusion is the hard part.
> 
> -- Kelsey Hightower (@kelseyhightower) [February 20, 2018](https://twitter.com/kelseyhightower/status/966000517892554752?ref_src=twsrc%5Etfw)

At what point do you determine you've met the limits of what a platform has available in regards to scale and resources? Additionally, when do you determine that a self-hosted solution is no longer as valuable as a Platform-as-a-Service?

### Why Build?

Building a solution for something such as data storage tends to be a common task for many teams in enterprise solutions. There are a number of concerns that major organizations tend to consider when deploying large storage arrays as well that can put pressure on a team:

  * How will we back this up?
  * Who will provide long-term maintenance?
  * Will costs remain reasonable?
  * Do we have any specific business or regulatory rules we need to be included in how we store data?

Answering these means planning out a long-term solution that includes application lifecycle, specifically, how long will you require the app this data uses to remain available?

### Why Buy?

Service-based hosting of applications has become the choice for many businesses who want to reduce their total footprint in their IT architecture. Gone are the days to requisition systems from a vendor, negotiations and lead time required for delivery. Any business can easily use a scalable solution like [MongoDB's Atlas](https://mongodb.com/atlas) or [AWS](https://aws.amazon.com/) with just a credit card. The ability to buy has reduced the time it takes to deliver applications. This change to "buy" has also put many other options in the hands of developers:

  * Self-service via APIs or GUI based interfaces.
  * Self-remedying failure response
  * Alerting.
  * Automated processes to handle common administration tasks.
  * Using a scalable solution (both scaling up and down).

### What's Going To Work For Me?

These are just a few reasons why businesses and developers turn to services to host their applications. Your use case will ultimately require you to put into a plan all of the potential risks using either solution will present. There is a valid point to state that you really should buy until it becomes evident it's time to build. This is one of the reasons to avoid service vendor lock-in when selecting technologies to leverage when building apps.

**Tips**:

  * Consider open formats like JSON to store your data that translate to many different languages.
  * If selecting a service, ensure that the vendor will permit your data to others if your situation changes. (costs, competition, credits)
  * Make checklists and document the architecture of your systems regardless of their hosting for future growth and scale.
  * Only use what your team can support.

That last tip is a critical one; what do I mean? Well, don't go for an on-premise solution if you do not have the staffing or the funds to handle hands-on support. Don't use a cloud solution if you haven't validated that the data you have is permitted to be within this environment.

I hope I gave you some thoughts on whether buying or building your next big IT solution. Feel free to contact me in the comments with any questions or comments.

[MongoDB Atlas](https://dzone.com/go?i=270427&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Fgeneral%3Futm_medium%3Ddzone-synd%26utm_source%3Ddzone%26utm_content%3Da2%26jmp%3Ddzone-ref) is the easiest way to run the fastest-growing database for modern applications -- no installation, setup, or configuration required. Easily live migrate an existing workload or start with 512MB of storage for free.

Opinions expressed by DZone contributors are their own.
