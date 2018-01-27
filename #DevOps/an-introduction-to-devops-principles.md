# An Introduction to DevOps Principles

_Captured: 2018-01-26 at 18:25 from [dzone.com](https://dzone.com/articles/an-introduction-to-devops-principles?edition=355142&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-01-26)_

**Best practices for [getting to continuous deployment](https://dzone.com/go?i=268427&u=https%3A%2F%2Finfo.rainforestqa.com%2Febook-getting-to-continuous-deployment%3Futm_campaign%3Dgetting-to-continuous-deployment%26utm_medium%3Ddisplay%26utm_source%3Ddzone) faster and with dramatic results in reduced outage minutes, development costs, and QA testing cycles. Brought to you by [Rainforest QA](https://dzone.com/go?i=268427&u=https%3A%2F%2Fwww.rainforestqa.com%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone).**

[This article is featured in the new DZone Guide to DevOps. Get your free copy for more insightful articles, industry statistics, and more! ](https://dzone.com/guides/devops-culture-and-process)

DevOps is a set of practices (not only tools) that aim to apply the lean concepts of the manufacturing world to the software world. At the heart of DevOps are the **Three Ways**:

  * The principles of Flow, which accelerate the delivery of work from Development, to Operations, to our customers;

  * The principles of Feedback, which enable us to create ever safer systems of work;

  * The principles of Continual Learning and experimentation, which foster a high-trust culture and a scientific approach to organizational improvement as part of our daily work.

If we follow these Ways, change will happen. I'm not saying that's easy.We're going to face every kind of difficulty: from the technical to the psychological. Our team has to strive every day to make this change happen. What you have to do is to commit to the Three Ways with small changes that provide quick feedback (think about days or weeks, not months) over and over again. This process will never stop, your team will be always improving in some aspects of their daily work.

## A Brief History

DevOps and its resulting technical, architectural, and cultural practices represent the sum of many management methodologies. DevOpsresulted from a number of movements and this shows an amazing progression of thinking and unlikely connections. There are decades of hard-learned lessons from manufacturing, high-reliability organizations,high-trust management models, and others that have contributed to the DevOps state of the art today.

DevOps is the result of applying the best-practices from the most trusted principles of the physical manufacturing world to the IT value stream.DevOps has its foundation on Lean, the Theory Of Constraints, the Toyota Production System, and many others. Other valuable contexts thatDevOps draws from include management culture and organizational change management. The result is world-class reliability, stability, and security at lower cost and effort; and accelerated flow and reliability throughout the tech value stream, including Product Management.

## The Lean Movement

Lean principles focus on how to create value for the customer through systems by creating flow and pull processes (versus push), moving quality closer to the source, leading with humility, and respecting every individual.

## The Agile Movement

Agile software development describes a set of values and principles for software development under which requirements and solutions evolve through the collaborative effort of self-organizing cross-functional teams.

The term "agile" became famous thanks to the manifesto for agile software development that was created in 2001 by seventeen of the leading thinkers in software development. They wanted to create a lightweight set of rules and principles against other software development processes like waterfall development. One of the main principles is "delivering working software frequently, from a couple of months to a couple of weeks."

## The Continuous Delivery Movement

Continuous Delivery (CD) is a software engineering approach in which teams produce software in short cycles, ensuring that the software can be reliably released at any time. Built upon the discipline of continuous build, testing, and integration, the concept of Continuous Delivery defines the role of a deployment pipeline to ensure that code and infrastructure are always in a deployable state, and that all code checked in to master can be safely deployed into production.

## The Manufacturing Value Stream

One of the fundamental concepts in Lean is the value stream. To better understand, we'll use some examples for the manufacturing world and then we'll extrapolate the concepts for our tech ecosystem.The value stream can be defined as the sequence of activities an organization undertakes to deliver upon a customer request, including the flow of information and material.

In manufacturing operations, the value stream is often easy to see and observe: it starts when a customer order is received and the raw materials are released onto the plant floor. In any value stream, there is usually a constant focus on creating a smooth flow of work (the first way of DevOps), using techniques such as small batch sizes, reducing work in process, and reducing rework.

## The Technology Value Stream

The same principles apply to the tech world. With DevOps, we typically define our technology value stream as the process required to convert a feature or change request into a technology-enabled service that delivers value to the end-user.

The input of our process is the formulation of a business concept or a customer request and starts when we accept the work in Development, writing it to our backlog.

Then, Development teams that follow a typical Agile or iterative process will transform that idea into some sort of specification, which is then implemented in the source code. The code is then checked in to the version control where each change is integrated and tested (with automation in the process) with the rest of the software system.

Because value is created only when our services are live in production, we must ensure that we are not only delivering fast flow, but also that our deployment can also be performed without causing service outages or security or compliance failures.

## Key Concepts and Metrics of DevOps

### Focus on Deployment Lead Time

The deployment lead time is a subset of the whole value stream. It starts when any engineer in our value stream pushes the change into version control and ends when that change is successfully running in production, providing value to the customer and generating useful feedback and telemetry.

Instead of large batches of work being processed sequentially through design and development and then through the test and operations value stream, our goal is to have testing and operations happening simultaneously with design and development, enabling fast flow and high quality.This method succeeds when we work in small batches and build quality into every part of our process.

### Lead Time and Process Time

In the Lean philosophy, lead time is one of two measures commonly used to measure performance, with the other being processing time.The lead time clock starts when the request is made and ends when it is fulfilled, the process time clock starts only when we begin work on the customer request - it omits the time that the work is in a queue, waiting to be processed. Because lead time is what the customer experiences, we typically focus our process improvement attention there instead of on process time. However, the proportion of process time to lead timeservers as an important measure of efficiency.

### The DevOps Ideal: Deployment Lead Times of Minutes

In the DevOps ideal, developers receive fast, constant feedback on their work, which enables them to quickly and independently implement, integrate, and validate their code, and have the code deployed into the production environment.

Teams achieve this by continually checking small code changes into a version control repository, performing automated and exploratory testing against it, and deploying it into production (automatically or with manual approval). This enables us to have a high probability that our changes will operate as designed in production and that any problems can be quickly detected and corrected.

In this ideal DevOps process, our deployment lead time is measured in minutes or, in the worst case, hours.

### Observing %C/A as a Measure of Rework

Another key metric in the technology value stream is percent complete and accurate (%C/A). This metric measures the quality of the output of each step in the process. It can be obtained by asking the customers that sit at our left what percentage of the time they receive work that is "usable as-is," meaning that they can do their work without having to correct the information that was provided, add missing information that should have been supplied, or clarify information that should have and could have been clearer.

## Conclusion

There's no DevOps enterprise edition to install in our company that turns things around in a few days. DevOps is not about perfection, is about consistency. But that's the key: everything that really matters and lasts for long periods of time requires patience and hard work.

The world is full of examples where DevOps principles are winning and improving companies in every aspect. Bringing DevOps into an organization is no small task. It can create risk and starts a process of change that someone might not like. But if we start small, there's nothing to fear.When we start we must demonstrate and broadcast early wins. We must start with small goals and incremental steps. This creates trust and as we generate successes we earn the right to expand the DevOps initiative.

[This article is featured in the new DZone Guide to DevOps. Get your free copy for more insightful articles, industry statistics, and more!](https://dzone.com/guides/devops-culture-and-process)

**Discover how to [optimize your DevOps workflows](https://dzone.com/go?i=268430&u=https%3A%2F%2Finfo.rainforestqa.com%2Febook-getting-to-continuous-deployment%3Futm_campaign%3Dgetting-to-continuous-deployment%26utm_medium%3Ddisplay%26utm_source%3Ddzone) with our on-demand QA solution, brought to you in partnership with [Rainforest QA](https://dzone.com/go?i=268430&u=https%3A%2F%2Fwww.rainforestqa.com%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone). **
