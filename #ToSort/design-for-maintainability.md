# Design for Maintainability

_Captured: 2018-04-03 at 18:37 from [dzone.com](https://dzone.com/articles/design-for-maintainability?edition=371203&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202018-04-03)_

**The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=275424&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dfooter). Learn how DevOps and SAFe® can be used either separately or in unison as a way to make your organization more efficient, more effective, and more successful in our [SAFe® vs DevOps eBook](https://dzone.com/go?i=275424&u=http%3A%2F%2Fpages.aspeinc.com%2FSAFe-vs-DevOps.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Dsafe_vs_devops%26utm_content%3Debook).**

![Build your momentum, and go away of being a sponge-bob. Be like a gear.](https://dzone.com/storage/temp/8518884-maxresdefault.jpg)

> _Build your momentum, and go away of being a sponge-bob. Be like a gear._

There are many attributes to design for; however, to understand the beauty of programming, you must practice the techniques that come with Maintainability.

#### Let's start with a few examples:

• When you want to add a logging feature in some layer/place and this will be achieved by modifying one place or couple of places.

• When that logging feature needs to be changed and all you should do is to drop the new logic in a specific path, change a configuration file, and restart the application if needed.

• When you want to extend a completed and operational functionality, and all you should do is add this new reference to your solution.

## What Maintainability Means

It means many concepts and techniques. It means extensibility, modularity, reusability, pluggability, readability, clean code, separation-of-concern, and SOLID principles.

When we build a large software, we are thinking of it as tower-building: the more we expand in-depth and horizontally, the more we can expand vertically, and we have a strong base that can support the upcoming expansions.

For me, the Redundancy-Elimination as motivation is enough to apply the M; it leads me to develop many reusable components. It leads me to use the following techniques:

  * Polymorphism (Late-binding)
  * Generic classes/methods
  * Delegates
  * Events (Pub-Sub)
  * Reflection (Dynamic-programming)
  * Custom attributes
  * Extension Methods

## Design a Skeleton with Joints for Pluggability

![Pluggability](https://media.licdn.com/dms/image/C5612AQEPp7oTNo8QBQ/article-inline_image-shrink_1000_1488/0?e=2120407200&v=alpha&t=moUynGcSqZWJVaVKd9W73_P08hmgQ190s0kLlfZzUVo)

## What Does "Design Skills" Mean?

  * Assess design/architecture
  * Ability to Refactor.
  * Guarding design
  * Developing a UML diagrams and technical documentations.

### What Practices Will Help You Promote Your Software in the Maintainability Scale?

  * Improve readability by writing a Clean-Code and following code standardization
  * Well understanding of the code context witch you are going to add and layers roles, so you will add the logic in the right place.

## Code-Context Dimensions

  * Is it Client or Server side?
  * Is it Technical or Business?
  * If technical, is it functional or non-functional?
  * Is the new code relates to Abstraction or Implementation / Concrete?
  * Is it PL, BL or DAL?
  * Is it a schema definition or operational?

## Other Attributes

There are many advantages that come when you are designing for Availability, Reliability, and Scalability. With them you feel--in some situation--like that the "system" has a soul, like it's is reacting. Testability is an important software attribute; it becomes a development driver with TDD.

The ROI of Maintainability as you see comes here in shortened time, effort, and cost.

There no excuse to not write a well-designed code.

Whenever you are a developer, you are a designer. Remember, don't just be a technologist.

**Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F). **

Opinions expressed by DZone contributors are their own.
