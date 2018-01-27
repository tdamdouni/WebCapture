# Make or Break, Design Does Both

_Captured: 2018-01-23 at 13:48 from [dzone.com](https://dzone.com/articles/make-or-break-design-does-both?edition=355119&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202018-01-23)_

The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266428&u=http%3A%2F%2Fwww.techtowntraining.com%2F). Understand how your role fits into your organization's DevOps transformation with our [DevOps eBook](https://dzone.com/go?i=266428&u=http%3A%2F%2Fpages.aspeinc.com%2Fdevops-enterprise-ebook.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Ddevebook).

The design process is one of the most important parts of any software project. In this article, I am going to address one of the situations which might happen in an Agile project. Let's start with my experience which can help you to understand the situation. In a period of time, some components of projects became famous. This popularity happened not because they played a significant role in the application but because you can find them always in any to-do list, doing list and done list. So, it means there is always an issue or a breaking change but at the end, you could see them again in the next two Sprint with another issue. It became bothersome to see that part of the project is fragile which has always influenced the all other parts of the project. The most damage was an amount of time which team should spend on this and it was really hard in the middle of the project to start from scratch. Most team members were complaining about this situation and for a client, the most important thing was to keep production working. I think you can imagine how the situation can be chaotic like this. So, let's take a look at how we define a design process in Agile.

## Problem: Lack of Design

In Agile, we have a cycle in which you have between 1 to 4 weeks' time for each sprint and you should have a complete software development cycle in each iteration. Usually, after the analysis step, we have the design part where designers usually analyze a requirement which is defined by a user story to come up with a design and then a team will make a plan to implement it.

![Image title](https://dzone.com/storage/temp/7749987-sdlc.jpg)

In many Agile projects, the focus is mostly on delivering the product on deadline. This leads to a situation in which some of the development steps are ignored or are not covered enough and teams jump to implementation from planning without having a proper design.

Let's give an example. Suppose you are in the project which is about an international webshop and it is supporting one language at the moment but the aim is to roll out for more countries in the future. One user story is to have a form in which customer can fill personal information to make an order. The first and easy solution for the front developers team is to design a form based on the fields and then the back-end developer should implement the form with submit process. This solution is fine and fast and at the end, we have a working form, but if later we want to extend the form for another country, it means we need to have a form with a new language. Now, if you would consider this before and put it in your design, then you will just add a new language content for a new country, but if the first form is designed without considering to support multiple languages, then you have to spend a time to copy everything for a new language and you can imagine what will happen whenever you want to change the entry form. You have to change the form in all languages but if you have a base form, you can easily just change the base form and it will change for all forms which are inherited from the base.

The outcome of both processes for the end user might be the same, but maintaining the code and scaling the project can be completely different in each scenario. Now, the question is how we can tackle this problem? In what way we can be Agile and have a good design?

## Solution: Collaborative Design

The first solution that might come to your mind is to spend more time on the design process, hiring a designer or set up a design team. Of course, we need to have a UX designer or a designer in general based on the project as a member of the team but the point is how we are going to define a design process. Is that just a task of some specific members of a team or we need to extend the domain the involvement of the team? I would vote for the second; it adds more knowledge to a team and you will have a definitely better design at the end. This is a kind of collaborative manner which incorporate the entire Agile team in the design process.

![Image title](https://dzone.com/storage/temp/7764645-next-gen-workspace-collaboration.png)

Most developers are familiar with the software or tools from Atlassian group like Jira or Confluences. Recently, I found that Atlassian group has implemented collaborative design and they are getting reaping the benefits of it. I think it can be considered as one of the good practices. I came up with action points based on the way they are doing collaborative design:

  * Incorporate all **team members** in a design process

  * Engage **customers** in the design process

  * Get **designers** and **developers** close

  * **Onboarding process** for a new member

  * **Share** work progress and get **feedback**

It seems knowledge sharing is a key point to achieve these action points. In Atlassian group, by using a **customer research**, they receive **customers feedback** and apply feedback in the design process. They create **effective workshops** in which team members can split up into a smaller group and start making a design with a less stress. Team members also can share ideas with each other which helps to have a continuous improvement. There is an onboarding process for new team members. The company will pair up new designers with a buddy to get a new designer up to speed. They bring newbies into workshops in order to get to know about company's way of working and other team members.

## Make or Break, It's Your Choice

In conclusion, a design process is the most important part of any project. At the end, it's up to you to choose how you are going to achieve the design in your projects. My last word is that a good design is like a concrete foundation of a building: you can build up a skyscraper on top of it, but a bad design is like a fragile thing which leads to breaking with any change.

Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F).

Opinions expressed by DZone contributors are their own.
