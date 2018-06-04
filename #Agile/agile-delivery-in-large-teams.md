# Agile Delivery in Large Teams

_Captured: 2018-03-20 at 18:02 from [dzone.com](https://dzone.com/articles/agile-delivery-in-large-teams?edition=368209&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202018-03-20)_

**The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=275424&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dfooter). Learn how DevOps and SAFe® can be used either separately or in unison as a way to make your organization more efficient, more effective, and more successful in our [SAFe® vs DevOps eBook](https://dzone.com/go?i=275424&u=http%3A%2F%2Fpages.aspeinc.com%2FSAFe-vs-DevOps.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Dsafe_vs_devops%26utm_content%3Debook).**

Over the past year, I had the chance to be quite close to a significant project in terms of scope and team size. All in all, over 100 people were involved, with more than 60 working full time on the project.

Out of those 60 people, over 40 were involved in engineering, while the others worked as the Technical & Solution Architects, Business Analysis, User Experience Engineers, and Project Managers. Out of the 40 engineers, over 60% of the team was involved in mobile and frontend implementations while the rest were focused on backend and QA automation.

The methodology selected for the project was Agile, more specifically Scrum. Multiple teams have been assembled with Scrum of Scrums high-level sync between teams. Everything looked good and ready.

Fast forward six months, the progress looked good compared to projects similar in terms of scope and team size, well above average. Still, there were things that could've gone better at all levels.

Looking past the inherent challenges of the newly formed team and the time to find its own rhythm, the communication process within large organizations, the delays from integration with dozens of external systems and the typical overhead when managing a large team, here are some of the things we've learned, that anyone should be aware of when dealing with a similar situation:

### **Methodology Recap**

A Scrum recap before project kickoff-while the vast majority of the team members were familiar with Scrum, each had some variations in understanding the process based on personal experience. Aligning team members as well as key stakeholders before the meeting might be a useful practice before kicking off any project, regardless of its size.

### **Agile for Management**

While there are millions of articles on how to implement Agile within a team, the topic of what should stakeholders / top managers expect from Agile probably still needs more exposure. While it is usually part of the digital transformation programs or part of the whole process of making an organization Agile, setting up expectations through a very specific alignment session, can help a lot along the way: "Here what it means for you, how you will interact with the product development, how it can affect deadlines, etc."

### **Progressive DoD**

Agreeing on a Definition of Done is fundamental to successful agile. What happens, however, if the live environment is gonna be ready in 5 months? Over the course of 5 months, no user story will respect DoD, and the product owner's perception is basically that nothing is actually done.

Adopting and adapting an intermediary DoD, valid for a certain phase of the product is key to setting the right expectations. Ideally, any project should have all its environments ready before project kickoff. The reality is different and it's not just about the typical multi-stage deployment of one solution, but also the various stages of other external systems. Within this particular case, a critical external system hasn't had its staging (or live) environments ready for over more than 5 months since development kickoff.

### **Technical Governance**

When dealing with dozens of good engineers, project governance should also include a way to address the typical healthy technical tensions that can come up in time. Setting up a technical escalation point per technology from the beginning is critical in preventing the potential delays from various team dynamics. Technical leaders for mobile (iOS and/or Android), frontend, or backend should smoothen things as the project progresses.

### **System Cross-Functional Teams**

A lot of time is spent integrating with external systems. As specifications become more and more clear, API changes make team members go back and forth, and can be a headache for both the team and the agile coach. A good architectural choice is to use an SPA framework that would allow mobile and desktop versions of an application to consume the same API implementation from the backend team.

In such a case, backend and frontend (be it mobile or desktop) can often be regarded as two different systems integrating through an API. While for this project the initial choice of cross-functional teams with 1-2 Backend engineers, 1-2 iOS, 1-2 Android, 1-2 desktop-frontend seemed like a good one given the flow of the input from the Business Analysis team, as the project progressed it became clear that the delays were mostly from the back and forth communication between frontend/mobile, backend and business analysis team.

One way to optimize this is through better planning in the backlog grooming meetings, trying to get the team to agree on API signatures as early as possible.

A second way is to try and have the backend move one sprint faster than the frontend/mobile teams since, as in most cases, there are still issues when doing the actual implementation that a grooming/planning session cannot foresee. Hence, the _system cross-functional teams_ moniker. While three engineers (one iOS, one Android, and one frontend) could work on the same functionality, having the API agreed and preferably ready before the sprint starts can drastically improve the overall team efficiency.

**Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F). **

Topics:

agile best practices ,governance ,delivery team ,team management ,team organization ,agile adoption ,digital transformation
