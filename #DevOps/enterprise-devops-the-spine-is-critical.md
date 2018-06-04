# Enterprise DevOps: The Spine is Critical

_Captured: 2018-03-30 at 19:33 from [www.cloudbees.com](https://www.cloudbees.com/blog/enterprise-devops-spine-critical)_

_This is the sixth in a series of blogs about enterprise DevOps. The series is co-authored by Sacha Labourey, CEO, CloudBees, and Nigel Willie, DevOps practitioner._

In previous articles, we discussed [creating a standard taxonomy of capabilities](https://www.cloudbees.com/blog/enterprise-devops-i-wouldn%E2%80%99t-start-here-understand-your-devops-starting-point) and, from here, identifying solutions for them.

While all capabilities are critical to deliver a complete solution, it is essential that you don't focus on delivering individual solutions to your enterprise. It is not an accident that the core DevOps capabilities are prefixed continuous (integration, delivery, deployment, monitoring). To misquote George Orwell in Animal Farm: in a DevOps context "all tools are equal, but some tools are more equal than others."

From experience, it is common for most of the early requests to be for individual capabilities. For example, "We need automated test tooling," or "We need improvements to the requirements tooling solution," etc. We recommend that you avoid delivering single capability solutions without ensuring you deliver something that can be easily integrated into your pipeline, or spine.

An early visual representation of your pipeline is an extremely useful way to force this discipline on yourself. It also stresses the place of individual solutions within the larger ecosystem when discussing requirements with your stakeholders across the enterprise. The concept of a pipeline is so fundamental to DevOps that it often is taken for granted by technicians. In a larger enterprise, it is critical that assumptions are avoided and the critical dependency on integrated capabilities is made clear to all your stakeholders.

![](https://www.cloudbees.com/sites/default/files/enterprise-devops-continuous-delivery.png)

> _A continuous delivery pipeline._

We would also like to issue a caution about falling prey to the opposite problem. While you cannot deliver continuous automation using point solutions, you should also avoid delivering a tightly integrated, automated pipeline. Your technologists should be regularly hearing the message that the solutions they deliver need to move from monoliths to microservices, that they need to decouple, remove dependencies and abstract via API's. The same fundamentals apply to the delivery pipeline. Do not create a monolithic, tightly coupled pipeline but rather use API's and configuration within the enterprise automation solution. A key question when investigating potential solutions (whether homegrown, open source or vendor delivered) should be, "Does this tie me into a specific ecosystem or solution going forward or can we continue to take advantage of a variety of solutions?"

The spine of your tool chain is critical to the success of any automation initiative. Without early delivery of a robust, consistent and configurable spine, you will create significant issues for you and your customers going forward. It is always easier to architect integration into the solution than to retrofit it to extant point solutions.

### Follow the series from Sacha and Nigel

### About the Authors

Sacha Labourey

_Sacha is a native of Switzerland and graduated in 1999 from EPFL. While at EPFL, he started his first consulting business - Cogito Informatique. In 2001, he joined Marc Fleury's JBoss project as a core contributor, and implemented JBoss' original clustering features. Sacha went on to become GM for JBoss Europe. In this role, he led the strategy and helped to recruit the partners that fueled the company's growth in that region. In 2005, he was appointed CTO, overseeing all of JBoss engineering._

_In June 2006, JBoss was acquired by Red Hat (NYSE:RHT). As CTO, Sacha played a crucial role in integrating and productizing the JBoss software with Red Hat offerings. In 2007, Sacha became co-General Manager of Red Hat's middleware division. He left Red Hat in 2009 and founded CloudBees in March 2010._

Nigel Willie

_With over 20 years' experience working in IT for one of the world's largest financial institutions, Nigel has experience managing and delivering global transformation programs. Starting his career as a developer, Nigel's most recent role was to deliver cross-platform DevOps automation capabilities to the enterprise._

_From his experience, he understands many of the challenges and mistakes involved; indeed, he claims to have made most of the mistakes himself. Nigel has also had the good fortune to work with a lot of highly skilled individuals, both as colleagues and across the industry. He is attempting to share some of his personal observations and thoughts in the hope they will be of value to others. Nigel is a great believer that every initiative is individual and any observations he makes are intended as principles or guidelines, not rules._
