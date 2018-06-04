# Enterprise DevOps: Move to Self-Service

_Captured: 2018-03-30 at 19:32 from [dzone.com](https://dzone.com/articles/enterprise-devops-move-to-self-service?edition=371193&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-30)_

_This is the seventh in a series of blogs about enterprise DevOps. The series is co-authored by Nigel Willie, DevOps practitioner, and Sacha Labourey, CEO, CloudBees._

![](https://www.cloudbees.com/sites/default/files/the-phoenix-project.png)

Hopefully, most of you have read _The Phoenix Project._ If not, we highly recommend it. (It is actually required reading for all new CloudBees employees.) Those of you who have done so will be aware that one of the critical issues experienced by the author was a critical dependence on Brent, the key technologist, who solved everybody's problems. It becomes clear in the book that Brent, as competent as he is, is a logjam as everything passes through that one individual.

Any centralized team introduces exactly this risk. It is one of the fundamental objections that many people raise whenever the idea of a central DevOps team or function is raised. We acknowledge this is a valid concern. Our previous article on [creating a service line](https://www.cloudbees.com/blog/enterprise-devops-creating-service-line) advises some potential approaches.

Regardless of the structure, or structures, you choose it is critical that you avoid becoming a bottleneck to progress. In a large enterprise, this can be very difficult, as DevOps initiatives tend to be high profile, flagship programmes. As a result, senior stakeholders are extremely keen to demonstrate rapid progress. This, of course, is a significantly better problem to face than customer apathy! Something it sometimes pays to remind yourself as you try to keep many plates spinning.

Many vendors now deliver capabilities as services. For example, [CloudBees Jenkins Enterprise](https://www.cloudbees.com/products/cloudbees-jenkins-enterprise) provides a delivery framework that couples a level of central control and consistency with customer self-service. It also decomposes the previous architecture based around larger, shared masters to a more flexible approach based around individual team- or project-specific masters, spun up in minutes. All this supports a self-service approach to be pursued in a larger enterprise.

Whether using external or internal capabilities, we recommend that you prioritize customer self-service as a core competence. There are fundamentals that need to be completed to achieve this; exposure of services via API's, defined patterns that integrate into an end-to-end flow, templated pipelines with drag and drop capabilities, etc.

Today, many larger enterprises follow a matrixed organizational structure. We do not intend to discuss the advantages of various organizational structures in these articles, we would, however, pass on specific advice for anyone working in an organization of this type. It is a given that any service will need maintenance and upgrades. These potentially impose a short service outage. From experience, if a service is shared across business streams within the organization, agreeing on an outage can involve significant negotiation. It is human nature to believe your personal priority has primacy. In matrixed organizations, cross-business stream priority requires consensus. When architecting any service, in addition to the usual considerations (availability, scalability, service latency, etc.) it is useful to consider this factor when allocating consumers to servers, masters, availability zones, LPAR's, etc.

In short, key considerations when providing a centralized capability should be:

  * Your customers can achieve self-service of the capabilities they require wherever possible.
  * Any service should, wherever possible, consider segmentation via customer to assist prioritization discussions around outages.
  * Once the fundamental foundation has been created, your focus should be on customer experience and ease of adoption.

The role of any central IT team is to enable its customers to deliver rapidly via fully supported, consistent automation capabilities. It is not acceptable to become an impediment to progress to the entire enterprise by imposing dependencies on one group of individuals.

### Follow the Series From Sacha and Nigel

  1. Enterprise DevOps: Move to Self-Service (this post)
