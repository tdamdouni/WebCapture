# Enterprise DevOps: Creating a Service Line

_Captured: 2018-03-30 at 19:34 from [www.cloudbees.com](https://www.cloudbees.com/blog/enterprise-devops-creating-service-line)_

_This is the fourth in a series of blogs about enterprise DevOps. The series is co-authored by Sacha Labourey, CEO, CloudBees, and Nigel Willie, DevOps practitioner._

[In a previous article](https://www.cloudbees.com/blog/enterprise-devops-i-wouldn%E2%80%99t-start-here-understand-your-devops-starting-point), we discussed creating a taxonomy and from there, listing those capabilities you already offer or wish to offer in the future. The next area we wish to address is possible mechanisms for delivering automation capabilities to the technicians.

In the simplest use case, in terms of organizational complexity, we could consider a small start-up or single product team. In this circumstance, it is possible that the product team owns the automation pipeline themselves, from selection to creation or procurement of the solutions used throughout the software delivery pipeline. In our experience, as an organization moves toward enterprise size, organizational complexity starts to impinge upon the ideal of each team owning and maintaining their own tool chain. Across an enterprise this can lead to increased cost, complexity and proliferation, as discussed in our earlier article.

In this article, we shall discuss a couple of alternative approaches, together with some high-level considerations if the approaches are pursued.

![](https://www.cloudbees.com/sites/default/files/devops-service-line-approaches.png)

> _Figure 1: Potential service line approaches_

**Product line team**  
Within the enterprise, you are likely to have a series of product lines (or at a larger level, business streams). For example, in the financial world an organization could have wealth management, insurance, analytics and HR business lines with separate IT leads. A common emerging pattern is that within these business streams a DevOps automation service line is created. This service line is tasked with identifying, delivering and supporting the automation pipeline for the business stream in question.

The advantages of this approach are that the service line tends to be closer to the customer (something that is a core pillar of the agile approach to delivery). Additionally, a service line within the business stream is less likely to have to juggle priorities and thus speed of delivery can often be improved.

The potential disadvantages that have to be guarded against are similar to that with product level teams; there is a risk of divergence of solutions and process between business lines, silos can be created and opportunities for cross-enterprise knowledge sharing and symbiotic relationships are lost.

**Cross-product line team**  
It is possible to create a central team tasked with providing automation solutions as a service across the enterprise. The rationale being that this enables the business lines to concentrate on delivering business value while consuming a consistent set of automation capabilities that are cross-funded by all business lines.

The advantages of this approach is that it drives consistency, which can lead to all business lines benefiting from best practices. In addition, this can lead to financial savings, as economies of scale can be realized both in terms of infrastructure and resource costs but also potentially in vendor negotiations. This approach can also build expertise rapidly by focusing on core enterprise scalable capabilities.

The disadvantages range from the risk of a centralized team losing touch with their customers and becoming remote, the feeling that solutions are imposed from above, a failure to react quickly enough to bespoke requests or requests that are critical to a niche audience. When most literature currently promotes autonomy and localization, a central team can seem an oxymoron. That said, many organizations are moving to public cloud provisioning, which is fundamentally a centralized approach, just one that has been outsourced from the enterprise.

**What do we recommend?**  
The correct approach to take is often a source of heated debate in many online forums and interest groups. It is our view that there is no definitive correct answer. Instead, the challenges and current structure of the enterprise should be considered rather than an orthodoxy chosen and imposed on all models.

It is very likely that a hybrid approach works for many companies with product teams supporting the solutions that are specific to them (a niche IDE for example), with product lines sometimes supporting products critical to all teams within their product line. For example, the analytics team could support specific Big Data tooling solutions. Finally, some products make sense to be centrally supported - SCM's are a good example of this.

What is critical is that a robust and lightweight governance process is in place. We shall discuss a potential approach to this in our next article.

**Setting the boundaries**  
Finally, whatever approach is chosen in terms of structure, it is critical that the boundaries of the service lines are clearly articulated. If this is not done, you risk experiencing a phenomenon we shall call "centralized autonomy." Technicians can fall into the trap of expecting a service to be provided and supported and to be allowed full autonomy to do whatever they want with this service - but then expect the central team to troubleshoot and resolve problems with their artifacts, as the artifacts are sitting on a provided pipeline or service. One possible approach we have seen is pipelines being offered with various flavors of customer autonomy and service levels set to reflect this. This can range from "If the service is down, we shall ensure it is back again," at the lowest level to "If you use the supplied pipeline in vanilla state we shall provide full support with a resolution time of…"

### Follow the series from Sacha and Nigel

### About the Authors

Sacha Labourey

_Sacha is a native of Switzerland and graduated in 1999 from EPFL. While at EPFL, he started his first consulting business - Cogito Informatique. In 2001, he joined Marc Fleury's JBoss project as a core contributor, and implemented JBoss' original clustering features. Sacha went on to become GM for JBoss Europe. In this role, he led the strategy and helped to recruit the partners that fueled the company's growth in that region. In 2005, he was appointed CTO, overseeing all of JBoss engineering._

_In June 2006, JBoss was acquired by Red Hat (NYSE:RHT). As CTO, Sacha played a crucial role in integrating and productizing the JBoss software with Red Hat offerings. In 2007, Sacha became co-General Manager of Red Hat's middleware division. He left Red Hat in 2009 and founded CloudBees in March 2010._

Nigel Willie

_With over 20 years' experience working in IT for one of the world's largest financial institutions, Nigel has experience managing and delivering global transformation programs. Starting his career as a developer, Nigel's most recent role was to deliver cross-platform DevOps automation capabilities to the enterprise._

_From his experience, he understands many of the challenges and mistakes involved; indeed, he claims to have made most of the mistakes himself. Nigel has also had the good fortune to work with a lot of highly skilled individuals, both as colleagues and across the industry. He is attempting to share some of his personal observations and thoughts in the hope they will be of value to others. Nigel is a great believer that every initiative is individual and any observations he makes are intended as principles or guidelines, not rules._
