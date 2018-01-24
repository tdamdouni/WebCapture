# Design Rules to Manage Software Architecture

_Captured: 2018-01-08 at 06:06 from [dzone.com](https://dzone.com/articles/design-rules-to-manage-software-architecture?edition=351091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-07)_

The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266428&u=http%3A%2F%2Fwww.techtowntraining.com%2F). Understand how your role fits into your organization's DevOps transformation with our [DevOps eBook](https://dzone.com/go?i=266428&u=http%3A%2F%2Fpages.aspeinc.com%2Fdevops-enterprise-ebook.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Ddevebook).

In _[Design Rules, The Power of Modularity](https://mitpress.mit.edu/books/design-rules),_ Carliss Y. Baldwin and Kim B. Clark argue the computer hardware industry has grown so quickly because of modularity, the building of complex products by breaking the functionality into smaller subsystems that are designed to work independently, yet can be used as building blocks to create a whole product. The key to this modularity is the use of design rules that must be followed and that allow designers (and software developers) to creatively solve complex problems. Design rules are also key to the computer software industry.

## What Are Design Rules?

Design rules are a way to specify the allowed nature of the relationship between various subsystems. Design rules have two purposes:

  * Flag architectural errors that erode the architecture over time.
  * Capture critical changes to the architecture that might necessitate further changes to the system as a whole or to how subsystems interact with each other.

There are many benefits to design rules. Design rules are an easy way for the software architecture to be communicated to the entire development team. With clearly defined design rules, new developers can come up to speed quickly on how the software is supposed to work and how they should structure their code. When design rules are monitored, tight scheduling does not erode the architecture and, if it does, the consequences of time pressure can be tracked ([architectural technical debt](https://www.sei.cmu.edu/architecture/research/arch_tech_debt/)) and monitored.

Design rules make managing large, complex software systems easier because there are clear rules on how different elements can and cannot interact. Distributed teams (outsourcing, offshoring) can be counted on to produce higher quality code because they have rules to follow. Without design rules, it is impossible to manage the long-term health and maintainability of the software.

## Consequences of Not Implementing Design Rules

Software architecture degrades over time with successive revisions. This is typically called [architecture erosion](http://lattix.com/blog/2017/03/31/architecture-erosion-agile-development). This happens because of the development team's inability to communicate and enforce architectural intent in the software, i.e. not implementing design rules. Without clear rules, developers can and will change the software with unintended consequences.

Architecture erosion also leads to maintainability issues. Bad dependencies are introduced which leads to code that is hard to understand and change. This is typically referred to as brittle code. Some of the other consequences of a lack of design rules include lower reliability, less modularity, lower performance, and lower interoperability. Design rules give actionable insight into violations of the intended architecture that are a consequence of normal development.

## How to Implement Design Rules

The first step is finding an easy way to communicate the architecture to the entire team. Architecture diagrams communicate important aspects of the model. We recommend using a mixture of the dependency structure matrix ([DSM](https://www.youtube.com/watch?v=4cL4xoy7cMc&t=), below left) and conceptual architecture diagrams ([CAD](https://www.youtube.com/watch?v=XFyh9rD1OV8&t=), below right). The DSM is a simple, compact, and visual representation of a system or project in the form of a square matrix. This is a good way of getting an understanding of the the entire software project in one view. DSMs are also a powerful way of setting and visualizing design rules. They make it easy to pinpoint violations to design rules. The CAD is a good way of looking at a smaller, more manageable subsystems because it is a simple diagram which is easily understood by managers, users, and business stakeholders.

![Design Rules: Dependency Structure Matrix and CAD](http://lattix.com/files/images/products/Nx172xdsm,P20cad,P20combo.PNG.pagespeed.ic.Sjvtr8z2mK@2x.png)

Once you understand your architecture, you need a way to enforce it with build-time checking and reporting. Here's a white paper on how Lattix does this: "[The Lattix Approach: Design Rules to Manage Software Architecture"](http://lattix.com/files/wp/DesignRules.pdf).

When you are creating design rules, the things that you want to enforce are:

  * Placement of UI, business, and data logic
  * Use of infrastructure or util modules
  * Design standards
  * Layered architecture

You need a process to evolve (update) the architecture when required. Sometimes you will be adjusting the architecture ahead of development and sometimes you will be changing the architecture during development as new information becomes available.

## Conclusion

The goal of using design rules to manage software architecture is to keep the code clean and consistent. This will allow you to keep maintenance costs down over the entire lifecycle of the product. This is especially important because, as the product evolves, new team members will be introduced and new business requirements will be needed that were not thought of in the original architecture. With design rules, this product evolution can be handled efficiently. If you are interested in trying out the "[Lattix Approach"](http://lattix.com/lattix-and-continuous-integration) to design rules, sign up for a [trial](http://lattix.com/download-form).

Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F).

Topics:

software architecture ,software application development ,architecture and design ,agile ,design rules

![](https://dz2cdn1.dzone.com/storage/rc-covers/7391100-dzone-aicover.jpg)
