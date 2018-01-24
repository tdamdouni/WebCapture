# Estimating a Software Project

_Captured: 2017-11-28 at 09:57 from [dzone.com](https://dzone.com/articles/estimating-a-software-project?edition=337920&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-27)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

![](https://www.objectstyle.com/f/blog_posts/estimate-software-project.png)

### Intro

Based on the type of planning done, software projects roughly fall into three categories:

  * Short- to mid-term **fixed price** projects.
  * Long-term **fixed price** projects (that usually follow the traditional Waterfall methodology).
  * Open-ended projects with **hourly rates** for engineering staff (projects in which we estimate "time and material").

This post will be most relevant to those who have the first type of projects.

### Prerequisites

When asking for your project to be estimated, be ready to answer the following questions:

#### 1\. What Real-World Problem Does Your Product Solve?

The mistake some businesses make is that they talk about the product they want to build, but not about the problem it solves. For example, saying that you want "a medical portal for your city" is not very helpful while saying that you want "a portal that helps people compare medical offices and find the best offering" is much better.

#### 2\. Who Is the App for and Where Will it Be Deployed?

Where are the users geographically, and how many users are you planning to have? What browsers do they use? Where will the app be deployed (on a server or in the cloud)? These are important questions to answer, as the answers may affect the architecture and server-side setup of your application.

#### 3\. Do You Have UI Sketches of the Product?

In the ideal world, you would have a mockup of the product you want to build. There are many [wireframing tools](https://www.objectstyle.com/software-development/software-prototyping-wireframing-tools-comparison) that can help you prepare one.

Why is this helpful? Seldom do non-techy people bother to read the specifications. It's much easier for them to look at the screens of their future app when discussing the features. Having the wireframes ensures everyone is on the same page and makes the estimate more accurate.

#### 4\. What Are the Functional Requirements?

Functional requirements have to do with your product features, business goals, and target market. Functional requirements may come in the form of:

  * User Stories or Use Cases (when the project is still being estimated, these are very high-level).
  * UI sketches (we discussed them in the previous paragraph; when available, UI sketches also provide information about the requirements).

**The more complete your requirements are, the more accurate the project estimate will be.** It helps if you have a business analyst who can go over the requirements with you on one end and with your software vendor on the other.

#### 5\. What Are the Non-Functional Requirements?

Non-functional requirements are project specifics that are not directly linked to product features. These include security, reliability (fault tolerance), performance, multi-language support, scalability, maintainability, and other requirements to the system that could increase the final estimate.

The choice of platform largely depends on them. For instance, Java allows you to build applications that are secure and scalable. Scala, in turn, is a great choice for multithreaded programming.

The code lines disparity that exists between different languages explains **why your estimate may vary dramatically** depending on the technology used. Newer-generation programming languages tend to take fewer lines of code. For example, _Assembler_ and _C_ are 2nd-generation languages. There's also _C++_ and _Java_ (3rd gen), _.NET_ and _JavaScript_ (4th gen). If you turn to a company that works with C or C++, you may get an estimate that's twice the quote from a company that works with Java.

The five prerequisites we just discussed are often described in a so-called [Vision and Scope document](https://www.stellman-greene.com/about/applied-software-project-management/applied-software-project-management-software-project-planning-practices/#Vision_and_Scope_Document), which is prepared by the Project Manager. So, if you have a PM who can put together this document for you, you'll probably have answers to these questions.

### Estimating the Project

Now it's time for a vendor representative to look at the data you have provided: requirements, wireframes, project description, etc.

Like I said earlier, this person will **first try to determine the risks** \- something atypical that requires further investigation, including non-functional requirements, integrations with third-party systems, and other tricky cases.

When the risks have been determined and the vendor is left with just the bare features to examine, they may take any of the following approaches:

#### Estimating From Experience

Some projects are typical and straightforward (e.g. static-content websites or out-of-the-box system deployments), and it's not hard to predict what it'll take to deliver them. If that's the case, the estimate will likely be quite accurate. Then sticking to the agreed plan is all it takes for the project to be completed on time.

#### Functional Analysis

Functional analysis became popular in the '80s when IBM analyzed a large corpus of software requirements that were mapped to product features. Each feature was assigned "functional points," and the number of points it got indicated its complexity (e.g., a mediocre feature could get 3 points, while a tough-to-implement feature could get 6 points).

It was discovered that there's a strong correlation between the number of functional points in a feature and the number of code lines used to implement it. There are also statistics on how programming languages compare in terms of code length. Combining these data allows us to estimate how long it takes to implement a functional point on average in a given language.

Closely related to functional analysis is **Work Breakdown Structure** (WBS) analysis. In pre-sales, it's common practice to prepare a WBS doc that is essentially a 2-level list of (1) system components, and (2) features included in those components.

A WBS document includes both functional and non-functional requirements. Each feature on the list is estimated (in hours) by each team member involved. The developer, the QA, the designer, and the business analyst each give their estimate independently, and a final estimate is prepared based on those individual votes.

If you're curious what a WBS doc looks like, here's an example.

![](https://www.objectstyle.com/f/blog_posts/work-breakdown-structure-example.png)

> _Reasons for Inaccurate Estimates_

According to statistics, 50% of projects exceed the original estimate by 50%. This could be for different reasons.

#### The Project Is too Large to Be Estimated Accurately

Some projects take too long to be estimated correctly at the onset. For such projects, it's important to revise your estimate from time to time.

#### Blind Spots in the Work Scope

It may be the case that non-functional requirements were not considered, or that some risks have been overlooked. Also, some people have a sloppy attitude towards preparing the requirements, which may lead to nagging details surfacing later in the project.

#### Poor Expectations Management

When you're just starting out, it's essential to set the priorities and determine which features must be completed before the deadline and which features can wait. Developers tend to be perfectionists. You may want them to ship an 80% working feature **on time** \- even if it has minor bugs - but the developer wants to take their time and polish the feature. That's when the management needs to choose whether to enforce deadlines and curb developer perfectionism or not.

#### Poor Project Management

Those who are not familiar with the development process sometimes have a costly misconception about it. They believe that if a project is said to take 2 man-months, you can slice and dice it in any way you want:

  * 2 people working for 1 month.
  * 1 person working for 2 months,
  * 4 people working for 0.5 months.

In practice, the ability to allocate resources in such an arbitrary fashion is a myth - which is discussed at length in [The Mythical Man-Month: Essays on Software Engineering](https://www.amazon.com/Mythical-Man-Month-Software-Engineering-Anniversary/dp/0201835959), a book by Frederick Brooks.

The gist of Brooks' writing is that "bringing more people to a late project only makes it later." With each newly added team member, the amount of management and communication increases, as well. Another famous quote from this book is that "it takes 9 months to make a baby, no matter how many women are assigned to the task."

#### "Scope Creep"

When project scope is not fixed, and its features are not prioritized, it may be very tempting to add a little button here and an extra form there - especially in the beginning, when the deadline is far in the future. In such cases, the project manager must stick to the plan and prioritize features according to the agreed scope. It is a good idea to make an MVP (Minimum Viable Product) that implements core features as soon as possible, and only then start adding bells and whistles to the stable core.

To sum it up, the process of estimating a project may be presented as the following flowchart:

![](https://www.objectstyle.com/f/blog_posts/project-estimation-workflow-infographic.png)

> _The key components of project estimation are:_

  * Vision and Scope.
  * Work Breakdown Structure.
  * UI mockups.
  * Estimated man-hours, costs, and deadlines.

When done right, these artifacts give solid ground for further development planning and set correct expectations for both sides - the customer and the developer.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
