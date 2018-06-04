# Enterprise DevOps: On Governance

_Captured: 2018-03-30 at 19:33 from [www.cloudbees.com](https://www.cloudbees.com/blog/enterprise-devops-governance)_

_This is the fifth in a series of blogs about enterprise DevOps. The series is co-authored by Nigel Willie, DevOps practitioner, and Sacha Labourey, CEO, CloudBees._

In a previous article we discussed [creating a standard taxonomy](https://www.cloudbees.com/blog/enterprise-devops-i-wouldn%E2%80%99t-start-here-understand-your-devops-starting-point) and from there defining your technology stack. This is an important first step; however, it is also critical that you define a process to govern request for changes to this stack.

It is a given that in the world of technology there is rapid change. It is also a given that the rate of change will only increase in the future. A technology stack that ossifies will lead to significant difficulties and lost opportunities. By the same token, an uncontrolled proliferation of solutions will lead to greater financial cost, a likely divergence in process and potentially a loss of the feedback and process control that is critical to successful DevOps. If your organization is heavily regulated, it could also lead to a reduction in auditability and the incumbent risks associated with this.

It is thus critical that a process is created to enable and govern change. This may already be in place in your organization, but in our experience once an organization starts to adopt a DevOps mindset, the rate of request for change increases and the cadence of governance decisions needs to be able to respond to this. A further consideration is that DevOps relies on practitioner empowerment. Many extant governance processes rely on central command control and this is anathema to the culture we are looking to inculcate in the organization.

Below we detail a range of considerations, and a potential approach to governance.

Within a governance board, we believe the following considerations should be represented.

  * **Governance ****chair****:** Chairs the meeting, ensures minutes are taken and discussions are documented. Is accountable for maintaining the core principles that requests are judged against. Includes any change to the core principles.
  * **Practitioner representative(s): **Presents the request(s) and represents their community.
  * **Enterprise architecture representative: **Owns the Enterprise Information Management (EIM) and acts as design authority for technology within the organization.
  * **Service line representative: **Owns the provisioning of services for those capabilities which are deemed to be centrally provisioned.
  * **Infrastructure representative:** Represents that part of the organization accountable for centralized infrastructure provisioning. Even in an organization that has fully adopted cloud, somebody will be accountable for that relationship and provisioning.
  * **Procurement representative: **It is likely you have a vendor strategy. This needs to be represented. Assists with RFP considerations if the proposed change looks to have potential to benefit the organization. You may have commercial arrangements with one vendor that are pertinent in the capability space. Larger organizations may have actually invested in a vendor (such as the automotive industry).
  * **Security representative: **Represents security considerations and ensures security is engaged at the earliest possible stage.
  * **Financial representative:** Represents whoever owns the overall budget and signs the check.
![](https://www.cloudbees.com/sites/default/files/devops-governance.png)

Please note in a large organization each consideration may be represented by a different individual. In smaller organizations, an individual may represent more than one consideration. At start up, having awareness of these considerations will assist in ensuring you create a robust and scalable process even if a single individual is involved in making the decisions.

Suggested governance board outputs:

  * This request is in line with our principles and should be centrally provisioned
  * This request is in line with our principles and should be locally provisioned
  * This request is not in line with our principles, our principles should change.
  * This request is not in line with our principles and is rejected.

Hopefully, this decision list is self-explanatory. In our view, a key consideration is decision point three. It is important that you consistently question whether your principles are correct and leave the opportunity to amend these in line with changes in circumstance and objectives. In our experience, this also stresses to the practitioners that they have a measure of control in the governance process and this helps to drive engagement and the collaborative culture that DevOps thrives upon.

The last point we wish to stress is that while all these considerations are material, any governance model has to be fit for the purpose of making robust and rational decisions rapidly. Governance is a means to an end, not an end in itself. You should constantly validate that you are not building bureaucracy and waste into this process, as boards and processes tend to mutate and bloat over time if not consistently challenged.

### Follow the series from Sacha and Nigel

### About the Authors

Nigel Willie

_With over 20 years' experience working in IT for one of the world's largest financial institutions, Nigel has experience managing and delivering global transformation programs. Starting his career as a developer, Nigel's most recent role was to deliver __cross platform__ DevOps automation capabilities to the enterprise._

_From his experience, he understands many of the challenges and mistakes involved; indeed, he claims to have made most of the mistakes himself. Nigel has also had the good fortune to work with a lot of highly skilled individuals, both as colleagues and across the industry. He is attempting to share some of his personal observations and thoughts in the hope they will be of value to others. Nigel is a great believer that every initiative is individual and any observations he makes are intended as principles or guidelines, not rules._

Sacha Labourey

_Sacha is a native of Switzerland and graduated in 1999 from EPFL. While at EPFL, he started his first consulting business - Cogito Informatique. In 2001, he joined Marc Fleury's JBoss project as a core __contributor,__ and implemented JBoss' original clustering features. Sacha went on to become GM for JBoss Europe. In this role, he led the strategy and helped to recruit the partners that fueled the company's growth in that region. In 2005, he was appointed CTO, overseeing all of JBoss engineering._

_In June 2006, JBoss was acquired by Red Hat (NYSE__:RHT__). As CTO, Sacha played a crucial role in integrating and productizing the JBoss software with Red Hat offerings. In 2007, Sacha became co-General Manager of Red Hat's middleware division. He left Red Hat in 2009 and founded CloudBees in March 2010._
