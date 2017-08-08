# Solution Architecture vs. Software Architecture

_Captured: 2017-08-07 at 08:21 from [dzone.com](https://dzone.com/articles/solution-architecture-vs-software-architecture?oid=twitter&utm_content=buffer54af3&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Download the blueprint](https://dzone.com/go?i=228233&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic's 20+ years of business automation experience, and the proven tools and practices the company is already leveraging.

In my tenure as a solution architect in financial services working for a global consulting firm, I've often been caught in a dilemma. This dilemma is whether to apply recognized industry standards to developing solution architecture or to leverage clients' solution architecture operational model and content. On the one hand, the value proposition of an architecture consultant is not just getting a job done, but also to help improve clients' architecture maturity. On the other hand, firms' architecture review boards are set in their ways of using their own architecture content, such as solution architecture templates and models. To my surprise, I have observed a common phenomenon in many financial firms large and small with various degrees of architecture maturity of confusing solution architecture with software architecture.

This is not meant to be an academic paper. Rather, I present my thoughts hoping that this article may help my colleagues better understand the vague differences between two similar but distinct architecture disciplines. At the very least, it'll trigger a conversation that may clear my own confusion.

_"If I Had More Time, I Would Have Written a Shorter Letter" \- Blaise Pascal._

## **Solution Architecture**

The term "solution architecture" is used to describe the process of developing, documenting, and reviewing with relevant stakeholders a multi-dimensional architecture construct that enables a specific business or operational outcome. The target architecture that enables this outcome is defined within the context of all impacted and applicable architecture domains such as business, data, application, technology, integration, security, etc. A solution architecture document will elaborate and further decompose the target architecture into architecture deliverables for each architecture domain. For example, the solution architecture for a loan application digital channel at a fictional bank to allow bank's customers to apply for a loan online will require an impact assessment of each architecture domain. Each domain will address the needs and concerns of the impacted stakeholders who are bound by that domain such as business, technology, operational, risk, legal, etc…

![Image title](https://dzone.com/storage/temp/6166458-solution-architecture.png)

> _Let's try to segregate some of these concerns into specific architecture domains:_

  * **Business Architecture:** How does a customer apply for a loan online?
  * **Data Architecture**: What information is needed to enable loan risk assessment and processing? How to manage customer info with maximum security, integrity and optimal cost, performance, reliability, consistency?
  * **Application Architecture**: What UX, process management, and functional system components/services are needed to enable customer loan application via mobile and web devices?
  * **Integration Architecture**: How will the distributed application component and services talk to each other?
  * **Security Architecture**: How to properly verify and authenticate customer identity? How to ensure that customer data is secure in a distributed environment? How to prevent unauthorized data access and data theft over the wire?
  * **Technology Architecture**: How to configure supporting infrastructure for high availability and recoverability in case of system or facility failure?
  * **DevOps Architecture**: How to enable rapid product delivery and continuous maintenance?

The solution architecture that best addresses these concerns will be derived by applying a formal architecture development process and incorporating established organization's architecture principles and reference architecture in order to define the most optimal technology solution that delivers the desired business outcome. The solution architecture must be well documented and presented to the project and architecture review boards to ensure that it satisfies the project constraints and technology standards established by the enterprise/chief architect.

The figure above is a sample of a few common solution architecture diagrams for a loan application use case. Please note that the actual solution architecture document will also contain a detail description of each domain target architecture and gaps. Other architecture artifacts such as catalogs and matrices may be used.

### **Software Architecture**

Once the solution architecture is defined, reviewed, and approved, software architecture can now be developed as part of the Design or Architectural Runway SDLC phase. The primary focus of software architecture is to define and document software structure and behavior in order to enable software engineering and delivery based on known functional and non-functional requirements. This is quite different from the goal of solution architecture, which is to define app, data, infra architecture building blocks, dependencies, and address all relevant stakeholders' concerns. Software architect, usually also a technology SME, will use architecture styles, object oriented analysis and software design patterns to design client and server side software components that implement the web/mobile customer experience (CX), process management, functional and data management application architecture blocks defined in the solution architecture document. As I mentioned, the focus of software architecture is to enable application development and delivery. The software engineering diagrams that I found most useful in my days as a software architect are the domain object model class, service component, sequence, and deployment diagrams.

![Image title](https://dzone.com/storage/temp/6166459-software-architecture.png)

> _Image title_

  * **Domain Object Model Class Diagram** is essential in defining a consistent data format for information management, persistence, and sharing.

  * **Services Component Diagram** breaks down system functional services into self-contained API components that can be implemented as microservices
  * **Sequence Diagram** demonstrates how software modules and distributed components integrate with one another in a context of each use case.
  * **Deployment Diagram** is necessary to demonstrate software deployment on compute and middleware infrastructure in order to engineer a DevOps pipeline, manage software/infrastructure dependencies, and design for performance and failure

I hope I was able to demonstrate that solution and software architecture are two distinct disciplines with different purposes and sets of stakeholders. Can a solution architect be a software architect and vice versa? In my opinion, a good solution architect is also a software architect. A great solution architect knows when solution or software architecture is appropriate.

I welcome your thoughts and feedback.

**Disclaimer**: The solution and software architecture artifacts used in this article have been exclusively created for this article. They do not represent or reflect any proprietary information I've worked with on any current or prior projects.

**References:**

[AWS Web Application Hosting Architecture](http://media.amazonwebservices.com/architecturecenter/AWS_ac_ra_web_01.pdf)

[Download](https://dzone.com/go?i=228234&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) the 'Practical Blueprint to Continuous Delivery' to learn how Automic Release Automation can help you begin or continue your company's digital transformation.
