# Enterprise DevOps: I Wouldn’t Start from Here - Understand Your DevOps Starting Point

_Captured: 2018-03-30 at 19:35 from [www.cloudbees.com](https://www.cloudbees.com/blog/enterprise-devops-i-wouldn%E2%80%99t-start-here-understand-your-devops-starting-point)_

_This is the second in a series of blogs about enterprise DevOps. The series is co-authored by Sacha Labourey, CEO at CloudBees, and Nigel Willie, DevOps practitioner._

There is an old joke in the UK about a couple of city dwellers driving through the countryside and becoming lost. After several minutes driving around they see a local farmer. Drawing next to him they wind down the car window.

_"Excuse me, could you tell us the best way to get to the nearest town?"_

The farmer looks at them, nods, pauses and says: _"Well if I wanted to go to town I wouldn't start from here."_

If you are introducing DevOps across a large enterprise you will probably have a lot of empathy for the farmer's view. Given an inherited technology estate, along with embedded process and practices, it is sometimes difficult to know where to start. You are also likely to inherit at least some vociferous individuals advising why current practices have to remain as they are.

We shall start by stating that it is a given that DevOps adoption revolves around creating a culture that provides support for autonomy and removing centralized command control behaviors. It is not delivering a raft of tools. That said, there is plenty of excellent content that details the concepts and behaviors required. We are not going to attempt to replicate that. Rather, in this post, we shall concentrate on providing thoughts and experiences on potential approaches to identifying an automation foundation to enable DevOps in a large established organisation.

### Create a standard taxonomy of capability

In large organizations, one of the key challenges is to ensure that a standard taxonomy is used. This assists in optimizing knowledge sharing and understanding the available solutions and experience in the enterprise. The Enterprise Architecture function should own the Enterprise Information Management (EIM) solution and it makes sense for this to detail the standard capabilities you are looking to deliver.

Defining these capabilities is critical. Technologists as a rule are better at defining solutions than requirements. By focusing on capabilities rather than solutions (or tool names) you drive a higher quality of debate. It is also easier to identify gaps. In a cross technology organization it can highlight surprising areas of strength. For example, the mainframe platform tends to have strong automated deployment capabilities which are often missed when continuous integration and automated testing is discussed.

### Define your current technology stack

The next step after defining your capability matrix is to detail the current solution(s) in each capability space. If you are fortunate, you will have an EIM solution that is comprehensive, current and already has all this information. It is more likely that your records will be, at best, partial.

In the first instance, focus on placing the current technologies in the correct categories rather than defining which solutions are valid and which are not strategic. If you can achieve a first pass quickly, this can start to drive discussions and decisions.

Stakeholder communication is also critical. While not normally a fan of duplication, you need to detail the solutions available to your engineers. Most EIM solutions are great as repositories but are not intended as communication media. We recommend an approach that enables your community to understand the options available to them within the organization. Create a page where this information is readily available. Content that you should consider linking from this page includes:

  * Capabilities
  * Solutions available for the capabilities
  * Precis of each solution
  * How to obtain access to the available solutions
  * Links to any training material
  * Links to vendor page
  * Links to social media content (stack overflow, internal blogs and forums etc.)

A good example of an easy to understand presentation of capabilities and tools is the Xebia Labs periodic table of DevOps tools.

![](https://www.cloudbees.com/sites/default/files/periodic-table-of-devops.png)

> _Figure 1: The DevOps Periodic Table of Elements_

Finally, we should consider the gray market in technology. People across the organization are likely to be using solutions to problems which are not officially recognized or documented in the EIM. There may be solutions already in the organization that will add great value at larger scale. Conversely, potential solutions may have already been tried and issues identified. A culture that encourages communication and sharing of experience and information will enable you to deliver more quickly and avoid replication of effort. Enabling others to feel they can safely share information without repercussions is key. There is obviously a balancing act between encouraging innovation and avoiding an uncontrolled proliferation of technology. In a later post, we shall talk about a potential approach to governance designed to mitigate some of these challenges.

### Follow the Enterprise DevOps blog series from Sacha and Nigel:

### About the Authors

Sacha Labourey

_Sacha is a native of Switzerland and graduated in 1999 from EPFL. While at EPFL, he started his first consulting business - Cogito Informatique. In 2001, he joined Marc Fleury's JBoss project as a core contributor, and implemented JBoss' original clustering features. Sacha went on to become GM for JBoss Europe. In this role, he led the strategy and helped to recruit the partners that fueled the company's growth in that region. In 2005, he was appointed CTO, overseeing all of JBoss engineering._

_In June 2006, JBoss was acquired by Red Hat (NYSE:RHT). As CTO, Sacha played a crucial role in integrating and productizing the JBoss software with Red Hat offerings. In 2007, Sacha became co-General Manager of Red Hat's middleware division. He left Red Hat in 2009 and founded CloudBees in March 2010._

Nigel Willie

_With over 20 years' experience working in IT for one of the world's largest financial institutions, Nigel has experience managing and delivering global transformation programs. Starting his career as a developer, Nigel's most recent role was to deliver cross-platform DevOps automation capabilities to the enterprise._

_From his experience, he understands many of the challenges and mistakes involved; indeed, he claims to have made most of the mistakes himself. Nigel has also had the good fortune to work with a lot of highly skilled individuals, both as colleagues and across the industry. He is attempting to share some of his personal observations and thoughts in the hope they will be of value to others. Nigel is a great believer that every initiative is individual and any observations he makes are intended as principles or guidelines, not rules._
