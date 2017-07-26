# A Designer’s Guide to Working with Product Managers

_Captured: 2017-02-28 at 02:26 from [uxdesign.cc](https://uxdesign.cc/a-designers-guide-to-working-with-product-managers-bcb164a473df#.qx0wdp82p)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*WbAVSnjMBKaxTYsm47_iUQ.png?q=20)![](https://cdn-images-1.medium.com/max/2000/1*WbAVSnjMBKaxTYsm47_iUQ.png)

Most organizations are structured in a way that designers work closely with Product Managers (PMs). They have an enormous say on how elements in a product function. They have the power to VETO a design decision or take a call on how a particular user-flow for a product is crafted. They are also completely involved in business needs and think about how the product has to be shaped to meet the above-mentioned needs. They think about how users interact with the product and analyze if the product meets the need of the intended target users. They help engineers prioritize the list of tasks that needs to be built. They are decision makers. They help build the roadmap and maintain/define the vision of the product.

These are a whole lot of responsibilities for one role, ain't it?

In short, they are **superstars** who work in very high-pressure environments. At any given point, there's always more on their plates than they can handle.

Designers need to work in tandem with the goals of a PM because at the end of the day, both these stakeholders have the same vision.

### Difference in thought process

To be honest, at first, I had a hard time syncing with the thought process of a PM. As designers we tend to think about the experience, the flow, how consistent the components are, how to make it better work in different resolutions, etc.

Aspects that we do not pay much attention to -- current business needs, engineering efforts being worked on, product strategy for the next few quarters to come, what's on the roadmap, resource allocation etc.

Obviously, this does not come to us instinctively which is why collaboration with a PM is a primal necessity in the product world -- it helps paint a broader picture.

After working closely with PMs for a significant amount of time, I decided to reflect and jot down methodologies that help me design with more intent.

Some of the steps I take, in no particular order --
    
    
    1. Prioritizing tasks  
    2. Maintaining a UX debt sheet  
    3. Creating a UX test plan  
    4. Tracking actions on the product 

#### 1\. Prioritizing tasks

I have noticed that bringing up topics about inconsistencies or pattern enhancement often times irked PMs. I realized this happened not because they don't want to fix it or it is unimportant to them, but because it was not _just the right time_. There is always a right time to bring up your biggest pet-peeves.

> And how do we know when is it a right time?

Well, answering this one was a little harder than I thought. What helped me was understanding the product status from a broader perspective.

I started making a note of current _business needs _and _engineering efforts_.

**Business needs **-- what needs to be done to deliver value at the earliest. Because if you don't sell, you don't have a successful business, and in effect, there is no real scope to _design _something that might not exist.

**Engineering needs** -- what needs to be done to stabilize the system so that the existing functionalities don't break. Things that need to be optimized to deliver a better experience.

Understanding engineering constraints help a lot with making design decisions. Something that works better interaction-wise might be a huge load on the system, and a trade-off has to be made to make it stable.

> What's the point of a sexy interaction when the functionality is broken?

With these two major considerations, in addition to the huge list of design changes that I wanted to work on, I started prioritizing.

Aspects of the product that required a major change usually went down in priority, and items that sent out maximum value went up the list. It helped me make peace with what I was working on.

When the time was right (believe me, this time will arrive.), I plugged the redesign ideas I had thought about. This makes the interaction with PMs productive with much lesser friction.

#### 2\. UX Debt Sheet

Almost all designers would have heard this from their PMs --

> "Let's get this out for MVP and we can get back to it later."

This had me hugely frustrated at a point because I realized the changes being made to the product were very minimal. It was not the _ideal experience _the designer in me wanted.

I feared that if we took an _always MVP_ approach, we would eventually be left with more work over time just trying to fix all the workarounds. More like an **MVP Paradox**.

Coincidentally, I noticed that the engineers had an account of technical backlog and they called it _Tech Debts. _This was an inventory of technical tasks that were pending. They dedicated a sprint to finish these tasks specifically. I thought this was a great idea and wondered if there could be an equivalent UX Debt sheet for the project I work on as well.

I had a conversation with my PM and decided to list out all the UX backlog. I chalked out a way of prioritizing tasks that can be finished by mapping it in a graph with **Impact** and **Ease of implementation **as parameters.

As you can notice there are four quadrants and the numbers represent the priority level.

**Quadrant 1 **-- tasks that are easy to implement and have a high impact. These need to be tackled first as they ship maximum value.

**Quadrant 2 **-- easy to implement but not very high impact. These need to be tackled next as _many_ small improvements snowball and help us ship a great experience.

**Quadrant 3** -- next we start dabbing at the difficult-to-implement portions of the product. It is important that when we start tackling tasks that are harder to implement, we go for the ones with maximum impact.

**Quadrant 4** -- this quadrant gets very low priority and usually never worked on. To remove this from a perennial back-burner, tasks in this quadrant can be split to subtasks and again, the process of prioritization can be applied to the subtasks as well. Working on tasks on this quadrant is quite challenging and I'm still trying to figure how to better handle these.

Next was actually having this documented somewhere so that it is not out of sight, and out of mind. The team I work with are comfortable using **JIRA **as a tool for most project tracking activities.

To bring the design priorities to better light, my PM suggested that we create a [JIRA Epic](https://confluence.atlassian.com/agile/jira-agile-user-s-guide/working-with-epics/creating-an-epic) named _UX Improvements. _This was a brilliant move. Now we have everyone on board with all the design improvements that need to see the light of the day at some point because it is out there documented with completed mocks.

Different teams have different such management tools. Our UX team uses **Trello** to maintain a list of all UX Backlogs, and I've also noticed certain engineering teams using **Basecamp** for similar needs.

#### 3\. UX Test Plan

The _design process_ for me at grad school was doing a significant amount of user-research and synthesis before actually deciding what goes on a design. This meant enough time to plan and execute the research. In an agile environment, this isn't always the case. Features are designed with certain assumptions made based on existing usage patterns and knowledge of target audience.

Most of these assumptions are validated on customer calls. It was important to create a game plan before talking to customers for validation. To get the maximum out of the 30-45 minutes we had with our customers, I tend to work with the PM to structure the customer calls.

A very simple approach to these calls was to clearly articulate what we intended to get out of the session. This is our chance to get as much information from our customer to better iterate on the product to deliver what they need.

The structure on most customer feedback calls look like --
    
    
    - Goals of the test  
    - Assumptions to be clarified  
    - Customer walkthrough of the interface  
    - Getting a sense of what they expect next 

#### **4\. Tracking actions on the product**

Existing user actions on the product are great starting points to think about redesigns. If a flow of using a feature requires a change due to technical constraints, or if existing customers had qualms about the usability, a great way to approach the redesign would be resorting to data. Analytical tools such as Google Analytics offer ways to measure drop-out rates, the sequence of actions etc but for the most part, products require much detailed tracking.

What happens when an action is clicked? Where do users go next? How do you measure the success of a feature? Such questions can be answered by tracking flows.
    
    
    A designer, to better inform their design decisions, needs to analyze and figure out _what needs to be tracked_, _why should they be tracked_, and lastly _what we aim to get out of tracking them_.

For more complex events tracking and detailed funnel analysis, tools such as [MixPanel](https://mixpanel.com/) and [Keen](https://keen.io/) offer ways to use their APIs to help us customize the very granular level of tracking. Such rich usage data helps designers take better decisions and articulate better to other stakeholders.

A designer's best friend to help with such data analysis is a PM. Product Managers have direct access to such data; some also get their feet wet with the working of such tools thereby having a bird's eye view of the usage data.

This is by no stretch an extensive guide on how designers can structure their work with Product Managers, but for sure is a step in the right direction. Product Mangers have helped me think over and above just pushing pixels. They help us prioritize and provide us with a holistic view of what we are designing for. Planning how to work with them helps in tapping the strengths of a Product Manager to create a better user experience.

I am also interested in knowing your process working with Product Managers, and I'd love to hear them in comments below :)

#### Some of the other stuff I've written:
